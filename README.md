# Avatar Ecosystem – Categorized Open‑Source Repositories

Este documento enumera los repositorios que hemos recopilado en **AVATAR_EVALUATION.md**, organizados de **más completo** (frameworks que ofrecen una suite completa) a **más específico / bajo nivel**. Cada categoría incluye el nombre del proyecto, el enlace al repositorio y una breve descripción.

---

## 🔟 Frameworks end‑to‑end (suite completa)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **AVTR‑1 / Avaturn** | N/A (candidato principal) | Renderizador incremental de avatar en tiempo real que combina captura de audio, síntesis de voz, generación de labios y renderizado sin requerir cámara. |
| **MuseTalk** | https://github.com/OpenAI/MuseTalk | Pipeline completo de generación de avatar que incluye captura de voz, generación de movimiento facial y renderizado 3D. |
| **SoulX‑FlashHead Lite** | https://github.com/SoulX/FlashHeadLite | Solución ligera de talking‑head que integra VAD, TTS y renderizado facial a partir de una sola imagen. |
| **LivePortrait** | https://github.com/KwaiVGI/LivePortrait | Framework que permite animar una foto estática a partir de audio y produce renderizado facial en tiempo real. |
| **OpenAvatarChat** | https://github.com/yourorg/OpenAvatarChat | Chatbot de avatar que combina captura de audio, modelo LLM, síntesis de voz y renderizado de avatar en tiempo real. |
| **Avatarify‑Full** | https://github.com/alievk/avatarify-full | Implementación completa que incluye captura webcam, modelado facial, transferencia de expresión y streaming vía WebRTC. |

---

## 1️⃣ Infraestructura de transmisión (SFU/MCU/Media‑servers)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **Kurento Media Server** | https://github.com/Kurento/kurento-media-server | Servidor multimedia C++ con filtros OpenCV, soporta WebRTC, RTSP y procesamiento de vídeo en tiempo real. |
| **Licode** | https://github.com/lynckia/licode | Plataforma MCU/SFU para comunicaciones WebRTC, escrita en C++/Node.js, con soporte de codecs y grabación. |
| **Galene** | https://github.com/jech/galene | SFU Go ultra‑ligero para streaming de audio/video con baja latencia. |
| **OWT‑Server (Open WebRTC Toolkit)** | https://github.com/open-webrtc-toolkit/owt-server | Servidor de medios que combina WebRTC, SFU y funciones de composición de vídeo. |
| **mediasoup** | https://github.com/versatica/mediasoup | Servidor SFU de alto rendimiento en Node.js, con API flexible para salas y pistas. |
| **LiveKit Server** | https://github.com/livekit/livekit-server | Servidor SFU escrito en Go, orientado a aplicaciones interactivas y bajo latencia. |

---

## 2️⃣ SDKs y client‑libraries (multiplataforma)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **LiveKit SDK (Go, JS, Unity, Flutter, iOS, Android)** | https://github.com/livekit/livekit-sdk | Conjunto de SDKs para crear clientes que se conectan a LiveKit Server, con soporte de audio, video y datos. |
| **Agora SDK (Web, Android, iOS, Unity, Unreal)** | https://github.com/AgoraIO/Agora-Web-RTC-SDK | SDK oficial de Agora para integración de llamadas y transmisión en tiempo real. |
| **Pion (Go)** | https://github.com/pion/pion | Biblioteca Go que implementa todo el stack WebRTC, usable tanto en cliente como en servidor. |
| **Daily SDK** | https://github.com/dailyco/daily‑js | SDK JavaScript para integrar videollamadas Daily en aplicaciones web. |
| **Pipecat Client (iOS, Android, Flutter)** | https://github.com/pipecat‑ai/pipecat‑client | SDK multiplataforma que combina captura de audio, VAD y streaming via WebRTC. |
| **mediasoup‑client (JS)** | https://github.com/versatica/mediasoup-client | Cliente JavaScript que se comunica con un servidor mediasoup. |
| **Simple‑Peer** | https://github.com/feross/simple-peer | Wrapper ligero de WebRTC para crear conexiones P2P en navegadores y Node.js. |
| **PeerJS** | https://github.com/peers/peerjs | Biblioteca para simplificar la señalización y conexión WebRTC entre navegadores. |

---

## 3️⃣ Captura y análisis de datos (audio / video / pose)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **pion/mediadevices** | https://github.com/pion/mediadevices | Librería Go para capturar cámara, micrófono y pantalla y alimentar WebRTC. |
| **MediaPipe** | https://github.com/google/mediapipe | Framework de Google para detección de manos, cara, pose y segmentación en tiempo real. |
| **OpenPose** | https://github.com/CMU-Perceptual-Computing-Lab/openpose | Biblioteca C++/Python para estimación de pose humana a partir de video. |
| **AlphaPose** | https://github.com/open-mmlab/AlphaPose | Estimación de pose multi‑persona en tiempo real, con soporte GPU. |
| **MMPose** | https://github.com/open-mmlab/mmpose | Toolkit de pose basado en PyTorch, con modelos 2D/3D. |
| **face‑alignment** | https://github.com/1adrianb/face‑alignment | Detección de landmarks faciales 2D/3D usando redes neuronales. |
| **SMPL / SMPL‑X** | https://github.com/vchoutas/smplx | Modelos paramétricos de cuerpo y cara para generar mallas 3D a partir de pose. |
| **Deep3DFaceReconstruction** | https://github.com/deep3dface/Deep3DFaceReconstruction | Reconstrucción 3D de la cara a partir de una sola imagen usando redes profundas. |

---

## 4️⃣ Codificación y compresión de medios
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **FFmpeg** | https://github.com/FFmpeg/FFmpeg | Herramienta de línea de comandos y librería para codificar, decodificar y transcodificar audio/video. |
| **x264 / x265** | https://code.videolan.org/videolan/x264 (x264) \n https://bitbucket.org/multicoreware/x265_git (x265) | Codificadores de vídeo H.264 y HEVC de alta eficiencia. |
| **Basis Universal** | https://github.com/BinomialLLC/basis_universal | Compresión de texturas GPU con calidad y ratios de reducción líderes. |
| **KTX‑Software** | https://github.com/KhronosGroup/KTX-Software | Herramientas para crear y manipular contenedores KTX 2.0 (compatible con Basis). |
| **webrtc‑vad** | https://github.com/wiseman/py-webrtcvad | Detector de voz (VAD) basado en el algoritmo WebRTC. |
| **RNNoise** | https://github.com/xiph/rnnoise | Red neuronal para reducción de ruido en audio en tiempo real. |

---

## 5️⃣ Transporte y protocolos WebRTC (bajo nivel)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **pion/turn** | https://github.com/pion/turn | Servidor TURN puro Go, para relé de tráfico WebRTC detrás de NAT. |
| **pion/ice** | https://github.com/pion/ice | Implementación de ICE en Go para descubrimiento de pares. |
| **pion/sctp** | https://github.com/pion/sctp | Protocolo SCTP para DataChannels WebRTC en Go. |
| **pion/rtp** | https://github.com/pion/rtp | Manipulación de paquetes RTP en Go. |
| **pion/rtcp** | https://github.com/pion/rtcp | Generación y parseo de paquetes RTCP. |
| **pion/sdp** | https://github.com/pion/sdp | Parser y generador de descripciones SDP. |
| **pion/interceptor** | https://github.com/pion/interceptor | Framework para interceptar y modificar paquetes RTP/RTCP. |
| **coturn** | https://github.com/coturn/coturn | Servidor TURN/STUN de referencia, escrito en C. |

---

## 6️⃣ Modelado, carga y optimización 3‑D
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **Assimp** | https://github.com/assimp/assimp | Biblioteca C++ para importar y exportar más de 40 formatos 3D (FBX, OBJ, glTF, etc.). |
| **cgltf** | https://github.com/jkuhlmann/cgltf | Parser C99 de un solo archivo para glTF 2.0, sin dependencias externas. |
| **tinygltf** | https://github.com/syoyo/tinygltf | Header‑only C++11 para leer y escribir archivos glTF/VRM. |
| **meshoptimizer** | https://github.com/zeux/meshoptimizer | Herramientas de optimización de mallas (cache‑friendly, compresión, LOD). |
| **ufbx** | https://github.com/bext-labs/ufbx | Loader ultra‑rápido de FBX en C/C++ sin el SDK oficial. |
| **openfbx** | https://github.com/nemitz/openfbx | Importador ligero de FBX para C++. |
| **glTF‑Validator** | https://github.com/KhronosGroup/glTF-Validator | Validador oficial de especificación glTF 2.0. |
| **glTF‑Transform** | https://github.com/donmccurdy/glTF-Transform | Toolkit JavaScript/TS para optimizar y procesar glTF (draco, meshopt, etc.). |
| **glTF‑Blender‑IO** | https://github.com/KhronosGroup/glTF-Blender-IO | Exportador/importador oficial de glTF para Blender. |

---

## 7️⃣ Animación y control del avatar (movimiento facial / cuerpo)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **First‑Order Motion Model** | https://github.com/AliaksandrSiarohin/first-order-model | Modelo de generación de vídeo a partir de una sola imagen y un mapa de movimiento. |
| **FaceFormer** | https://github.com/EvelynBao/FaceFormer | Red neuronal que genera secuencias faciales a partir de audio y una foto de referencia. |
| **CodeTalker** | https://github.com/doubtingwah/CodeTalker | Sistema que sincroniza labios con audio generado por modelos de código‑a‑voz. |
| **StyleTalk** | https://github.com/microsoft/StyleTalk | Transferencia de estilo facial y generación de conversación animada. |
| **NerfStudio** | https://github.com/nerfstudio/nerfstudio | Framework para entrenar y renderizar NeRFs interactivos, útil para avatares 3‑D. |
| **Instant‑NGP** | https://github.com/NVlabs/instant-ngp | Implementación ultra‑rápida de NeRF para reconstrucción y rendering en tiempo real. |
| **PIFuHD** | https://github.com/shunsukesaito/PIFuHD | Reconstrucción de superficies 3‑D de alta resolución a partir de imágenes. |
| **PIFu** | https://github.com/shunsukesaito/PIFu | Versión original de PI‑Fu para reconstrucción de mallas a partir de fotos. |
| **DeepFaceLab** | https://github.com/iperov/DeepFaceLab | Herramienta para crear deepfakes y transferencia de expresiones faciales. |
| **AlphaPose** | https://github.com/open-mmlab/AlphaPose | Estimación de pose multi‑persona en tiempo real, útil para captura de movimiento. |
| **MMPose** | https://github.com/open-mmlab/mmpose | Conjunto de modelos de pose 2D/3D basados en PyTorch. |

---

## 8️⃣ Renderizado y UI (WebGL / WebGPU / Desktop)
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **PixiJS** | https://github.com/pixijs/pixijs | Motor 2D acelerado por WebGL/WebGPU, ideal para avatares Live2D y sprites. |
| **TWGL.js** | https://github.com/greggman/twgl.js | Biblioteca ligera para simplificar shaders y buffers WebGL. |
| **regl** | https://github.com/regl-project/regl | Abstracción declarativa para crear pipelines WebGL de forma concisa. |
| **Three.js** | https://github.com/mrdoob/three.js | Motor 3D WebGL ampliamente usado para visualización de avatares. |
| **Babylon.js** | https://github.com/BabylonJS/Babylon.js | Motor 3D completo con soporte WebGPU y real‑time rendering. |
| **ModernGL** | https://github.com/moderngl/moderngl | Wrapper Python de OpenGL orientado a rendimiento y facilidad de uso. |
| **pygfx** | https://github.com/vispy/pygfx | Motor de renderizado WebGPU en Python. |
| **Godot‑VRM** | https://github.com/vrm-c/vrm-godot | Add‑on para Godot que permite importar y animar modelos VRM. |
| **VRM Add‑on for Blender** | https://github.com/saturday06/VRM_Addon_for_Blender | Herramienta para importar/exportar avatares VRM en Blender. |
| **DearPyGui** | https://github.com/hoffstadt/DearPyGui | GUI GPU‑acelerada para aplicaciones Python, útil para paneles de control de avatar. |
| **Kivy** | https://github.com/kivy/kivy | Framework multiplataforma para aplicaciones UI con soporte OpenGL. |
| **Flet** | https://github.com/flet-dev/flet | Framework para crear apps de escritorio/web con Python y renderizado por navegador. |

---

## 9️⃣ Síntesis de voz y procesamiento de audio
| **Proyecto** | **Repositorio** | **Descripción** |
|---|---|---|
| **xtts‑api‑server** | https://github.com/coqui-ai/TTS | Servicio API para TTS basado en los modelos XTTS de Coqui. |
| **VALL‑E** | https://github.com/microsoft/VALL-E | Modelo de voz de alta fidelidad capaz de clonación y generación a partir de texto. |
| **MetaVoice‑1B** | https://github.com/meta-voice/MetaVoice-1B | Modelo de generación de voz en 1B parámetros, orientado a aplicaciones de conversación. |
| **Silero Models** | https://github.com/snakers4/silero‑models | Conjunto de modelos para TTS, ASR y VAD de alta calidad en PyTorch. |
| **edge‑tts** | https://github.com/rany2/edge-tts | Cliente Python para la API de voz de Microsoft Edge. |
| **torchaudio** | https://github.com/pytorch/audio | Librería de PyTorch para procesamiento de audio y extracción de características. |
| **librosa** | https://github.com/librosa/librosa | Biblioteca Python para análisis y visualización de audio. |
| **py‑soundfile** | https://github.com/bastibe/python‑soundfile | Lectura/escritura de archivos de audio en varios formatos. |
| **Resampy** | https://github.com/bmcfee/resampy | Herramienta para resampling de audio de alta calidad. |
| **RNNoise** | https://github.com/xiph/rnnoise | Red neuronal para reducción de ruido en tiempo real. |

---

*Este README se generó automáticamente a partir del archivo **AVATAR_EVALUATION.md** y está pensado como referencia rápida para decidir qué componentes integrar en la arquitectura de un avatar en tiempo real.*
