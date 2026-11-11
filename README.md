<h1 align="center">Spawn: Armageddon — port nativo para PC</h1>

<p align="center"><i>Spawn: Armageddon (PS2, PAL SLES-52326): port nativo para PC por recompilação estática (PS2Recomp). Gera a partir da sua ISO. Em desenvolvimento.</i></p>

<p align="center">
  <a href="https://github.com/otavix010/spawn-armageddon-pc/commits/main"><img alt="Última atualização" src="https://img.shields.io/github/last-commit/otavix010/spawn-armageddon-pc?label=%C3%BAltima%20atualiza%C3%A7%C3%A3o"></a>
  <a href="https://github.com/otavix010/otavix-launcher/releases/latest"><img alt="Baixar o Otavix Launcher" src="https://img.shields.io/badge/Otavix%20Launcher-baixar-b00020"></a>
  <img alt="Windows 10/11" src="https://img.shields.io/badge/Windows-10%2F11-0078d4">
  <img alt="Linux: não suportado no momento" src="https://img.shields.io/badge/Linux-n%C3%A3o%20suportado-lightgrey">
</p>

<p align="center">
  <a href="#o-que-é">O que é</a> ·
  <a href="#estado-atual-em-desenvolvimento">Estado atual: em desenvolvimento</a> ·
  <a href="#plataformas">Plataformas</a> ·
  <a href="#requisitos">Requisitos</a> ·
  <a href="#desempenho-medido">Desempenho</a> ·
  <a href="#como-gerar">Como gerar</a> ·
  <a href="#perguntas-frequentes">Perguntas frequentes</a> ·
  <a href="#como-funciona">Como funciona</a> ·
  <a href="#licença-e-créditos">Licença e créditos</a> ·
  <a href="#english-summary">English</a>
</p>

> **Projeto de fãs, sem fins lucrativos.** *Spawn* é marca registrada da Todd McFarlane Productions; o jogo *Spawn: Armageddon* foi publicado pela Namco; este projeto não tem relação com a Todd McFarlane Productions nem a Bandai Namco. Este repositório **não contém o jogo**: você precisa da **sua própria cópia** do DVD (a versão europeia, **SLES-52326**).

> [!IMPORTANT]
> **Para jogar, baixe o [Otavix Launcher](https://github.com/otavix010/otavix-launcher/releases/latest).** Ele baixa este port, pede a sua ISO, gera o jogo no seu PC e o mantém atualizado. Para relatar um problema ou pedir algo, use **"Reportar problema"** na página do jogo no launcher: o relatório já vai com o log e as configurações, e é por ele que as correções saem mais rápido.
>
> **To play, download the [Otavix Launcher](https://github.com/otavix010/otavix-launcher/releases/latest).** It downloads this port, asks for your ISO, makes the game on your PC and keeps it updated. To report a problem or ask for something, use **"Report a problem"** on the game's page in the launcher: the report carries the log and the settings, and that is how fixes come out fastest.

[English summary below](#english-summary)

## O que é

Um port **nativo** do *Spawn: Armageddon* (PlayStation 2, 2003) para Windows. Não é um emulador: o código do jogo é **traduzido para C++ e compilado** para x86-64 (recompilação estática), com o motor PS2 próprio do projeto (Otavix).

Como o código do jogo não pode ser distribuído, **o seu PC gera e compila a parte do jogo a partir da sua ISO**. Um comando só faz tudo.

## Estado atual: em desenvolvimento

Já dá para ver o jogo: inicia, carrega os módulos do IOP e os sons, passa pela escolha de idioma, pela checagem do cartão de memória e pelo **menu principal** (com a arte e o logo originais) e entra na **primeira fase em 3D**, com a cidade, a catedral, o Spawn e as cenas texturizados como no PlayStation 2. **Agora roda a 60 FPS, inclusive nas cenas mais pesadas** (testado num Ryzen 7 9800X3D; usa uns 6 núcleos e mantém 60 FPS mesmo limitado a 8 threads lógicas). Os microprogramas de geometria do VU1 são traduzidos para C++ na sua máquina, a partir do executável do seu disco (a etapa "VU1" do gerador; o repositório só traz onde eles ficam: offsets e tamanhos), e a rasterização usa AVX2 em várias threads. **Agora com som** (o chip de som SPU2 é emulado: música, efeitos e ambiente) **e com os vídeos** (abertura, história e demonstração). A jogabilidade já foi testada (andar, pular, atacar, tutorial da primeira fase; 15 minutos seguidos sem travar); falta testar salvar e as fases seguintes. Por enquanto, só para testes.

## Plataformas

| | **Windows** | **Linux / SteamOS** |
|---|---|---|
| Situação | **em desenvolvimento** (este port) | **não suportado no momento** |
| Como jogar | pelo launcher, ou `gerar.cmd` e `jogar.cmd` | só o port de *God of War: Ascension* tem versão Linux (beta) por enquanto |

## Requisitos

- **Windows 10/11 64 bits**, com o **Visual Studio 2022 Build Tools** (C++ e CMake; o comando está em [Como gerar](#como-gerar)). O launcher confere isso para você.
- A **sua ISO** do *Spawn: Armageddon*, na versão europeia (PAL) (**SLES-52326**). O gerador confere o executável e, se não bater, diz se é outra edição (outra região ou versão) ou o mesmo disco com o executável modificado.
- **Memória:** o gerador usa uns 3 GB de RAM por compilação em paralelo e escolhe o paralelismo pela memória livre; com pouca RAM funciona, só demora mais.
- **Disco:** alguns GB livres para os arquivos do disco, o código traduzido e a compilação (um jogo desta família usa uns 5 GB; o seu pode variar com o tamanho do disco).
- **AVX2 não é obrigatório**: o gerador detecta a CPU e usa as bibliotecas AVX2 ou SSE4.

## Desempenho medido

FPS de jogo, no motor publicado, sem a resolução interna (1x). **Só colocamos o que foi medido**; as demais máquinas ainda não foram testadas com este jogo.

| Máquina | CPU | GPU | FPS |
|---|---|---|---|
| **PC 1** | Ryzen 7 9800X3D | RTX 5080 | ~60 (60 s seguidos, build de 09/11) |
| **PC 2** | Core i5-11400F | RX 9060 XT | não medido |
| **Notebook** | Core i5-10300H (4/8) | GTX 1650 | não medido |
| **Portátil** | Legion Go S (Linux) | Radeon 780M | não suportado |

## Problemas conhecidos

- No motor publicado, o jogo pode **cair por volta dos 25 s ao pular os vídeos**. Já não acontece na build de 09/11 que estamos testando; a correção ainda não foi publicada.
- Esta é a **versão europeia (PAL)** apenas (SLES-52326); outras regiões e versões são recusadas pelo gerador, com o motivo.

## Como gerar

### Pelo Otavix Launcher

O [Otavix Launcher](https://github.com/otavix010/otavix-launcher/releases/latest) lista este port como **em desenvolvimento**: ele baixa o port, pede a ISO, gera o jogo e abre.

### À mão

**1. O que você precisa ter:** a sua cópia do *Spawn: Armageddon* **europeu** (SLES-52326, "Spawn - Armageddon (Europe) (En,Fr,De,Es,It)") como imagem **.iso** do DVD. O gerador confere o executável do jogo pelo hash: outras versões não servem, porque o mapa de funções é o da europeia.

**2. Instale as ferramentas (uma vez só)**, num terminal:
```
winget install Microsoft.VisualStudio.2022.BuildTools --override "--quiet --wait --add Microsoft.VisualStudio.Workload.VCTools --add Microsoft.VisualStudio.Component.VC.CMake.Project --includeRecommended"
```
O resto o gerador baixa sozinho: o motor do port (pacote pronto, conferido pelo SHA-256) e o FFmpeg (LGPL). Não precisa de Python nem de Git.

**3. Baixe este repositório** (botão *Code > Download ZIP*, ou `git clone`) e extraia numa pasta **sem espaços no caminho**, por exemplo `C:\spawn-armageddon-pc`. Deixe uns 5 GB livres nesse disco (os arquivos do disco, o código traduzido e a compilação).

**4. Clique duas vezes em `gerar.cmd`** e escolha a ISO. Ele:
- confere a ISO e extrai os arquivos do disco para `trabalho\disc`;
- baixa o motor do port (pacote pronto, conferido pelo SHA-256);
- traduz o código do jogo para C++ (só no seu PC);
- compila o código do jogo (de 5 a 30 minutos, conforme o PC; precisa de 16 GB de RAM ou mais).

**5. Jogue com `jogar.cmd`.** O jogo lê os arquivos de `trabalho\disc` e a ISO no lugar onde ela estava na geração (se mudar a ISO de lugar, rode `gerar.cmd -RefazerDe 2`).

Depois de atualizar o port, `gerar.cmd -RefazerDe 3` baixa o motor novo, retraduz e recompila sem extrair o disco de novo. Com o componente "C++ Clang tools" do Visual Studio instalado, a geometria compila com o clang-cl e fica um pouco mais rápida (sem ele, usa o MSVC).

## Perguntas frequentes

**Este repositório tem o jogo?** Não. Você precisa da sua própria cópia do DVD; o gerador monta o port no seu PC a partir da sua ISO.

**Roda no Linux ou no SteamOS?** Ainda não: só o port de *God of War: Ascension* tem versão Linux (beta). Este roda no Windows.

**O gerador disse "executável modificado" ou "edição diferente". E agora?** "Edição diferente" é outra região ou versão do disco; "executável modificado" é o mesmo disco com um executável alterado (patch, tradução, hack ou outra tiragem). Use uma cópia original sem modificações (SLES-52326).

**Saiu uma atualização do port. O que faço?** Atualize pelo launcher e gere de novo (`gerar.cmd -RefazerDe 3` à mão): ele baixa o motor novo, retraduz e recompila sem extrair o disco de novo.

**Onde relato um problema?** No launcher, em **"Reportar problema"** na página do jogo.

## Como funciona

- **O motor** (tradutor MIPS R5900 → C++ e runtime: GS, VU1, DMA, IOP, áudio SPU2, cartão de memória) é próprio do projeto e vem pronto (bibliotecas compiladas); o seu PC só traduz e compila o código do jogo.
- **O mapa de funções** (`jogo\ghidra_funcoes.csv`) veio de uma análise com o [Ghidra](https://ghidra-sre.org/) e a extensão ghidra-emotionengine-reloaded: são só endereços e nomes, nada do código do jogo. `jogo\entradas_extra.txt` lista funções chamadas só por ponteiro e alvos de tabelas de salto que a análise não marcou, e `jogo\stubs_extra.txt` as funções trocadas por respostas fixas; `jogo\stubs_tirar.txt` as que voltam a rodar o código do jogo (o som fala com o driver de som de verdade).

## Licença e créditos

- **O nosso código** (`gerar.ps1`, `gerar.cmd`, `ferramentas\`): [MIT](LICENSE).
- **O motor do port** (pacote `otx-motor-ps2`, baixado pronto pelo gerador) não é coberto pela licença MIT; os avisos de terceiros dele (raylib e glfw: zlib; FFmpeg: LGPL, DLLs à parte) estão no `TERCEIROS.txt` do pacote.
- *Spawn* é marca registrada da Todd McFarlane Productions; o jogo *Spawn: Armageddon* foi publicado pela Namco. Este é um projeto de fãs, sem fins lucrativos, sem relação com a Todd McFarlane Productions nem a Bandai Namco nem endossado por elas.

## English summary

A **native PC port** of *Spawn: Armageddon* (PlayStation 2, 2003) made by **static recompilation** with the project's own PS2 engine. **Work in progress.** It reaches the 3D levels at 60 FPS, **with sound** (emulated SPU2) **and the FMV videos**.

**Platforms:** Windows 10/11 only for now (Linux is not supported yet; only the *God of War: Ascension* port has a Linux beta). Performance is listed only where we measured it (see the table above); machines not listed are not measured yet. **Easiest: the [Otavix Launcher](https://github.com/otavix010/otavix-launcher/releases/latest).**

**Bring your own game**: no game code or data here, only the function map (addresses) and translation settings. You need the **European** release (SLES-52326, Redump "Spawn - Armageddon (Europe) (En,Fr,De,Es,It)") as an **.iso**. Install Visual Studio 2022 Build Tools with C++ and CMake (commands above), download this repository to a path without spaces, double-click **`gerar.cmd`** (it checks your ISO, extracts the disc files, downloads the prebuilt engine package (no Git needed), translates the game code on your PC and builds it, in 5 to 30 minutes), then play with **`jogar.cmd`**.

License: our scripts are MIT; the engine package is not covered by it, and its third-party notices are in its `TERCEIROS.txt`. *Spawn* is a trademark of Todd McFarlane Productions; *Spawn: Armageddon* was published by Namco; this is a non-commercial fan project, not affiliated with or endorsed by Todd McFarlane Productions or Bandai Namco.
