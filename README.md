# Ecosistema de Avatares e Infraestructura Conversacional Real-Time

Este documento reúne los **579 proyectos open-source** evaluados en , organizados de forma estrictamente jerárquica desde los **frameworks conversacionales de suite completa (end-to-end)** hasta los **componentes de bajo nivel y motores de inferencia**.

## 1️⃣ Frameworks y Suites Conversacionales End-to-End
*Frameworks que ofrecen la suite completa para avatares conversacionales, agentes de voz interactivos y sistemas end-to-end.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **Prometheus Avatar** | [myths-labs/prometheus-avatar](https://github.com/myths-labs/prometheus-avatar) | **[Prueba integrada exitosa]** Candidato activo: Live2D vertical conectado a micrófono, STT, LLM, TTS, WebRTC y lipsync |
| **OpenAvatarChat** | [HumanAIGC-Engineering/OpenAvatarChat](https://github.com/HumanAIGC-Engineering/OpenAvatarChat) | **[Usado]** Framework local de referencia para integrar audio, WebRTC y avatares |
| **TEN Framework** | [TEN-framework/ten-framework](https://github.com/TEN-framework/ten-framework) | **[Investigado]** Buen pipeline de audio; avatar local no resuelto |
| **Vision Agents** | [GetStream/Vision-Agents](https://github.com/GetStream/Vision-Agents) | **[Investigado]** Alternativa interesante con transporte local; no probada |
| **AIAvatarKit** | [uezo/aiavatarkit](https://github.com/uezo/aiavatarkit) | SDK en Python para construir avatares conversacionales IA combinando OpenAI LLMs, VRM y TTS. |
| **Amica** | [semperai/amica](https://github.com/semperai/amica) | Interfaz web interactiva 3D para conversar con avatares VRM utilizando modelos local o de la nube. |
| **Linly-Talker-Stream** | [Kedreamix/Linly-Talker-Stream](https://github.com/Kedreamix/Linly-Talker-Stream) | Sistema completo conversacional que integra LLMs, TTS y sincronización de avatar parlante en streaming. |
| **Open-LLM-VTuber** | [Open-LLM-VTuber/Open-LLM-VTuber](https://github.com/Open-LLM-VTuber/Open-LLM-VTuber) | Avatar VTuber conversacional impulsado por LLMs locales y renderizado VRM. |
| **Ultralight-Digital-Human** | [anliyuan/Ultralight-Digital-Human](https://github.com/anliyuan/Ultralight-Digital-Human) | Implementación ultraligera de humano digital para dispositivos de bajos recursos. |
| **NodeAva** | [Lucasmind/nodeava](https://github.com/Lucasmind/nodeava) | Plataforma Node.js para despliegue de avatares conversacionales interactivos. |
| **AI Avatar System** | [PunithVT/ai-avatar-system](https://github.com/PunithVT/ai-avatar-system) | Sistema integrado de avatar interactivo conversacional. |
| **Avatar Chat Server** | [myned-ai/avatar-chat-server](https://github.com/myned-ai/avatar-chat-server) | Servidor de backend para gestión de sesiones y streaming de audio/video para avatares. |
| **Meta-Human** | [LessUp/meta-human](https://github.com/LessUp/meta-human) | Framework para integración de avatares hiperrealistas y pipelines de streaming. |
| **Ghost Vessel** | [ghdtjrtka/ghost-vessel](https://github.com/ghdtjrtka/ghost-vessel) | Cliente y servidor de renderizado de avatares con baja latencia. |
| **LinguaLinker** | [TencentQQGYLab/LinguaLinker](https://github.com/TencentQQGYLab/LinguaLinker) | Librería de enlace conversacional multilingüe para sistemas de voz y avatar. |
| **NarratingForYou** | [narratingForYou/NarratingForYou](https://github.com/narratingForYou/NarratingForYou) | Sistema de narración y sincronización de avatares a partir de texto o audio. |
| **JUST-DUB-IT** | [justdubit/just-dub-it](https://github.com/justdubit/just-dub-it) | Pipeline de doblaje y sincronización labial automatizada sobre videos. |
| **ChatVTuber** | [lTaGll/ChatVTuber](https://github.com/lTaGll/ChatVTuber) | Agente VTuber interactivo para streaming en vivo con reconocimiento de voz y respuesta parlante. |
| **Surge** | [Darussalamnoor/surge](https://github.com/Darussalamnoor/surge) | Motor de orquestación conversacional y agentes de voz en tiempo real. |
| **Bolna** | [bolna-ai/bolna](https://github.com/bolna-ai/bolna) | Framework open-source para construir agentes conversacionales de voz y video en tiempo real. |
| **TEN Agent** | [TEN-framework/TEN-Agent](https://github.com/TEN-framework/TEN-Agent) | Agente multimodal de tiempo real construido sobre TEN Framework. |
| **realtime-ai (RTVI)** | [realtime-ai/realtime-ai](https://github.com/realtime-ai/realtime-ai) | **[Evaluado]** Estándar abierto y framework para pipelines de inferencia de voz y video en tiempo real sobre WebRTC. |
| **TalkingFace** | [tien02/talking-face](https://github.com/tien02/talking-face) | **[Evaluado]** Pipeline end-to-end de generación de video parlante acelerado por TensorRT con transmisión WebRTC. |
| **LangQing** | [langzizhixin/LangQing](https://github.com/langzizhixin/LangQing) | **[Evaluado]** Plataforma de humanos digitales interactivos en tiempo real (<500ms latencia) para avatares 2D/2.5D/3D sobre WebRTC. |
| **Riverst** | [Riverst/Riverst](https://github.com/Riverst/Riverst) | **[Evaluado]** Plataforma de conversación avatar-usuario con lip-sync en tiempo real y transmisión WebRTC. |
| **Vibe AI Partner** | [vibe-ai/vibe-ai-partner](https://github.com/vibe-ai/vibe-ai-partner) | **[Evaluado]** Plataforma de avatares de escritorio con soporte para modelos Live2D y VRM con memoria activa. |
| **CrewAI** | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | **[Evaluado]** Framework para orquestación de agentes IA autónomos y herramientas de voz. |
| **AutoGen** | [microsoft/autogen](https://github.com/microsoft/autogen) | **[Evaluado]** Framework de Microsoft para sistemas conversacionales de múltiples agentes de IA. |
| **LangChain** | [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | **[Evaluado]** Framework para desarrollo de aplicaciones impulsadas por LLMs y conectores de voz. |
| **Semantic Kernel** | [microsoft/semantic-kernel](https://github.com/microsoft/semantic-kernel) | **[Evaluado]** SDK de Microsoft para integrar LLMs y plugins de audio en C#, Python y Java. |

## 2️⃣ Generación y Animación de Avatar 2D/3D & Talking Heads
*Modelos de IA de generación de video facial, sincronización labial (lip-sync), NeRF, 3D Gaussian Splatting y animación guiada por audio/video.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **LiteAvatar** | [HumanAIGC/lite-avatar](https://github.com/HumanAIGC/lite-avatar) | **[Probado]** Baseline rápido; no descartado formalmente |
| **MuseTalk** | [TMElyralab/MuseTalk](https://github.com/TMElyralab/MuseTalk) | **[Probado]** Descartado por calidad visual, sincronización y comportamiento inestable en nuestro stack |
| **SoulX-FlashHead Lite** | [Soul-AILab/SoulX-FlashHead](https://github.com/Soul-AILab/SoulX-FlashHead) | **[Probado]** Descartado para esta línea de trabajo |
| **EchoMimicV3-Flash** | [antgroup/echomimic_v3](https://github.com/antgroup/echomimic_v3) | **[Prueba aislada exitosa]** No apto para tiempo real con nuestra GPU; queda para offline/híbrido |
| **FasterLivePortrait** | [warmshao/FasterLivePortrait](https://github.com/warmshao/FasterLivePortrait) | **[Evaluado]** La ruta de audio requiere un adaptador incremental propio; la ruta lista depende de cámara/video |
| **JoyVASA** | [jdh-algo/JoyVASA](https://github.com/jdh-algo/JoyVASA) | **[Evaluado]** Se podría reutilizar por ventanas, pero no trae streaming conversacional listo |
| **Duix-Avatar** | [duixcom/Duix-Avatar](https://github.com/duixcom/Duix-Avatar) | **[Evaluado]** Descartado: generación de clips offline, explícitamente no realtime |
| **Duix-Mobile** | [duixcom/Duix-Mobile](https://github.com/duixcom/Duix-Mobile) | **[Evaluado]** Candidato experimental Android; bloqueado para nuestro stack web/WSL y con licencia restrictiva |
| **AVTR-1 / Avaturn** | [avaturn-live/avtr-1](https://github.com/avaturn-live/avtr-1) | **[Validado]** **Candidato principal**: renderer incremental, dual-stream, avatar independiente y conversación local en español |
| **AvatarForcing** | [KlingAIResearch/AvatarForcing](https://github.com/KlingAIResearch/AvatarForcing) | **[Evaluado]** Descartado para 16 GB: pesado, lento y con licencia no apta para nuestro uso |
| **LAM / LAM-Audio2Expression** | [aigc3d/LAM](https://github.com/aigc3d/LAM) | **[Prueba realtime exitosa]** Candidato activo: audio → blendshapes ARKit → renderer Gaussian/WebGL |
| **OpenTalking** | [datascale-ai/opentalking](https://github.com/datascale-ai/opentalking) | **[Probado E2E]** Orquestador local viable de voz/WebRTC; Wav2Lip queda como prototipo funcional, no solución final |
| **IMTalker** | [bigai-nlco/IMTalker](https://github.com/bigai-nlco/IMTalker) | **[Evaluado]** Descartado: ruta oficial offline/batch, sin streaming conversacional reutilizable |
| **PersonaLive** | [GVCLab/PersonaLive](https://github.com/GVCLab/PersonaLive) | **[Evaluado]** Descartado: streaming basado en imagen/video, sin audio-driven, TTS ni STT; además declara uso académico |
| **Ditto TalkingHead** | [antgroup/ditto-talkinghead](https://github.com/antgroup/ditto-talkinghead) | **[Evaluado]** Streaming técnico verificado, pero demasiado lento en 16 GB y sin salida WebRTC/frame queue lista |
| **CyberVerse** | [Lynpoint/CyberVerse](https://github.com/Lynpoint/CyberVerse) | **[Evaluado]** Arquitectura full-duplex interesante, pero bloqueada por hardware objetivo y licencia GPL-3.0 |
| **ARACHNE-X-ULTRA-AVATAR** | [HF: ARACHNE-X-ULTRA-AVATAR](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR) | **[Evaluado]** Descartado: sin runtime reproducible, más de 128 GB y fuera de nuestra GPU de 16 GB |
| **TalkingGaussian** | [Fictionarry/TalkingGaussian](https://github.com/Fictionarry/TalkingGaussian) | **[Evaluado]** Descartado: pipeline batch por identidad, sin streaming conversacional ni entorno compatible |
| **LongCat-Video-Avatar 1.5** | [meituan-longcat/LongCat-Video](https://github.com/meituan-longcat/LongCat-Video) | **[Investigado]** MIT y 8 pasos, pero 13.6B y orientado a clips; no viable en 16 GB para conversación |
| **MultiTalk** | [MeiGen-AI/MultiTalk](https://github.com/MeiGen-AI/MultiTalk) | **[Investigado]** Audio-driven y Apache-2.0, pero generación por clips demasiado lenta para vivo |
| **InfiniteTalk** | [MeiGen-AI/InfiniteTalk](https://github.com/MeiGen-AI/InfiniteTalk) | **[Investigado]** Video largo audio-driven, pero muy alejado de realtime en GPU de consumo |
| **Wan2.2-S2V** | [Wan-Video/Wan2.2](https://github.com/Wan-Video/Wan2.2) | **[Investigado]** Ecosistema amplio, pero 14B y sin streaming conversacional viable en 16 GB |
| **HunyuanVideo-Avatar** | [Tencent-Hunyuan/HunyuanVideo-Avatar](https://github.com/Tencent-Hunyuan/HunyuanVideo-Avatar) | **[Investigado]** Muy pesado, lento y con licencia territorial incompatible con la UE |
| **SkyReels-V3-A2V** | [SkyworkAI/SkyReels-V3](https://github.com/SkyworkAI/SkyReels-V3) | **[Investigado]** Modelo grande y licencia comunitaria; sin justificación para 16 GB |
| **HuMo** | [Phantom-video/HuMo](https://github.com/Phantom-video/HuMo) | **[Investigado]** 1.7B disponible, pero generación de clips; no renderer incremental probado |
| **OmniHuman** | [Project page](https://omnihuman-lab.github.io/) | **[Investigado]** Sin código ni pesos oficiales; únicamente servicio/API cerrado |
| **LiveTalking** | [lipku/LiveTalking](https://github.com/lipku/LiveTalking) | Generación de video parlante en streaming con soporte para entradas de audio y modelos de difución/GAN en tiempo real. |
| **LiveAvatar** | [Alibaba-Quark/LiveAvatar](https://github.com/Alibaba-Quark/LiveAvatar) | Framework de avatar digital parlante en vivo desarrollado por Alibaba para interacción conversacional. |
| **LiveTalk** | [GAIR-NLP/livetalk](https://github.com/GAIR-NLP/livetalk) | Sistema conversacional de avatar en tiempo real guiado por audio y modelos de lenguaje. |
| **Hallo** | [fudan-generative-vision/hallo](https://github.com/fudan-generative-vision/hallo) | Modelo de difusión guiado por audio para generación de retratos parlantes con expresividad emocional. |
| **Hallo2** | [fudan-generative-vision/hallo2](https://github.com/fudan-generative-vision/hallo2) | Segunda versión de Hallo con mayor resolución, sincronización labial mejorada y control temporal largo. |
| **LivePortrait** | [KwaiVGI/LivePortrait](https://github.com/KwaiVGI/LivePortrait) | Modelo de animación portrait eficiente basado en control de landmarks faciales y flujo de movimiento. |
| **V-Express** | [tencent-ailab/V-Express](https://github.com/tencent-ailab/V-Express) | Pipeline de retratos parlantes que utiliza múltiples señales de control (audio, pose, expresión). |
| **LatentSync** | [bytedance/LatentSync](https://github.com/bytedance/LatentSync) | Sincronización labial (lip-sync) en espacio latente basada en modelos de difusión para video. |
| **AniPortrait** | [Zejun-Yang/AniPortrait](https://github.com/Zejun-Yang/AniPortrait) | Generación de avatares fotorealistas y de anime animados mediante mapas de pose y audio. |
| **SadTalker** | [OpenTalker/SadTalker](https://github.com/OpenTalker/SadTalker) | Modelo clásico de generación de avatares 2D parlantes guiados por coeficientes 3DMM a partir de audio de entrada. |
| **AniTalker** | [X-LANCE/AniTalker](https://github.com/X-LANCE/AniTalker) | Animación facial expresiva para avatares 2D con movimiento dinámico de cabeza. |
| **Real3D-Portrait** | [yerfor/Real3DPortrait](https://github.com/yerfor/Real3DPortrait) | Reconstrucción y renderizado 3D de retratos parlantes en tiempo real con control de pose 3D completo. |
| **GeneFace++** | [yerfor/GeneFacePlusPlus](https://github.com/yerfor/GeneFacePlusPlus) | Generador NeRF facial guiado por audio para interacción parlante en tiempo real con alta fidelidad. |
| **SyncTalk** | [ZiqiaoPeng/SyncTalk](https://github.com/ZiqiaoPeng/SyncTalk) | Sincronización labial y movimiento de cabeza photorealista 3D mediante representaciones NeRF de alta precisión. |
| **ER-NeRF** | [Fictionarry/ER-NeRF](https://github.com/Fictionarry/ER-NeRF) | Modelo NeRF eficiente acelerado por Hash Grid para retratos parlantes en tiempo real. |
| **RAD-NeRF** | [ashawkey/RAD-NeRF](https://github.com/ashawkey/RAD-NeRF) | NeRF audiorrefinado para sintetizar retratos parlantes con latencia ultrabaja en GPUs de consumo. |
| **Wav2Lip** | [Rudrabha/Wav2Lip](https://github.com/Rudrabha/Wav2Lip) | Modelo ampliamente utilizado para sincronización labial precisa de audios sobre cualquier video de rostro. |
| **TalkingHead.js** | [met4citizen/TalkingHead](https://github.com/met4citizen/TalkingHead) | Librería JavaScript ligera para renderizar avatares 3D parlantes directamente en el navegador con WebGL. |
| **GaussianTalker** | [cvlab-kaist/GaussianTalker](https://github.com/cvlab-kaist/GaussianTalker) | Avatar parlante 3D basado en 3D Gaussian Splatting animado por audio en tiempo real. |
| **SplattingAvatar** | [initialneil/SplattingAvatar](https://github.com/initialneil/SplattingAvatar) | Representación de avatares humanos 3D dinámicos mediante 3D Gaussian Splatting animables. |
| **EchoMimic** | [antgroup/echomimic](https://github.com/antgroup/echomimic) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EchoMimic). |
| **LiveSpeechPortraits** | [YuanxunLu/LiveSpeechPortraits](https://github.com/YuanxunLu/LiveSpeechPortraits) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LiveSpeechPortraits). |
| **SoulX-LiveAct** | [Soul-AILab/SoulX-LiveAct](https://github.com/Soul-AILab/SoulX-LiveAct) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (SoulX-LiveAct). |
| **Audio2Face 3D SDK** | [NVIDIA/Audio2Face-3D-SDK](https://github.com/NVIDIA/Audio2Face-3D-SDK) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Audio2Face 3D SDK). |
| **Video-Retalking** | [OpenTalker/video-retalking](https://github.com/OpenTalker/video-retalking) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Video-Retalking). |
| **EmoTaG** | [jamesdemon923/EmoTaG](https://github.com/jamesdemon923/EmoTaG) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EmoTaG). |
| **EchoAvatar** | [RobinWitch/EchoAvatar](https://github.com/RobinWitch/EchoAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EchoAvatar). |
| **LHM** | [aigc3d/LHM](https://github.com/aigc3d/LHM) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LHM). |
| **TalkBody4D** | [HF: PixelAI-Team/TalkBody4D](https://huggingface.co/datasets/PixelAI-Team/TalkBody4D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TalkBody4D). |
| **GMTalker** | [GML-MMGroup/GMTalker](https://github.com/GML-MMGroup/GMTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (GMTalker). |
| **ARTalk** | [xg-chu/ARTalk](https://github.com/xg-chu/ARTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (ARTalk). |
| **Hallo-Live** | [fudan-generative-vision/Hallo-Live](https://github.com/fudan-generative-vision/Hallo-Live) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Hallo-Live). |
| **EMO** | [HumanAIGC/EMO](https://github.com/HumanAIGC/EMO) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EMO). |
| **MEMO** | [memoavatar/memo](https://github.com/memoavatar/memo) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MEMO). |
| **LetsTalk** | [zhang-haojie/letstalk](https://github.com/zhang-haojie/letstalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LetsTalk). |
| **HelloMeme** | [HelloVision/HelloMeme](https://github.com/HelloVision/HelloMeme) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HelloMeme). |
| **DAWN** | [Hanbo-Cheng/DAWN-pytorch](https://github.com/Hanbo-Cheng/DAWN-pytorch) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DAWN). |
| **JoyHallo** | [jdh-algo/JoyHallo](https://github.com/jdh-algo/JoyHallo) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (JoyHallo). |
| **EDTalk** | [tanshuai0219/EDTalk](https://github.com/tanshuai0219/EDTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EDTalk). |
| **Talk3D** | [KU-CVLAB/Talk3D](https://github.com/KU-CVLAB/Talk3D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Talk3D). |
| **DynTet** | [zhangzc21/DynTet](https://github.com/zhangzc21/DynTet) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DynTet). |
| **DreamTalk** | [meitu/DreamTalk](https://github.com/meitu/DreamTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DreamTalk). |
| **GeneFace** | [yinglinjia/GeneFace](https://github.com/yinglinjia/GeneFace) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (GeneFace). |
| **CodeTalker** | [zhouhangz/CodeTalker](https://github.com/zhouhangz/CodeTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (CodeTalker). |
| **Gaussian-Head-Avatar** | [xuchen-eth/Gaussian-Head-Avatar](https://github.com/xuchen-eth/Gaussian-Head-Avatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Gaussian-Head-Avatar). |
| **LivePortrait-AudioDriven** | [Hekenye/LivePortrait-AudioDriven](https://github.com/Hekenye/LivePortrait-AudioDriven) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LivePortrait-AudioDriven). |
| **FaceFormer** | [Evelyn-yy/FaceFormer](https://github.com/Evelyn-yy/FaceFormer) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (FaceFormer). |
| **MakeItTalk** | [yzhou359/MakeItTalk](https://github.com/yzhou359/MakeItTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MakeItTalk). |
| **TalkLip** | [Sxjdwang/TalkLip](https://github.com/Sxjdwang/TalkLip) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TalkLip). |
| **GaussianSpeech** | [shivangi-aneja/gaussianspeech](https://github.com/shivangi-aneja/gaussianspeech) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (GaussianSpeech). |
| **GaussianHeadTalk** | [madhav-agarwal/GaussianHeadTalk](https://github.com/madhav-agarwal/GaussianHeadTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (GaussianHeadTalk). |
| **AD-NeRF** | [YudongGuo/AD-NeRF](https://github.com/YudongGuo/AD-NeRF) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AD-NeRF). |
| **DFA-NeRF** | [ShunyuYao/DFA-NeRF](https://github.com/ShunyuYao/DFA-NeRF) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DFA-NeRF). |
| **HeadNeRF** | [CrisHY1995/headnerf](https://github.com/CrisHY1995/headnerf) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HeadNeRF). |
| **DeepLiveCam** | [hacksider/Deep-Live-Cam](https://github.com/hacksider/Deep-Live-Cam) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DeepLiveCam). |
| **FaceFusion** | [facefusion/facefusion](https://github.com/facefusion/facefusion) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (FaceFusion). |
| **ChatAvatar** | [DeemosTech/ChatAvatar](https://github.com/DeemosTech/ChatAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (ChatAvatar). |
| **VividTalk** | [HumanAIGC/VividTalk](https://github.com/HumanAIGC/VividTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (VividTalk). |
| **PIRenderer** | [RenYurui/PIRender](https://github.com/RenYurui/PIRender) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PIRenderer). |
| **TalkSHOW** | [yhw-yhw/TalkSHOW](https://github.com/yhw-yhw/TalkSHOW) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TalkSHOW). |
| **StyleTalk** | [FuxiVirtualHuman/styletalk](https://github.com/FuxiVirtualHuman/styletalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (StyleTalk). |
| **MeshTalk** | [facebookresearch/meshtalk](https://github.com/facebookresearch/meshtalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MeshTalk). |
| **EMOCA** | [rdanecek/emoca](https://github.com/rdanecek/emoca) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EMOCA). |
| **talking-head-anime-3-demo** | [pkhungurn/talking-head-anime-3-demo](https://github.com/pkhungurn/talking-head-anime-3-demo) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (talking-head-anime-3-demo). |
| **DiffPoseTalk** | [DiffPoseTalk/DiffPoseTalk](https://github.com/DiffPoseTalk/DiffPoseTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DiffPoseTalk). |
| **StyleHEAT** | [FeiiYin/StyleHEAT](https://github.com/FeiiYin/StyleHEAT) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (StyleHEAT). |
| **First Order Motion Model** | [AliaksandrSiarohin/first-order-model](https://github.com/AliaksandrSiarohin/first-order-model) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (First Order Motion Model). |
| **Neural Voice Puppetry** | [JustusThies/NeuralVoicePuppetry](https://github.com/JustusThies/NeuralVoicePuppetry) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Neural Voice Puppetry). |
| **HighSync** | [saeed5959/high_sync](https://github.com/saeed5959/high_sync) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HighSync). |
| **SEDTalker** | [FarzanehJafari1987/SEDTalker](https://github.com/FarzanehJafari1987/SEDTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (SEDTalker). |
| **C-MET** | [ChanHyeok-Choi/C-MET](https://github.com/ChanHyeok-Choi/C-MET) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (C-MET). |
| **DiFlowDubber** | [Fsoft-AIC/DiFlowDubber](https://github.com/Fsoft-AIC/DiFlowDubber) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DiFlowDubber). |
| **OmniEdit** | [l1346792580123/OmniEdit](https://github.com/l1346792580123/OmniEdit) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (OmniEdit). |
| **TempoSyncDiff** | [mazumdarsoumya/TempoSyncDiff](https://github.com/mazumdarsoumya/TempoSyncDiff) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TempoSyncDiff). |
| **DreamID-Omni** | [Guoxu1233/DreamID-Omni](https://github.com/Guoxu1233/DreamID-Omni) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DreamID-Omni). |
| **3DXTalker** | [EngineeringAI-LAB/3DXTalker](https://github.com/EngineeringAI-LAB/3DXTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (3DXTalker). |
| **AUHead** | [laura990501/AUHead_ICLR](https://github.com/laura990501/AUHead_ICLR) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AUHead). |
| **MOVA** | [OpenMOSS/MOVA](https://github.com/OpenMOSS/MOVA) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MOVA). |
| **SoulX-FlashTalk** | [Soul-AILab/SoulX-FlashTalk](https://github.com/Soul-AILab/SoulX-FlashTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (SoulX-FlashTalk). |
| **UA-3DTalk** | [Mrask999/UA-3DTalk](https://github.com/Mrask999/UA-3DTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (UA-3DTalk). |
| **THFEM** | [liluoqaq/THFEM](https://github.com/liluoqaq/THFEM) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (THFEM). |
| **DyStream** | [RobinWitch/DyStream](https://github.com/RobinWitch/DyStream) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DyStream). |
| **X-Dub** | [KlingAIResearch/X-Dub](https://github.com/KlingAIResearch/X-Dub) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (X-Dub). |
| **TalkVerse** | [snap-research/TalkVerse](https://github.com/snap-research/TalkVerse) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TalkVerse). |
| **JoVA** | [Visual-AI/JoVA](https://github.com/Visual-AI/JoVA) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (JoVA). |
| **STARCaster** | [foivospar/STARCaster](https://github.com/foivospar/STARCaster) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (STARCaster). |
| **UniLS** | [xg-chu/UniLS](https://github.com/xg-chu/UniLS) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (UniLS). |
| **AnyTalker** | [HKUST-C4G/AnyTalker](https://github.com/HKUST-C4G/AnyTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AnyTalker). |
| **LSF-Animation** | [Dogter521/LSF-Animation](https://github.com/Dogter521/LSF-Animation) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LSF-Animation). |
| **IASA** | [Beijia11/IASA](https://github.com/Beijia11/IASA) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (IASA). |
| **EmoCAST** | [GVCLab/EmoCAST](https://github.com/GVCLab/EmoCAST) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EmoCAST). |
| **FantasyTalking2** | [Fantasy-AMAP/fantasy-talking2](https://github.com/Fantasy-AMAP/fantasy-talking2) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (FantasyTalking2). |
| **StableAvatar** | [Francis-Rings/StableAvatar](https://github.com/Francis-Rings/StableAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (StableAvatar). |
| **MemoryTalker** | [kimhyungkyu-1208/MemoryTalker](https://github.com/kimhyungkyu-1208/MemoryTalker) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MemoryTalker). |
| **ATL-Diff** | [sonvth/ATL-Diff](https://github.com/sonvth/ATL-Diff) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (ATL-Diff). |
| **MOSPA** | [xsy27/Mospa-Acoustic-driven-Motion-Generation](https://github.com/xsy27/Mospa-Acoustic-driven-Motion-Generation) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MOSPA). |
| **MEDTalk** | [SJTU-Lucy/MEDTalk](https://github.com/SJTU-Lucy/MEDTalk) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MEDTalk). |
| **AnimateAnyone** | [HumanAIGC/AnimateAnyone](https://github.com/HumanAIGC/AnimateAnyone) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AnimateAnyone). |
| **audio2photoreal** | [facebookresearch/audio2photoreal](https://github.com/facebookresearch/audio2photoreal) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (audio2photoreal). |
| **HunyuanPortrait** | [Tencent/HunyuanPortrait](https://github.com/Tencent/HunyuanPortrait) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HunyuanPortrait). |
| **LangYing** | [langzizhixin/LangYing](https://github.com/langzizhixin/LangYing) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LangYing). |
| **LangYuan** | [langzizhixin/LangYuan](https://github.com/langzizhixin/LangYuan) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LangYuan). |
| **SyncNet** | [joonson/syncnet_python](https://github.com/joonson/syncnet_python) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (SyncNet). |
| **SpatialReal** | [spatialwalk/livekit-plugins-spatialreal](https://github.com/spatialwalk/livekit-plugins-spatialreal) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (SpatialReal). |
| **FlashAvatar** | [ustc3dv/FlashAvatar](https://github.com/ustc3dv/FlashAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (FlashAvatar). |
| **RAM-Avatar** | [Xiang-Deng00/RAM-Avatar](https://github.com/Xiang-Deng00/RAM-Avatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (RAM-Avatar). |
| **AnimatableGaussians** | [lizhe00/AnimatableGaussians](https://github.com/lizhe00/AnimatableGaussians) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AnimatableGaussians). |
| **GauHuman** | [skhu101/GauHuman](https://github.com/skhu101/GauHuman) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (GauHuman). |
| **NeRFBlendShape** | [USTC3DV/NeRFBlendShape-code](https://github.com/USTC3DV/NeRFBlendShape-code) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (NeRFBlendShape). |
| **DreamGaussian** | [dreamgaussian/dreamgaussian](https://github.com/dreamgaussian/dreamgaussian) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DreamGaussian). |
| **LGM** | [3DTopia/LGM](https://github.com/3DTopia/LGM) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LGM). |
| **Splatter Image** | [szymanowiczs/splatter-image](https://github.com/szymanowiczs/splatter-image) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Splatter Image). |
| **HumanNeRF** | [chungyiweng/humannerf](https://github.com/chungyiweng/humannerf) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HumanNeRF). |
| **FreeMan** | [wangjiongw/FreeMan_API](https://github.com/wangjiongw/FreeMan_API) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (FreeMan). |
| **MRAA** | [snap-research/articulated-animation](https://github.com/snap-research/articulated-animation) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (MRAA). |
| **TPSMM** | [yoyo-nb/Thin-Plate-Spline-Motion-Model](https://github.com/yoyo-nb/Thin-Plate-Spline-Motion-Model) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TPSMM). |
| **LIA** | [wyhsirius/LIA](https://github.com/wyhsirius/LIA) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LIA). |
| **face-vid2vid** | [NVlabs/face-vid2vid](https://github.com/NVlabs/face-vid2vid) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (face-vid2vid). |
| **EG3D** | [NVlabs/eg3d](https://github.com/NVlabs/eg3d) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EG3D). |
| **PanoHead** | [sizhean/panohead](https://github.com/sizhean/panohead) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PanoHead). |
| **Next3D** | [MrTornado24/Next3D](https://github.com/MrTornado24/Next3D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Next3D). |
| **AvatarCraft** | [songrise/avatarcraft](https://github.com/songrise/avatarcraft) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AvatarCraft). |
| **PointAvatar** | [zhengyuf/pointavatar](https://github.com/zhengyuf/pointavatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PointAvatar). |
| **EVA3D** | [hongfz16/EVA3D](https://github.com/hongfz16/EVA3D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (EVA3D). |
| **AvatarCLIP** | [hongfz16/AvatarCLIP](https://github.com/hongfz16/AvatarCLIP) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AvatarCLIP). |
| **Latent-NeRF** | [eladrich/latent-nerf](https://github.com/eladrich/latent-nerf) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Latent-NeRF). |
| **AG3D** | [zj-dong/AG3D](https://github.com/zj-dong/AG3D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AG3D). |
| **Get3DHuman** | [X-zhangyang/Get3DHuman](https://github.com/X-zhangyang/Get3DHuman) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Get3DHuman). |
| **TADA** | [TingtingLiao/TADA](https://github.com/TingtingLiao/TADA) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TADA). |
| **RodinHD** | [RodinHD/RodinHD](https://github.com/RodinHD/RodinHD) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (RodinHD). |
| **HumanNorm** | [xhuangcv/humannorm](https://github.com/xhuangcv/humannorm) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (HumanNorm). |
| **PrimDiffusion** | [FrozenBurning/PrimDiffusion](https://github.com/FrozenBurning/PrimDiffusion) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PrimDiffusion). |
| **XAGen** | [magic-research/xagen](https://github.com/magic-research/xagen) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (XAGen). |
| **TalkinNeRF** | [aggelinacha/talkinnerf](https://github.com/aggelinacha/talkinnerf) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (TalkinNeRF). |
| **StyleAvatar3D** | [icoz69/StyleAvatar3D](https://github.com/icoz69/StyleAvatar3D) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (StyleAvatar3D). |
| **LatentAvatar** | [YuelangX/LatentAvatar](https://github.com/YuelangX/LatentAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LatentAvatar). |
| **NeRSemble** | [tobias-kirschstein/nersemble](https://github.com/tobias-kirschstein/nersemble) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (NeRSemble). |
| **OTAvatar** | [theEricMa/OTAvatar](https://github.com/theEricMa/OTAvatar) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (OTAvatar). |
| **ClipFace** | [shivangi-aneja/ClipFace](https://github.com/shivangi-aneja/ClipFace) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (ClipFace). |
| **AvatarMe** | [lattas/AvatarMe](https://github.com/lattas/AvatarMe) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AvatarMe). |
| **NeRFEditor** | [Chuny1/NeRFEditor](https://github.com/Chuny1/NeRFEditor) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (NeRFEditor). |
| **3DGS-Avatar** | [mikeqzy/3dgs-avatar-release](https://github.com/mikeqzy/3dgs-avatar-release) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (3DGS-Avatar). |
| **ExAvatar** | [mks0601/ExAvatar_RELEASE](https://github.com/mks0601/ExAvatar_RELEASE) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (ExAvatar). |
| **face-api.js** | [justadudewhohacks/face-api.js](https://github.com/justadudewhohacks/face-api.js) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (face-api.js). |
| **clmtrackr** | [auduno/clmtrackr](https://github.com/auduno/clmtrackr) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (clmtrackr). |
| **jeelizFaceFilter** | [jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (jeelizFaceFilter). |
| **tfjs-models** | [tensorflow/tfjs-models](https://github.com/tensorflow/tfjs-models) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (tfjs-models). |
| **DiffGesture** | [Advocate99/DiffGesture](https://github.com/Advocate99/DiffGesture) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (DiffGesture). |
| **StyleSync** | [guanjz20/StyleSync](https://github.com/guanjz20/StyleSync) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (StyleSync). |
| **AnimateDiff** | [guoyww/AnimateDiff](https://github.com/guoyww/AnimateDiff) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (AnimateDiff). |
| **IP-Adapter** | [tencent-aio/IP-Adapter](https://github.com/tencent-aio/IP-Adapter) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (IP-Adapter). |
| **Silero Models** | [snakers4/silero-models](https://github.com/snakers4/silero-models) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Silero Models). |
| **NerfStudio** | [nerfstudio/nerfstudio](https://github.com/nerfstudio/nerfstudio) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (NerfStudio). |
| **Instant-NGP** | [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Instant-NGP). |
| **PIFuHD** | [shunsukesaito/PIFuHD](https://github.com/shunsukesaito/PIFuHD) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PIFuHD). |
| **PIFu** | [shunsukesaito/PIFu](https://github.com/shunsukesaito/PIFu) | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (PIFu). |
| **Proyecto** | Motivo para no seguir ahora | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Proyecto). |
| **[LongCat-Video-Avatar 1.5](https://github.com/meituan-longcat/LongCat-Video)** | MIT y 8 pasos, pero modelo de 13.6B; orientado a generación de clips, no a latencia conversacional en 16 GB | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([LongCat-Video-Avatar 1.5](https://github.com/meituan-longcat/LongCat-Video)). |
| **[MultiTalk](https://github.com/MeiGen-AI/MultiTalk)** | Apache 2.0 y multi-persona, pero generación por clips; demasiado lento para vivo | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([MultiTalk](https://github.com/MeiGen-AI/MultiTalk)). |
| **[InfiniteTalk](https://github.com/MeiGen-AI/InfiniteTalk)** | Apache 2.0 y video largo, pero los reportes de uso real muestran tiempos muy alejados del tiempo real en GPUs de consumo | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([InfiniteTalk](https://github.com/MeiGen-AI/InfiniteTalk)). |
| **[Wan2.2-S2V](https://github.com/Wan-Video/Wan2.2)** | Ecosistema amplio y quants disponibles, pero 14B; 16 GB es un mínimo muy exigente y no resuelve streaming conversacional | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([Wan2.2-S2V](https://github.com/Wan-Video/Wan2.2)). |
| **[HunyuanVideo-Avatar](https://github.com/Tencent-Hunyuan/HunyuanVideo-Avatar)** | Muy pesado, lento y con licencia territorial que excluye UE/UK/Corea del Sur | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([HunyuanVideo-Avatar](https://github.com/Tencent-Hunyuan/HunyuanVideo-Avatar)). |
| **[SkyReels-V3-A2V](https://github.com/SkyworkAI/SkyReels-V3)** | Modelo grande y licencia comunitaria; sin medición local que justifique el coste en 16 GB | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([SkyReels-V3-A2V](https://github.com/SkyworkAI/SkyReels-V3)). |
| **[HuMo](https://github.com/Phantom-video/HuMo)** | 1.7B disponible, pero continúa siendo generación de clips y no un renderer incremental probado | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync ([HuMo](https://github.com/Phantom-video/HuMo)). |
| **OmniHuman** | Sin pesos ni código oficiales; solo servicio/API | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (OmniHuman). |
| **LAM-Audio2Expression** | Produce blendshapes ARKit en tiempo real; es un buen candidato si elegimos un avatar 3D, pero todavía no se integró | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (LAM-Audio2Expression). |
| **Gaussian/3D talking heads** | Prometedores, pero el coste de preparar identidad, runtime y render todavía no está resuelto para este equipo | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (Gaussian/3D talking heads). |
| **NVIDIA Audio2Face** | Alternativa de rigging, no un renderer local completo listo para nuestro flujo; requiere una capa 3D y conexión con el pipeline | Modelo de IA para generación de retratos parlantes, animación facial y lip-sync (NVIDIA Audio2Face). |
| **PyTorch, 50 pasos** | 10.12 s | **[195 (7.8 s)]** 16.50 s |
| **PyTorch, 10 pasos** | 10.12 s | **[195 (7.8 s)]** 14.20 s |
| **PyTorch, 4 pasos** | 10.12 s | **[195 (7.8 s)]** 13.63 s |
| **ACTalker** | [harlanhong/ACTalker](https://github.com/harlanhong/ACTalker) | **[Evaluado]** Framework de difusión de video que soporta control simultáneo de audio y expresión facial. |
| **RealVideo** | [zai-org/RealVideo](https://github.com/zai-org/RealVideo) | **[Evaluado]** Sistema conversacional en streaming que utiliza difusión autorregresiva para generar respuestas continuas de video. |
| **FastGHA** | [cvlab-kaist/FastGHA](https://github.com/cvlab-kaist/FastGHA) | **[Evaluado]** Encoder de avatares 3D Gaussian Splatting few-shot que permite renderizado en tiempo real a partir de pocas imágenes. |
| **GaussianEmoTalker** | [GaussianEmoTalker](https://arxiv.org/abs/2607.00194) | **[Evaluado]** Síntesis de avatar 3DGS emocional en tiempo real mediante espacio de deformación residual neutral a emocional. |
| **OmniTalker** | [OmniTalker](https://github.com/OmniTalker) | **[Evaluado]** Generador unificado end-to-end de habla y video sincronizado desde texto hasta 25 FPS. |
| **Awesome-Talking-Head-Synthesis** | [Kedreamix/Awesome-Talking-Head-Synthesis](https://github.com/Kedreamix/Awesome-Talking-Head-Synthesis) | **[Evaluado]** Repositorio curado de referencia de papers, benchmarks y código de talking heads. |
| **MMTalker** | [harlanhong/MMTalker](https://github.com/harlanhong/MMTalker) | **[Evaluado]** Modelo multimodal de generación de cabeza parlante con control de expresión fina guiado por audio. |
| **GenFaceTalk** | [GenFaceTalk](https://github.com/GenFaceTalk/GenFaceTalk) | **[Evaluado]** Generador one-shot de cabezas parlantes 3D Gaussian Splatting animadas por voz. |
| **UniTalking** | [UniTalking](https://github.com/UniTalking/UniTalking) | **[Evaluado]** Modelo unificado de animación de retrato parlante guiado por audio y promps de movimiento. |
| **EchoMimicV2** | [antgroup/echomimic_v2](https://github.com/antgroup/echomimic_v2) | **[Evaluado]** Segunda versión de EchoMimic orientada a animación humana de medio cuerpo guiada por audio. |
| **FLOAT** | [FLOAT](https://github.com/FLOAT) | **[Evaluado]** Modelo de flow matching latente para retratos parlantes con alta consistencia temporal. |
| **LlamaIndex** | [run-llama/llama_index](https://github.com/run-llama/llama_index) | **[Evaluado]** Framework de datos para agentes de IA conversacionales y asistentes RAG de voz. |

## 3️⃣ Infraestructura de Transmisión Media, SFU/MCU y Servidores WebRTC
*Servidores de medios, arquitecturas SFU/MCU, gateways de audio/video y servidores de streaming WebRTC de baja latencia.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **Livepeer Mission Control** | [Documentación Livepeer](https://docs.livepeer.org/v2/home/mission-control) | **[Evaluado]** Descartado: infraestructura distribuida de video, no avatar conversacional audio-driven local |
| **LiveKit Agents** | [livekit/agents](https://github.com/livekit/agents) | **[Investigado]** Buen transporte WebRTC; requiere implementar el renderer local |
| **LiveKit** | [livekit/livekit](https://github.com/livekit/livekit) | Plataforma SFU de código abierto líder para audio/video WebRTC y agentes conversacionales de IA en tiempo real. |
| **OWT Server** | [open-webrtc-toolkit/owt-server](https://github.com/open-webrtc-toolkit/owt-server) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (OWT Server). |
| **mediasoup** | [versatica/mediasoup](https://github.com/versatica/mediasoup) | Servidor SFU de WebRTC súper potente y modular escrito en C++ con bindings de Node.js/Python. |
| **Janus Gateway** | [meetecho/janus-gateway](https://github.com/meetecho/janus-gateway) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (Janus Gateway). |
| **LiveKit CLI** | [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit CLI). |
| **LiveKit Protocol** | [livekit/protocol](https://github.com/livekit/protocol) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit Protocol). |
| **LiveKit Egress** | [livekit/egress](https://github.com/livekit/egress) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit Egress). |
| **LiveKit Ingress** | [livekit/ingress](https://github.com/livekit/ingress) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit Ingress). |
| **LiveKit JS Agents SDK** | [livekit/agents-js](https://github.com/livekit/agents-js) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit JS Agents SDK). |
| **LiveKit SIP Gateway** | [livekit/sip](https://github.com/livekit/sip) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit SIP Gateway). |
| **mediasoup-client** | [versatica/mediasoup-client](https://github.com/versatica/mediasoup-client) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (mediasoup-client). |
| **GStreamer** | [GStreamer/gstreamer](https://github.com/GStreamer/gstreamer) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (GStreamer). |
| **SRS** | [ossrs/srs](https://github.com/ossrs/srs) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (SRS). |
| **LiveKit Helm Charts** | [livekit/livekit-helm](https://github.com/livekit/livekit-helm) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (LiveKit Helm Charts). |
| **webrtc-streamer** | [mpromonet/webrtc-streamer](https://github.com/mpromonet/webrtc-streamer) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (webrtc-streamer). |
| **mediasoup-demo** | [versatica/mediasoup-demo](https://github.com/versatica/mediasoup-demo) | Servidor de medios, infraestructura SFU/MCU o gateway de transmisión WebRTC (mediasoup-demo). |
| **Kurento Media Server** | [Kurento/kurento-media-server](https://github.com/Kurento/kurento-media-server) | Servidor de medios WebRTC legacy para filtrado, enrutamiento y procesamiento de flujos de video. |
| **Licode** | [lynckia/licode](https://github.com/lynckia/licode) | Solución SFU/MCU open source en C++ y Node.js para comunicación en tiempo real WebRTC. |
| **Galene** | [jech/galene](https://github.com/jech/galene) | Servidor WebRTC SFU ligero escrito en Go enfocado en baja latencia y videoconferencia. |
| **ion-sfu** | [ionorg/ion-sfu](https://github.com/ionorg/ion-sfu) | **[Evaluado]** Implementación SFU pura en Go de alto rendimiento para escalabilidad de WebRTC. |
| **mirotalksfu** | [miroslavpejic85/mirotalksfu](https://github.com/miroslavpejic85/mirotalksfu) | **[Evaluado]** Plataforma SFU de conferencias y streaming WebRTC auto-hospedada en NodeJS. |
| **MediaMTX** | [bluenviron/mediamtx](https://github.com/bluenviron/mediamtx) | **[Evaluado]** Servidor de medios multiprotocolo (RTSP, RTMP, WebRTC, HLS) de baja latencia escrito en Go. |
| **Ant Media Server** | [ant-media/Ant-Media-Server](https://github.com/ant-media/Ant-Media-Server) | **[Evaluado]** Servidor de streaming WebRTC ultra-baja latencia con transcodificación en tiempo real. |

## 4️⃣ SDKs de Cliente y Protocolos de Comunicación WebRTC / Red
*Librerías SDK cliente/servidor multiplataforma (Python, JS, C++, Rust, Go, Mobile, Game Engines) e implementaciones de protocolo WebRTC/RTP/ICE/SDP.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **Pipecat** | [pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat) | **[Investigado]** Alternativa de orquestación local; no probada en este equipo |
| **FastRTC** | [gradio-app/fastrtc](https://github.com/gradio-app/fastrtc) | Librería Python por Gradio para transmisión WebRTC en tiempo real con modelos de IA. |
| **Daily Python** | [daily-co/daily-python](https://github.com/daily-co/daily-python) | SDK de Python para interactuar con la infraestructura WebRTC de Daily. |
| **GANHead** | [wsj-sjtu/GANHead](https://github.com/wsj-sjtu/GANHead) | SDK de cliente/servidor o librería de protocolo WebRTC/red (GANHead). |
| **aiortc** | [aiortc/aiortc](https://github.com/aiortc/aiortc) | SDK de cliente/servidor o librería de protocolo WebRTC/red (aiortc). |
| **Pion WebRTC** | [pion/webrtc](https://github.com/pion/webrtc) | Implementación pura en Go del protocolo WebRTC, base de infraestructuras de baja latencia. |
| **OpenAI Realtime Console** | [openai/openai-realtime-console](https://github.com/openai/openai-realtime-console) | SDK de cliente/servidor o librería de protocolo WebRTC/red (OpenAI Realtime Console). |
| **LiveKit JS Client SDK** | [livekit/client-sdk-js](https://github.com/livekit/client-sdk-js) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit JS Client SDK). |
| **LiveKit Python SDK** | [livekit/client-sdk-python](https://github.com/livekit/client-sdk-python) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Python SDK). |
| **LiveKit Components React** | [livekit/components-js](https://github.com/livekit/components-js) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Components React). |
| **LiveKit Rust SDK** | [livekit/rust-sdks](https://github.com/livekit/rust-sdks) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Rust SDK). |
| **LiveKit Server SDK Node** | [livekit/server-sdk-js](https://github.com/livekit/server-sdk-js) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Server SDK Node). |
| **LiveKit Server SDK Python** | [livekit/server-sdk-python](https://github.com/livekit/server-sdk-python) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Server SDK Python). |
| **Pipecat Client Web** | [pipecat-ai/pipecat-client-web](https://github.com/pipecat-ai/pipecat-client-web) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pipecat Client Web). |
| **Pipecat Client React** | [pipecat-ai/pipecat-client-react](https://github.com/pipecat-ai/pipecat-client-react) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pipecat Client React). |
| **Daily JS SDK** | [daily-co/daily-js](https://github.com/daily-co/daily-js) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Daily JS SDK). |
| **simple-peer** | [feross/simple-peer](https://github.com/feross/simple-peer) | SDK de cliente/servidor o librería de protocolo WebRTC/red (simple-peer). |
| **PeerJS** | [peers/peerjs](https://github.com/peers/peerjs) | SDK de cliente/servidor o librería de protocolo WebRTC/red (PeerJS). |
| **libmediasoupclient** | [versatica/libmediasoupclient](https://github.com/versatica/libmediasoupclient) | SDK de cliente/servidor o librería de protocolo WebRTC/red (libmediasoupclient). |
| **Agora Web SDK NG** | [AgoraIO/Agora-Web-SDK-NG](https://github.com/AgoraIO/Agora-Web-SDK-NG) | SDK de cliente WebRTC para integración de audio, video y comunicación interactiva. |
| **Agora RTC React** | [AgoraIO/Agora-RTC-React](https://github.com/AgoraIO/Agora-RTC-React) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora RTC React). |
| **Agora Realtime Voice Agent** | [AgoraIO/Agora-Realtime-Voice-Agent](https://github.com/AgoraIO/Agora-Realtime-Voice-Agent) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora Realtime Voice Agent). |
| **LiveKit Unity SDK** | [livekit/client-sdk-unity](https://github.com/livekit/client-sdk-unity) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Unity SDK). |
| **LiveKit Flutter SDK** | [livekit/client-sdk-flutter](https://github.com/livekit/client-sdk-flutter) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Flutter SDK). |
| **LiveKit Go SDK** | [livekit/go-sdk](https://github.com/livekit/go-sdk) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Go SDK). |
| **webrtc-rs** | [webrtc-rs/webrtc](https://github.com/webrtc-rs/webrtc) | SDK de cliente/servidor o librería de protocolo WebRTC/red (webrtc-rs). |
| **libdatachannel** | [paullouisageneau/libdatachannel](https://github.com/paullouisageneau/libdatachannel) | SDK de cliente/servidor o librería de protocolo WebRTC/red (libdatachannel). |
| **LiveKit Android SDK** | [livekit/client-sdk-android](https://github.com/livekit/client-sdk-android) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Android SDK). |
| **LiveKit iOS SDK** | [livekit/client-sdk-ios](https://github.com/livekit/client-sdk-ios) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit iOS SDK). |
| **LiveKit C++ SDK** | [livekit/cpp-sdks](https://github.com/livekit/cpp-sdks) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit C++ SDK). |
| **LiveKit React Native SDK** | [livekit/client-sdk-react-native](https://github.com/livekit/client-sdk-react-native) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit React Native SDK). |
| **Pipecat Client iOS** | [pipecat-ai/pipecat-client-ios](https://github.com/pipecat-ai/pipecat-client-ios) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pipecat Client iOS). |
| **Pipecat Client Android** | [pipecat-ai/pipecat-client-android](https://github.com/pipecat-ai/pipecat-client-android) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pipecat Client Android). |
| **Daily React SDK** | [daily-co/daily-react](https://github.com/daily-co/daily-react) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Daily React SDK). |
| **Agora Electron SDK** | [AgoraIO/Electron-SDK](https://github.com/AgoraIO/Electron-SDK) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora Electron SDK). |
| **Agora Flutter SDK** | [AgoraIO/Flutter-SDK](https://github.com/AgoraIO/Flutter-SDK) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora Flutter SDK). |
| **Agora Unity RTC SDK** | [AgoraIO/Agora-Unity-RTC-SDK](https://github.com/AgoraIO/Agora-Unity-RTC-SDK) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora Unity RTC SDK). |
| **Agora Unreal RTC SDK** | [AgoraIO/Agora-Unreal-RTC-SDK](https://github.com/AgoraIO/Agora-Unreal-RTC-SDK) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Agora Unreal RTC SDK). |
| **Pipecat Client Flutter** | [pipecat-ai/pipecat-client-flutter](https://github.com/pipecat-ai/pipecat-client-flutter) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pipecat Client Flutter). |
| **Daily Android SDK** | [daily-co/daily-android](https://github.com/daily-co/daily-android) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Daily Android SDK). |
| **Daily iOS SDK** | [daily-co/daily-ios](https://github.com/daily-co/daily-ios) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Daily iOS SDK). |
| **LiveKit Swift SDK** | [livekit/client-sdk-swift](https://github.com/livekit/client-sdk-swift) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Swift SDK). |
| **LiveKit Components Android** | [livekit/components-android](https://github.com/livekit/components-android) | SDK de cliente/servidor o librería de protocolo WebRTC/red (LiveKit Components Android). |
| **node-webrtc** | [node-webrtc/node-webrtc](https://github.com/node-webrtc/node-webrtc) | SDK de cliente/servidor o librería de protocolo WebRTC/red (node-webrtc). |
| **FastAPI** | [fastapi/fastapi](https://github.com/fastapi/fastapi) | SDK de cliente/servidor o librería de protocolo WebRTC/red (FastAPI). |
| **uvicorn** | [encode/uvicorn](https://github.com/encode/uvicorn) | SDK de cliente/servidor o librería de protocolo WebRTC/red (uvicorn). |
| **websockets** | [python-websockets/websockets](https://github.com/python-websockets/websockets) | SDK de cliente/servidor o librería de protocolo WebRTC/red (websockets). |
| **Socket.IO** | [socketio/socket.io](https://github.com/socketio/socket.io) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Socket.IO). |
| **ws** | [websockets/ws](https://github.com/websockets/ws) | SDK de cliente/servidor o librería de protocolo WebRTC/red (ws). |
| **coturn** | [coturn/coturn](https://github.com/coturn/coturn) | SDK de cliente/servidor o librería de protocolo WebRTC/red (coturn). |
| **Pion TURN** | [pion/turn](https://github.com/pion/turn) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion TURN). |
| **Pion ICE** | [pion/ice](https://github.com/pion/ice) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion ICE). |
| **Pion DTLS** | [pion/dtls](https://github.com/pion/dtls) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion DTLS). |
| **Pion SRTP** | [pion/srtp](https://github.com/pion/srtp) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion SRTP). |
| **Pion RTP** | [pion/rtp](https://github.com/pion/rtp) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion RTP). |
| **Pion SCTP** | [pion/sctp](https://github.com/pion/sctp) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion SCTP). |
| **Pion RTCP** | [pion/rtcp](https://github.com/pion/rtcp) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion RTCP). |
| **Pion MediaDevices** | [pion/mediadevices](https://github.com/pion/mediadevices) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion MediaDevices). |
| **Pion Interceptor** | [pion/interceptor](https://github.com/pion/interceptor) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion Interceptor). |
| **Pion SDP** | [pion/sdp](https://github.com/pion/sdp) | SDK de cliente/servidor o librería de protocolo WebRTC/red (Pion SDP). |
| **sample-nova-sonic-webrtc** | [aws-samples/sample-nova-sonic-speech2speech-webrtc](https://github.com/aws-samples/sample-nova-sonic-speech2speech-webrtc) | **[Evaluado]** Pipeline de agente de voz speech-to-speech en tiempo real con WebRTC. |
| **webrtc-rs-sfu** | [webrtc-rs/sfu](https://github.com/webrtc-rs/sfu) | **[Evaluado]** Implementación SFU de WebRTC Sans-IO escrita en Rust. |
| **Vocode Python** | [vocodehq/vocode-python](https://github.com/vocodehq/vocode-python) | **[Evaluado]** Framework open-source para construir aplicaciones de voz conversacional en tiempo real. |
| **Vapi Python** | [vapi-ai/vapi-python](https://github.com/vapi-ai/vapi-python) | **[Evaluado]** SDK de cliente para integración de agentes de voz conversacionales de baja latencia. |
| **RestoreFormer** | [wsi-lab/RestoreFormer](https://github.com/wsi-lab/RestoreFormer) | **[Evaluado]** Modelo basado en transformadores para restauración y super-resolución de rostros deteriorados. |
| **peerjs-server** | [peers/peerjs-server](https://github.com/peers/peerjs-server) | **[Evaluado]** Servidor de señalización WebRTC ligero para conexiones P2P PeerJS. |
| **Amazon Kinesis WebRTC C SDK** | [awslabs/amazon-kinesis-video-streams-webrtc-sdk-c](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c) | **[Evaluado]** SDK oficial en C de AWS para streaming multimedia WebRTC de baja latencia en dispositivos y servidor. |

## 5️⃣ Modelos de Lenguaje & Conversación Multimodal (Speech-to-Speech LLMs & Motores de Inferencia)
*LLMs multimodales nativos de audio/voz, motores de inferencia acelerados y orquestadores conversacionales.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **Ultravox** | [fixie-ai/ultravox](https://github.com/fixie-ai/ultravox) | Modelo Speech-to-Speech LLM de código abierto para interacción conversacional nativa de audio. |
| **Mini-Omni** | [gpt-omni/mini-omni](https://github.com/gpt-omni/mini-omni) | Modelo de lenguaje multimodal Speech-to-Speech que genera voz en streaming en tiempo real. |
| **GLM-4-Voice** | [THUDM/GLM-4-Voice](https://github.com/THUDM/GLM-4-Voice) | LLM multimodal nativo de voz capaz de comprensión y generación directa de audio conversacional. |
| **Qwen2-Audio** | [Qwen/Qwen2-Audio](https://github.com/Qwen/Qwen2-Audio) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Qwen2-Audio). |
| **ONNX Runtime** | [microsoft/onnxruntime](https://github.com/microsoft/onnxruntime) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (ONNX Runtime). |
| **vLLM** | [vllm-project/vllm](https://github.com/vllm-project/vllm) | Motor de inferencia de LLMs de alto rendimiento con PagedAttention y servidor HTTP/gRPC. |
| **Ollama** | [ollama/ollama](https://github.com/ollama/ollama) | Herramienta para ejecutar y servir LLMs locales fácilmente en macOS, Linux y Windows. |
| **Llama-Omni** | [ictnlp/Llama-Omni](https://github.com/ictnlp/Llama-Omni) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Llama-Omni). |
| **Mini-Omni2** | [gpt-omni/mini-omni2](https://github.com/gpt-omni/mini-omni2) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Mini-Omni2). |
| **TensorRT-LLM** | [NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) | Librería de NVIDIA para optimizar y acelerar la inferencia de LLMs en GPUs Tensor Core. |
| **SGLang** | [sgl-project/sglang](https://github.com/sgl-project/sglang) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (SGLang). |
| **Text Generation Inference** | [huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Text Generation Inference). |
| **DeepStream Python Apps** | [NVIDIA-AI-IOT/deepstream_python_apps](https://github.com/NVIDIA-AI-IOT/deepstream_python_apps) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (DeepStream Python Apps). |
| **Aphrodite Engine** | [PygmalionAI/aphrodite-engine](https://github.com/PygmalionAI/aphrodite-engine) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Aphrodite Engine). |
| **LMDeploy** | [open-mmlab/lmdeploy](https://github.com/open-mmlab/lmdeploy) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (LMDeploy). |
| **MLX** | [ml-explore/mlx](https://github.com/ml-explore/mlx) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (MLX). |
| **Ollama JS** | [ollama/ollama-js](https://github.com/ollama/ollama-js) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Ollama JS). |
| **Ollama Python** | [ollama/ollama-python](https://github.com/ollama/ollama-python) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Ollama Python). |
| **llama-cpp-python** | [abetlen/llama-cpp-python](https://github.com/abetlen/llama-cpp-python) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (llama-cpp-python). |
| **Transformers.js** | [huggingface/transformers.js](https://github.com/huggingface/transformers.js) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Transformers.js). |
| **Web LLM** | [mlc-ai/web-llm](https://github.com/mlc-ai/web-llm) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (Web LLM). |
| **MLC LLM** | [mlc-ai/mlc-llm](https://github.com/mlc-ai/mlc-llm) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (MLC LLM). |
| **ncnn** | [Tencent/ncnn](https://github.com/Tencent/ncnn) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (ncnn). |
| **MNN** | [alibaba/MNN](https://github.com/alibaba/MNN) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (MNN). |
| **ExecuTorch** | [pytorch/executorch](https://github.com/pytorch/executorch) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (ExecuTorch). |
| **OpenVINO** | [openvinotoolkit/openvino](https://github.com/openvinotoolkit/openvino) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (OpenVINO). |
| **DirectML** | [microsoft/DirectML](https://github.com/microsoft/DirectML) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (DirectML). |
| **coremltools** | [apple/coremltools](https://github.com/apple/coremltools) | Modelo de lenguaje conversacional multimodal o motor de inferencia acelerado (coremltools). |
| **LocalAI** | [go-skynet/LocalAI](https://github.com/go-skynet/LocalAI) | **[Evaluado]** Motor de IA local open-source con soporte nativo para audio WebRTC y voz Speech-to-Speech. |
| **Mem0** | [mem0ai/mem0](https://github.com/mem0ai/mem0) | **[Evaluado]** Capa de memoria persistente de baja latencia para agentes conversacionales y avatares de voz. |
| **Outlines** | [dottxt-ai/outlines](https://github.com/dottxt-ai/outlines) | **[Evaluado]** Librería para generación de texto estructurado y control estricto de esquemas JSON en agentes LLM. |

## 6️⃣ Síntesis de Voz (TTS / Voice Cloning / Voice Conversion)
*Modelos y motores de texto a voz (TTS), clonación de voz en tiempo real y conversión espectral de voz.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **Fish Speech** | [fishaudio/fish-speech](https://github.com/fishaudio/fish-speech) | Sistema de síntesis de voz y clonación de audio en tiempo real basado en modelos LLaMA. |
| **CosyVoice** | [FunAudioLLM/CosyVoice](https://github.com/FunAudioLLM/CosyVoice) | Modelo de generación de voz multilingüe y clonación en tiempo real por Alibaba. |
| **SenseVoice** | [FunAudioLLM/SenseVoice](https://github.com/FunAudioLLM/SenseVoice) | Modelo multilingüe de reconocimiento de habla, emoción y eventos de audio de alta velocidad. |
| **RealtimeTTS** | [KoljaB/RealtimeTTS](https://github.com/KoljaB/RealtimeTTS) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (RealtimeTTS). |
| **ChatTTS** | [2noise/ChatTTS](https://github.com/2noise/ChatTTS) | Modelo de TTS conversacional diseñado para diálogo natural en español, inglés y chino. |
| **Coqui TTS** | [coqui-ai/TTS](https://github.com/coqui-ai/TTS) | Framework completo de síntesis de voz (TTS) de alta calidad en Python. |
| **Bark** | [suno-ai/bark](https://github.com/suno-ai/bark) | Modelo transformador generativo de audio para texto a voz con risas, suspiros y expresividad. |
| **VALL-E-X** | [Plachtaa/VALL-E-X](https://github.com/Plachtaa/VALL-E-X) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (VALL-E-X). |
| **OpenVoice** | [myshell-ai/OpenVoice](https://github.com/myshell-ai/OpenVoice) | Sistema de clonación de voz versátil con control preciso de tono, emoción y acento. |
| **MeloTTS** | [myshell-ai/MeloTTS](https://github.com/myshell-ai/MeloTTS) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (MeloTTS). |
| **F5-TTS** | [SW-MMLAB/F5-TTS](https://github.com/SW-MMLAB/F5-TTS) | Modelo de TTS no autorregresivo ultrarrápido basado en Flow Matching. |
| **Speech2Face** | [ravising-h/speech2face](https://github.com/ravising-h/speech2face) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Speech2Face). |
| **Piper TTS** | [rhasspy/piper](https://github.com/rhasspy/piper) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Piper TTS). |
| **Rhubarb Lip Sync** | [DanielSWolf/rhubarb-lip-sync](https://github.com/DanielSWolf/rhubarb-lip-sync) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Rhubarb Lip Sync). |
| **CozyVoice** | [FunAudioLLM/CozyVoice](https://github.com/FunAudioLLM/CozyVoice) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (CozyVoice). |
| **Amphion** | [open-mmlab/Amphion](https://github.com/open-mmlab/Amphion) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Amphion). |
| **VoiceCraft** | [jasonppy/VoiceCraft](https://github.com/jasonppy/VoiceCraft) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (VoiceCraft). |
| **SoundStorm PyTorch** | [lucidrains/soundstorm-pytorch](https://github.com/lucidrains/soundstorm-pytorch) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (SoundStorm PyTorch). |
| **VALL-E PyTorch** | [lifeiteng/vall-e](https://github.com/lifeiteng/vall-e) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (VALL-E PyTorch). |
| **Parler-TTS** | [huggingface/parler-tts](https://github.com/huggingface/parler-tts) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Parler-TTS). |
| **Matcha-TTS** | [shivammg/Matcha-TTS](https://github.com/shivammg/Matcha-TTS) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (Matcha-TTS). |
| **StyleTTS2** | [yl4579/StyleTTS2](https://github.com/yl4579/StyleTTS2) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (StyleTTS2). |
| **MetaVoice-1B** | [metavoice-ai/metavoice-src](https://github.com/metavoice-ai/metavoice-src) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (MetaVoice-1B). |
| **xtts-api-server** | [daswer123/xtts-api-server](https://github.com/daswer123/xtts-api-server) | Modelo de síntesis de voz (TTS), clonación de voz o conversión de audio (xtts-api-server). |
| **Wispr Flow** | [wispr-flow/wispr-flow](https://github.com/wispr-flow/wispr-flow) | **[Evaluado]** Pipeline de voz en streaming optimizado para interacción continua. |
| **RVC** | [RVC-Project/Retrieval-based-Voice-Conversion-WebUI](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI) | **[Evaluado]** Framework de conversión de voz en tiempo real basado en recuperación de características VITS. |
| **GPT-SoVITS** | [RVC-Boss/GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | **[Evaluado]** Modelo de síntesis de voz TTS zero-shot y clonación de voz a partir de 1 minuto de audio. |
| **So-VITS-SVC** | [svc-develop-team/so-vits-svc](https://github.com/svc-develop-team/so-vits-svc) | **[Evaluado]** Modelo de conversión de voz cantada basado en VITS con extracción de características de audio. |
| **Tortoise-TTS** | [neonbjb/tortoise-tts](https://github.com/neonbjb/tortoise-tts) | **[Evaluado]** Sistema de texto a voz multivoz con prosodia expresiva y clonación de voz alta fidelidad. |
| **Google Lyra** | [google/lyra](https://github.com/google/lyra) | **[Evaluado]** Codec de audio neuronal ultracomprimido de ultra-baja latencia para transmisión de voz en tiempo real. |
| **Meta EnCodec** | [facebookresearch/encodec](https://github.com/facebookresearch/encodec) | **[Evaluado]** Modelo de compresión de audio neuronal en tiempo real de alta fidelidad desarrollado por Meta. |
| **Descript DAC** | [descriptinc/dac](https://github.com/descriptinc/dac) | **[Evaluado]** Codec de audio neuronal universal de alta fidelidad y baja latencia para música y voz. |
| **SpeechTokenizer** | [ZhangXingHe/SpeechTokenizer](https://github.com/ZhangXingHe/SpeechTokenizer) | **[Evaluado]** Tokenizer de habla unificado para modelos de lenguaje multimodales Speech-to-Speech. |
| **HiFi-GAN** | [jik876/hifi-gan-demo](https://github.com/jik876/hifi-gan-demo) | **[Evaluado]** Vocoder neuronal GAN de alta fidelidad para síntesis de audio a partir de espectrogramas Mel. |
| **BigVGAN** | [NVIDIA/BigVGAN](https://github.com/NVIDIA/BigVGAN) | **[Evaluado]** Vocoder neuronal universal desarrollado por NVIDIA de hasta 112M de parámetros para audio transparente. |
| **Vocos** | [gemelo-ai/vocos](https://github.com/gemelo-ai/vocos) | **[Evaluado]** Vocoder neuronal ultra-rápido basado en Fourier que sintetiza audio desde tokens EnCodec o espectrogramas. |
| **libopus** | [xiph/opus](https://github.com/xiph/opus) | **[Evaluado]** Librería de referencia del codec de audio interactivo IETF Opus para comunicación WebRTC de baja latencia. |
| **UnivNet** | [maum-ai/univnet](https://github.com/maum-ai/univnet) | **[Evaluado]** Vocoder neuronal de alta fidelidad basado en discriminadores de espectrograma multi-resolución. |
| **WaveGlow** | [NVIDIA/waveglow](https://github.com/NVIDIA/waveglow) | **[Evaluado]** Red generativa basada en flujos desarrollada por NVIDIA para síntesis de voz en tiempo real. |
| **MelGAN** | [descriptinc/melgan-neurips](https://github.com/descriptinc/melgan-neurips) | **[Evaluado]** Red generativa antagónica en tiempo real para síntesis de audio desde espectrogramas mel. |
| **Parallel WaveGAN** | [kan-bayashi/ParallelWaveGAN](https://github.com/kan-bayashi/ParallelWaveGAN) | **[Evaluado]** Implementación paralela en PyTorch de WaveGAN para vocoder neuronal eficiente. |

## 7️⃣ Reconocimiento de Voz (ASR), VAD y Procesamiento de Audio
*Modelos de transcripción ASR en tiempo real, Detección de Actividad de Voz (VAD), supresión de ruido y procesamiento de señal de audio.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **LPIPS-AttnWav2Lip** | [FelixChan9527/LPIPS-AttnWav2Lip](https://github.com/FelixChan9527/LPIPS-AttnWav2Lip) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (LPIPS-AttnWav2Lip). |
| **SynchroRaMa** | [novicemm/synchrorama_](https://github.com/novicemm/synchrorama_) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (SynchroRaMa). |
| **faster-whisper** | [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) | Reimplementación de OpenAI Whisper con CTranslate2 para transcripción de voz súper rápida. |
| **silero-vad** | [snakers4/silero-vad](https://github.com/snakers4/silero-vad) | Modelo de Detección de Actividad de Voz (VAD) ultraligero y preciso en tiempo real. |
| **whisperX** | [m-bain/whisperX](https://github.com/m-bain/whisperX) | ASR basado en Whisper con alineación fonética precisa a nivel de palabra y diarización. |
| **whisper.cpp** | [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (whisper.cpp). |
| **OpenAI Whisper** | [openai/whisper](https://github.com/openai/whisper) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (OpenAI Whisper). |
| **FunASR** | [modelscope/FunASR](https://github.com/modelscope/FunASR) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (FunASR). |
| **Whisper-Live** | [collabora/whisper-live](https://github.com/collabora/whisper-live) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (Whisper-Live). |
| **Whisper-Streaming** | [ufal/whisper_streaming](https://github.com/ufal/whisper_streaming) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (Whisper-Streaming). |
| **SeamlessCommunication** | [facebookresearch/SeamlessCommunication](https://github.com/facebookresearch/SeamlessCommunication) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (SeamlessCommunication). |
| **py-webrtcvad** | [wiseman/py-webrtcvad](https://github.com/wiseman/py-webrtcvad) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (py-webrtcvad). |
| **librosa** | [librosa/librosa](https://github.com/librosa/librosa) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (librosa). |
| **torchaudio** | [pytorch/audio](https://github.com/pytorch/audio) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (torchaudio). |
| **python-soundfile** | [bastibe/python-soundfile](https://github.com/bastibe/python-soundfile) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (python-soundfile). |
| **resampy** | [librosa/resampy](https://github.com/librosa/resampy) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (resampy). |
| **sherpa-onnx** | [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (sherpa-onnx). |
| **faster-whisper-server** | [fedirz/faster-whisper-server](https://github.com/fedirz/faster-whisper-server) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (faster-whisper-server). |
| **webrtc-audio-processing** | [freedesktop/webrtc-audio-processing](https://github.com/freedesktop/webrtc-audio-processing) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (webrtc-audio-processing). |
| **RNNoise** | [xiph/rnnoise](https://github.com/xiph/rnnoise) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (RNNoise). |
| **Lipreading Deep Learning** | [mpcbr/lipreading](https://github.com/mpcbr/lipreading) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (Lipreading Deep Learning). |
| **TalkNet-ASD** | [TaoRuijie/TalkNet-ASD](https://github.com/TaoRuijie/TalkNet-ASD) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (TalkNet-ASD). |
| **moviepy** | [Zulko/moviepy](https://github.com/Zulko/moviepy) | Librería de procesamiento de audio, ASR (reconocimiento de habla) o VAD (moviepy). |
| **pyannote-audio** | [pyannote/pyannote-audio](https://github.com/pyannote/pyannote-audio) | **[Evaluado]** Toolkit en PyTorch para diarización de hablantes y segmentación de señal de audio. |
| **SpeechBrain** | [speechbrain/speechbrain](https://github.com/speechbrain/speechbrain) | **[Evaluado]** Toolkit de IA conversacional para ASR, TTS, reconocimiento de hablante y procesamiento de audio. |
| **Vosk** | [alphacep/vosk-api](https://github.com/alphacep/vosk-api) | **[Evaluado]** Toolkit de reconocimiento del habla (ASR) offline multiplataforma ligero para 20+ idiomas. |
| **WeNet** | [wenet-e2e/wenet](https://github.com/wenet-e2e/wenet) | **[Evaluado]** Toolkit de ASR end-to-end en tiempo real orientado a producción en C++ y Python. |
| **ESPnet** | [espnet/espnet](https://github.com/espnet/espnet) | **[Evaluado]** Toolkit completo en PyTorch para procesamiento de habla (ASR, TTS, traducción y separación de fuentes). |
| **Kaldi** | [kaldi-asr/kaldi](https://github.com/kaldi-asr/kaldi) | **[Evaluado]** Toolkit estándar C++ para reconocimiento del habla y procesamiento de audio. |

## 8️⃣ Captura de Movimiento, Estimación de Pose y Tracking Facial/Corporal
*Sistemas de captura de movimiento, detección de puntos clave faciales/corporales (landmarks), modelos paramétricos (SMPL/FLAME) y tracking facial.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **uLipSync** | [hecomi/uLipSync](https://github.com/hecomi/uLipSync) | Librería de captura de movimiento, estimación de pose o tracking facial (uLipSync). |
| **Loopy** | [loopyavatar/loopy](https://github.com/loopyavatar/loopy) | Librería de captura de movimiento, estimación de pose o tracking facial (Loopy). |
| **FaceX-Zoo** | [JDAI-CV/FaceX-Zoo](https://github.com/JDAI-CV/FaceX-Zoo) | Librería de captura de movimiento, estimación de pose o tracking facial (FaceX-Zoo). |
| **DeepFaceLive** | [iperov/DeepFaceLive](https://github.com/iperov/DeepFaceLive) | Librería de captura de movimiento, estimación de pose o tracking facial (DeepFaceLive). |
| **DECA** | [YadiraF/DECA](https://github.com/YadiraF/DECA) | Librería de captura de movimiento, estimación de pose o tracking facial (DECA). |
| **MICA** | [Zielonka/MICA](https://github.com/Zielonka/MICA) | Librería de captura de movimiento, estimación de pose o tracking facial (MICA). |
| **OpenFace** | [TadasBaltrusaitis/OpenFace](https://github.com/TadasBaltrusaitis/OpenFace) | Librería de captura de movimiento, estimación de pose o tracking facial (OpenFace). |
| **DeepFaceLab** | [iperov/DeepFaceLab](https://github.com/iperov/DeepFaceLab) | Librería de captura de movimiento, estimación de pose o tracking facial (DeepFaceLab). |
| **MotionGPT** | [OpenMotionLab/MotionGPT](https://github.com/OpenMotionLab/MotionGPT) | Librería de captura de movimiento, estimación de pose o tracking facial (MotionGPT). |
| **MDM** | [GuyTevet/motion-diffusion-model](https://github.com/GuyTevet/motion-diffusion-model) | Librería de captura de movimiento, estimación de pose o tracking facial (MDM). |
| **EDGE** | [Stanford-TML/EDGE](https://github.com/Stanford-TML/EDGE) | Librería de captura de movimiento, estimación de pose o tracking facial (EDGE). |
| **SMPL-X** | [vchoutas/smplx](https://github.com/vchoutas/smplx) | Modelo paramétrico humano 3D hiperrealista que integra cuerpo, rostro (FLAME) y manos (MANO). |
| **PyMAF-X** | [HongwenZhang/PyMAF-X](https://github.com/HongwenZhang/PyMAF-X) | Librería de captura de movimiento, estimación de pose o tracking facial (PyMAF-X). |
| **4D-Humans** | [shubham-goel/4D-Humans](https://github.com/shubham-goel/4D-Humans) | Librería de captura de movimiento, estimación de pose o tracking facial (4D-Humans). |
| **CLIFF** | [ZhengDong-Work/CLIFF](https://github.com/ZhengDong-Work/CLIFF) | Librería de captura de movimiento, estimación de pose o tracking facial (CLIFF). |
| **ExPose** | [vchoutas/expose](https://github.com/vchoutas/expose) | Librería de captura de movimiento, estimación de pose o tracking facial (ExPose). |
| **kalidoface** | [yeemachine/kalidoface](https://github.com/yeemachine/kalidoface) | Librería de captura de movimiento, estimación de pose o tracking facial (kalidoface). |
| **OpenSeeFace** | [emilianavt/OpenSeeFace](https://github.com/emilianavt/OpenSeeFace) | Librería de captura de movimiento, estimación de pose o tracking facial (OpenSeeFace). |
| **VTubeStudio** | [DenchiSoft/VTubeStudio](https://github.com/DenchiSoft/VTubeStudio) | Librería de captura de movimiento, estimación de pose o tracking facial (VTubeStudio). |
| **pyvts** | [DenverCoder1/pyvts](https://github.com/DenverCoder1/pyvts) | Librería de captura de movimiento, estimación de pose o tracking facial (pyvts). |
| **face3d** | [YadiraF/face3d](https://github.com/YadiraF/face3d) | Librería de captura de movimiento, estimación de pose o tracking facial (face3d). |
| **FaceVerse** | [LizhenWangT/FaceVerse_v4](https://github.com/LizhenWangT/FaceVerse_v4) | Librería de captura de movimiento, estimación de pose o tracking facial (FaceVerse). |
| **LACE** | [NVlabs/LACE](https://github.com/NVlabs/LACE) | Librería de captura de movimiento, estimación de pose o tracking facial (LACE). |
| **MediaPipeUnityPlugin** | [homuler/MediaPipeUnityPlugin](https://github.com/homuler/MediaPipeUnityPlugin) | Librería de captura de movimiento, estimación de pose o tracking facial (MediaPipeUnityPlugin). |
| **FLAME_PyTorch** | [soubhiksanyal/FLAME_PyTorch](https://github.com/soubhiksanyal/FLAME_PyTorch) | Librería de captura de movimiento, estimación de pose o tracking facial (FLAME_PyTorch). |
| **MediaPipe** | [google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) | Suite de Google para visión por computadora en tiempo real, detección de rostros, manos y pose. |
| **RingNet** | [soubhiksanyal/RingNet](https://github.com/soubhiksanyal/RingNet) | Librería de captura de movimiento, estimación de pose o tracking facial (RingNet). |
| **InsightFace** | [deepinsight/insightface](https://github.com/deepinsight/insightface) | Librería de captura de movimiento, estimación de pose o tracking facial (InsightFace). |
| **face_recognition** | [ageitgey/face_recognition](https://github.com/ageitgey/face_recognition) | Librería de captura de movimiento, estimación de pose o tracking facial (face_recognition). |
| **DeepFace** | [serengil/deepface](https://github.com/serengil/deepface) | Librería de captura de movimiento, estimación de pose o tracking facial (DeepFace). |
| **Pytorch_Retinaface** | [biubug6/Pytorch_Retinaface](https://github.com/biubug6/Pytorch_Retinaface) | Librería de captura de movimiento, estimación de pose o tracking facial (Pytorch_Retinaface). |
| **facenet-pytorch** | [timesler/facenet-pytorch](https://github.com/timesler/facenet-pytorch) | Librería de captura de movimiento, estimación de pose o tracking facial (facenet-pytorch). |
| **dlib** | [davisking/dlib](https://github.com/davisking/dlib) | Librería de captura de movimiento, estimación de pose o tracking facial (dlib). |
| **OpenCV** | [opencv/opencv](https://github.com/opencv/opencv) | Librería de captura de movimiento, estimación de pose o tracking facial (OpenCV). |
| **PyAV** | [PyAV-Org/PyAV](https://github.com/PyAV-Org/PyAV) | Librería de captura de movimiento, estimación de pose o tracking facial (PyAV). |
| **iFacialMocap-Python** | [iFacialMocap/iFacialMocap-Python](https://github.com/iFacialMocap/iFacialMocap-Python) | Librería de captura de movimiento, estimación de pose o tracking facial (iFacialMocap-Python). |
| **OpenPose** | [CMU-Perceptual-Computing-Lab/openpose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) | Sistema clásico de detección de pose corporal, manos y facial multi-persona en tiempo real. |
| **AlphaPose** | [MVIG-SJTU/AlphaPose](https://github.com/MVIG-SJTU/AlphaPose) | Librería de captura de movimiento, estimación de pose o tracking facial (AlphaPose). |
| **DWPose** | [IDEA-Research/DWPose](https://github.com/IDEA-Research/DWPose) | Librería de captura de movimiento, estimación de pose o tracking facial (DWPose). |
| **MMPose** | [open-mmlab/mmpose](https://github.com/open-mmlab/mmpose) | Librería de captura de movimiento, estimación de pose o tracking facial (MMPose). |
| **controlnet_aux** | [patrickvonplaten/controlnet_aux](https://github.com/patrickvonplaten/controlnet_aux) | Librería de captura de movimiento, estimación de pose o tracking facial (controlnet_aux). |
| **face-alignment** | [1adrianb/face-alignment](https://github.com/1adrianb/face-alignment) | Librería de captura de movimiento, estimación de pose o tracking facial (face-alignment). |
| **PRNet** | [YadiraF/PRNet](https://github.com/YadiraF/PRNet) | Librería de captura de movimiento, estimación de pose o tracking facial (PRNet). |
| **EOS** | [patrikhuber/eos](https://github.com/patrikhuber/eos) | Librería de captura de movimiento, estimación de pose o tracking facial (EOS). |
| **edge-tts** | [rany2/edge-tts](https://github.com/rany2/edge-tts) | Librería de captura de movimiento, estimación de pose o tracking facial (edge-tts). |
| **Deep3DFaceReconstruction** | [deep3dface/Deep3DFaceReconstruction](https://github.com/deep3dface/Deep3DFaceReconstruction) | Librería de captura de movimiento, estimación de pose o tracking facial (Deep3DFaceReconstruction). |
| **VRM/Unity + uLipSync** | Camino técnicamente sólido para tiempo real, pero implica crear o conseguir un modelo VRM y resolver la capa de expresiones/animación | Librería de captura de movimiento, estimación de pose o tracking facial (VRM/Unity + uLipSync). |
| **Chatterbox** | [ai-avatar-system/chatterbox](https://github.com/ai-avatar-system/chatterbox) | **[Evaluado]** Motor de sincronización labial y procesamiento de audio para humanos digitales interactivos. |
| **PantoMatrix** | [PantoMatrix](https://github.com/PantoMatrix) | **[Evaluado]** Generador de animación corporal 3D y facial a partir de habla soportando SMPL-X y FLAME. |
| **Awesome-Gesture_Generation** | [Awesome-Gesture_Generation](https://github.com/Awesome-Gesture_Generation) | **[Evaluado]** Índice de referencia y código de investigación en generación de gestos corporales guiados por audio. |
| **Kalidokit** | [yeemachine/kalidokit](https://github.com/yeemachine/kalidokit) | **[Evaluado]** Solver de cinemática y blendshapes para convertir pose y landmarks de MediaPipe a avatares VRM y Live2D. |

## 9️⃣ Renderizado, Visualización 2D/3D y Motores de UI
*Motores gráficos WebGL/WebGPU, visores y librerías de avatares VRM/Live2D, motores de videojuegos y frameworks de UI para escritorio y web.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **pixi-live2d-display** | [guansss/pixi-live2d-display](https://github.com/guansss/pixi-live2d-display) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (pixi-live2d-display). |
| **CubismWebSDK** | [Live2D/CubismWebSDK](https://github.com/Live2D/CubismWebSDK) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (CubismWebSDK). |
| **UniVRM** | [vrm-c/UniVRM](https://github.com/vrm-c/UniVRM) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (UniVRM). |
| **live2d-py** | [EasyLive2D/live2d-py](https://github.com/EasyLive2D/live2d-py) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (live2d-py). |
| **three-vrm** | [pixiv/three-vrm](https://github.com/pixiv/three-vrm) | Extensión de Three.js para cargar, renderizar y animar modelos de avatar en formato 3D VRM. |
| **live2d-widget** | [stevenjoezhang/live2d-widget](https://github.com/stevenjoezhang/live2d-widget) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (live2d-widget). |
| **CubismUnityComponents** | [Live2D/CubismUnityComponents](https://github.com/Live2D/CubismUnityComponents) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (CubismUnityComponents). |
| **vrm-specification** | [vrm-c/vrm-specification](https://github.com/vrm-c/vrm-specification) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (vrm-specification). |
| **CubismWebFramework** | [Live2D/CubismWebFramework](https://github.com/Live2D/CubismWebFramework) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (CubismWebFramework). |
| **CubismWebSamples** | [Live2D/CubismWebSamples](https://github.com/Live2D/CubismWebSamples) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (CubismWebSamples). |
| **three-vrm-animation** | [pixiv/three-vrm-animation](https://github.com/pixiv/three-vrm-animation) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (three-vrm-animation). |
| **CubismNativeFramework** | [Live2D/CubismNativeFramework](https://github.com/Live2D/CubismNativeFramework) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (CubismNativeFramework). |
| **three-vrm-materials-mtoon** | [pixiv/three-vrm-materials-mtoon](https://github.com/pixiv/three-vrm-materials-mtoon) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (three-vrm-materials-mtoon). |
| **Three.js** | [mrdoob/three.js](https://github.com/mrdoob/three.js) | Librería 3D en JavaScript ampliamente utilizada para renderizado WebGL en navegadores. |
| **Babylon.js** | [BabylonJS/Babylon.js](https://github.com/BabylonJS/Babylon.js) | Motor gráfico 3D en JavaScript/TypeScript completo para la web. |
| **Live2D-Python** | [qinyonghang/Live2D-Python](https://github.com/qinyonghang/Live2D-Python) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Live2D-Python). |
| **godot-vrm** | [V-Sekai/godot-vrm](https://github.com/V-Sekai/godot-vrm) | Plugin para el motor Godot Engine que permite la importación y animación de avatares VRM 3D. |
| **babylon-vrm-loader** | [virtual-cast/babylon-vrm-loader](https://github.com/virtual-cast/babylon-vrm-loader) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (babylon-vrm-loader). |
| **VRM Add-on for Blender** | [saturday06/VRM-Addon-for-Blender](https://github.com/saturday06/VRM-Addon-for-Blender) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (VRM Add-on for Blender). |
| **vrm-validator** | [vrm-c/vrm-validator](https://github.com/vrm-c/vrm-validator) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (vrm-validator). |
| **headless-gl** | [stackgl/headless-gl](https://github.com/stackgl/headless-gl) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (headless-gl). |
| **three-gltf-viewer** | [donmccurdy/three-gltf-viewer](https://github.com/donmccurdy/three-gltf-viewer) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (three-gltf-viewer). |
| **wgpu** | [gfx-rs/wgpu](https://github.com/gfx-rs/wgpu) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (wgpu). |
| **PyGLM** | [Zplab/PyGLM](https://github.com/Zplab/PyGLM) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (PyGLM). |
| **ModernGL** | [moderngl/moderngl](https://github.com/moderngl/moderngl) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (ModernGL). |
| **pygfx** | [pygfx/pygfx](https://github.com/pygfx/pygfx) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (pygfx). |
| **Taichi Graphics** | [taichi-dev/taichi](https://github.com/taichi-dev/taichi) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Taichi Graphics). |
| **PyOpenGL** | [mcfletch/pyopengl](https://github.com/mcfletch/pyopengl) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (PyOpenGL). |
| **Panda3D** | [panda3d/panda3d](https://github.com/panda3d/panda3d) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Panda3D). |
| **Pyglet** | [pyglet/pyglet](https://github.com/pyglet/pyglet) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Pyglet). |
| **Ursina Engine** | [pokepoke/ursina](https://github.com/pokepoke/ursina) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Ursina Engine). |
| **DearPyGui** | [hoffstadt/DearPyGui](https://github.com/hoffstadt/DearPyGui) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (DearPyGui). |
| **Kivy** | [kivy/kivy](https://github.com/kivy/kivy) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Kivy). |
| **Flet** | [flet-dev/flet](https://github.com/flet-dev/flet) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Flet). |
| **PixiJS** | [pixijs/pixijs](https://github.com/pixijs/pixijs) | Motor de renderizado 2D 2D súper rápido basado en WebGL para la web. |
| **TWGL.js** | [greggman/twgl.js](https://github.com/greggman/twgl.js) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (TWGL.js). |
| **regl** | [regl-project/regl](https://github.com/regl-project/regl) | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (regl). |
| **Live2D** | Podría dar muy baja latencia, pero requiere un avatar 2D preparado y no entrega el realismo buscado | Motor gráfico, visor 3D/2D o framework de interfaz de usuario (Live2D). |
| **threejs-talking-avatar** | [majidmanzarpour/threejs-talking-avatar](https://github.com/majidmanzarpour/threejs-talking-avatar) | **[Evaluado]** Avatar parlante ejecutable en navegador cliente mediante WebGPU y sincronización labial en tiempo real. |
| **Resonite** | [Yellow-Dog-Man/Resonite](https://github.com/Yellow-Dog-Man/Resonite) | **[Evaluado]** Motor y plataforma open-source de mundos virtuales 3D y avatares espaciales interactivos. |
| **Vircadia** | [vircadia/vircadia](https://github.com/vircadia/vircadia) | **[Evaluado]** Plataforma descentralizada de metaverso 3D con soporte para avatares y agentes. |
| **Filament** | [google/filament](https://github.com/google/filament) | **[Evaluado]** Motor de renderizado PBR en tiempo real multiplataforma desarrollado por Google para WebGL/C++. |
| **bgfx** | [bkaradzic/bgfx](https://github.com/bkaradzic/bgfx) | **[Evaluado]** Librería de renderizado 3D agnóstica de API gráfica (Vulkan, Direct3D, OpenGL, WebGL). |
| **Diligent Engine** | [DiligentGraphics/DiligentEngine](https://github.com/DiligentGraphics/DiligentEngine) | **[Evaluado]** Motor gráfico 3D moderno multiplataforma con soporte para WebGPU, Vulkan y Metal. |
| **O3DE** | [o3de/o3de](https://github.com/o3de/o3de) | **[Evaluado]** Open 3D Engine de la Linux Foundation para simulación y renderizado 3D modular de alta fidelidad. |
| **Rapier** | [dimforge/rapier](https://github.com/dimforge/rapier) | **[Evaluado]** Motor de física 2D/3D súper rápido escrito en Rust con bindings para WebAssembly/JavaScript. |
| **Jolt Physics** | [jrouwe/JoltPhysics](https://github.com/jrouwe/JoltPhysics) | **[Evaluado]** Motor de física 3D multihilo escrito en C++ para juegos y entornos VR/AR en tiempo real. |
| **ammo.js** | [kripken/ammo.js](https://github.com/kripken/ammo.js) | **[Evaluado]** Puerto directo del motor Bullet Physics a JavaScript/WebAssembly para física 3D en la web. |
| **cannon.js** | [schteppe/cannon.js](https://github.com/schteppe/cannon.js) | **[Evaluado]** Motor de física 3D ligero escrito en JavaScript para avatares y entornos 3D interactivos. |

## 🔟 Formatos 3D, Carga de Modelos y Optimizadores de Mallas
*Herramientas y librerías de bajo nivel para carga, validación, optimización y compresión de formatos 3D (glTF, FBX, OBJ, Draco).*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **gltf-pipeline** | [CesiumGS/gltf-pipeline](https://github.com/CesiumGS/gltf-pipeline) | Librería o herramienta de optimización, conversión y carga de formatos 3D (gltf-pipeline). |
| **Draco** | [google/draco](https://github.com/google/draco) | Librería o herramienta de optimización, conversión y carga de formatos 3D (Draco). |
| **Assimp** | [assimp/assimp](https://github.com/assimp/assimp) | Librería estándar C++ de importación y exportación de más de 40 formatos 3D. |
| **cgltf** | [jkuhlmann/cgltf](https://github.com/jkuhlmann/cgltf) | Librería o herramienta de optimización, conversión y carga de formatos 3D (cgltf). |
| **tinygltf** | [syoyo/tinygltf](https://github.com/syoyo/tinygltf) | Librería o herramienta de optimización, conversión y carga de formatos 3D (tinygltf). |
| **meshoptimizer** | [zeux/meshoptimizer](https://github.com/zeux/meshoptimizer) | Librería o herramienta de optimización, conversión y carga de formatos 3D (meshoptimizer). |
| **ufbx** | [bext-labs/ufbx](https://github.com/bext-labs/ufbx) | Librería o herramienta de optimización, conversión y carga de formatos 3D (ufbx). |
| **openfbx** | [nemitz/openfbx](https://github.com/nemitz/openfbx) | Librería o herramienta de optimización, conversión y carga de formatos 3D (openfbx). |
| **glTF-Validator** | [KhronosGroup/glTF-Validator](https://github.com/KhronosGroup/glTF-Validator) | Librería o herramienta de optimización, conversión y carga de formatos 3D (glTF-Validator). |
| **glTF-Transform** | [donmccurdy/glTF-Transform](https://github.com/donmccurdy/glTF-Transform) | Herramienta CLI y librería JS para optimizar, comprimir y transformar archivos 3D glTF/GLB. |
| **glTF-Blender-IO** | [KhronosGroup/glTF-Blender-IO](https://github.com/KhronosGroup/glTF-Blender-IO) | Librería o herramienta de optimización, conversión y carga de formatos 3D (glTF-Blender-IO). |
| **Awesome-3D-Gaussian-Splatting** | [MrNeRF/Awesome-3D-Gaussian-Splatting-Paper-List](https://github.com/MrNeRF/Awesome-3D-Gaussian-Splatting-Paper-List) | **[Evaluado]** Índice de referencia para investigación en 3DGS y avatares dinámicos en tiempo real. |
| **Talking-face-arxiv-daily** | [liutaocode/talking-face-arxiv-daily](https://github.com/liutaocode/talking-face-arxiv-daily) | **[Evaluado]** Repositorio de actualización diaria con avances en investigación de síntesis de rostros parlantes. |
| **Awesome-Multimodal-Agent** | [OpenEnvision/Awesome-Multimodal-Agent](https://github.com/OpenEnvision/Awesome-Multimodal-Agent) | **[Evaluado]** Índice de referencia de agentes multimodales e interacción guiada por voz. |
| **Awesome-AI-Agents-2026** | [ARUNAGIRINATHAN-K/awesome-ai-agents-2026](https://github.com/ARUNAGIRINATHAN-K/awesome-ai-agents-2026) | **[Evaluado]** Colección curada de frameworks, modelos y despliegues de agentes de IA de voz. |
| **gsplat** | [nerfstudio-project/gsplat](https://github.com/nerfstudio-project/gsplat) | **[Evaluado]** Librería CUDA hiperacelerada para rasterización y entrenamiento de 3D Gaussian Splatting por Nerfstudio. |
| **nerfacc** | [KAIR-BAIR/nerfacc](https://github.com/KAIR-BAIR/nerfacc) | **[Evaluado]** Toolbox de aceleración en PyTorch para muestreo y renderizado volumétrico rápido de NeRFs. |
| **three-mesh-bvh** | [gkjohnson/three-mesh-bvh](https://github.com/gkjohnson/three-mesh-bvh) | **[Evaluado]** Estructura de aceleración espacial BVH para trazado de rayos ultrarrápido en mallas Three.js. |

## 11. Super-Resolución Facial, Segmentación, Matting y Edición de Imagen/Video
*Modelos de post-procesamiento facial (enhancers), segmentación de sujetos, matting de video y remoción de fondos.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **GFPGAN** | [TencentARC/GFPGAN](https://github.com/TencentARC/GFPGAN) | Modelo de restauración y super-resolución de rostros ciegos basado en GANs de estilo. |
| **CodeFormer** | [sczhou/CodeFormer](https://github.com/sczhou/CodeFormer) | Red de predicción de transformadores de código para restauración facial de alta calidad. |
| **Real-ESRGAN** | [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) | Modelo de escalado de imágenes y rostros en tiempo real para mejorar detalles de textura. |
| **FFmpeg** | [FFmpeg/FFmpeg](https://github.com/FFmpeg/FFmpeg) | Herramienta de super-resolución facial, segmentación o procesamiento de video (FFmpeg). |
| **spandrel** | [chaiNNer-org/spandrel](https://github.com/chaiNNer-org/spandrel) | Herramienta de super-resolución facial, segmentación o procesamiento de video (spandrel). |
| **rembg** | [danielgatis/rembg](https://github.com/danielgatis/rembg) | Herramienta de super-resolución facial, segmentación o procesamiento de video (rembg). |
| **BiRefNet** | [ZhengPeng7/BiRefNet](https://github.com/ZhengPeng7/BiRefNet) | Herramienta de super-resolución facial, segmentación o procesamiento de video (BiRefNet). |
| **InSPyReNet** | [PyeongGang/InSPyReNet](https://github.com/PyeongGang/InSPyReNet) | Herramienta de super-resolución facial, segmentación o procesamiento de video (InSPyReNet). |
| **RobustVideoMatting** | [PeterLSO/RobustVideoMatting](https://github.com/PeterLSO/RobustVideoMatting) | Herramienta de super-resolución facial, segmentación o procesamiento de video (RobustVideoMatting). |
| **ViTMatting** | [hustvl/ViTMatting](https://github.com/hustvl/ViTMatting) | Herramienta de super-resolución facial, segmentación o procesamiento de video (ViTMatting). |
| **MODNet** | [ZhengPeng7/MODNet](https://github.com/ZhengPeng7/MODNet) | Herramienta de super-resolución facial, segmentación o procesamiento de video (MODNet). |
| **ffmpeg-python** | [kkroening/ffmpeg-python](https://github.com/kkroening/ffmpeg-python) | Herramienta de super-resolución facial, segmentación o procesamiento de video (ffmpeg-python). |
| **Basis Universal** | [BinomialLLC/basis_universal](https://github.com/BinomialLLC/basis_universal) | Herramienta de super-resolución facial, segmentación o procesamiento de video (Basis Universal). |
| **KTX-Software** | [KhronosGroup/KTX-Software](https://github.com/KhronosGroup/KTX-Software) | Herramienta de super-resolución facial, segmentación o procesamiento de video (KTX-Software). |
| **SAM 2** | [facebookresearch/segment-anything-2](https://github.com/facebookresearch/segment-anything-2) | **[Evaluado]** Modelo de Meta para segmentación y matting de objetos y sujetos en video en tiempo real. |
| **Grounded-SAM** | [IDEA-Research/Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) | **[Evaluado]** Combinación de DINO y SAM para detección y segmentación de imágenes/video por texto. |
| **GPEN** | [yangxy/GPEN](https://github.com/yangxy/GPEN) | **[Evaluado]** Red incrustada de priores GAN para restauración facial y mejora de resolución. |
| **SVT-AV1** | [AOMediaCodec/SVT-AV1](https://gitlab.com/AOMediaCodec/SVT-AV1) | **[Evaluado]** Codificador de video AV1 de alta eficiencia optimizado para transmisión en tiempo real de AOMedia. |
| **dav1d** | [videolan/dav1d](https://github.com/videolan/dav1d) | **[Evaluado]** Decodificador AV1 open-source súper rápido de VideoLAN optimizado para reproducir video de baja latencia. |
| **libvpx** | [webmproject/libvpx](https://github.com/webmproject/libvpx) | **[Evaluado]** Librería de referencia para codificación y decodificación de formatos de video VP8 y VP9. |
| **Video Processing Framework** | [NVIDIA/VideoProcessingFramework](https://github.com/NVIDIA/VideoProcessingFramework) | **[Evaluado]** Bindings en Python/PyTorch de NVIDIA para decodificación y codificación de video acelerada por hardware (NVDEC/NVENC). |

## 12. Ecosistemas, Nodos y Plugins para Frameworks de Inferencia (ComfyUI / WebUI)
*Suites de nodos, plugins y conectores de flujo de trabajo para ejecución modular en ComfyUI y otros entornos de inferencia.*

| **Proyecto / Solución** | **Repositorio / Enlace** | **Descripción / Evaluación Técnica** |
|---|---|---|
| **ComfyStream** | [yolain/ComfyStream](https://github.com/yolain/ComfyStream) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (ComfyStream). |
| **ComfyUI-LivePortraitKJ** | [kijai/ComfyUI-LivePortraitKJ](https://github.com/kijai/ComfyUI-LivePortraitKJ) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (ComfyUI-LivePortraitKJ). |
| **Comfyui-SadTalker** | [haomole/Comfyui-SadTalker](https://github.com/haomole/Comfyui-SadTalker) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (Comfyui-SadTalker). |
| **ComfyUI-MuseTalk_FSH** | [AIFSH/ComfyUI-MuseTalk_FSH](https://github.com/AIFSH/ComfyUI-MuseTalk_FSH) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (ComfyUI-MuseTalk_FSH). |
| **comfyui_openvino** | [openvino-dev-samples/comfyui_openvino](https://github.com/openvino-dev-samples/comfyui_openvino) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (comfyui_openvino). |
| **VideoHelperSuite** | [Kosinkadink/ComfyUI-VideoHelperSuite](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (VideoHelperSuite). |
| **ComfyUI-Wav2Lip** | [numz/ComfyUI-Wav2Lip](https://github.com/numz/ComfyUI-Wav2Lip) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (ComfyUI-Wav2Lip). |
| **ComfyUI-MuseTalk** | [chaojie/ComfyUI-MuseTalk](https://github.com/chaojie/ComfyUI-MuseTalk) | Plugin, suite de nodos o extensión para ComfyUI / WebUI de inferencia (ComfyUI-MuseTalk). |
