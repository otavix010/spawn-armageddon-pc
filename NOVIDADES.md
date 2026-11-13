# Novidades do port

O Otavix Launcher mostra este arquivo na página "Novidades" do jogo. Cada atualização tem um título
"## <data> · <versão>" e o texto em português (### pt), inglês (### en) e espanhol (### es). As mais novas ficam em cima.

## 13/11/2026 · 0.4.7
### pt
- **Corrigida uma causa de fechamento do jogo com o erro 0xC0000005** depois de alguns minutos de jogo: em certas cenas o motor lia memória fora do lugar ao enviar os gráficos.
- **Geração mais robusta em alguns Windows**: quando o Prompt de Comando do Windows roda um script de inicialização próprio, a extração da ISO não acontecia e o gerador dizia, por engano, que a ISO não era a certa. Agora isso não interfere mais; e se a extração parar sem motivo claro, a mensagem não acusa mais a ISO.
- Motor 0.1.10: na próxima geração o gerador refaz da etapa 3 sozinho (o disco extraído continua valendo).
### en
- **Fixed a cause of the game closing with error 0xC0000005** after a few minutes of play: in some scenes the engine read memory out of bounds while sending graphics.
- **More reliable generation on some Windows setups**: when the Windows Command Prompt runs a startup script of its own, the ISO was not extracted and the generator wrongly said the ISO was not the right one. This no longer interferes; and if the extraction stops for no clear reason, the message no longer blames the ISO.
- Engine 0.1.10: on the next generation the generator redoes it from step 3 on its own (the extracted disc is kept).
### es
- **Corregida una causa de cierre del juego con el error 0xC0000005** tras algunos minutos de juego: en ciertas escenas el motor leía memoria fuera de lugar al enviar los gráficos.
- **Generación más robusta en algunos Windows**: cuando el Símbolo del sistema de Windows ejecuta un script de inicio propio, la ISO no se extraía y el generador decía, por error, que la ISO no era la correcta. Eso ya no interfiere; y si la extracción se detiene sin un motivo claro, el mensaje ya no culpa a la ISO.
- Motor 0.1.10: en la próxima generación el generador rehace desde la etapa 3 solo (el disco extraído se mantiene).

## 12/11/2026 · 0.4.6
### pt
- **Mais fps em processadores de 6 núcleos** (como Core i5 e Ryzen 5) com outros programas abertos: o motor não prende mais as tarefas principais em núcleos fixos do processador.
- Motor 0.1.9: na próxima geração o gerador refaz da etapa 3 sozinho (o disco extraído continua valendo).
### en
- **Higher fps on 6-core processors** (such as Core i5 and Ryzen 5) with other programs open: the engine no longer pins its main tasks to fixed cores.
- Engine 0.1.9: on the next generation the generator redoes it from step 3 on its own (the extracted disc is kept).
### es
- **Más fps en procesadores de 6 núcleos** (como Core i5 y Ryzen 5) con otros programas abiertos: el motor ya no fija sus tareas principales en núcleos fijos.
- Motor 0.1.9: en la próxima generación el generador rehace desde la etapa 3 solo (el disco extraído se mantiene).

## 12/11/2026 · 0.4.5
### pt
- Na primeira vez depois de uma atualização, uma mensagem avisa enquanto os gráficos são preparados (pode levar até 1 minuto).
- Motor 0.1.8: na próxima geração o gerador refaz da etapa 3 sozinho (o disco extraído continua valendo).
### en
- The first time after an update, a message is shown while the graphics are being prepared (it may take up to 1 minute).
- Engine 0.1.8: on the next generation the generator redoes it from step 3 on its own (the extracted disc is kept).
### es
- La primera vez tras una actualización, un mensaje avisa mientras se preparan los gráficos (puede tardar hasta 1 minuto).
- Motor 0.1.8: en la próxima generación el generador rehace desde la etapa 3 solo (el disco extraído se mantiene).

## 06/11/2026 · 0.4.5
### pt
- **Mais fps pelo launcher**: aberto pelo launcher, o jogo deixava de usar a thread própria de desenho e esperava a placa de vídeo a cada quadro. Isso derrubava o fps, principalmente em placas de entrada (RTX 5060, por exemplo). Corrigido.
- Reduções e ampliações de imagem que o jogo faz nos efeitos agora seguem o PS2 ponto a ponto.
- Motor 0.1.2: na próxima geração o gerador refaz da etapa 3 sozinho (o disco extraído continua valendo).
### en
- **More fps from the launcher**: when opened from the launcher, the game stopped using its own drawing thread and waited for the graphics card every frame. That lowered the fps, mostly on entry-level cards (an RTX 5060, for example). Fixed.
- Picture reductions and enlargements the game does in its effects now match the PS2 pixel for pixel.
- Engine 0.1.2: on the next generation the generator redoes it from step 3 on its own (the extracted disc is kept).
### es
- **Más fps desde el launcher**: abierto desde el launcher, el juego dejaba de usar su propio hilo de dibujo y esperaba a la tarjeta gráfica en cada fotograma. Eso bajaba los fps, sobre todo en tarjetas de entrada (una RTX 5060, por ejemplo). Corregido.
- Las reducciones y ampliaciones de imagen que el juego hace en sus efectos ahora siguen a la PS2 píxel a píxel.
- Motor 0.1.2: en la próxima generación el generador rehace desde la etapa 3 solo (el disco extraído se mantiene).

## 06/11/2026 · 0.4.4
### pt
- **Motor próprio**: o gerador não baixa nem compila mais o PS2Recomp. Agora baixa o motor do port pronto (conferido pelo SHA-256) e compila só o código do jogo: mais rápido (de 5 a 30 minutos, conforme o PC), usa menos memória e não precisa de Git.
- **Sem Python**: as ferramentas do gerador agora vêm dentro do motor (um executável só). Basta instalar o Visual Studio Build Tools; Python e Git não são mais necessários.
- Quem já tinha o port gerado: a próxima geração apaga a pasta `ps2recomp\` antiga e refaz da etapa 3 sozinha.
### en
- **Own engine**: the generator no longer downloads or builds PS2Recomp. It now downloads the prebuilt port engine (checked by SHA-256) and builds only the game code: faster (5 to 30 minutes, depending on the PC), less memory, and no Git needed.
- **No Python**: the generator tools now ship inside the engine (a single executable). Only Visual Studio Build Tools is needed; Python and Git are no longer required.
- If you had already generated the port: the next generation deletes the old `ps2recomp\` folder and redoes it from step 3 on its own.
### es
- **Motor propio**: el generador ya no descarga ni compila PS2Recomp. Ahora descarga el motor del port ya listo (verificado por SHA-256) y compila solo el código del juego: más rápido (de 5 a 30 minutos, según el PC), usa menos memoria y no necesita Git.
- **Sin Python**: las herramientas del generador ahora vienen dentro del motor (un solo ejecutable). Solo hace falta Visual Studio Build Tools; ya no se necesitan Python ni Git.
- Si ya tenías el port generado: la próxima generación borra la carpeta `ps2recomp\` antigua y rehace desde la etapa 3 sola.

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
