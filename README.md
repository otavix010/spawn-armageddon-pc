# Spawn: Armageddon — port nativo para PC

> **Projeto de fãs, sem fins lucrativos.** *Spawn* é marca registrada da Todd McFarlane Productions; o jogo *Spawn: Armageddon* foi publicado pela Namco; este projeto não tem relação com a Todd McFarlane Productions nem a Bandai Namco. Este repositório **não contém o jogo**: você precisa da **sua própria cópia** do DVD (a versão europeia, **SLES-52326**).

[English summary below](#english-summary)

## O que é

Um port **nativo** do *Spawn: Armageddon* (PlayStation 2, 2003) para Windows. Não é um emulador: o código do jogo é **traduzido para C++ e compilado** para x86-64 (recompilação estática), em cima do [PS2Recomp](https://github.com/ran-j/PS2Recomp).

Como o código do jogo não pode ser distribuído, **o seu PC gera e compila a parte do jogo a partir da sua ISO**. Um comando só faz tudo.

## Estado atual: em desenvolvimento

Já dá para ver o jogo: inicia, carrega os módulos do IOP e os sons, passa pela escolha de idioma, pela checagem do cartão de memória e pelo **menu principal** (com a arte e o logo originais) e entra na **primeira fase em 3D**, com a cidade, a catedral, o Spawn e as cenas texturizados como no PlayStation 2. **Agora roda a 60 FPS, inclusive nas cenas mais pesadas** (testado num Ryzen 7 9800X3D; usa uns 6 núcleos e mantém 60 FPS mesmo limitado a 8 threads lógicas). Os microprogramas de geometria do VU1 são traduzidos para C++ na sua máquina, a partir do executável do seu disco (a etapa "VU1" do gerador; o repositório só traz onde eles ficam: offsets e tamanhos), e a rasterização usa AVX2 em várias threads. **Agora com som** (o chip de som SPU2 é emulado: música, efeitos e ambiente) **e com os vídeos** (abertura, história e demonstração). A jogabilidade já foi testada (andar, pular, atacar, tutorial da primeira fase; 15 minutos seguidos sem travar); falta testar salvar e as fases seguintes. Por enquanto, só para testes.

## Como gerar

### Pelo Otavix Launcher

O [Otavix Launcher](https://github.com/otavix010/otavix-launcher/releases/latest) lista este port como **em desenvolvimento**: ele baixa o port, pede a ISO, gera o jogo e abre.

### À mão

**1. O que você precisa ter:** a sua cópia do *Spawn: Armageddon* **europeu** (SLES-52326, "Spawn - Armageddon (Europe) (En,Fr,De,Es,It)") como imagem **.iso** do DVD. O gerador confere o executável do jogo pelo hash: outras versões não servem, porque o mapa de funções é o da europeia.

**2. Instale as ferramentas (uma vez só)**, num terminal:
```
winget install Python.Python.3.12
winget install Microsoft.VisualStudio.2022.BuildTools --override "--quiet --wait --add Microsoft.VisualStudio.Workload.VCTools --add Microsoft.VisualStudio.Component.VC.CMake.Project --includeRecommended"
```
O resto o gerador baixa sozinho: o PS2Recomp (na versão fixada), as bibliotecas dele e, se o PC não tiver Git, o Git portátil (MinGit).

**3. Baixe este repositório** (botão *Code > Download ZIP*, ou `git clone`) e extraia numa pasta **sem espaços no caminho**, por exemplo `C:\spawn-armageddon-pc`. Deixe uns 15 GB livres nesse disco (o código traduzido e a compilação ocupam bastante).

**4. Clique duas vezes em `gerar.cmd`** e escolha a ISO. Ele:
- confere a ISO e extrai os arquivos do disco para `trabalho\disc`;
- baixa o PS2Recomp, aplica as nossas correções (`patches\`) e compila o tradutor;
- traduz o código do jogo para C++ (só no seu PC);
- compila o jogo (de 20 minutos a 1 hora, conforme o PC; precisa de 16 GB de RAM ou mais).

**5. Jogue com `jogar.cmd`.** O jogo lê os arquivos de `trabalho\disc` e a ISO no lugar onde ela estava na geração (se mudar a ISO de lugar, rode `gerar.cmd -RefazerDe 2`).

Depois de atualizar o port, `gerar.cmd -RefazerDe 3` aplica as correções novas, retraduz e recompila sem extrair o disco de novo. Com o componente "C++ Clang tools" do Visual Studio instalado, a geometria compila com o clang-cl e fica um pouco mais rápida (sem ele, usa o MSVC).

## Como funciona

- **PS2Recomp** traduz o executável do PS2 (MIPS R5900, o "Emotion Engine") para C++ e compila com o runtime dele (GS por software, VU1, DMA, IOP, áudio, cartão de memória).
- **O mapa de funções** (`jogo\ghidra_funcoes.csv`) veio de uma análise com o [Ghidra](https://ghidra-sre.org/) e a extensão [ghidra-emotionengine-reloaded](https://github.com/chaoticgd/ghidra-emotionengine-reloaded): são só endereços e nomes, nada do código do jogo. `jogo\entradas_extra.txt` lista funções chamadas só por ponteiro e alvos de tabelas de salto que a análise não marcou, e `jogo\stubs_extra.txt` as funções trocadas por respostas fixas; `jogo\stubs_tirar.txt` as que voltam a rodar o código do jogo (o som fala com o driver de som de verdade).
- **As nossas correções no PS2Recomp** (GPLv3 como ele):
  - no tradutor (`patches\recomp_otavix.patch`): os desvios BLTZ/BGEZ/BLEZ/BGTZ testam o registrador inteiro de 64 bits, como no EE (antes, a subtração de `double` por software e o `pow` davam lixo);
  - no runtime (`patches\runtime_otavix.patch`): interrupções que respeitam o `di`/`ei` do EE, pilha do `SetupThread` no topo da RAM, pilha do executável de 256 MB (o código traduzido tem funções com quadros de mais de 1 MB), pacotes internos numa área do kernel em vez do heap do jogo, callback do `sceCdCallback`, comandos SIF do EE entregues aos módulos que rodam no IOP emulado, leitura de setores direto da ISO, transferência de som EE→IOP, o chip de som SPU2 emulado no IOP (vozes ADPCM, envelopes, DMA, reverberação, saída 48 kHz), vídeos do HLE de MPEG na janela, prioridades de thread como no EE, `sceCdReadDvdDualInfo`, cache de textura invalidado nos uploads, VU1 mais rápido e ferramentas de diagnóstico;
  - na montagem (`ferramentas\monta_config.py`): as funções de `double` da libm (`pow`, `sin`, `sqrt`…) rodam o código do próprio jogo em vez dos substitutos de `float` do runtime.

## Licença e créditos

- **O nosso código** (`gerar.ps1`, `gerar.cmd`, `ferramentas\`): [MIT](LICENSE).
- **PS2Recomp** (baixado pelo gerador) e **as nossas correções nele** (`patches\`): [GPLv3](https://github.com/ran-j/PS2Recomp/blob/main/LICENSE), de ran-j e colaboradores. O executável gerado no seu PC também é GPLv3.
- *Spawn* é marca registrada da Todd McFarlane Productions; o jogo *Spawn: Armageddon* foi publicado pela Namco. Este é um projeto de fãs, sem fins lucrativos, sem relação com a Todd McFarlane Productions nem a Bandai Namco nem endossado por elas.

## English summary

A **native PC port** of *Spawn: Armageddon* (PlayStation 2, 2003) made by **static recompilation** with [PS2Recomp](https://github.com/ran-j/PS2Recomp). **Work in progress.** It reaches the 3D levels at 60 FPS, **with sound** (emulated SPU2) **and the FMV videos**.

**Bring your own game**: no game code or data here, only the function map (addresses) and translation settings. You need the **European** release (SLES-52326, Redump "Spawn - Armageddon (Europe) (En,Fr,De,Es,It)") as an **.iso**. Install Python 3.11+ and Visual Studio 2022 Build Tools with C++ and CMake (commands above), download this repository to a path without spaces, double-click **`gerar.cmd`** (it checks your ISO, extracts the disc files, fetches the pinned PS2Recomp, applies our runtime patches, translates the game code on your PC and builds it), then play with **`jogar.cmd`**.

License: our scripts are MIT; PS2Recomp and our patches to it are GPLv3. *Spawn* is a trademark of Todd McFarlane Productions; *Spawn: Armageddon* was published by Namco; this is a non-commercial fan project, not affiliated with or endorsed by Todd McFarlane Productions or Bandai Namco.
