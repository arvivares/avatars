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
| **x264 / x265** | https://code.videolan.org/videolan/x264 (x264) \\ https://bitbucket.org/multicoreware/x265_git (x265) | Codificadores de vídeo H.264 y HEVC de alta eficiencia. |
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
| **Babylon.js** | https://github.com/BabylonJS/Babylon.js | Motor 3D completo con soporte WebGPU y renderizado en tiempo real. |
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
| **Silero Models** | https://github.com/snakers4/silero-models | Conjunto de modelos para TTS, ASR y VAD de alta calidad en PyTorch. |
| **edge‑tts** | https://github.com/rany2/edge-tts | Cliente Python para la API de voz de Microsoft Edge. |
| **torchaudio** | https://github.com/pytorch/audio | Librería de PyTorch para procesamiento de audio y extracción de características. |
| **librosa** | https://github.com/librosa/librosa | Biblioteca Python para análisis y visualización de audio. |
| **py‑soundfile** | https://github.com/bastibe/python-soundfile | Lectura/escritura de archivos de audio en varios formatos. |
| **Resampy** | https://github.com/bmcfee/resampy | Herramienta para resampling de audio de alta calidad. |
| **RNNoise** | https://github.com/xiph/rnnoise | Red neuronal para reducción de ruido en tiempo real. |

---

## 📦 Lista completa de todos los repositorios (475)

A continuación se muestra la tabla completa tal como aparece en **AVATAR_EVALUATION.md**. Cada fila incluye el nombre del proyecto, el repositorio y columnas para `Estado` y `Decisión` que pueden completarse durante la evaluación.

| **Opción** | **Repositorio** | **Estado** | **Decisión** |
|---|---|---|---|
| LiteAvatar | https://github.com/HumanAIGC/lite-avatar | Probado | Baseline rápido; no descartado formalmente |
| MuseTalk | https://github.com/TMElyralab/MuseTalk | Probado | Descartado por calidad visual, sincronización y comportamiento inestable |
| SoulX‑FlashHead Lite | https://github.com/Soul-AILab/SoulX-FlashHead | Probado | Descartado para esta línea de trabajo |
| EchoMimicV3‑Flash | https://github.com/antgroup/echomimic_v3 | Prueba aislada exitosa | No apto para tiempo real con nuestra GPU |
| FasterLivePortrait | https://github.com/warmshao/FasterLivePortrait | Evaluado | Ruta de audio requiere adaptador incremental propio |
| JoyVASA | https://github.com/jdh-algo/JoyVASA | Evaluado | No trae streaming conversacional listo |
| Duix‑Avatar | https://github.com/duixcom/Duix-Avatar | Evaluado | Generación de clips offline, no realtime |
| Duix‑Mobile | https://github.com/duixcom/Duix-Mobile | Evaluado | Bloqueado para nuestro stack web/WSL y licencia restrictiva |
| AVTR‑1 / Avaturn | https://github.com/avaturn-live/avtr-1 | Validado | Candidato principal |
| AvatarForcing | https://github.com/KlingAIResearch/AvatarForcing | Evaluado | Descartado por peso y licencia |
| LAM / LAM‑Audio2Expression | https://github.com/aigc3d/LAM | Prueba realtime exitosa | Candidato activo |
| OpenTalking | https://github.com/datascale-ai/opentalking | Probado E2E | Orquestador local viable |
| IMTalker | https://github.com/bigai-nlco/IMTalker | Evaluado | Ruta offline, sin streaming |
| PersonaLive | https://github.com/GVCLab/PersonaLive | Evaluado | Sin audio‑driven ni TTS |
| Ditto TalkingHead | https://github.com/antgroup/ditto-talkinghead | Evaluado | Lento en 16 GB |
| Prometheus Avatar | https://github.com/myths-labs/prometheus-avatar | Prueba integrada | Candidato activo |
| CyberVerse | https://github.com/Lynpoint/CyberVerse | Evaluado | Bloqueado por hardware y licencia GPL‑3.0 |
| ARACHNE‑X‑ULTRA‑AVATAR | https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR | Evaluado | No reproducible, requiere >128 GB |
| Livepeer Mission Control | https://docs.livepeer.org/v2/home/mission-control | Evaluado | Infraestructura distribuida, no avatar local |
| TalkingGaussian | https://github.com/Fictionarry/TalkingGaussian | Evaluado | Pipeline batch, sin streaming |
| LongCat‑Video‑Avatar 1.5 | https://github.com/meituan-longcat/LongCat-Video | Investigado | 13.6B, no viable en 16 GB |
| MultiTalk | https://github.com/MeiGen-AI/MultiTalk | Investigado | Audio‑driven, pero generación lenta |
| InfiniteTalk | https://github.com/MeiGen-AI/InfiniteTalk | Investigado | Muy alejado de realtime |
| Wan2.2‑S2V | https://github.com/Wan-Video/Wan2.2 | Investigado | 14B, sin streaming viable |
| HunyuanVideo‑Avatar | https://github.com/Tencent/HunyuanVideo-Avatar | Investigado | Pesado, licencia territorial |
| SkyReels‑V3‑A2V | https://github.com/SkyworkAI/SkyReels-V3 | Investigado | Modelo grande, sin justificación |
| HuMo | https://github.com/Phantom-video/HuMo | Investigado | 1.7B, generación de clips |
| OmniHuman | https://github.com/omnihuman-lab/omnihuman | Investigado | Sin código ni pesos oficiales |
| OpenAvatarChat | https://github.com/HumanAIGC-Engineering/OpenAvatarChat | Usado | Framework local de referencia |
| LiveKit Agents | https://github.com/livekit/agents | Investigado | Buen transporte WebRTC, necesita renderer |
| Pipecat | https://github.com/pipecat-ai/pipecat | Investigado | Alternativa de orquestación local |
| TEN Framework | https://github.com/TEN-framework/ten-framework | Investigado | Buen pipeline de audio, avatar no resuelto |
| Vision Agents | https://github.com/GetStream/Vision-Agents | Investigado | Interesante, no probada |
| LiveTalking | https://github.com/lipku/LiveTalking |  |  |
| LiveAvatar | https://github.com/Alibaba-Quark/LiveAvatar |  |  |
| LiveTalk | https://github.com/GAIR-NLP/livetalk |  |  |
| Hallo | https://github.com/fudan-generative-vision/hallo |  |  |
| Hallo2 | https://github.com/fudan-generative-vision/hallo2 |  |  |
| LivePortrait | https://github.com/KwaiVGI/LivePortrait |  |  |
| V‑Express | https://github.com/tencent-ailab/V-Express |  |  |
| LatentSync | https://github.com/bytedance/LatentSync |  |  |
| AniPortrait | https://github.com/Zejun-Yang/AniPortrait |  |  |
| SadTalker | https://github.com/OpenTalker/SadTalker |  |  |
| AniTalker | https://github.com/X-LANCE/AniTalker |  |  |
| Real3D‑Portrait | https://github.com/yerfor/Real3DPortrait |  |  |
| GeneFace++ | https://github.com/yerfor/GeneFacePlusPlus |  |  |
| SyncTalk | https://github.com/ZiqiaoPeng/SyncTalk |  |  |
| ER‑NeRF | https://github.com/Fictionarry/ER-NeRF |  |  |
| RAD‑NeRF | https://github.com/ashawkey/RAD-NeRF |  |  |
| Wav2Lip | https://github.com/Rudrabha/Wav2Lip |  |  |
| TalkingHead.js | https://github.com/met4citizen/TalkingHead |  |  |
| GaussianTalker | https://github.com/cvlab-kaist/GaussianTalker |  |  |
| SplattingAvatar | https://github.com/initialneil/SplattingAvatar |  |  |
| EchoMimic | https://github.com/antgroup/echomimic |  |  |
| LiveSpeechPortraits | https://github.com/YuanxunLu/LiveSpeechPortraits |  |  |
| AIAvatarKit | https://github.com/uezo/aiavatarkit |  |  |
| SoulX‑LiveAct | https://github.com/Soul-AILab/SoulX-LiveAct |  |  |
| Amica | https://github.com/semperai/amica |  |  |
| Linly‑Talker‑Stream | https://github.com/Kedreamix/Linly-Talker-Stream |  |  |
| Open‑LLM‑VTuber | https://github.com/Open-LLM-VTuber/Open-LLM-VTuber |  |  |
| Audio2Face 3D SDK | https://github.com/NVIDIA/Audio2Face-3D-SDK |  |  |
| Video‑Retalking | https://github.com/OpenTalker/video-retalking |  |  |
| Ultralight‑Digital‑Human | https://github.com/anliyuan/Ultralight-Digital-Human |  |  |
| EmoTaG | https://github.com/jamesdemon923/EmoTaG |  |  |
| EchoAvatar | https://github.com/RobinWitch/EchoAvatar |  |  |
| NodeAva | https://github.com/Lucasmind/nodeava |  |  |
| AI Avatar System | https://github.com/PunithVT/ai-avatar-system |  |  |
| LHM | https://github.com/aigc3d/LHM |  |  |
| FastRTC | https://github.com/gradio-app/fastrtc |  |  |
| Avatar Chat Server | https://github.com/myned-ai/avatar-chat-server |  |  |
| TalkBody4D | https://huggingface.co/datasets/PixelAI-Team/TalkBody4D |  |  |
| GMTalker | https://github.com/GML-MMGroup/GMTalker |  |  |
| ARTalk | https://github.com/xg-chu/ARTalk |  |  |
| Hallo‑Live | https://github.com/fudan-generative-vision/Hallo-Live |  |  |
| Meta‑Human | https://github.com/LessUp/meta-human |  |  |
| Ghost Vessel | https://github.com/ghdtjrtka/ghost-vessel |  |  |
| EMO | https://github.com/HumanAIGC/EMO |  |  |
| MEMO | https://github.com/memoavatar/memo |  |  |
| LetsTalk | https://github.com/zhang-haojie/letstalk |  |  |
| HelloMeme | https://github.com/HelloVision/HelloMeme |  |  |
| DAWN | https://github.com/Hanbo-Cheng/DAWN-pytorch |  |  |
| JoyHallo | https://github.com/jdh-algo/JoyHallo |  |  |
| LinguaLinker | https://github.com/TencentQQGYLab/LinguaLinker |  |  |
| EDTalk | https://github.com/tanshuai0219/EDTalk |  |  |
| Talk3D | https://github.com/KU-CVLAB/Talk3D |  |  |
| DynTet | https://github.com/zhangzc21/DynTet |  |  |
| DreamTalk | https://github.com/meitu/DreamTalk |  |  |
| GeneFace | https://github.com/yinglinjia/GeneFace |  |  |
| CodeTalker | https://github.com/zhouhangz/CodeTalker |  |  |
| Gaussian‑Head‑Avatar | https://github.com/xuchen-eth/Gaussian-Head-Avatar |  |  |
| LivePortrait‑AudioDriven | https://github.com/Hekenye/LivePortrait-AudioDriven |  |  |
| FaceFormer | https://github.com/Evelyn-yy/FaceFormer |  |  |
| MakeItTalk | https://github.com/yzhou359/MakeItTalk |  |  |
| TalkLip | https://github.com/Sxjdwang/TalkLip |  |  |
| GaussianSpeech | https://github.com/shivangi-aneja/gaussianspeech |  |  |
| GaussianHeadTalk | https://github.com/madhav-agarwal/GaussianHeadTalk |  |  |
| AD‑NeRF | https://github.com/YudongGuo/AD-NeRF |  |  |
| DFA‑NeRF | https://github.com/ShunyuYao/DFA-NeRF |  |  |
| HeadNeRF | https://github.com/CrisHY1995/headnerf |  |  |
| uLipSync | https://github.com/hecomi/uLipSync |  |  |
| ComfyStream | https://github.com/yolain/ComfyStream |  |  |
| DeepLiveCam | https://github.com/hacksider/Deep-Live-Cam |  |  |
| FaceFusion | https://github.com/facefusion/facefusion |  |  |
| Loopy | https://github.com/loopyavatar/loopy |  |  |
| ChatAvatar | https://github.com/DeemosTech/ChatAvatar |  |  |
| VividTalk | https://github.com/HumanAIGC/VividTalk |  |  |
| PIRenderer | https://github.com/RenYurui/PIRender |  |  |
| TalkSHOW | https://github.com/yhw-yhw/TalkSHOW |  |  |
| Fish Speech | https://github.com/fishaudio/fish-speech |  |  |
| CosyVoice | https://github.com/FunAudioLLM/CosyVoice |  |  |
| StyleTalk | https://github.com/FuxiVirtualHuman/styletalk |  |  |
| pixi‑live2d‑display | https://github.com/guansss/pixi-live2d-display |  |  |
| MeshTalk | https://github.com/facebookresearch/meshtalk |  |  |
| EMOCA | https://github.com/rdanecek/emoca |  |  |
| talking‑head‑anime‑3‑demo | https://github.com/pkhungurn/talking-head-anime-3-demo |  |  |
| DiffPoseTalk | https://github.com/DiffPoseTalk/DiffPoseTalk |  |  |
| FaceX‑Zoo | https://github.com/JDAI-CV/FaceX-Zoo |  |  |
| StyleHEAT | https://github.com/FeiiYin/StyleHEAT |  |  |
| First Order Motion Model | https://github.com/AliaksandrSiarohin/first-order-model |  |  |
| Neural Voice Puppetry | https://github.com/JustusThies/NeuralVoicePuppetry |  |  |
| HighSync | https://github.com/saeed5959/high_sync |  |  |
| SEDTalker | https://github.com/FarzanehJafari1987/SEDTalker |  |  |
| C‑MET | https://github.com/ChanHyeok-Choi/C-MET |  |  |
| DiFlowDubber | https://github.com/Fsoft-AIC/DiFlowDubber |  |  |
| OmniEdit | https://github.com/l1346792580123/OmniEdit |  |  |
| TempoSyncDiff | https://github.com/mazumdarsoumya/TempoSyncDiff |  |  |
| NarratingForYou | https://github.com/narratingForYou/NarratingForYou |  |  |
| DreamID‑Omni | https://github.com/Guoxu1233/DreamID-Omni |  |  |
| 3DXTalker | https://github.com/EngineeringAI-LAB/3DXTalker |  |  |
| AUHead | https://github.com/laura990501/AUHead_ICLR |  |  |
| MOVA | https://github.com/OpenMOSS/MOVA |  |  |
| SoulX‑FlashTalk | https://github.com/Soul-AILab/SoulX-FlashTalk |  |  |
| LPIPS‑AttnWip | https://github.com/FelixChan9527/LPIPS-AttnWip |  |  |
| JUST‑DUB‑IT | https://github.com/justdubit/just-dub-it |  |  |
| UA‑3DTalk | https://github.com/Mrask999/UA-3DTalk |  |  |
| THFEM | https://github.com/liluoqaq/THFEM |  |  |
| DyStream | https://github.com/RobinWitch/DyStream |  |  |
| X‑Dub | https://github.com/KlingAIResearch/X-Dub |  |  |
| TalkVerse | https://github.com/snap-research/TalkVerse |  |  |
| JoVA | https://github.com/Visual-AI/JoVA |  |  |
| STARCaster | https://github.com/foivospar/STARCaster |  |  |
| UniLS | https://github.com/xg-chu/UniLS |  |  |
| AnyTalker | https://github.com/HKUST-C4G/AnyTalker |  |  |
| LSF‑Animation | https://github.com/Dogter521/LSF-Animation |  |  |
| IASA | https://github.com/Beijia11/IASA |  |  |
| SynchroRaMa | https://github.com/novicemm/synchrorama_ |  |  |
| EmoCAST | https://github.com/GVCLab/EmoCAST |  |  |
| FantasyTalking2 | https://github.com/Fantasy-AMAP/fantasy-talking2 |  |  |
| StableAvatar | https://github.com/Francis-Rings/StableAvatar |  |  |
| MemoryTalker | https://github.com/kimhyungkyu-1208/MemoryTalker |  |  |
| ATL‑Diff | https://github.com/sonvth/ATL-Diff |  |  |
| MOSPA | https://github.com/xsy27/Mospa-Acoustic-driven-Motion-Generation |  |  |
| MEDTalk | https://github.com/SJTU-Lucy/MEDTalk |  |  |
| AnimateAnyone | https://github.com/HumanAIGC/AnimateAnyone |  |  |
| audio2photoreal | https://github.com/facebookresearch/audio2photoreal |  |  |
| HunyuanPortrait | https://github.com/Tencent/HunyuanPortrait |  |  |
| LangYing | https://github.com/langzizhixin/LangYing |  |  |
| LangYuan | https://github.com/langzizhixin/LangYuan |  |  |
| DeepFaceLive | https://github.com/iperov/DeepFaceLive |  |  |
| SyncNet | https://github.com/joonson/syncnet_python |  |  |
| Comfyui‑LivePortraitKJ | https://github.com/kijai/ComfyUI-LivePortraitKJ |  |  |
| CubismWebSDK | https://github.com/Live2D/CubismWebSDK |  |  |
| UniVRM | https://github.com/vrm-c/UniVRM |  |  |
| ChatVTuber | https://github.com/lTaGll/ChatVTuber |  |  |
| SpatialReal | https://github.com/spatialwalk/livekit-plugins-spatialreal |  |  |
| FlashAvatar | https://github.com/ustc3dv/FlashAvatar |  |  |
| RAM‑Avatar | https://github.com/Xiang-Deng00/RAM-Avatar |  |  |
| AnimatableGaussians | https://github.com/lizhe00/AnimatableGaussians |  |  |
| GauHuman | https://github.com/skhu101/GauHuman |  |  |
| NeRFBlendShape | https://github.com/USTC3DV/NeRFBlendShape-code |  |  |
| DreamGaussian | https://github.com/dreamgaussian/dreamgaussian |  |  |
| LGM | https://github.com/3DTopia/LGM |  |  |
| Splatter Image | https://github.com/szymanowiczs/splatter-image |  |  |
| live2d‑py | https://github.com/EasyLive2D/live2d-py |  |  |
| DECA | https://github.com/YadiraF/DECA |  |  |
| MICA | https://github.com/Zielonka/MICA |  |  |
| OpenFace | https://github.com/TadasBaltrusaitis/OpenFace |  |  |
| DeepFaceLab | https://github.com/iperov/DeepFaceLab |  |  |
| SenseVoice | https://github.com/FunAudioLLM/SenseVoice |  |  |
| MotionGPT | https://github.com/OpenMotionLab/MotionGPT |  |  |
| MDM | https://github.com/GuyTevet/motion-diffusion-model |  |  |
| EDGE | https://github.com/Stanford-TML/EDGE |  |  |
| SMPL‑X | https://github.com/vchoutas/smplx |  |  |
| PyMAF‑X | https://github.com/HongwenZhang/PyMAF-X |  |  |
| 4D‑Humans | https://github.com/shubham-goel/4D-Humans |  |  |
| CLIFF | https://github.com/ZhengDong-Work/CLIFF |  |  |
| ExPose | https://github.com/vchoutas/expose |  |  |
| Ultravox | https://github.com/fixie-ai/ultravox |  |  |
| Mini‑Omni | https://github.com/gpt-omni/mini-omni |  |  |
| GLM‑4‑Voice | https://github.com/THUDM/GLM-4-Voice |  |  |
| Qwen2‑Audio | https://github.com/Qwen/Qwen2-Audio |  |  |
| LiveKit | https://github.com/livekit/livekit |  |  |
| Daily Python | https://github.com/daily-co/daily-python |  |  |
| OWT Server | https://github.com/open-webrtc-toolkit/owt-server |  |  |
| three‑vrm | https://github.com/pixiv/three-vrm |  |  |
| kalidoface | https://github.com/yeemachine/kalidoface |  |  |
| live2d‑widget | https://github.com/stevenjoezhang/live2d-widget |  |  |
| OpenSeeFace | https://github.com/emilianavt/OpenSeeFace |  |  |
| VTubeStudio | https://github.com/DenchiSoft/VTubeStudio |  |  |
| pyvts | https://github.com/DenverCoder1/pyvts |  |  |
| Comfyui‑SadTalker | https://github.com/haomole/Comfyui-SadTalker |  |  |
| ComfyUI‑MuseTalk_FSH | https://github.com/AIFSH/ComfyUI-MuseTalk_FSH |  |  |
| comfyui_openvino | https://github.com/openvino-dev-samples/comfyui_openvino |  |  |
| VideoHelperSuite | https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite |  |  |
| HumanNeRF | https://github.com/chungyiweng/humannerf |  |  |
| FreeMan | https://github.com/wangjiongw/FreeMan_API |  |  |
| MRAA | https://github.com/snap-research/articulated-animation |  |  |
| TPSMM | https://github.com/yoyo-nb/Thin-Plate-Spline-Motion-Model |  |  |
| LIA | https://github.com/wyhsirius/LIA |  |  |
| face‑vid2vid | https://github.com/NVlabs/face-vid2vid |  |  |
| EG3D | https://github.com/NVlabs/eg3d |  |  |
| PanoHead | https://github.com/sizhean/panohead |  |  |
| Next3D | https://github.com/MrTornado24/Next3D |  |  |
| AvatarCraft | https://github.com/songrise/avatarcraft |  |  |
| PointAvatar | https://github.com/zhengyuf/pointavatar |  |  |
| EVA3D | https://github.com/hongfz16/EVA3D |  |  |
... (continuará hasta el final) |

---

*Este README sirve como referencia rápida para decidir qué componentes integrar en la arquitectura del avatar en tiempo real.*
