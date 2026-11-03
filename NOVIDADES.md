# Novidades do port

O Otavix Launcher mostra este arquivo na página "Novidades" do jogo. Cada atualização tem um título
"## <data> · <versão>" e o texto em português (### pt), inglês (### en) e espanhol (### es). As mais novas ficam em cima.

## 03/11/2026 · 0.4.3
### pt
- Correção de desempenho (a 0.4.2 podia deixar o jogo mais lento).
- Atualizar o port pelo launcher não falha mais ("already exists in working directory"); o gerador também funciona em discos exFAT/FAT e baixa de novo o Git portátil se ele estiver danificado ou bloqueado.
- O ponteiro do mouse some sobre o jogo; com a janela do tamanho do monitor, o jogo abre sem bordas.
### en
- Performance fix (0.4.2 could make the game slower).
- Updating the port from the launcher no longer fails ("already exists in working directory"); the generator also works on exFAT/FAT drives and downloads the portable Git again if it is damaged or blocked.
- The mouse pointer hides over the game; with the window set to the monitor's size, the game opens borderless.
### es
- Corrección de rendimiento (la 0.4.2 podía dejar el juego más lento).
- Actualizar el port desde el launcher ya no falla ("already exists in working directory"); el generador también funciona en discos exFAT/FAT y vuelve a descargar el Git portátil si está dañado o bloqueado.
- El puntero del ratón se oculta sobre el juego; con la ventana del tamaño del monitor, el juego se abre sin bordes.

## 03/11/2026 · 0.4.2
### pt
- Efeitos que leem a profundidade agora saem como no PS2.
- **Controle novo**: Xbox (XInput), DualSense e DualShock 4 por USB ou Bluetooth e outros controles USB, com **vibração**. Corrigido o analógico que invertia no fim do curso.
- **Medidor de desempenho (F10)**: FPS, tempo de quadro, uso de CPU/GPU, temperaturas, VRAM e RAM.
- Imagem estável: o entrelaçamento agora junta os dois campos (antes a imagem tremia, principalmente em telas grandes/4K).
- A janela de depuração não abre mais junto com o jogo (F1 mostra, se precisar).
### en
- Effects that read the depth buffer now look like on the PS2.
- **New controller support**: Xbox (XInput), DualSense and DualShock 4 over USB or Bluetooth and other USB pads, with **vibration**. Fixed the analog stick flipping at the end of its travel.
- **Performance meter (F10)**: FPS, frame time, CPU/GPU usage, temperatures, VRAM and RAM.
- Stable image: interlacing now weaves both fields (the image used to shake, mostly on big/4K screens).
- The debug window no longer opens with the game (F1 shows it if needed).
### es
- Los efectos que leen la profundidad ahora se ven como en PS2.
- **Mando nuevo**: Xbox (XInput), DualSense y DualShock 4 por USB o Bluetooth y otros mandos USB, con **vibración**. Corregido el analógico que se invertía al final del recorrido.
- **Medidor de rendimiento (F10)**: FPS, tiempo de cuadro, uso de CPU/GPU, temperaturas, VRAM y RAM.
- Imagen estable: el entrelazado ahora une los dos campos (antes la imagen temblaba, sobre todo en pantallas grandes/4K).
- La ventana de depuración ya no se abre con el juego (F1 la muestra si hace falta).

## 02/11/2026 · 0.4.1
### pt
- **Telas ultrawide**: a proporção da imagem agora tem 21:9, 32:9 e "Igual ao monitor", além de 4:3 e 16:9. Em tela larga o jogo abre o campo de visão para os lados, sem esticar o cenário nem os personagens, e o modo widescreen do jogo liga sozinho. O 21:9 se ajusta ao seu monitor (2560x1080, 3440x1440...). O HUD fica um pouco mais largo e os vídeos continuam em 4:3.
- Correções: imagens desenhadas de baixo para cima saem na posição certa; o gerador diz de que jogo é a ISO quando ela é de outro jogo ou versão.
### en
- **Ultrawide screens**: the aspect ratio now has 21:9, 32:9 and "Match monitor", besides 4:3 and 16:9. On a wide screen the game widens its field of view to the sides, without stretching the scenery or the characters, and the game's widescreen mode turns on by itself. 21:9 adjusts to your monitor (2560x1080, 3440x1440...). The HUD gets a bit wider and videos stay 4:3.
- Fixes: images drawn bottom to top now come out the right way; the generator tells which game an ISO belongs to when it is another game or version.
### es
- **Pantallas ultrawide**: la relación de aspecto ahora tiene 21:9, 32:9 e "Igual al monitor", además de 4:3 y 16:9. En pantalla ancha el juego amplía el campo de visión hacia los lados, sin estirar el escenario ni los personajes, y el modo panorámico del juego se activa solo. El 21:9 se ajusta a tu monitor (2560x1080, 3440x1440...). El HUD queda un poco más ancho y los videos siguen en 4:3.
- Correcciones: las imágenes dibujadas de abajo hacia arriba salen en la posición correcta; el generador indica de qué juego es la ISO cuando es de otro juego o versión.

## 02/11/2026 · 0.4.0
### pt
- **Menu de opções** no launcher: modo de tela (janela ou tela cheia; F11 ou Alt+Enter alternam no jogo), tamanho da janela, escalonador (bilinear, AMD FSR 1 ou NVIDIA Image Scaling), nitidez, anti-serrilhamento FXAA, proporção 4:3/16:9 e predefinições Leve, Equilibrado e Qualidade.
- **Desenho na placa de vídeo**: a parte gráfica do console (GS) agora roda na GPU, com o resultado conferido pixel a pixel contra o desenho no processador.
- Geometria (VU1) mais rápida e as partes pesadas do jogo em núcleos separados em processadores de até 6 núcleos.
- Correção: aberto pelo launcher, o jogo agora usa as mesmas configurações do gerador (antes ficava sem elas e mais lento).
### en
- **Options menu** in the launcher: display mode (window or fullscreen; F11 or Alt+Enter switch in game), window size, upscaler (bilinear, AMD FSR 1 or NVIDIA Image Scaling), sharpness, FXAA anti-aliasing, 4:3/16:9 aspect ratio and Light, Balanced and Quality presets.
- **Drawing on the graphics card**: the console's graphics chip (GS) now runs on the GPU, its output checked pixel by pixel against drawing on the processor.
- Faster geometry (VU1), and the game's heavy parts on separate cores on processors with up to 6 cores.
- Fix: started from the launcher, the game now uses the same settings as the generator (it used to run without them, slower).
### es
- **Menú de opciones** en el launcher: modo de pantalla (ventana o pantalla completa; F11 o Alt+Enter alternan en el juego), tamaño de la ventana, escalador (bilineal, AMD FSR 1 o NVIDIA Image Scaling), nitidez, antialiasing FXAA, relación 4:3/16:9 y preajustes Ligero, Equilibrado y Calidad.
- **Dibujo en la tarjeta gráfica**: el chip gráfico de la consola (GS) ahora funciona en la GPU, con el resultado comprobado píxel a píxel contra el dibujo en el procesador.
- Geometría (VU1) más rápida y las partes pesadas del juego en núcleos separados en procesadores de hasta 6 núcleos.
- Corrección: abierto desde el launcher, el juego ahora usa la misma configuración que el generador (antes iba sin ella y más lento).

## 30/10/2026 · 0.3.0
### pt
- **Som**: o chip de som do PS2 (SPU2) agora é emulado — música, efeitos, vozes e sons de ambiente tocam como no console (antes o jogo era mudo).
- **Vídeos**: as cenas em vídeo (abertura, história e demonstração) agora tocam, com som.
- Correções no "sistema operacional" do console que o jogo usa (prioridade das tarefas), necessárias para os vídeos e para o carregamento das fases.
- Testado: menu, vídeos, primeira fase (andar, pular, atacar, tutorial) e 15 minutos seguidos sem travar.
### en
- **Sound**: the PS2 sound chip (SPU2) is now emulated — music, effects, voices and ambience play like on the console (the game used to be silent).
- **Videos**: the FMV scenes (intro, story and attract mode) now play, with sound.
- Fixes in the console "operating system" used by the game (task priorities), needed for the videos and for level loading.
- Tested: menu, videos, first level (walking, jumping, attacking, tutorial) and 15 minutes in a row without hanging.

## 29/10/2026 · 0.2.0
### pt
- **Jogável a 60 FPS**, inclusive nas cenas mais pesadas (antes: ~3 FPS na fase 3D).
- A geometria (VU1) agora é traduzida para C++ na sua máquina, a partir do executável do seu disco: o gerador ganhou a etapa "VU1". Nada do jogo vem no repositório.
- Rasterização em AVX2 e em várias threads, filas mais leves entre as partes do console; usa uns 6 núcleos (testado também limitado a 8 threads lógicas: 60 FPS).
- Se o Visual Studio tiver o componente "C++ Clang tools", a geometria fica um pouco mais rápida.
### en
- **Playable at 60 FPS**, even in the heaviest scenes (before: ~3 FPS in the 3D level).
- The geometry processor (VU1) is now translated to C++ on your machine, from your disc's executable: the generator got a new "VU1" step. Nothing from the game ships in this repository.
- AVX2 multi-threaded rasterizer and lighter queues between the console parts; uses about 6 cores (also tested limited to 8 logical threads: 60 FPS).
- With the Visual Studio "C++ Clang tools" component installed, the geometry runs a bit faster.

## 26/10/2026 · 0.1.0
### pt
- **Primeira versão de testes.** O gerador recompila o jogo a partir da sua ISO (versão europeia).
- Já dá para passar pelos menus (60 FPS) e entrar na primeira fase em 3D, com as texturas e as cores do PlayStation 2.
- **Ainda não dá para jogar:** a fase 3D roda a uns 3 FPS, porque o processador de geometria (VU1) e a rasterização (GS) ainda são emulados por software. Os vídeos são pulados por enquanto.
### en
- **First test version.** The generator rebuilds the game from your ISO (European release).
- You can go through the menus (60 FPS) and enter the first 3D level, with the PlayStation 2 textures and colours.
- **Not playable yet:** the 3D level runs at about 3 FPS, because the geometry processor (VU1) and the rasterizer (GS) are still emulated in software. Videos are skipped for now.
