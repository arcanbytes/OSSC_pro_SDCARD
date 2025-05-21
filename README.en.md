# OSSC Pro SD CARD

[![en](https://img.shields.io/badge/lang-en-red.svg)](README.en.md)
[![es](https://img.shields.io/badge/lang-es-yellow.svg)](README.es.md)

Este repositorio contiene mi configuración personalizada para la tarjeta SD del OSSC Pro, incluyendo perfiles, algoritmos de escalado y máscaras CRT adicionales. También se incluye una breve guía para la instalación opcional de un ventilador.


## Contenido de la Tarjeta SD
He subido la estructura completa de mi tarjeta SD, lista para ser clonada o descargada. Asegúrate de mantener la organización de los archivos para que el OSSC Pro los detecte correctamente:

````
├─ ossc_pro.bin              # Actualizacion del firmware (no incluido)
├─ prof_n_i.txt              # Nombres para los perfiles internos 0–9
├─ prof_n.txt                # Nombres para perfiles en la SD 0–99
├─ prof00.bin … prof99.bin   # Perfiles guardados en SD (slots 00–99)
│
├─ edid/                     # Archivos EDID personalizados (no incluido)
│   └─ your_edid.bin
│
├─ scl_alg/                  # Algoritmos de escalado
│   ├─ *.cfg                  # Configuraciones de algoritmos de escalado personalizados
│   └─ *.txt                  # Filtros de 64 fases del proyecto MiSTer
│
└─ shmask/                   # Archivos de máscaras CRT del proyecto MiSTer
    └─ *.txt
````
Nota: Es crucial que no crees subcarpetas dentro de scl_alg/ o shmask/, ya que el OSSC Pro solo detecta los archivos directamente en esas carpetas
## Perfiles
En la raíz del repositorio, encontrarás mis perfiles guardados en la SD (prof00.bin a prof99.bin), optimizados para televisores 4K como la Xiaomi TV F2. Perfiles incluidos hasta la fecha:

* prof00.bin → MyDefault: Configuración por defecto para una TV 4K, ideal como punto de partida.
* prof01.bin → PS2_480p/i_P4: Para contenido 480p/480i 4:3 (ej. Persona 4).
* prof02.bin → PS2_480p/i/W_P4: Para contenido 480p/480i 16:9 (ej. Persona 4).
* prof03.bin → PS2_240p_Pixel: Para contenido 240p en modo LM.
* prof04.bin → PS2_480i_CSNK2: Para contenido Pixel Art 480i 4:3 (ej. Capcom vs SNK 2).
* prof05.bin → NS_720p1080pScl: Para Nintendo Switch (720p/1080p).
* prof06.bin → NS_Retro_LM: Para Nintendo Switch (Pixel Art 720p en modo LM

El archivo prof_n.txt asocia estos slots a nombres legibles en el menú del OSSC Pro. Para que los nombres aparezcan correctamente, debes cargar el perfil del slot correspondiente y luego salvarlo en el mismo slot desde el OSSC Pro.

Adicionalmente, prof_n_i.txt mapea los slots de perfiles internos del OSSC Pro a nombres personalizados.
## Algoritmos de Escalado (scl_alg/)
En la carpeta scl_alg/ encontrarás mis configuraciones personalizadas en formato .cfg. Estos combinan algoritmos internos del OSSC Pro (como nearest, lanczos3, gs_soft) con filtros de 64 fases del proyecto MiSTer (https://github.com/MiSTer-devel/Filters_MiSTer/) como Bicubic.txt, SNES Interpolation, Scanlines, etc..

Nota: Los algoritmos de escalado en formato .txt son filtros de 64 fases, ya que otras fases no son compatibles con el OSSC Pro. Si deseas usar efectos visuales como Scanlines_*.txt, actívalos solo en la línea 2 de tu archivo .cfg y no combines los scanlines de los algoritmos de escalado con la función de scanlines interna del OSSC Pro.
## Máscaras CRT (shmask/)
La carpeta shmask/ contiene archivos .txt con máscaras CRT del proyecto MiSTer (https://github.com/MiSTer-devel/ShadowMasks_MiSTer). Estas se cargan en el menú Post‑proc → Shadow mask → Custom del OSSC Pro y se dividen en:

* Máscaras simples (monocromáticas), como rejillas o franjas verticales.
* Máscaras complejas (multicromáticas), ordenadas por subpíxeles (RGB, BGR, etc.), incluyendo archivos raíz como PVM, Trinitron o Bayer.

Simplemente copia la máscara que prefieras, selecciónala en el menú del OSSC Pro, ajusta la intensidad y guarda los cambios con "SD Save profile".