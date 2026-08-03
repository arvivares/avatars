# Evaluación de avatares locales en tiempo real

Documento vivo del proyecto de avatar local. Se actualiza después de cada prueba para conservar decisiones, resultados y motivos de descarte.

Última actualización: 2026-08-02  
Estado de los servicios: stack Prometheus/OpenTalking activo para pruebas en Windows (`:3010`) y backend en WSL (`:8210`); Ollama activo en Windows (`:11434`).

Estado actualizado 2026-08-02: AVTR-1 / Avaturn es el candidato principal. El renderer y el streamer web fueron validados desde Windows con audio local en espanol, previews de avatar/background y formato vertical.

## Objetivo y restricciones

Buscamos un avatar conversacional local con:

- LLM, STT, TTS y renderizado local.
- Audio y video sincronizados.
- Conversación en español.
- Posibilidad de escuchar mientras el avatar habla.
- Latencia suficientemente baja para una interacción natural.
- Uso en una GPU NVIDIA RTX 5060 Ti con 16 GB de VRAM, dentro de WSL2.

La prioridad práctica es un pipeline que pueda producir video de forma continua. Un modelo que genere un clip terminado después de varios segundos puede ser útil para contenido offline, pero no equivale a un avatar en vivo.

## Resumen de decisiones

| **Opción** | **Repositorio** | **Estado** | **Decisión** |
|---|---|---|---|
| LiteAvatar | [HumanAIGC/lite-avatar](https://github.com/HumanAIGC/lite-avatar) | Probado | Baseline rápido; no descartado formalmente |
| MuseTalk | [TMElyralab/MuseTalk](https://github.com/TMElyralab/MuseTalk) | Probado | Descartado por calidad visual, sincronización y comportamiento inestable en nuestro stack |
| SoulX-FlashHead Lite | [Soul-AILab/SoulX-FlashHead](https://github.com/Soul-AILab/SoulX-FlashHead) | Probado | Descartado para esta línea de trabajo |
| EchoMimicV3-Flash | [antgroup/echomimic_v3](https://github.com/antgroup/echomimic_v3) | Prueba aislada exitosa | No apto para tiempo real con nuestra GPU; queda para offline/híbrido |
| FasterLivePortrait | [warmshao/FasterLivePortrait](https://github.com/warmshao/FasterLivePortrait) | Evaluado | La ruta de audio requiere un adaptador incremental propio; la ruta lista depende de cámara/video |
| JoyVASA | [jdh-algo/JoyVASA](https://github.com/jdh-algo/JoyVASA) | Evaluado | Se podría reutilizar por ventanas, pero no trae streaming conversacional listo |
| Duix-Avatar | [duixcom/Duix-Avatar](https://github.com/duixcom/Duix-Avatar) | Evaluado | Descartado: generación de clips offline, explícitamente no realtime |
| Duix-Mobile | [duixcom/Duix-Mobile](https://github.com/duixcom/Duix-Mobile) | Evaluado | Candidato experimental Android; bloqueado para nuestro stack web/WSL y con licencia restrictiva |
| AVTR-1 / Avaturn | [avaturn-live/avtr-1](https://github.com/avaturn-live/avtr-1) | Validado | **Candidato principal**: renderer incremental, dual-stream, avatar independiente y conversación local en español |
| AvatarForcing | [KlingAIResearch/AvatarForcing](https://github.com/KlingAIResearch/AvatarForcing) | Evaluado | Descartado para 16 GB: pesado, lento y con licencia no apta para nuestro uso |
| LAM / LAM-Audio2Expression | [aigc3d/LAM](https://github.com/aigc3d/LAM) | Prueba realtime exitosa | Candidato activo: audio → blendshapes ARKit → renderer Gaussian/WebGL |
| OpenTalking | [datascale-ai/opentalking](https://github.com/datascale-ai/opentalking) | Probado E2E | Orquestador local viable de voz/WebRTC; Wav2Lip queda como prototipo funcional, no solución final |
| IMTalker | [bigai-nlco/IMTalker](https://github.com/bigai-nlco/IMTalker) | Evaluado | Descartado: ruta oficial offline/batch, sin streaming conversacional reutilizable |
| PersonaLive | [GVCLab/PersonaLive](https://github.com/GVCLab/PersonaLive) | Evaluado | Descartado: streaming basado en imagen/video, sin audio-driven, TTS ni STT; además declara uso académico |
| Ditto TalkingHead | [antgroup/ditto-talkinghead](https://github.com/antgroup/ditto-talkinghead) | Evaluado | Streaming técnico verificado, pero demasiado lento en 16 GB y sin salida WebRTC/frame queue lista |
| Prometheus Avatar | [myths-labs/prometheus-avatar](https://github.com/myths-labs/prometheus-avatar) | Prueba integrada exitosa | Candidato activo: Live2D vertical conectado a micrófono, STT, LLM, TTS, WebRTC y lipsync |
| CyberVerse | [Lynpoint/CyberVerse](https://github.com/Lynpoint/CyberVerse) | Evaluado | Arquitectura full-duplex interesante, pero bloqueada por hardware objetivo y licencia GPL-3.0 |
| ARACHNE-X-ULTRA-AVATAR | [HF: ARACHNE-X-ULTRA-AVATAR](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR) | Evaluado | Descartado: sin runtime reproducible, más de 128 GB y fuera de nuestra GPU de 16 GB |
| Livepeer Mission Control | [Documentación Livepeer](https://docs.livepeer.org/v2/home/mission-control) | Evaluado | Descartado: infraestructura distribuida de video, no avatar conversacional audio-driven local |
| TalkingGaussian | [Fictionarry/TalkingGaussian](https://github.com/Fictionarry/TalkingGaussian) | Evaluado | Descartado: pipeline batch por identidad, sin streaming conversacional ni entorno compatible |
| LongCat-Video-Avatar 1.5 | [meituan-longcat/LongCat-Video](https://github.com/meituan-longcat/LongCat-Video) | Investigado | MIT y 8 pasos, pero 13.6B y orientado a clips; no viable en 16 GB para conversación |
| MultiTalk | [MeiGen-AI/MultiTalk](https://github.com/MeiGen-AI/MultiTalk) | Investigado | Audio-driven y Apache-2.0, pero generación por clips demasiado lenta para vivo |
| InfiniteTalk | [MeiGen-AI/InfiniteTalk](https://github.com/MeiGen-AI/InfiniteTalk) | Investigado | Video largo audio-driven, pero muy alejado de realtime en GPU de consumo |
| Wan2.2-S2V | [Wan-Video/Wan2.2](https://github.com/Wan-Video/Wan2.2) | Investigado | Ecosistema amplio, pero 14B y sin streaming conversacional viable en 16 GB |
| HunyuanVideo-Avatar | [Tencent-Hunyuan/HunyuanVideo-Avatar](https://github.com/Tencent-Hunyuan/HunyuanVideo-Avatar) | Investigado | Muy pesado, lento y con licencia territorial incompatible con la UE |
| SkyReels-V3-A2V | [SkyworkAI/SkyReels-V3](https://github.com/SkyworkAI/SkyReels-V3) | Investigado | Modelo grande y licencia comunitaria; sin justificación para 16 GB |
| HuMo | [Phantom-video/HuMo](https://github.com/Phantom-video/HuMo) | Investigado | 1.7B disponible, pero generación de clips; no renderer incremental probado |
| OmniHuman | [Project page](https://omnihuman-lab.github.io/) | Investigado | Sin código ni pesos oficiales; únicamente servicio/API cerrado |
| OpenAvatarChat | [HumanAIGC-Engineering/OpenAvatarChat](https://github.com/HumanAIGC-Engineering/OpenAvatarChat) | Usado | Framework local de referencia para integrar audio, WebRTC y avatares |
| LiveKit Agents | [livekit/agents](https://github.com/livekit/agents) | Investigado | Buen transporte WebRTC; requiere implementar el renderer local |
| Pipecat | [pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat) | Investigado | Alternativa de orquestación local; no probada en este equipo |
| TEN Framework | [TEN-framework/ten-framework](https://github.com/TEN-framework/ten-framework) | Investigado | Buen pipeline de audio; avatar local no resuelto |
| Vision Agents | [GetStream/Vision-Agents](https://github.com/GetStream/Vision-Agents) | Investigado | Alternativa interesante con transporte local; no probada |
| LiveTalking | [lipku/LiveTalking](https://github.com/lipku/LiveTalking) | | |
| LiveAvatar | [Alibaba-Quark/LiveAvatar](https://github.com/Alibaba-Quark/LiveAvatar) | | |
| LiveTalk | [GAIR-NLP/livetalk](https://github.com/GAIR-NLP/livetalk) | | |
| Hallo | [fudan-generative-vision/hallo](https://github.com/fudan-generative-vision/hallo) | | |
| Hallo2 | [fudan-generative-vision/hallo2](https://github.com/fudan-generative-vision/hallo2) | | |
| LivePortrait | [KwaiVGI/LivePortrait](https://github.com/KwaiVGI/LivePortrait) | | |
| V-Express | [tencent-ailab/V-Express](https://github.com/tencent-ailab/V-Express) | | |
| LatentSync | [bytedance/LatentSync](https://github.com/bytedance/LatentSync) | | |
| AniPortrait | [Zejun-Yang/AniPortrait](https://github.com/Zejun-Yang/AniPortrait) | | |
| SadTalker | [OpenTalker/SadTalker](https://github.com/OpenTalker/SadTalker) | | |
| AniTalker | [X-LANCE/AniTalker](https://github.com/X-LANCE/AniTalker) | | |
| Real3D-Portrait | [yerfor/Real3DPortrait](https://github.com/yerfor/Real3DPortrait) | | |
| GeneFace++ | [yerfor/GeneFacePlusPlus](https://github.com/yerfor/GeneFacePlusPlus) | | |
| SyncTalk | [ZiqiaoPeng/SyncTalk](https://github.com/ZiqiaoPeng/SyncTalk) | | |
| ER-NeRF | [Fictionarry/ER-NeRF](https://github.com/Fictionarry/ER-NeRF) | | |
| RAD-NeRF | [ashawkey/RAD-NeRF](https://github.com/ashawkey/RAD-NeRF) | | |
| Wav2Lip | [Rudrabha/Wav2Lip](https://github.com/Rudrabha/Wav2Lip) | | |
| TalkingHead.js | [met4citizen/TalkingHead](https://github.com/met4citizen/TalkingHead) | | |
| GaussianTalker | [cvlab-kaist/GaussianTalker](https://github.com/cvlab-kaist/GaussianTalker) | | |
| SplattingAvatar | [initialneil/SplattingAvatar](https://github.com/initialneil/SplattingAvatar) | | |
| EchoMimic | [antgroup/echomimic](https://github.com/antgroup/echomimic) | | |
| LiveSpeechPortraits | [YuanxunLu/LiveSpeechPortraits](https://github.com/YuanxunLu/LiveSpeechPortraits) | | |
| AIAvatarKit | [uezo/aiavatarkit](https://github.com/uezo/aiavatarkit) | | |
| SoulX-LiveAct | [Soul-AILab/SoulX-LiveAct](https://github.com/Soul-AILab/SoulX-LiveAct) | | |
| Amica | [semperai/amica](https://github.com/semperai/amica) | | |
| Linly-Talker-Stream | [Kedreamix/Linly-Talker-Stream](https://github.com/Kedreamix/Linly-Talker-Stream) | | |
| Open-LLM-VTuber | [Open-LLM-VTuber/Open-LLM-VTuber](https://github.com/Open-LLM-VTuber/Open-LLM-VTuber) | | |
| Audio2Face 3D SDK | [NVIDIA/Audio2Face-3D-SDK](https://github.com/NVIDIA/Audio2Face-3D-SDK) | | |
| Video-Retalking | [OpenTalker/video-retalking](https://github.com/OpenTalker/video-retalking) | | |
| Ultralight-Digital-Human | [anliyuan/Ultralight-Digital-Human](https://github.com/anliyuan/Ultralight-Digital-Human) | | |
| EmoTaG | [jamesdemon923/EmoTaG](https://github.com/jamesdemon923/EmoTaG) | | |
| EchoAvatar | [RobinWitch/EchoAvatar](https://github.com/RobinWitch/EchoAvatar) | | |
| NodeAva | [Lucasmind/nodeava](https://github.com/Lucasmind/nodeava) | | |
| AI Avatar System | [PunithVT/ai-avatar-system](https://github.com/PunithVT/ai-avatar-system) | | |
| LHM | [aigc3d/LHM](https://github.com/aigc3d/LHM) | | |
| FastRTC | [gradio-app/fastrtc](https://github.com/gradio-app/fastrtc) | | |
| Avatar Chat Server | [myned-ai/avatar-chat-server](https://github.com/myned-ai/avatar-chat-server) | | |
| TalkBody4D | [HF: PixelAI-Team/TalkBody4D](https://huggingface.co/datasets/PixelAI-Team/TalkBody4D) | | |
| GMTalker | [GML-MMGroup/GMTalker](https://github.com/GML-MMGroup/GMTalker) | | |
| ARTalk | [xg-chu/ARTalk](https://github.com/xg-chu/ARTalk) | | |
| Hallo-Live | [fudan-generative-vision/Hallo-Live](https://github.com/fudan-generative-vision/Hallo-Live) | | |
| Meta-Human | [LessUp/meta-human](https://github.com/LessUp/meta-human) | | |
| Ghost Vessel | [ghdtjrtka/ghost-vessel](https://github.com/ghdtjrtka/ghost-vessel) | | |
| EMO | [HumanAIGC/EMO](https://github.com/HumanAIGC/EMO) | | |
| MEMO | [memoavatar/memo](https://github.com/memoavatar/memo) | | |
| LetsTalk | [zhang-haojie/letstalk](https://github.com/zhang-haojie/letstalk) | | |
| HelloMeme | [HelloVision/HelloMeme](https://github.com/HelloVision/HelloMeme) | | |
| DAWN | [Hanbo-Cheng/DAWN-pytorch](https://github.com/Hanbo-Cheng/DAWN-pytorch) | | |
| JoyHallo | [jdh-algo/JoyHallo](https://github.com/jdh-algo/JoyHallo) | | |
| LinguaLinker | [TencentQQGYLab/LinguaLinker](https://github.com/TencentQQGYLab/LinguaLinker) | | |
| EDTalk | [tanshuai0219/EDTalk](https://github.com/tanshuai0219/EDTalk) | | |
| Talk3D | [KU-CVLAB/Talk3D](https://github.com/KU-CVLAB/Talk3D) | | |
| DynTet | [zhangzc21/DynTet](https://github.com/zhangzc21/DynTet) | | |
| DreamTalk | [meitu/DreamTalk](https://github.com/meitu/DreamTalk) | | |
| GeneFace | [yinglinjia/GeneFace](https://github.com/yinglinjia/GeneFace) | | |
| CodeTalker | [zhouhangz/CodeTalker](https://github.com/zhouhangz/CodeTalker) | | |
| Gaussian-Head-Avatar | [xuchen-eth/Gaussian-Head-Avatar](https://github.com/xuchen-eth/Gaussian-Head-Avatar) | | |
| LivePortrait-AudioDriven | [Hekenye/LivePortrait-AudioDriven](https://github.com/Hekenye/LivePortrait-AudioDriven) | | |
| FaceFormer | [Evelyn-yy/FaceFormer](https://github.com/Evelyn-yy/FaceFormer) | | |
| MakeItTalk | [yzhou359/MakeItTalk](https://github.com/yzhou359/MakeItTalk) | | |
| TalkLip | [Sxjdwang/TalkLip](https://github.com/Sxjdwang/TalkLip) | | |
| GaussianSpeech | [shivangi-aneja/gaussianspeech](https://github.com/shivangi-aneja/gaussianspeech) | | |
| GaussianHeadTalk | [madhav-agarwal/GaussianHeadTalk](https://github.com/madhav-agarwal/GaussianHeadTalk) | | |
| AD-NeRF | [YudongGuo/AD-NeRF](https://github.com/YudongGuo/AD-NeRF) | | |
| DFA-NeRF | [ShunyuYao/DFA-NeRF](https://github.com/ShunyuYao/DFA-NeRF) | | |
| HeadNeRF | [CrisHY1995/headnerf](https://github.com/CrisHY1995/headnerf) | | |
| uLipSync | [hecomi/uLipSync](https://github.com/hecomi/uLipSync) | | |
| ComfyStream | [yolain/ComfyStream](https://github.com/yolain/ComfyStream) | | |
| DeepLiveCam | [hacksider/Deep-Live-Cam](https://github.com/hacksider/Deep-Live-Cam) | | |
| FaceFusion | [facefusion/facefusion](https://github.com/facefusion/facefusion) | | |
| Loopy | [loopyavatar/loopy](https://github.com/loopyavatar/loopy) | | |
| ChatAvatar | [DeemosTech/ChatAvatar](https://github.com/DeemosTech/ChatAvatar) | | |
| VividTalk | [HumanAIGC/VividTalk](https://github.com/HumanAIGC/VividTalk) | | |
| PIRenderer | [RenYurui/PIRender](https://github.com/RenYurui/PIRender) | | |
| TalkSHOW | [yhw-yhw/TalkSHOW](https://github.com/yhw-yhw/TalkSHOW) | | |
| Fish Speech | [fishaudio/fish-speech](https://github.com/fishaudio/fish-speech) | | |
| CosyVoice | [FunAudioLLM/CosyVoice](https://github.com/FunAudioLLM/CosyVoice) | | |
| StyleTalk | [FuxiVirtualHuman/styletalk](https://github.com/FuxiVirtualHuman/styletalk) | | |
| pixi-live2d-display | [guansss/pixi-live2d-display](https://github.com/guansss/pixi-live2d-display) | | |
| MeshTalk | [facebookresearch/meshtalk](https://github.com/facebookresearch/meshtalk) | | |
| EMOCA | [rdanecek/emoca](https://github.com/rdanecek/emoca) | | |
| talking-head-anime-3-demo | [pkhungurn/talking-head-anime-3-demo](https://github.com/pkhungurn/talking-head-anime-3-demo) | | |
| DiffPoseTalk | [DiffPoseTalk/DiffPoseTalk](https://github.com/DiffPoseTalk/DiffPoseTalk) | | |
| FaceX-Zoo | [JDAI-CV/FaceX-Zoo](https://github.com/JDAI-CV/FaceX-Zoo) | | |
| StyleHEAT | [FeiiYin/StyleHEAT](https://github.com/FeiiYin/StyleHEAT) | | |
| First Order Motion Model | [AliaksandrSiarohin/first-order-model](https://github.com/AliaksandrSiarohin/first-order-model) | | |
| Neural Voice Puppetry | [JustusThies/NeuralVoicePuppetry](https://github.com/JustusThies/NeuralVoicePuppetry) | | |
| HighSync | [saeed5959/high_sync](https://github.com/saeed5959/high_sync) | | |
| SEDTalker | [FarzanehJafari1987/SEDTalker](https://github.com/FarzanehJafari1987/SEDTalker) | | |
| C-MET | [ChanHyeok-Choi/C-MET](https://github.com/ChanHyeok-Choi/C-MET) | | |
| DiFlowDubber | [Fsoft-AIC/DiFlowDubber](https://github.com/Fsoft-AIC/DiFlowDubber) | | |
| OmniEdit | [l1346792580123/OmniEdit](https://github.com/l1346792580123/OmniEdit) | | |
| TempoSyncDiff | [mazumdarsoumya/TempoSyncDiff](https://github.com/mazumdarsoumya/TempoSyncDiff) | | |
| NarratingForYou | [narratingForYou/NarratingForYou](https://github.com/narratingForYou/NarratingForYou) | | |
| DreamID-Omni | [Guoxu1233/DreamID-Omni](https://github.com/Guoxu1233/DreamID-Omni) | | |
| 3DXTalker | [EngineeringAI-LAB/3DXTalker](https://github.com/EngineeringAI-LAB/3DXTalker) | | |
| AUHead | [laura990501/AUHead_ICLR](https://github.com/laura990501/AUHead_ICLR) | | |
| MOVA | [OpenMOSS/MOVA](https://github.com/OpenMOSS/MOVA) | | |
| SoulX-FlashTalk | [Soul-AILab/SoulX-FlashTalk](https://github.com/Soul-AILab/SoulX-FlashTalk) | | |
| LPIPS-AttnWav2Lip | [FelixChan9527/LPIPS-AttnWav2Lip](https://github.com/FelixChan9527/LPIPS-AttnWav2Lip) | | |
| JUST-DUB-IT | [justdubit/just-dub-it](https://github.com/justdubit/just-dub-it) | | |
| UA-3DTalk | [Mrask999/UA-3DTalk](https://github.com/Mrask999/UA-3DTalk) | | |
| THFEM | [liluoqaq/THFEM](https://github.com/liluoqaq/THFEM) | | |
| DyStream | [RobinWitch/DyStream](https://github.com/RobinWitch/DyStream) | | |
| X-Dub | [KlingAIResearch/X-Dub](https://github.com/KlingAIResearch/X-Dub) | | |
| TalkVerse | [snap-research/TalkVerse](https://github.com/snap-research/TalkVerse) | | |
| JoVA | [Visual-AI/JoVA](https://github.com/Visual-AI/JoVA) | | |
| STARCaster | [foivospar/STARCaster](https://github.com/foivospar/STARCaster) | | |
| UniLS | [xg-chu/UniLS](https://github.com/xg-chu/UniLS) | | |
| AnyTalker | [HKUST-C4G/AnyTalker](https://github.com/HKUST-C4G/AnyTalker) | | |
| LSF-Animation | [Dogter521/LSF-Animation](https://github.com/Dogter521/LSF-Animation) | | |
| IASA | [Beijia11/IASA](https://github.com/Beijia11/IASA) | | |
| SynchroRaMa | [novicemm/synchrorama_](https://github.com/novicemm/synchrorama_) | | |
| EmoCAST | [GVCLab/EmoCAST](https://github.com/GVCLab/EmoCAST) | | |
| FantasyTalking2 | [Fantasy-AMAP/fantasy-talking2](https://github.com/Fantasy-AMAP/fantasy-talking2) | | |
| StableAvatar | [Francis-Rings/StableAvatar](https://github.com/Francis-Rings/StableAvatar) | | |
| MemoryTalker | [kimhyungkyu-1208/MemoryTalker](https://github.com/kimhyungkyu-1208/MemoryTalker) | | |
| ATL-Diff | [sonvth/ATL-Diff](https://github.com/sonvth/ATL-Diff) | | |
| MOSPA | [xsy27/Mospa-Acoustic-driven-Motion-Generation](https://github.com/xsy27/Mospa-Acoustic-driven-Motion-Generation) | | |
| MEDTalk | [SJTU-Lucy/MEDTalk](https://github.com/SJTU-Lucy/MEDTalk) | | |
| AnimateAnyone | [HumanAIGC/AnimateAnyone](https://github.com/HumanAIGC/AnimateAnyone) | | |
| audio2photoreal | [facebookresearch/audio2photoreal](https://github.com/facebookresearch/audio2photoreal) | | |
| HunyuanPortrait | [Tencent/HunyuanPortrait](https://github.com/Tencent/HunyuanPortrait) | | |
| LangYing | [langzizhixin/LangYing](https://github.com/langzizhixin/LangYing) | | |
| LangYuan | [langzizhixin/LangYuan](https://github.com/langzizhixin/LangYuan) | | |
| DeepFaceLive | [iperov/DeepFaceLive](https://github.com/iperov/DeepFaceLive) | | |
| SyncNet | [joonson/syncnet_python](https://github.com/joonson/syncnet_python) | | |
| ComfyUI-LivePortraitKJ | [kijai/ComfyUI-LivePortraitKJ](https://github.com/kijai/ComfyUI-LivePortraitKJ) | | |
| CubismWebSDK | [Live2D/CubismWebSDK](https://github.com/Live2D/CubismWebSDK) | | |
| UniVRM | [vrm-c/UniVRM](https://github.com/vrm-c/UniVRM) | | |
| ChatVTuber | [lTaGll/ChatVTuber](https://github.com/lTaGll/ChatVTuber) | | |
| SpatialReal | [spatialwalk/livekit-plugins-spatialreal](https://github.com/spatialwalk/livekit-plugins-spatialreal) | | |
| FlashAvatar | [ustc3dv/FlashAvatar](https://github.com/ustc3dv/FlashAvatar) | | |
| RAM-Avatar | [Xiang-Deng00/RAM-Avatar](https://github.com/Xiang-Deng00/RAM-Avatar) | | |
| AnimatableGaussians | [lizhe00/AnimatableGaussians](https://github.com/lizhe00/AnimatableGaussians) | | |
| GauHuman | [skhu101/GauHuman](https://github.com/skhu101/GauHuman) | | |
| NeRFBlendShape | [USTC3DV/NeRFBlendShape-code](https://github.com/USTC3DV/NeRFBlendShape-code) | | |
| DreamGaussian | [dreamgaussian/dreamgaussian](https://github.com/dreamgaussian/dreamgaussian) | | |
| LGM | [3DTopia/LGM](https://github.com/3DTopia/LGM) | | |
| Splatter Image | [szymanowiczs/splatter-image](https://github.com/szymanowiczs/splatter-image) | | |
| live2d-py | [EasyLive2D/live2d-py](https://github.com/EasyLive2D/live2d-py) | | |
| DECA | [YadiraF/DECA](https://github.com/YadiraF/DECA) | | |
| MICA | [Zielonka/MICA](https://github.com/Zielonka/MICA) | | |
| OpenFace | [TadasBaltrusaitis/OpenFace](https://github.com/TadasBaltrusaitis/OpenFace) | | |
| DeepFaceLab | [iperov/DeepFaceLab](https://github.com/iperov/DeepFaceLab) | | |
| SenseVoice | [FunAudioLLM/SenseVoice](https://github.com/FunAudioLLM/SenseVoice) | | |
| MotionGPT | [OpenMotionLab/MotionGPT](https://github.com/OpenMotionLab/MotionGPT) | | |
| MDM | [GuyTevet/motion-diffusion-model](https://github.com/GuyTevet/motion-diffusion-model) | | |
| EDGE | [Stanford-TML/EDGE](https://github.com/Stanford-TML/EDGE) | | |
| SMPL-X | [vchoutas/smplx](https://github.com/vchoutas/smplx) | | |
| PyMAF-X | [HongwenZhang/PyMAF-X](https://github.com/HongwenZhang/PyMAF-X) | | |
| 4D-Humans | [shubham-goel/4D-Humans](https://github.com/shubham-goel/4D-Humans) | | |
| CLIFF | [ZhengDong-Work/CLIFF](https://github.com/ZhengDong-Work/CLIFF) | | |
| ExPose | [vchoutas/expose](https://github.com/vchoutas/expose) | | |
| Ultravox | [fixie-ai/ultravox](https://github.com/fixie-ai/ultravox) | | |
| Mini-Omni | [gpt-omni/mini-omni](https://github.com/gpt-omni/mini-omni) | | |
| GLM-4-Voice | [THUDM/GLM-4-Voice](https://github.com/THUDM/GLM-4-Voice) | | |
| Qwen2-Audio | [Qwen/Qwen2-Audio](https://github.com/Qwen/Qwen2-Audio) | | |
| LiveKit | [livekit/livekit](https://github.com/livekit/livekit) | | |
| Daily Python | [daily-co/daily-python](https://github.com/daily-co/daily-python) | | |
| OWT Server | [open-webrtc-toolkit/owt-server](https://github.com/open-webrtc-toolkit/owt-server) | | |
| three-vrm | [pixiv/three-vrm](https://github.com/pixiv/three-vrm) | | |
| kalidoface | [yeemachine/kalidoface](https://github.com/yeemachine/kalidoface) | | |
| live2d-widget | [stevenjoezhang/live2d-widget](https://github.com/stevenjoezhang/live2d-widget) | | |
| OpenSeeFace | [emilianavt/OpenSeeFace](https://github.com/emilianavt/OpenSeeFace) | | |
| VTubeStudio | [DenchiSoft/VTubeStudio](https://github.com/DenchiSoft/VTubeStudio) | | |
| pyvts | [DenverCoder1/pyvts](https://github.com/DenverCoder1/pyvts) | | |
| Comfyui-SadTalker | [haomole/Comfyui-SadTalker](https://github.com/haomole/Comfyui-SadTalker) | | |
| ComfyUI-MuseTalk_FSH | [AIFSH/ComfyUI-MuseTalk_FSH](https://github.com/AIFSH/ComfyUI-MuseTalk_FSH) | | |
| comfyui_openvino | [openvino-dev-samples/comfyui_openvino](https://github.com/openvino-dev-samples/comfyui_openvino) | | |
| VideoHelperSuite | [Kosinkadink/ComfyUI-VideoHelperSuite](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite) | | |
| HumanNeRF | [chungyiweng/humannerf](https://github.com/chungyiweng/humannerf) | | |
| FreeMan | [wangjiongw/FreeMan_API](https://github.com/wangjiongw/FreeMan_API) | | |
| MRAA | [snap-research/articulated-animation](https://github.com/snap-research/articulated-animation) | | |
| TPSMM | [yoyo-nb/Thin-Plate-Spline-Motion-Model](https://github.com/yoyo-nb/Thin-Plate-Spline-Motion-Model) | | |
| LIA | [wyhsirius/LIA](https://github.com/wyhsirius/LIA) | | |
| face-vid2vid | [NVlabs/face-vid2vid](https://github.com/NVlabs/face-vid2vid) | | |
| EG3D | [NVlabs/eg3d](https://github.com/NVlabs/eg3d) | | |
| PanoHead | [sizhean/panohead](https://github.com/sizhean/panohead) | | |
| Next3D | [MrTornado24/Next3D](https://github.com/MrTornado24/Next3D) | | |
| AvatarCraft | [songrise/avatarcraft](https://github.com/songrise/avatarcraft) | | |
| PointAvatar | [zhengyuf/pointavatar](https://github.com/zhengyuf/pointavatar) | | |
| EVA3D | [hongfz16/EVA3D](https://github.com/hongfz16/EVA3D) | | |
| AvatarCLIP | [hongfz16/AvatarCLIP](https://github.com/hongfz16/AvatarCLIP) | | |
| Latent-NeRF | [eladrich/latent-nerf](https://github.com/eladrich/latent-nerf) | | |
| AG3D | [zj-dong/AG3D](https://github.com/zj-dong/AG3D) | | |
| Get3DHuman | [X-zhangyang/Get3DHuman](https://github.com/X-zhangyang/Get3DHuman) | | |
| TADA | [TingtingLiao/TADA](https://github.com/TingtingLiao/TADA) | | |
| RodinHD | [RodinHD/RodinHD](https://github.com/RodinHD/RodinHD) | | |
| HumanNorm | [xhuangcv/humannorm](https://github.com/xhuangcv/humannorm) | | |
| PrimDiffusion | [FrozenBurning/PrimDiffusion](https://github.com/FrozenBurning/PrimDiffusion) | | |
| XAGen | [magic-research/xagen](https://github.com/magic-research/xagen) | | |
| TalkinNeRF | [aggelinacha/talkinnerf](https://github.com/aggelinacha/talkinnerf) | | |
| RealtimeTTS | [KoljaB/RealtimeTTS](https://github.com/KoljaB/RealtimeTTS) | | |
| ChatTTS | [2noise/ChatTTS](https://github.com/2noise/ChatTTS) | | |
| StyleAvatar3D | [icoz69/StyleAvatar3D](https://github.com/icoz69/StyleAvatar3D) | | |
| LatentAvatar | [YuelangX/LatentAvatar](https://github.com/YuelangX/LatentAvatar) | | |
| NeRSemble | [tobias-kirschstein/nersemble](https://github.com/tobias-kirschstein/nersemble) | | |
| OTAvatar | [theEricMa/OTAvatar](https://github.com/theEricMa/OTAvatar) | | |
| ClipFace | [shivangi-aneja/ClipFace](https://github.com/shivangi-aneja/ClipFace) | | |
| GANHead | [wsj-sjtu/GANHead](https://github.com/wsj-sjtu/GANHead) | | |
| AvatarMe | [lattas/AvatarMe](https://github.com/lattas/AvatarMe) | | |
| NeRFEditor | [Chuny1/NeRFEditor](https://github.com/Chuny1/NeRFEditor) | | |
| face3d | [YadiraF/face3d](https://github.com/YadiraF/face3d) | | |
| FaceVerse | [LizhenWangT/FaceVerse_v4](https://github.com/LizhenWangT/FaceVerse_v4) | | |
| LACE | [NVlabs/LACE](https://github.com/NVlabs/LACE) | | |
| MediaPipeUnityPlugin | [homuler/MediaPipeUnityPlugin](https://github.com/homuler/MediaPipeUnityPlugin) | | |
| faster-whisper | [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) | | |
| silero-vad | [snakers4/silero-vad](https://github.com/snakers4/silero-vad) | | |
| whisperX | [m-bain/whisperX](https://github.com/m-bain/whisperX) | | |
| Coqui TTS | [coqui-ai/TTS](https://github.com/coqui-ai/TTS) | | |
| CubismUnityComponents | [Live2D/CubismUnityComponents](https://github.com/Live2D/CubismUnityComponents) | | |
| vrm-specification | [vrm-c/vrm-specification](https://github.com/vrm-c/vrm-specification) | | |
| aiortc | [aiortc/aiortc](https://github.com/aiortc/aiortc) | | |
| Pion WebRTC | [pion/webrtc](https://github.com/pion/webrtc) | | |
| mediasoup | [versatica/mediasoup](https://github.com/versatica/mediasoup) | | |
| Janus Gateway | [meetecho/janus-gateway](https://github.com/meetecho/janus-gateway) | | |
| 3DGS-Avatar | [mikeqzy/3dgs-avatar-release](https://github.com/mikeqzy/3dgs-avatar-release) | | |
| ExAvatar | [mks0601/ExAvatar_RELEASE](https://github.com/mks0601/ExAvatar_RELEASE) | | |
| face-api.js | [justadudewhohacks/face-api.js](https://github.com/justadudewhohacks/face-api.js) | | |
| clmtrackr | [auduno/clmtrackr](https://github.com/auduno/clmtrackr) | | |
| jeelizFaceFilter | [jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) | | |
| tfjs-models | [tensorflow/tfjs-models](https://github.com/tensorflow/tfjs-models) | | |
| CubismWebFramework | [Live2D/CubismWebFramework](https://github.com/Live2D/CubismWebFramework) | | |
| CubismWebSamples | [Live2D/CubismWebSamples](https://github.com/Live2D/CubismWebSamples) | | |
| three-vrm-animation | [pixiv/three-vrm-animation](https://github.com/pixiv/three-vrm-animation) | | |
| Bark | [suno-ai/bark](https://github.com/suno-ai/bark) | | |
| VALL-E-X | [Plachtaa/VALL-E-X](https://github.com/Plachtaa/VALL-E-X) | | |
| OpenVoice | [myshell-ai/OpenVoice](https://github.com/myshell-ai/OpenVoice) | | |
| MeloTTS | [myshell-ai/MeloTTS](https://github.com/myshell-ai/MeloTTS) | | |
| F5-TTS | [SW-MMLAB/F5-TTS](https://github.com/SW-MMLAB/F5-TTS) | | |
| DiffGesture | [Advocate99/DiffGesture](https://github.com/Advocate99/DiffGesture) | | |
| Speech2Face | [ravising-h/speech2face](https://github.com/ravising-h/speech2face) | | |
| GFPGAN | [TencentARC/GFPGAN](https://github.com/TencentARC/GFPGAN) | | |
| CodeFormer | [sczhou/CodeFormer](https://github.com/sczhou/CodeFormer) | | |
| Real-ESRGAN | [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) | | |
| CubismNativeFramework | [Live2D/CubismNativeFramework](https://github.com/Live2D/CubismNativeFramework) | | |
| three-vrm-materials-mtoon | [pixiv/three-vrm-materials-mtoon](https://github.com/pixiv/three-vrm-materials-mtoon) | | |
| FLAME_PyTorch | [soubhiksanyal/FLAME_PyTorch](https://github.com/soubhiksanyal/FLAME_PyTorch) | | |
| whisper.cpp | [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp) | | |
| Piper TTS | [rhasspy/piper](https://github.com/rhasspy/piper) | | |
| OpenAI Realtime Console | [openai/openai-realtime-console](https://github.com/openai/openai-realtime-console) | | |
| StyleSync | [guanjz20/StyleSync](https://github.com/guanjz20/StyleSync) | | |
| Rhubarb Lip Sync | [DanielSWolf/rhubarb-lip-sync](https://github.com/DanielSWolf/rhubarb-lip-sync) | | |
| Surge | [Darussalamnoor/surge](https://github.com/Darussalamnoor/surge) | | |
| Bolna | [bolna-ai/bolna](https://github.com/bolna-ai/bolna) | | |
| TEN Agent | [TEN-framework/TEN-Agent](https://github.com/TEN-framework/TEN-Agent) | | |
| LiveKit CLI | [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | | |
| LiveKit Protocol | [livekit/protocol](https://github.com/livekit/protocol) | | |
| LiveKit Egress | [livekit/egress](https://github.com/livekit/egress) | | |
| LiveKit Ingress | [livekit/ingress](https://github.com/livekit/ingress) | | |
| OpenAI Whisper | [openai/whisper](https://github.com/openai/whisper) | | |
| MediaPipe | [google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) | | |
| ONNX Runtime | [microsoft/onnxruntime](https://github.com/microsoft/onnxruntime) | | |
| vLLM | [vllm-project/vllm](https://github.com/vllm-project/vllm) | | |
| Ollama | [ollama/ollama](https://github.com/ollama/ollama) | | |
| RingNet | [soubhiksanyal/RingNet](https://github.com/soubhiksanyal/RingNet) | | |
| CozyVoice | [FunAudioLLM/CozyVoice](https://github.com/FunAudioLLM/CozyVoice) | | |
| FunASR | [modelscope/FunASR](https://github.com/modelscope/FunASR) | | |
| Amphion | [open-mmlab/Amphion](https://github.com/open-mmlab/Amphion) | | |
| InsightFace | [deepinsight/insightface](https://github.com/deepinsight/insightface) | | |
| face_recognition | [ageitgey/face_recognition](https://github.com/ageitgey/face_recognition) | | |
| DeepFace | [serengil/deepface](https://github.com/serengil/deepface) | | |
| Pytorch_Retinaface | [biubug6/Pytorch_Retinaface](https://github.com/biubug6/Pytorch_Retinaface) | | |
| facenet-pytorch | [timesler/facenet-pytorch](https://github.com/timesler/facenet-pytorch) | | |
| dlib | [davisking/dlib](https://github.com/davisking/dlib) | | |
| OpenCV | [opencv/opencv](https://github.com/opencv/opencv) | | |
| FFmpeg | [FFmpeg/FFmpeg](https://github.com/FFmpeg/FFmpeg) | | |
| PyAV | [PyAV-Org/PyAV](https://github.com/PyAV-Org/PyAV) | | |
| spandrel | [chaiNNer-org/spandrel](https://github.com/chaiNNer-org/spandrel) | | |
| LiveKit JS Client SDK | [livekit/client-sdk-js](https://github.com/livekit/client-sdk-js) | | |
| LiveKit Python SDK | [livekit/client-sdk-python](https://github.com/livekit/client-sdk-python) | | |
| LiveKit Components React | [livekit/components-js](https://github.com/livekit/components-js) | | |
| LiveKit Rust SDK | [livekit/rust-sdks](https://github.com/livekit/rust-sdks) | | |
| Three.js | [mrdoob/three.js](https://github.com/mrdoob/three.js) | | |
| Babylon.js | [BabylonJS/Babylon.js](https://github.com/BabylonJS/Babylon.js) | | |
| gltf-pipeline | [CesiumGS/gltf-pipeline](https://github.com/CesiumGS/gltf-pipeline) | | |
| Draco | [google/draco](https://github.com/google/draco) | | |
| LiveKit JS Agents SDK | [livekit/agents-js](https://github.com/livekit/agents-js) | | |
| LiveKit Server SDK Node | [livekit/server-sdk-js](https://github.com/livekit/server-sdk-js) | | |
| LiveKit Server SDK Python | [livekit/server-sdk-python](https://github.com/livekit/server-sdk-python) | | |
| LiveKit SIP Gateway | [livekit/sip](https://github.com/livekit/sip) | | |
| Pipecat Client Web | [pipecat-ai/pipecat-client-web](https://github.com/pipecat-ai/pipecat-client-web) | | |
| Pipecat Client React | [pipecat-ai/pipecat-client-react](https://github.com/pipecat-ai/pipecat-client-react) | | |
| Daily JS SDK | [daily-co/daily-js](https://github.com/daily-co/daily-js) | | |
| Whisper-Live | [collabora/whisper-live](https://github.com/collabora/whisper-live) | | |
| Whisper-Streaming | [ufal/whisper_streaming](https://github.com/ufal/whisper_streaming) | | |
| SeamlessCommunication | [facebookresearch/SeamlessCommunication](https://github.com/facebookresearch/SeamlessCommunication) | | |
| ComfyUI-Wav2Lip | [numz/ComfyUI-Wav2Lip](https://github.com/numz/ComfyUI-Wav2Lip) | | |
| ComfyUI-MuseTalk | [chaojie/ComfyUI-MuseTalk](https://github.com/chaojie/ComfyUI-MuseTalk) | | |
| Live2D-Python | [qinyonghang/Live2D-Python](https://github.com/qinyonghang/Live2D-Python) | | |
| iFacialMocap-Python | [iFacialMocap/iFacialMocap-Python](https://github.com/iFacialMocap/iFacialMocap-Python) | | |
| py-webrtcvad | [wiseman/py-webrtcvad](https://github.com/wiseman/py-webrtcvad) | | |
| librosa | [librosa/librosa](https://github.com/librosa/librosa) | | |
| torchaudio | [pytorch/audio](https://github.com/pytorch/audio) | | |
| python-soundfile | [bastibe/python-soundfile](https://github.com/bastibe/python-soundfile) | | |
| resampy | [librosa/resampy](https://github.com/librosa/resampy) | | |
| mediasoup-client | [versatica/mediasoup-client](https://github.com/versatica/mediasoup-client) | | |
| simple-peer | [feross/simple-peer](https://github.com/feross/simple-peer) | | |
| PeerJS | [peers/peerjs](https://github.com/peers/peerjs) | | |
| godot-vrm | [V-Sekai/godot-vrm](https://github.com/V-Sekai/godot-vrm) | | |
| babylon-vrm-loader | [virtual-cast/babylon-vrm-loader](https://github.com/virtual-cast/babylon-vrm-loader) | | |
| libmediasoupclient | [versatica/libmediasoupclient](https://github.com/versatica/libmediasoupclient) | | |
| GStreamer | [GStreamer/gstreamer](https://github.com/GStreamer/gstreamer) | | |
| SRS | [ossrs/srs](https://github.com/ossrs/srs) | | |
| Agora Web SDK NG | [AgoraIO/Agora-Web-SDK-NG](https://github.com/AgoraIO/Agora-Web-SDK-NG) | | |
| Agora RTC React | [AgoraIO/Agora-RTC-React](https://github.com/AgoraIO/Agora-RTC-React) | | |
| Agora Realtime Voice Agent | [AgoraIO/Agora-Realtime-Voice-Agent](https://github.com/AgoraIO/Agora-Realtime-Voice-Agent) | | |
| VRM Add-on for Blender | [saturday06/VRM-Addon-for-Blender](https://github.com/saturday06/VRM-Addon-for-Blender) | | |
| vrm-validator | [vrm-c/vrm-validator](https://github.com/vrm-c/vrm-validator) | | |
| LiveKit Unity SDK | [livekit/client-sdk-unity](https://github.com/livekit/client-sdk-unity) | | |
| LiveKit Flutter SDK | [livekit/client-sdk-flutter](https://github.com/livekit/client-sdk-flutter) | | |
| LiveKit Go SDK | [livekit/go-sdk](https://github.com/livekit/go-sdk) | | |
| webrtc-rs | [webrtc-rs/webrtc](https://github.com/webrtc-rs/webrtc) | | |
| libdatachannel | [paullouisageneau/libdatachannel](https://github.com/paullouisageneau/libdatachannel) | | |
| LiveKit Helm Charts | [livekit/livekit-helm](https://github.com/livekit/livekit-helm) | | |
| LiveKit Android SDK | [livekit/client-sdk-android](https://github.com/livekit/client-sdk-android) | | |
| LiveKit iOS SDK | [livekit/client-sdk-ios](https://github.com/livekit/client-sdk-ios) | | |
| LiveKit C++ SDK | [livekit/cpp-sdks](https://github.com/livekit/cpp-sdks) | | |
| LiveKit React Native SDK | [livekit/client-sdk-react-native](https://github.com/livekit/client-sdk-react-native) | | |
| Pipecat Client iOS | [pipecat-ai/pipecat-client-ios](https://github.com/pipecat-ai/pipecat-client-ios) | | |
| Pipecat Client Android | [pipecat-ai/pipecat-client-android](https://github.com/pipecat-ai/pipecat-client-android) | | |
| Daily React SDK | [daily-co/daily-react](https://github.com/daily-co/daily-react) | | |
| Agora Electron SDK | [AgoraIO/Electron-SDK](https://github.com/AgoraIO/Electron-SDK) | | |
| Agora Flutter SDK | [AgoraIO/Flutter-SDK](https://github.com/AgoraIO/Flutter-SDK) | | |
| Agora Unity RTC SDK | [AgoraIO/Agora-Unity-RTC-SDK](https://github.com/AgoraIO/Agora-Unity-RTC-SDK) | | |
| Agora Unreal RTC SDK | [AgoraIO/Agora-Unreal-RTC-SDK](https://github.com/AgoraIO/Agora-Unreal-RTC-SDK) | | |
| Pipecat Client Flutter | [pipecat-ai/pipecat-client-flutter](https://github.com/pipecat-ai/pipecat-client-flutter) | | |
| Daily Android SDK | [daily-co/daily-android](https://github.com/daily-co/daily-android) | | |
| Daily iOS SDK | [daily-co/daily-ios](https://github.com/daily-co/daily-ios) | | |
| webrtc-streamer | [mpromonet/webrtc-streamer](https://github.com/mpromonet/webrtc-streamer) | | |
| mediasoup-demo | [versatica/mediasoup-demo](https://github.com/versatica/mediasoup-demo) | | |
| LiveKit Swift SDK | [livekit/client-sdk-swift](https://github.com/livekit/client-sdk-swift) | | |
| LiveKit Components Android | [livekit/components-android](https://github.com/livekit/components-android) | | |
| node-webrtc | [node-webrtc/node-webrtc](https://github.com/node-webrtc/node-webrtc) | | |
| headless-gl | [stackgl/headless-gl](https://github.com/stackgl/headless-gl) | | |
| three-gltf-viewer | [donmccurdy/three-gltf-viewer](https://github.com/donmccurdy/three-gltf-viewer) | | |
| FastAPI | [fastapi/fastapi](https://github.com/fastapi/fastapi) | | |
| uvicorn | [encode/uvicorn](https://github.com/encode/uvicorn) | | |
| websockets | [python-websockets/websockets](https://github.com/python-websockets/websockets) | | |
| Socket.IO | [socketio/socket.io](https://github.com/socketio/socket.io) | | |
| ws | [websockets/ws](https://github.com/websockets/ws) | | |
| OpenPose | [CMU-Perceptual-Computing-Lab/openpose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) | | |
| AlphaPose | [MVIG-SJTU/AlphaPose](https://github.com/MVIG-SJTU/AlphaPose) | | |
| AnimateDiff | [guoyww/AnimateDiff](https://github.com/guoyww/AnimateDiff) | | |
| IP-Adapter | [tencent-aio/IP-Adapter](https://github.com/tencent-aio/IP-Adapter) | | |
| DWPose | [IDEA-Research/DWPose](https://github.com/IDEA-Research/DWPose) | | |
| MMPose | [open-mmlab/mmpose](https://github.com/open-mmlab/mmpose) | | |
| controlnet_aux | [patrickvonplaten/controlnet_aux](https://github.com/patrickvonplaten/controlnet_aux) | | |
| Llama-Omni | [ictnlp/Llama-Omni](https://github.com/ictnlp/Llama-Omni) | | |
| Mini-Omni2 | [gpt-omni/mini-omni2](https://github.com/gpt-omni/mini-omni2) | | |
| VoiceCraft | [jasonppy/VoiceCraft](https://github.com/jasonppy/VoiceCraft) | | |
| SoundStorm PyTorch | [lucidrains/soundstorm-pytorch](https://github.com/lucidrains/soundstorm-pytorch) | | |
| VALL-E PyTorch | [lifeiteng/vall-e](https://github.com/lifeiteng/vall-e) | | |
| rembg | [danielgatis/rembg](https://github.com/danielgatis/rembg) | | |
| BiRefNet | [ZhengPeng7/BiRefNet](https://github.com/ZhengPeng7/BiRefNet) | | |
| InSPyReNet | [PyeongGang/InSPyReNet](https://github.com/PyeongGang/InSPyReNet) | | |
| RobustVideoMatting | [PeterLSO/RobustVideoMatting](https://github.com/PeterLSO/RobustVideoMatting) | | |
| ViTMatting | [hustvl/ViTMatting](https://github.com/hustvl/ViTMatting) | | |
| MODNet | [ZhengPeng7/MODNet](https://github.com/ZhengPeng7/MODNet) | | |
| face-alignment | [1adrianb/face-alignment](https://github.com/1adrianb/face-alignment) | | |
| PRNet | [YadiraF/PRNet](https://github.com/YadiraF/PRNet) | | |
| EOS | [patrikhuber/eos](https://github.com/patrikhuber/eos) | | |
| TensorRT-LLM | [NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) | | |
| SGLang | [sgl-project/sglang](https://github.com/sgl-project/sglang) | | |
| Text Generation Inference | [huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference) | | |
| DeepStream Python Apps | [NVIDIA-AI-IOT/deepstream_python_apps](https://github.com/NVIDIA-AI-IOT/deepstream_python_apps) | | |
| Aphrodite Engine | [PygmalionAI/aphrodite-engine](https://github.com/PygmalionAI/aphrodite-engine) | | |
| LMDeploy | [open-mmlab/lmdeploy](https://github.com/open-mmlab/lmdeploy) | | |
| MLX | [ml-explore/mlx](https://github.com/ml-explore/mlx) | | |
| Ollama JS | [ollama/ollama-js](https://github.com/ollama/ollama-js) | | |
| Ollama Python | [ollama/ollama-python](https://github.com/ollama/ollama-python) | | |
| llama-cpp-python | [abetlen/llama-cpp-python](https://github.com/abetlen/llama-cpp-python) | | |
| Transformers.js | [huggingface/transformers.js](https://github.com/huggingface/transformers.js) | | |
| Web LLM | [mlc-ai/web-llm](https://github.com/mlc-ai/web-llm) | | |
| MLC LLM | [mlc-ai/mlc-llm](https://github.com/mlc-ai/mlc-llm) | | |
| wgpu | [gfx-rs/wgpu](https://github.com/gfx-rs/wgpu) | | |
| ncnn | [Tencent/ncnn](https://github.com/Tencent/ncnn) | | |
| MNN | [alibaba/MNN](https://github.com/alibaba/MNN) | | |
| ExecuTorch | [pytorch/executorch](https://github.com/pytorch/executorch) | | |
| OpenVINO | [openvinotoolkit/openvino](https://github.com/openvinotoolkit/openvino) | | |
| DirectML | [microsoft/DirectML](https://github.com/microsoft/DirectML) | | |
| coremltools | [apple/coremltools](https://github.com/apple/coremltools) | | |
| Parler-TTS | [huggingface/parler-tts](https://github.com/huggingface/parler-tts) | | |
| Matcha-TTS | [shivammg/Matcha-TTS](https://github.com/shivammg/Matcha-TTS) | | |
| StyleTTS2 | [yl4579/StyleTTS2](https://github.com/yl4579/StyleTTS2) | | |
| MetaVoice-1B | [metavoice-ai/metavoice-src](https://github.com/metavoice-ai/metavoice-src) | | |
| xtts-api-server | [daswer123/xtts-api-server](https://github.com/daswer123/xtts-api-server) | | |
| sherpa-onnx | [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) | | |
| Silero Models | [snakers4/silero-models](https://github.com/snakers4/silero-models) | | |
| edge-tts | [rany2/edge-tts](https://github.com/rany2/edge-tts) | | |
| faster-whisper-server | [fedirz/faster-whisper-server](https://github.com/fedirz/faster-whisper-server) | | |
| webrtc-audio-processing | [freedesktop/webrtc-audio-processing](https://github.com/freedesktop/webrtc-audio-processing) | | |
| RNNoise | [xiph/rnnoise](https://github.com/xiph/rnnoise) | | |
| Lipreading Deep Learning | [mpcbr/lipreading](https://github.com/mpcbr/lipreading) | | |
| TalkNet-ASD | [TaoRuijie/TalkNet-ASD](https://github.com/TaoRuijie/TalkNet-ASD) | | |
| ffmpeg-python | [kkroening/ffmpeg-python](https://github.com/kkroening/ffmpeg-python) | | |
| moviepy | [Zulko/moviepy](https://github.com/Zulko/moviepy) | | |
| PyGLM | [Zplab/PyGLM](https://github.com/Zplab/PyGLM) | | |
| ModernGL | [moderngl/moderngl](https://github.com/moderngl/moderngl) | | |
| pygfx | [pygfx/pygfx](https://github.com/pygfx/pygfx) | | |
| Taichi Graphics | [taichi-dev/taichi](https://github.com/taichi-dev/taichi) | | |
| PyOpenGL | [mcfletch/pyopengl](https://github.com/mcfletch/pyopengl) | | |
| Panda3D | [panda3d/panda3d](https://github.com/panda3d/panda3d) | | |
| Pyglet | [pyglet/pyglet](https://github.com/pyglet/pyglet) | | |
| Ursina Engine | [pokepoke/ursina](https://github.com/pokepoke/ursina) | | |
| DearPyGui | [hoffstadt/DearPyGui](https://github.com/hoffstadt/DearPyGui) | | |
| Kivy | [kivy/kivy](https://github.com/kivy/kivy) | | |
| Flet | [flet-dev/flet](https://github.com/flet-dev/flet) | | |
| coturn | [coturn/coturn](https://github.com/coturn/coturn) | | |
| Pion TURN | [pion/turn](https://github.com/pion/turn) | | |
| Pion ICE | [pion/ice](https://github.com/pion/ice) | | |
| Pion DTLS | [pion/dtls](https://github.com/pion/dtls) | | |
| Pion SRTP | [pion/srtp](https://github.com/pion/srtp) | | |
| Pion RTP | [pion/rtp](https://github.com/pion/rtp) | | |
| Pion SCTP | [pion/sctp](https://github.com/pion/sctp) | | |
| Pion RTCP | [pion/rtcp](https://github.com/pion/rtcp) | | |
| Assimp | [assimp/assimp](https://github.com/assimp/assimp) | | |
| cgltf | [jkuhlmann/cgltf](https://github.com/jkuhlmann/cgltf) | | |
| tinygltf | [syoyo/tinygltf](https://github.com/syoyo/tinygltf) | | |
| meshoptimizer | [zeux/meshoptimizer](https://github.com/zeux/meshoptimizer) | | |
| ufbx | [bext-labs/ufbx](https://github.com/bext-labs/ufbx) | | |
| openfbx | [nemitz/openfbx](https://github.com/nemitz/openfbx) | | |
| glTF-Validator | [KhronosGroup/glTF-Validator](https://github.com/KhronosGroup/glTF-Validator) | | |
| glTF-Transform | [donmccurdy/glTF-Transform](https://github.com/donmccurdy/glTF-Transform) | | |
| glTF-Blender-IO | [KhronosGroup/glTF-Blender-IO](https://github.com/KhronosGroup/glTF-Blender-IO) | | |
| Basis Universal | [BinomialLLC/basis_universal](https://github.com/BinomialLLC/basis_universal) | | |
| KTX-Software | [KhronosGroup/KTX-Software](https://github.com/KhronosGroup/KTX-Software) | | |
| PixiJS | [pixijs/pixijs](https://github.com/pixijs/pixijs) | | |
| TWGL.js | [greggman/twgl.js](https://github.com/greggman/twgl.js) | | |
| regl | [regl-project/regl](https://github.com/regl-project/regl) | | |
| Pion MediaDevices | [pion/mediadevices](https://github.com/pion/mediadevices) | | |
| Pion Interceptor | [pion/interceptor](https://github.com/pion/interceptor) | | |
| Pion SDP | [pion/sdp](https://github.com/pion/sdp) | | |
| Kurento Media Server | [Kurento/kurento-media-server](https://github.com/Kurento/kurento-media-server) | | |
| Licode | [lynckia/licode](https://github.com/lynckia/licode) | | |
| Galene | [jech/galene](https://github.com/jech/galene) | | |




| NerfStudio | [nerfstudio/nerfstudio](https://github.com/nerfstudio/nerfstudio) | | |
| Instant-NGP | [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) | | |
| PIFuHD | [shunsukesaito/PIFuHD](https://github.com/shunsukesaito/PIFuHD) | | |
| PIFu | [shunsukesaito/PIFu](https://github.com/shunsukesaito/PIFu) | | |



| Deep3DFaceReconstruction | [deep3dface/Deep3DFaceReconstruction](https://github.com/deep3dface/Deep3DFaceReconstruction) | | |

## Candidato principal actual: AVTR-1 / Avaturn

AVTR-1 es, hasta ahora, la alternativa que mejor encaja con nuestras
restricciones. No depende de una camara del usuario ni genera videos completos
antes de reproducirlos: parte de una imagen fija y produce frames de forma
incremental mientras recibe audio.

Las razones para colocarlo por encima de MuseTalk, SoulX-FlashHead Lite,
EchoMimicV3 y los modelos de video diffusion son:

- renderer incremental medido cerca de tiempo real en nuestra RTX 5060 Ti de
  16 GB;
- dual-stream real: `audio_speech` mueve la boca y `audio_listen` permite que el
  avatar siga escuchando mientras habla;
- no requiere webcam, captura de movimiento ni una persona frente a la camara;
- integracion local con Faster-Whisper, Ollama y Piper;
- salida web accesible desde Windows y presentacion vertical 9:16;
- la identidad se puede cambiar usando una imagen de referencia, sin preparar
  un modelo 3D ni entrenar un avatar nuevo.

La principal reserva no es tecnica sino legal: el renderer y el streamer tienen
licencia PolyForm Noncommercial y los modelos incluidos tienen restricciones
adicionales. Es un candidato muy fuerte para el prototipo local, pero habria
que resolver la licencia de Avaturn antes de un uso comercial.

## Opciones probadas localmente

### LiteAvatar

**Estado:** baseline disponible, no descartado formalmente.

**Qué probamos:** integración dentro de OpenAvatarChat, incluyendo audio, TTS y reproducción de frames.

**Resultado:**

- Llegó a funcionar de extremo a extremo.
- Después de ajustar VAD y mover el procesamiento del avatar a CPU, la respuesta mejoró de forma apreciable.
- La experiencia seguía teniendo latencia perceptible y el avatar depende de paquetes de identidad preparados.
- Es una solución 2D/ligera, no un talking head fotorealista generalizable desde una imagen cualquiera.

**Conclusión:** conservar como fallback de baja latencia y como referencia de sincronización, pero no tomarlo como solución visual final si necesitamos una identidad nueva o mayor realismo.

### MuseTalk

Repositorio oficial: [TMElyralab/MuseTalk](https://github.com/TMElyralab/MuseTalk)

**Qué probamos:** integración con OpenAvatarChat, Faster-Whisper, Kokoro/Piper y el pipeline de conversación en español.

**Problemas observados:**

- Desfase entre audio y movimiento de boca.
- Algunas ejecuciones entregaban el audio antes de que comenzara la animación.
- Hubo ejecuciones congeladas o sin respuesta.
- El TTS también presentó fallos en determinadas configuraciones.
- El resultado visual fue considerado insatisfactorio por comparación directa.

**Decisión:** descartado. No seguir invirtiendo en ajustes de MuseTalk para este objetivo.

### SoulX-FlashHead Lite

Repositorio oficial: [Soul-AILab/SoulX-FlashHead](https://github.com/Soul-AILab/SoulX-FlashHead)

**Qué probamos:** instalación local, ejecución en WSL2, integración con el flujo conversacional y prueba vertical 9:16.

**Problemas observados:**

- Desfase audio-video en la integración en vivo.
- Ejecuciones congeladas o poco confiables.
- La conexión entre generación de frames y reproducción de audio no quedó suficientemente robusta.
- La calidad/estabilidad práctica no compensó la complejidad de integración.

**Decisión:** descartado por ahora, a pedido del usuario. El checkout y el handler pueden conservarse como referencia histórica, pero no forman parte del camino activo.

### EchoMimicV3-Flash

Repositorio oficial: [antgroup/echomimic_v3](https://github.com/antgroup/echomimic_v3)  
Pesos oficiales: [BadToBest/EchoMimicV3](https://huggingface.co/BadToBest/EchoMimicV3)

**Instalación:**

- Checkout: `/home/usuario/EchoMimicV3`
- Entorno aislado: `/home/usuario/EchoMimicV3/.venv`
- Backbone: Wan2.1-Fun-V1.1-1.3B-InP
- Encoder de audio Flash: `chinese-wav2vec2-base`
- PyTorch CUDA operativo en WSL2.
- Se fijó Diffusers 0.31.0 dentro del venv porque la versión compartida 0.39.0 no exponía el helper de carga meta esperado por el repositorio.

**Prueba realizada:**

- Audio Piper en español.
- Imagen vertical de demo.
- 81 frames.
- 25 FPS.
- 8 pasos.
- Resolución resultante: 368×672, aproximadamente 9:16.
- Tiempo de generación: aproximadamente 75 segundos.
- Duración del video: 3,24 segundos.

Resultado: [video de prueba](echomimic_flash_spanish_512.mp4).

**Resultado técnico:** la generación terminó correctamente, conservó la identidad visual y produjo un MP4 con audio. El frame intermedio inspeccionado tiene buena calidad visual.

**Motivo por el que no pasa todavía a producción:** genera aproximadamente 23 veces más lento que la reproducción en nuestra RTX 5060 Ti de 16 GB. Es un pipeline offline de video diffusion, no un renderer incremental de tiempo real. Además, la variante Flash usa un encoder de audio chino, por lo que la calidad de sincronización con español debe evaluarse con más muestras si se considera para contenido offline.

**Decisión:** no integrarlo al avatar conversacional en vivo. Mantenerlo como opción para clips offline o como referencia visual de calidad.

## Alternativas de avatar investigadas pero no probadas localmente

Estas opciones se estudiaron durante la comparación, pero no deben marcarse como “fallaron” porque no se ejecutaron en este equipo.

### Audio-driven video diffusion

| Proyecto | Motivo para no seguir ahora |
|---|---|
| [LongCat-Video-Avatar 1.5](https://github.com/meituan-longcat/LongCat-Video) | MIT y 8 pasos, pero modelo de 13.6B; orientado a generación de clips, no a latencia conversacional en 16 GB |
| [MultiTalk](https://github.com/MeiGen-AI/MultiTalk) | Apache 2.0 y multi-persona, pero generación por clips; demasiado lento para vivo |
| [InfiniteTalk](https://github.com/MeiGen-AI/InfiniteTalk) | Apache 2.0 y video largo, pero los reportes de uso real muestran tiempos muy alejados del tiempo real en GPUs de consumo |
| [Wan2.2-S2V](https://github.com/Wan-Video/Wan2.2) | Ecosistema amplio y quants disponibles, pero 14B; 16 GB es un mínimo muy exigente y no resuelve streaming conversacional |
| [HunyuanVideo-Avatar](https://github.com/Tencent-Hunyuan/HunyuanVideo-Avatar) | Muy pesado, lento y con licencia territorial que excluye UE/UK/Corea del Sur |
| [SkyReels-V3-A2V](https://github.com/SkyworkAI/SkyReels-V3) | Modelo grande y licencia comunitaria; sin medición local que justifique el coste en 16 GB |
| [HuMo](https://github.com/Phantom-video/HuMo) | 1.7B disponible, pero continúa siendo generación de clips y no un renderer incremental probado |
| OmniHuman | Sin pesos ni código oficiales; solo servicio/API |

### Renderers rápidos o de rigging

| Opción | Motivo para no seguirla aún |
|---|---|
| Live2D | Podría dar muy baja latencia, pero requiere un avatar 2D preparado y no entrega el realismo buscado |
| VRM/Unity + uLipSync | Camino técnicamente sólido para tiempo real, pero implica crear o conseguir un modelo VRM y resolver la capa de expresiones/animación |
| LAM-Audio2Expression | Produce blendshapes ARKit en tiempo real; es un buen candidato si elegimos un avatar 3D, pero todavía no se integró |
| Gaussian/3D talking heads | Prometedores, pero el coste de preparar identidad, runtime y render todavía no está resuelto para este equipo |
| NVIDIA Audio2Face | Alternativa de rigging, no un renderer local completo listo para nuestro flujo; requiere una capa 3D y conexión con el pipeline |

## Frameworks y orquestación

### OpenAvatarChat

Es el framework que usamos en las pruebas locales de extremo a extremo.

Componentes usados o validados:

- RTC y frontend accesible desde Windows a través de WSL2.
- Faster-Whisper para STT.
- Silero VAD.
- Smart Turn EOU / detector semántico.
- Ollama como servidor LLM compatible.
- Kokoro y Piper como TTS.
- Handlers de LiteAvatar, MuseTalk y SoulX-FlashHead.

Ventaja: ya contiene handlers de avatar, audio y conversación local.  
Desventaja: cada renderer tiene restricciones de sincronización distintas y no existe todavía un handler genérico para EchoMimicV3.

### LiveKit Agents

Repositorio: [livekit/agents](https://github.com/livekit/agents)

Ventajas:

- Excelente transporte WebRTC y arquitectura de agentes.
- Soporta servidores locales y endpoints compatibles con OpenAI.
- Tiene un punto de extensión claro para un `VideoGenerator` personalizado.

Limitación para este proyecto: los avatares documentados son proveedores cloud. Para un avatar local habría que implementar el renderer y su sincronización como componente propio.

### Pipecat

Repositorio: [pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat)

Es probablemente el camino de menor fricción para un pipeline de audio 100% local: Whisper/faster-whisper, Ollama, Piper, Kokoro y otros motores están contemplados. Sin embargo, el renderer de avatar local también habría que desarrollarlo.

### TEN Framework

Repositorio: [TEN Framework](https://github.com/TEN-framework/ten-framework)

Tiene primitives locales interesantes para VAD, turn detection, STT y TTS. Su capa de avatar está fuertemente orientada a participantes RTC de proveedores cloud, por lo que no elimina el trabajo de crear un renderer local.

### Vision Agents

Repositorio: [GetStream/Vision-Agents](https://github.com/GetStream/Vision-Agents)

Alternativa investigada por su transporte local y su interfaz de avatar/video. No se ha probado en este equipo. Puede ser candidato si decidimos abandonar OpenAvatarChat como base.

## Componentes de audio y conversación

### LLM

- Servidor: Ollama.
- Modelo probado: `qwen2.5:7b`.
- Uso: endpoint local compatible con OpenAI.
- Se configuró el comportamiento en español y un prompt de conversación conectado con preguntas nuevas mientras el avatar continúa hablando.

### STT

- Motor probado: Faster-Whisper.
- Modelo: `large-v3`.
- Dispositivo: CUDA.
- Idioma: español.

El modelo funciona, pero su coste de latencia es mayor que un modelo streaming dedicado. Para una siguiente iteración conviene comparar un ASR streaming más pequeño antes de seguir optimizando el avatar.

### TTS

Probados:

- Kokoro: rápido y local; voces españolas con calidad variable.
- Piper: muy rápido y usable en español.
- Voz seleccionada para las pruebas: `es_MX-claude-high`.

Se detectó ruido continuo en algunos WAV. La comparación aislada mostró que el ruido estaba presente incluso en los archivos generados directamente por Piper, no introducido únicamente por el avatar. La voz mexicana seleccionada fue la que mejor resultado práctico dio en la conversación.

## Arquitectura actual de referencia

```text
Micrófono
   ↓
OpenAvatarChat
   ├── Silero VAD / Smart Turn
   ├── Faster-Whisper large-v3 (es)
   ├── Ollama + qwen2.5:7b
   ├── Piper es_MX-claude-high
   └── LiteAvatar como baseline de baja latencia
```

EchoMimicV3-Flash queda fuera de este diagrama porque su generación actual no es streaming.

## Próximas líneas de trabajo

1. Mantener AVTR-1 como camino principal y medir TTFF, p95 de chunks y uso de VRAM en conversaciones largas.
2. Evaluar un avatar 3D/VRM con audio-to-blendshapes si la prioridad es tiempo real.
3. Comparar un ASR streaming más pequeño para reducir el tiempo hasta la primera respuesta.
4. Considerar LiveKit o Pipecat solo después de definir el renderer local; cambiar el framework no resuelve por sí solo la generación de video.
5. No integrar EchoMimicV3 hasta disponer de una estrategia de chunking/streaming que reduzca sustancialmente los aproximadamente 75 segundos por clip corto.
## FasterLivePortrait + JoyVASA - evaluacion 2026-08-02

Repositorio clonado localmente: `FasterLivePortrait/` desde
`warmshao/FasterLivePortrait`.

### Lo que si resuelve

La ruta base de LivePortrait procesa una webcam o un video frame a frame. El
proyecto declara mas de 30 FPS con TensorRT en una RTX 3090, incluyendo
preprocesado y postprocesado, y ofrece ejecucion de camara en tiempo real. El
codigo es MIT, aunque los modelos conservan sus propias licencias.

### Lo que no resuelve para nuestro caso

La ruta de audio usa JoyVASA. En el codigo actual, `run_audio_driving()` pasa el
WAV completo a `gen_motion_sequence(audio_path)`. Esa funcion carga el audio
entero, lo divide internamente en ventanas, genera todos los movimientos y
devuelve la secuencia completa antes de comenzar a renderizar y guardar el MP4.
No hay un productor/consumidor de audio y frames que permita empezar a hablar
mientras sigue llegando el audio.

Ademas, la configuracion de FasterLivePortrait usa `chinese-hubert-base` y
`motion_generator_hubert_chinese.pt` para JoyVASA. La calidad para audio en
espanol queda sin validar y no debe asumirse por la mencion generica de soporte
multilingue.

La ruta recomendada por el proyecto depende de TensorRT 8.x y cuDNN 8.x, con
referencias de CUDA 12.1/12.2. No hay una medicion oficial para nuestra RTX
5060 Ti de 16 GB ni una ruta documentada para Blackwell/WSL que podamos dar por
segura.

**Estado:** no se descarga todavia el paquete de modelos ni se integra al
stack. La ruta de webcam no entra en nuestro alcance, porque necesitamos un
avatar independiente. La ruta audio-driven puede reutilizar componentes de
nuestro stack, pero requiere un adaptador incremental propio:

1. Piper entrega audio PCM/WAV en chunks, sin camara.
2. Un buffer acumula una ventana minima de audio y la envia a JoyVASA.
3. Se conservan `prev_motion_feat` y `prev_audio_feat` entre ventanas para
   continuar la secuencia sin reinicializarla.
4. Los movimientos se pasan al renderer LivePortrait con una imagen fija.
5. Los frames resultantes se publican junto con el audio en OpenAvatarChat.

La prueba correcta seria medir TTFF, tiempo por ventana y continuidad de audio
durante una respuesta TTS real. Si la primera ventana tarda mas que su duracion
de audio, el modelo no cumple realtime aunque el renderer posterior alcance
30 FPS. Esto seria una validacion de un adaptador propio, no del pipeline
audio-driven listo para usar que trae el repositorio.

Referencias:

- [FasterLivePortrait](https://github.com/warmshao/FasterLivePortrait)
- [JoyVASA](https://github.com/jdh-algo/JoyVASA)
- [Licencia de FasterLivePortrait](https://github.com/warmshao/FasterLivePortrait/blob/master/LICENSE)

## Duix-Avatar + Duix-Mobile - evaluacion 2026-08-02

Repositorios clonados localmente:

- `Duix-Avatar/`: `duixcom/Duix-Avatar`
- `Duix-Mobile/`: `duixcom/Duix-Mobile`

### Duix-Avatar

Duix-Avatar es un generador offline de videos de avatar. El `docker-compose.yml`
define tres servicios separados: Fish-Speech para TTS, FunASR para ASR y
`duix.avatar` para generar el video. El `docker-compose-lite.yml` deja solo el
servicio de generacion de video. El compose se valido sin errores, pero no se
descargaron las imagenes Docker.

La documentacion oficial expone los endpoints `/v1/invoke`, `/easy/submit` y
`/easy/query`, y describe explicitamente la sintesis como **no realtime**. El
README recomienda RTX 4070, 32 GB de RAM y mas de 100 GB de espacio; tambien
indica que el despliegue completo descarga aproximadamente 70 GB. Nuestra
RTX 5060 Ti tiene 16 GB de VRAM y no aparece entre las configuraciones
oficialmente verificadas.

**Resultado:** no es un reemplazo viable para el renderer conversacional de
OpenAvatarChat. Puede servir para generar clips offline, pero no para la
respuesta incremental que necesitamos. No se inicia el compose por defecto
porque implicaria una descarga grande y no validaria tiempo real.

### Duix-Mobile

Duix-Mobile si contiene un renderer local en tiempo real, pero como SDK nativo
para Android/iOS. La variante Android documenta:

- Android 10+, `arm64-v8a`/`armeabi-v7a`.
- Render con OpenGL ES mediante `DUIXRenderer` o un `RenderSink` propio.
- Entrada de audio PCM mono, 16 kHz, 16 bits.
- Streaming con `startPush()`, `pushPcm()` y `stopPush()`.
- Modelos de avatar descargables como paquetes ZIP y configuracion base propia.
- Requisito de al menos 1 GB libre para el avatar y hardware movil de 8 nucleos
  como referencia.

El repositorio afirma soporte de streaming, interrupcion y barge-in. Esas
funciones son interesantes para nuestro objetivo, pero no existe un backend
Windows/Web listo ni un adaptador para OpenAvatarChat. Para probarlo de forma
real hay que compilar la app Android, instalar los modelos en un dispositivo o
emulador y conectar nuestro LLM/STT/TTS mediante una nueva capa nativa.

En este equipo la prueba quedo bloqueada por infraestructura, no por un error
del SDK: no estan instalados JDK, Android SDK ni `adb`, y no hay un dispositivo
Android/emulador disponible. No se modifico el SDK ni se descargo un modelo.

### Licencia y riesgo de producto

Ambos repositorios usan la **DUIX.COM Community License**, no una licencia OSS
permisiva. Exige atribucion, avisos visibles y el texto de marca indicado por
Duix. La licencia establece que por encima de 1.000 usuarios activos mensuales
hay que solicitar una licencia comercial expresa. Esto contradice el umbral
mas alto que aparece en el README de Duix-Avatar, por lo que la licencia debe
considerarse el documento vinculante hasta obtener confirmacion escrita.

Referencias:

- [Duix-Avatar](https://github.com/duixcom/Duix-Avatar)
- [Duix-Mobile](https://github.com/duixcom/Duix-Mobile)
- [Licencia de Duix-Avatar](https://raw.githubusercontent.com/duixcom/Duix-Avatar/main/LICENSE)
- [Licencia de Duix-Mobile](https://github.com/duixcom/Duix-Mobile/blob/main/LICENSE)

**Decision:** Duix-Avatar queda descartado para tiempo real y Duix-Mobile queda
como candidato experimental condicionado a disponer de Android. No se incorpora
ninguno al stack web/WSL actual; LAM permanece sin cambios.

## AVTR-1 / Avaturn - evaluacion 2026-08-02

Repositorio clonado localmente:

- `avtr-1/`: `avaturn-live/avtr-1`

### Encaje tecnico

#### Ruta principal del prototipo

AVTR-1 reemplaza a LiteAvatar como renderer principal del camino activo:

```text
Mic -> OpenAvatarChat / streamer web
       |-- Faster-Whisper large-v3 (es)
       |-- Ollama + qwen2.5:7b
       |-- Piper es_MX-claude-high
       `-- AVTR-1 / Avaturn (audio_speech + audio_listen)
```

LiteAvatar queda como fallback de baja latencia. LAM permanece como alternativa
si mas adelante decidimos adoptar un avatar 3D/Gaussian con blendshapes.

AVTR-1 esta disenado especificamente para dialogo en vivo a partir de una
imagen de retrato fija. No requiere webcam ni video de una persona. Recibe dos
streams de audio en paralelo:

- `audio_speech`: voz que el avatar esta reproduciendo y que mueve los labios.
- `audio_listen`: voz del interlocutor, usada para generar escucha activa,
  microexpresiones y continuidad mientras el avatar habla.

### Formato de avatares y backgrounds

En nuestra instalacion, los avatares no son archivos GLB ni modelos 3D. Son
imagenes PNG de referencia en:

```text
artifacts/main/avatars_artifacts/reference_frames/
```

Los backgrounds tambien son PNG y viven en:

```text
artifacts/main/avatars_artifacts/backgrounds/
```

El renderer preprocesa la imagen del avatar y extrae sus caracteristicas
faciales al arrancar. Para agregar una identidad nueva alcanza con incorporar
un PNG compatible, preferentemente RGBA, frontal, bien iluminado y con cabeza y
hombros visibles. Opcionalmente puede agregarse una mascara
`<avatar>.pbmask.png`. No hay que entrenar un modelo nuevo ni preparar un GLB.

La UI descubre automaticamente los nuevos PNG al reiniciar el renderer. Se
agrego una preview local para elegir avatar y background antes de `Start
Session`; la prueba desde Windows valido 18 avatares y 10 backgrounds.

El renderer genera chunks de 5 frames a 25 FPS, equivalentes a 200 ms de
salida. La tabla oficial declara 166 ms por chunk en una RTX 4060 Ti; nuestra
RTX 5060 Ti debera medirse localmente y no se considera validada hasta tener
esa medicion.

### Preparacion local

- WSL Ubuntu-26.04 arranca correctamente y expone la RTX 5060 Ti de 16 GB.
- Entorno Pixi `renderer` instalado de forma aislada dentro de WSL.
- PyTorch 2.7.1 + CUDA 12.8: CUDA disponible y GPU detectada.
- TensorRT 10.11.0: importacion correcta.
- No se modifico el entorno activo de OpenAvatarChat/LAM.

Los artefactos ya fueron descargados despues de autorizar la cuenta en
Hugging Face. Incluyen aproximadamente 613 MB del checkpoint, 1.26 GB de
HuBERT ONNX y otros modelos del renderer. Los siete engines TensorRT fueron
compilados para la RTX 5060 Ti.

### Validacion local del renderer

Prueba single-stream:

- Avatar: `maria` desde una imagen estatica.
- Entrada: `example/speaker_1.ogg`.
- Salida: 60.07 s, 1505 frames, 25 FPS, 1280x720, con audio muxed.

Prueba dual-stream:

- `speech`: `example/speaker_1.ogg`.
- `listen`: `example/speaker_2.ogg`.
- 301 chunks, 60.2 s de salida.
- Promedio medido: **186 ms por chunk de 200 ms**, aproximadamente 1.08x
  realtime en la RTX 5060 Ti.

El dual-stream funciona en el renderer: el avatar puede seguir generando su
habla mientras procesa el audio del interlocutor para escucha activa. La
validacion offline se complemento con el streamer web local y el transporte
WebRTC. La conversacion en espanol, el audio del avatar, el lipsync y la salida
vertical fueron validados desde Windows.

Tambien se probo la muestra real `cmp_piper_es_MX-claude-high.wav`: 7.62 s de
audio, 195 frames y 7.8 s de video, con un promedio de 185 ms por chunk tras
el warm-up. El formato de la voz Piper actual es compatible con el renderer.

### Integracion con nuestro stack

Se agrego un adaptador local en `avtr-1/src/avaturn_live_streamer/conversation_engines/local_client.py`.
El streamer web usa ahora:

- Faster-Whisper `large-v3`, CUDA, idioma espanol, para transcribir los turnos.
- Ollama `qwen2.5:7b` en `127.0.0.1:11434` para el dialogo.
- Piper `es_MX-claude-high` para sintetizar la respuesta.

El adaptador aplica VAD energetico local sobre los chunks de 20 ms, encola la
pregunta sin publicar `DiscardAvatarSpeechBuffer`, y procesa la respuesta
mientras el renderer sigue recibiendo `audio_listen`. Las frases se envian a
`SpeechScheduler` en chunks PCM de 80 ms; las respuestas consecutivas se
serializan para no perder segmentos cuando el avatar aun esta hablando.

La web local se levanta con un unico orquestador: renderer en `:8000` y
streamer en `:7860`. La UI deja seleccionado `Local espanol` y presenta el
video en 9:16 mediante un recorte centrado del frame nativo 1280x720. Esto es
vertical a nivel de presentacion; cambiar el modelo para generar nativamente
9:16 no es necesario para esta validacion.

Antes de iniciar la sesion, la UI muestra tarjetas de preview para cada avatar
y background. Las imagenes se sirven desde el renderer a traves del streamer,
por lo que Windows solo necesita acceder a `http://<wsl-ip>:7860`.

### Licencia y decision provisional

El modelo tiene una licencia comunitaria con umbral comercial de USD 10M de
ingresos anuales. En cambio, el renderer y el streamer estan bajo PolyForm
Noncommercial; para uso comercial requieren licencia de Avaturn sin importar
los ingresos. Ademas, los modelos InsightFace incluidos tienen restricciones
de uso comercial. Por eso:

**Estado: candidato principal. Renderer validado en realtime y dual-stream;
adaptador local espanol implementado; audio, lipsync, preview de assets y web
9:16 validados desde Windows. La integracion queda como prototipo de evaluacion
hasta resolver la licencia PolyForm del renderer y del streamer antes de
cualquier uso comercial.**

Referencias:

- [AVTR-1](https://github.com/avaturn-live/avtr-1)
- [Licencia del modelo](https://github.com/avaturn-live/avtr-1/blob/main/LICENSE-MODEL.md)
- [Licencia del renderer](https://github.com/avaturn-live/avtr-1/blob/main/LICENSE-RENDERER.md)
- [Licencia del streamer](https://github.com/avaturn-live/avtr-1/blob/main/LICENSE-STREAMER.md)

## AvatarForcing - resultado de la prueba

Repositorio clonado localmente en `AvatarForcing/`, commit `63b73e6`.

### Que promete

AvatarForcing implementa una arquitectura de difusion causal de un paso con
ventana de futuro local. El paper reporta 34 ms por frame a 25 FPS y un retardo
por defecto de aproximadamente 0,51 s, pero no especifica una RTX 4090, RTX
5060 Ti ni otra GPU de consumo para esa cifra.

El repositorio actual no trae un servidor WebRTC, WebSocket ni una API de
streaming de audio. `inference.py` solo acepta una imagen, un audio y un prompt
fijo para generar un MP4 offline. Por lo tanto, aunque la arquitectura sea
interesante para tiempo real, no es enchufable directamente a nuestro
streamer/web stack.

### Prueba en nuestra maquina

Hardware: RTX 5060 Ti con 16 GB de VRAM, WSL limitado a 22 GB de RAM y 8 GB de
swap.

Se descargaron los pesos oficiales necesarios. El checkpoint de AvatarForcing
contiene tres bloques de aproximadamente 6,38 GB cada uno (`generator`,
`critic`, `generator_ema`); el encoder UMT5-XXL ocupa aproximadamente 11,4 GB
en disco y el DiT Wan otros 5,7 GB.

La CLI original fue terminada por el kernel durante `torch.load`, con un OOM
documentado en el journal de WSL. Se probaron localmente optimizaciones de
carga (`mmap`, `assign=True`, BF16 y UMT5 en CPU). Con ellas el DiT llego a
reservar aproximadamente 5,7 GB de VRAM y 10 GB de RAM, pero WSL volvio a caer
al cargar UMT5-XXL. No se genero ningun MP4 y no se valido español, 9:16 ni
streaming.

### Licencia y decision

El README declara Apache-2.0, pero el `LICENSE.txt` incluido impone de forma
explicita uso exclusivamente academico y prohibe uso comercial o de
produccion. Esa discrepancia es un bloqueo independiente del problema de
hardware.

**Estado: descartado para nuestro stack realtime local de 16 GB.** Puede ser
interesante para una futura maquina con mas RAM/VRAM y un adaptador de streaming
propio, pero no conviene invertir en integrarlo ahora: requiere superar el
limite de memoria de WSL, adaptar la inferencia offline a streaming y resolver
la licencia restrictiva.

Referencias:

- [Repositorio AvatarForcing](https://github.com/KlingAIResearch/AvatarForcing)
- [Modelo AvatarForcing](https://huggingface.co/lycui/AvatarForcing)
- [Paper](https://arxiv.org/html/2603.14331)
- [LICENSE.txt efectiva](https://github.com/KlingAIResearch/AvatarForcing/blob/main/LICENSE.txt)

## LAM - resultado de la prueba actual

## OpenTalking — probado en local

Repositorio: [datascale-ai/opentalking](https://github.com/datascale-ai/opentalking)

**Estado:** probado de extremo a extremo el 2026-08-02. OpenTalking es un
orquestador de voz, WebRTC y avatares; no es un único modelo de avatar. En
esta prueba se usó su backend local de Wav2Lip.

**Configuración validada:**

- API unificada en `8210` y frontend web en `5280`, accesibles desde Windows:
  `http://127.0.0.1:5280`.
- LLM: Ollama con `qwen2.5:7b`, endpoint OpenAI-compatible local.
- STT: SenseVoiceSmall de FunASR, descargado localmente y cargado en CPU.
- TTS: Edge TTS con voz `es-MX-DaliaNeural`.
- Avatar: Wav2Lip local con `wav2lip384.pth`, imagen de referencia y detector
  facial en CPU; inferencia del modelo en `cuda:0`.
- GPU: RTX 5060 Ti de 16 GB; el uso observado quedó alrededor de 2,5 GB de
  VRAM después de la prueba.
- No requiere webcam: el avatar parte de una imagen/asset preparado y recibe
  audio generado.

**Resultado:**

- `/health` respondió `200` y `/models` reportó Wav2Lip como
  `local_runtime` conectado.
- La sesión WebRTC llegó a estado conectado desde la interfaz Windows.
- Una prueba de texto en español recorrió LLM → TTS → audio/video WebRTC →
  Wav2Lip, con respuesta visible y audio generado.
- Los logs registraron chunks de aproximadamente 933 ms renderizados en
  0,92–1,02 s. Es una medición de backend, no todavía una medición completa
  de latencia percibida por micrófono.

**Limitaciones y decisión:**

- Wav2Lip modifica principalmente la región de la boca; no resuelve gestos de
  manos, postura o acciones bajo demanda.
- El TTS usado en esta validación (`edge`) no es local. Para cumplir la
  exigencia de 100% offline hay que conectar un proveedor local compatible,
  por ejemplo Piper, Kokoro o CosyVoice.
- La interfaz activa de conversación, configuración y previsualización quedó
  traducida al español; los textos chinos que permanecen en el código sólo
  pertenecen a prototipos y espacios no montados en esta validación.
- Se marca como **candidato viable para prototipo realtime**, no como solución
  final: falta medir interacción por micrófono y comparar la latencia sostenida
  contra AVTR-1/Avaturn.

**Incidencias resueltas durante la prueba:** el health check devolvía `500`
porque se había incluido `edge` dentro de los proveedores STT; `edge` es un
proveedor TTS y no un proveedor STT válido en OpenTalking. Se corrigió a
`sensevoice,openai_compatible`. También fue necesario instalar `torchaudio`
para que FunASR pudiera cargar SenseVoiceSmall.

### Actualización: prueba exitosa de español y audio

El 2026-08-02 se recompiló y se validó nuevamente el flujo con:

- Qwen2.5:7B local vía Ollama.
- SenseVoiceSmall local para STT.
- Edge TTS `es-MX-DaliaNeural`.
- Wav2Lip local en CUDA.

La API respondió `200` en `/health` y `/models`, con una sola instancia de la
API y una sola instancia de la web. El endpoint `/tts/preview` generó un WAV
PCM válido de 16 bits, mono, 16 kHz y 109868 bytes con texto en español. La
reproducción WebRTC se ajustó para reintentar el `play()` cuando la pista de
audio llega después del `MediaStream`, además de mostrar un fallback de
activación manual si el navegador bloquea el autoplay.

**Estado actualizado: prueba exitosa para prototipo realtime local en español.**
El TTS está verificado en backend y la salida de audio/video WebRTC está
integrada; queda como siguiente paso medir de forma sistemática la latencia
percibida por micrófono y la reproducción en distintos navegadores.

LAM-Audio2Expression se inicializ¢ correctamente dentro de OpenAvatarChat. El predictor devuelve 52 blendshapes ARKit a 30 FPS y proces¢ bloques de un segundo en aproximadamente 7--9 ms despu‚s del warm-up inicial de 565 ms. El stack carg¢ el asset WebGL `barbara.zip`, Faster-Whisper, Piper y el handler LAM; frontend y asset respondieron con HTTP 200 en `https://localhost:8282`.

Los pesos usados fueron `LAM_audio2exp_streaming.tar` y el wav2vec2 local existente. La VRAM observada fue de aproximadamente 6,2 GB sobre 16 GB. A diferencia de MuseTalk, SoulX-FlashHead y EchoMimicV3, LAM no sintetiza un clip de video por difusi¢n: convierte audio en expresiones y deja el render Gaussian en WebGL. Por eso queda como candidato activo para el camino de tiempo real.

Pendiente: validar con una conversaci¢n real la sincronizaci¢n, la calidad visual y el comportamiento duplex desde Windows.

## IMTalker - evaluado y descartado para realtime

Repositorio clonado localmente en `IMTalker/`, commit `bd91867`.

### Qué promete

IMTalker es un talking face audio-driven basado en Flow Matching e Implicit
Motion Transfer. El README reporta 42 FPS en una RTX 4090 a 512x512 para la
generación guiada por audio, además de control de pose de cabeza y mirada.

### Verificación contra nuestro requisito principal

La implementación oficial no es streaming:

- `app.py` recibe un archivo de audio completo y lo procesa con Wav2Vec2.
- `generator.sample(...)` calcula toda la secuencia de movimiento antes de
  devolverla.
- El renderer decodifica todos los frames, los acumula con `torch.stack` y
  recién después escribe y muxea un MP4 con FFmpeg.
- No incluye WebRTC, WebSocket, salida de frames incremental ni métrica de
  tiempo hasta el primer frame.

El generador divide internamente secuencias largas en chunks para gestionar la
memoria, pero esos chunks no se publican al consumidor: se vuelven a unir y se
devuelve el resultado completo. Por tanto, los 42 FPS son throughput offline,
no 42 FPS interactivos.

### Otros límites

- La salida está fijada a 512x512; no resuelve directamente nuestro formato
  vertical 9:16.
- El propio proyecto recomienda audio inglés y fue entrenado principalmente
  con datasets ingleses. No es una opción segura para nuestro requisito de
  conversación completamente en español.
- El código está bajo Apache-2.0; la licencia de los pesos alojados en
  Hugging Face requiere verificarse por separado antes de un uso comercial.

**Estado: descartado para nuestro stack realtime local.** No se instalaron sus
dependencias ni se descargaron checkpoints porque la ruta oficial es offline y
no aporta una base reutilizable inmediata para streaming. Para recuperarlo
habría que diseñar un scheduler causal por chunks, mantener estado entre
ventanas y publicar frames/audio progresivamente; eso sería una adaptación de
arquitectura, no una simple integración con OpenTalking.

Referencias:

- [Repositorio IMTalker](https://github.com/bigai-nlco/IMTalker)
- [Paper IMTalker](https://arxiv.org/abs/2511.22167)
- [Pesos IMTalker](https://huggingface.co/cbsjtu01/IMTalker)

## Plan de validacion secuencial - candidatos pendientes

Este plan mantiene una regla estricta: cada candidato se evalua de forma
aislada y el resultado se documenta en este archivo antes de pasar al
siguiente. El objetivo no es medir solo calidad visual, sino encontrar una
base viable para un avatar independiente, local y conversacional en tiempo
real.

### Criterios comunes

1. **Tiempo real real:** debe aceptar audio incremental o tener una ruta clara
   para publicar frames progresivamente. Un video generado despues de recibir
   todo el audio no cuenta como realtime.
2. **Avatar independiente:** no debe depender de una persona frente a una
   camara. Se priorizan imagen, rig, Gaussian/avatar asset o referencia fija.
3. **Audio y lipsync:** debe poder conectarse al TTS local y mantener audio y
   movimiento sincronizados, con medicion de TTFA, FPS y latencia percibida.
4. **Espanol:** se prueba con audio y TTS en espanol. Si el modelo fue
   entrenado solo en ingles, queda marcado como riesgo aunque funcione.
5. **Formato vertical:** se valida salida o composicion 9:16 sin deformar el
   avatar ni depender de un recorte inutilizable.
6. **Hardware:** se prueba en Linux/WSL con nuestra GPU de 16 GB de VRAM,
   registrando VRAM pico, RAM, tiempo de carga y estabilidad.
7. **Licencia y disponibilidad:** se separan licencia de codigo, pesos,
   checkpoints, assets y cualquier dependencia cloud/API.
8. **Integracion:** se evalua si puede reutilizar nuestro pipeline de LLM,
   STT, TTS y transporte web, o si exige reescribir la arquitectura.

### Procedimiento por candidato

- Verificar repositorio, releases, licencia, pesos y requisitos.
- Clasificar la arquitectura: streaming, chunked con estado, batch/offline o
  solo plataforma cloud.
- Instalar unicamente si supera el filtro inicial de independencia y posible
  realtime.
- Ejecutar una prueba minima con audio espanol, avatar fijo y composicion
  vertical cuando sea posible.
- Medir: carga, TTFA, tiempo por frame/chunk, FPS, VRAM pico, cortes,
  sincronizacion audio-video y posibilidad de hablar mientras el avatar sigue
  respondiendo.
- Registrar resultado, evidencias, limitaciones, licencia y decision en este
  Markdown.
- Solo despues de guardar la evaluacion, avanzar al siguiente proyecto.

### Orden de evaluacion

1. [GVCLab/PersonaLive](https://github.com/GVCLab/PersonaLive)
2. [antgroup/ditto-talkinghead](https://github.com/antgroup/ditto-talkinghead)
3. ~~[myths-labs/prometheus-avatar](https://github.com/myths-labs/prometheus-avatar)~~ — evaluación inicial exitosa; pendiente profundización
4. [Lynpoint/CyberVerse](https://github.com/Lynpoint/CyberVerse)
5. [ARACHNE-X-ULTRA-AVATAR](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR/tree/main)
6. [Livepeer Mission Control](https://docs.livepeer.org/v2/home/mission-control)
7. [Fictionarry/TalkingGaussian](https://github.com/Fictionarry/TalkingGaussian)

Livepeer se evaluara como plataforma/servicio de infraestructura y no se
mezclara con los modelos self-hosted. Para todos los demas se documentara
explicitamente si el proyecto produce video completo, solo expresiones,
frames incrementales o un avatar renderizado en cliente.

## PersonaLive - evaluado y descartado en el filtro inicial

Repositorio: [GVCLab/PersonaLive](https://github.com/GVCLab/PersonaLive)

### Lo que ofrece

PersonaLive es un sistema de animacion de retrato orientado a live streaming.
Tiene una estrategia de generacion streamable para videos largos, un Web UI
con FastAPI/WebSocket y una ruta TensorRT opcional. El README configura la
inferencia online a 512x512, 16 FPS y cuatro pasos DDIM. El repositorio publica
codigo bajo Apache-2.0.

### Verificacion contra nuestro requisito

No es un avatar audio-driven independiente. La ruta online recibe bytes de
imagenes por `/api/ws/{user_id}` y los procesa como frames de entrada; el
frontend esta construido alrededor de una fuente de video/webcam. No hay en
el pipeline oficial una entrada de audio, TTS, STT ni un adaptador audio ->
movimiento. El termino `streaming` se refiere a publicar frames generados a
partir de una secuencia de imagen/video, no a sincronizar labios con el audio
de nuestro agente.

Tambien presenta estos limites para nuestra matriz:

- salida base cuadrada 512x512; no tiene composicion vertical 9:16 integrada;
- el README declara el proyecto para investigacion academica solamente;
- la licencia de los pesos descargados desde Hugging Face/ModelScope debe
  verificarse por separado del Apache-2.0 del codigo;
- el README menciona soporte para 12 GB en su estrategia offline, pero no
  constituye una medida de VRAM para un avatar audio-driven en nuestra GPU;
- no se justifica instalarlo para este stack porque no reutiliza directamente
  la cadena local LLM -> TTS -> audio -> avatar.

### Decision

**Descartado para la validacion realtime de nuestro avatar.** No se instalaron
dependencias ni checkpoints. Queda registrado como referencia interesante de
difusion causal/streamable y como posible candidato para animacion guiada por
video, pero no cumple el requisito de avatar independiente sin camara y
audio-driven en espanol.

Evidencia primaria revisada:

- [README y configuracion de PersonaLive](https://github.com/GVCLab/PersonaLive)
- [inference_online.py](https://github.com/GVCLab/PersonaLive/blob/main/inference_online.py)
- [requirements_base.txt](https://github.com/GVCLab/PersonaLive/blob/main/requirements_base.txt)
- [LICENSE](https://github.com/GVCLab/PersonaLive/blob/main/LICENSE)

## Ditto TalkingHead - streaming verificado, pero descartado para realtime en 16 GB

Repositorio local: `ditto-talkinghead/`, commit `c3e47ee` (`release training
code`). Repositorio oficial: [antgroup/ditto-talkinghead](https://github.com/antgroup/ditto-talkinghead).

### Lo que si cumple

Ditto es audio-driven y acepta una imagen fija como fuente del avatar. El
codigo incluye `stream_pipeline_online.py`, un encoder Hubert con estado y
`run_chunk(audio_chunk)`: el audio puede entrar por ventanas de aproximadamente
200 ms, mientras varios workers producen movimiento, stitching, warp, decode y
frames de salida. Esto confirma que no es solamente un generador batch.

La licencia del codigo es Apache-2.0. Los checkpoints se descargaron desde el
modelo oficial de Hugging Face en la variante PyTorch, sin traer los engines
TensorRT ni el duplicado ONNX completo. La licencia de los pesos debe
confirmarse por separado antes de un uso comercial.

### Prueba local

Entorno aislado: Python 3.11, PyTorch CUDA reutilizado desde OpenAvatarChat,
ONNX Runtime GPU, imagen fija y audio TTS en espanol. GPU: NVIDIA RTX 5060 Ti
con 16 GB de VRAM. Se anadio el harness reutilizable
`ditto-talkinghead/scripts/validate_online.py`.

Resultados despues de cargar los modelos, sin contar el tiempo de arranque:

| Configuracion | Audio | Frames producidos | Tiempo total | Resultado |
|---|---:|---:|---:|---|
| PyTorch, 50 pasos | 10.12 s | 195 (7.8 s) | 16.50 s | 1.63x realtime |
| PyTorch, 10 pasos | 10.12 s | 195 (7.8 s) | 14.20 s | 1.40x realtime |
| PyTorch, 4 pasos | 10.12 s | 195 (7.8 s) | 13.63 s | 1.35x realtime |

El pipeline necesita una ventana inicial de aproximadamente 2.8 s para llenar
su contexto de 80 frames; por eso no emite los primeros frames inmediatamente.
En regimen sostenido, el writer se mantuvo alrededor de 15--16 FPS en nuestra
GPU. El MP4 generado fue valido, con 960x960, 25 FPS y audio muxeado; el frame
de control se ve estable y el lipsync se genero desde la imagen fija.

### Integracion pendiente y decision

El repositorio no trae WebRTC/WebSocket ni una API de frames para el frontend:
su writer actual escribe MP4. Para integrarlo a nuestro stack habria que
reemplazar el writer por una cola de frames y conectar `run_chunk` al audio
saliente del TTS.

**Resultado: streaming tecnico verificado, pero descartado como candidato
principal para realtime en nuestro hardware actual.** La ruta PyTorch queda
demasiado lenta y con demasiado warm-up para una conversacion natural. Podria
reabrirse con un engine TensorRT compilado especificamente para la GPU o con
una GPU mas rapida, pero no vale la pena integrarlo ahora en el stack estable.

Evidencia primaria:

- [README Ditto](https://github.com/antgroup/ditto-talkinghead)
- [Pipeline online](https://github.com/antgroup/ditto-talkinghead/blob/main/stream_pipeline_online.py)
- [Inferencia](https://github.com/antgroup/ditto-talkinghead/blob/main/inference.py)
- [LICENSE](https://github.com/antgroup/ditto-talkinghead/blob/main/LICENSE)

## Prometheus Avatar - candidato realtime con stack conversacional integrado

Repositorio clonado localmente en `prometheus-avatar/`, commit de evaluacion:
`main` en la fecha de prueba. Repositorio oficial:
[myths-labs/prometheus-avatar](https://github.com/myths-labs/prometheus-avatar).

### Que es realmente

Prometheus no es un modelo neural de talking-head que genere un video nuevo por
frame. Es un SDK/browser app que renderiza un avatar Live2D con PixiJS/WebGL y
aplica parametros al modelo en cada frame del navegador. El avatar es
independiente de la camara: se carga un asset `.model.json` (Cubism 2) o
`.model3.json` (Cubism 3/4), se ejecutan sus motions idle y se controlan
expresiones y `ParamMouthOpenY`.

La boca puede moverse de dos formas:

- con analisis del audio reproducido mediante `AnalyserNode` y bandas de
  frecuencia;
- con una animacion aproximada basada en texto cuando no hay audio crudo.

Esto lo hace muy ligero y apto para realtime, pero la calidad del lipsync y la
riqueza corporal dependen del rig Live2D y de sus motions; no hay generacion
neural de cabeza, manos o cuerpo.

### Verificacion local

El SDK compilo correctamente con `corepack pnpm -r build` para:
`@prometheusavatar/core`, `mcp-server` y `openclaw-plugin`.

Se creo un harness aislado en
`run/prometheus-avatar-test-direct.html` para no confundir fallos del demo
comercial con el renderer. La prueba uso:

- modelo Haru Live2D fijo cargado desde el asset publico de
  `pixi-live2d-display`;
- audio WAV local en espanol:
  `opentalking/data/tts_validation_es.wav`;
- reproduccion desde el navegador y analisis de energia/frecuencia para
  modificar la boca;
- composicion vertical 9:16;
- cero camara, cero captura de video y cero checkpoint de GPU.

Resultado observado: `Avatar listo. Renderer Live2D verificado`, el audio local
respondio con HTTP 200 y finalizo con `Audio terminado`; la preview vertical
mostro el modelo estable durante la prueba. Para esta ruta el uso de VRAM del
modelo neural es cero; el consumo es el del navegador/WebGL.

### Integracion con nuestro stack

La interfaz `ITTSEngine` es pluggable y acepta un TTS propio, pero el contrato
del SDK solo recibe `Float32Array` para el lipsync. Para integrarlo con nuestro
stack habria que conectar el audio que ya produce Piper/Kokoro al elemento de
audio del renderer o implementar un adaptador que entregue los samples al
engine. Esto es sencillo comparado con integrar un modelo de video, y permite
mantener LLM, STT y TTS locales.

El demo oficial, sin embargo, no es local de punta a punta:

- `useLiveVoice.ts` conecta el microfono directamente con Gemini Live API;
- `/api/tts` genera audio con Gemini TTS y si falla cae a Web Speech del
  navegador;
- la documentacion menciona endpoints OpenAI-compatible y Ollama, pero la ruta
  de voz realtime publicada esta acoplada a Gemini.

Por tanto, Prometheus puede ser el renderer local de nuestro pipeline, pero no
se debe considerar un stack local listo para usar sin sustituir sus rutas de
LLM/TTS cloud por nuestros endpoints locales.

### Validación integrada con nuestro stack

El 2026-08-02 se conectó el renderer a una página de prueba accesible desde
Windows: `http://127.0.0.1:3010/run/prometheus-live.html`. El flujo validado fue:

- micrófono del navegador con detección automática de voz;
- SenseVoiceSmall local para STT, en CPU;
- Ollama local con `qwen2.5:7b` mediante API compatible con OpenAI;
- Edge TTS en español con `es-MX-DaliaNeural`;
- transporte de audio por WebRTC desde OpenTalking;
- Live2D vertical 9:16 con lipsync por análisis de energía del audio, sin
  cámara.

Para que Windows no dependa del acceso directo al puerto de WSL, se añadió un
proxy local en `:3010/api` hacia el backend OpenTalking en `:8210`. La página
cargó el avatar, creó la sesión, negoció WebRTC, activó los eventos de
conversación y dejó operativo el flujo micrófono → STT → LLM → TTS →
audio/lipsync. La respuesta de audio se validó en español.

**Estado actualizado:** prueba integrada exitosa y candidato activo para
profundizar. Queda pendiente medir TTFA y latencia percibida, comparar otros
assets Live2D, comprobar la sincronización en conversaciones largas y revisar
la licencia efectiva de cada asset/modelo. Edge TTS no es local; para una ruta
100% offline habría que sustituirlo por un TTS local.

### Licencia y assets

- Codigo y SDK: MIT.
- Los assets Live2D no quedan cubiertos automaticamente por la licencia del
  SDK. El modelo Haru usado en la prueba tiene una licencia separada de
  `Live2D Free Material`; cada avatar adicional debe revisarse por separado.
- La licencia de cada modelo, textura, motion y accesorio debe registrarse
  independientemente antes de uso comercial.

### Problemas del demo oficial

El demo completo no compilo limpio en esta revision:

- `src/app/layout.tsx` importa `@/components/ParticleBackground`, pero ese
  archivo no esta presente;
- `src/app/dashboard/page.tsx` contiene un error de sintaxis JSX;
- `apps/demo/public/avatar.html` referencia `/lib/live2d.min.js`,
  `/lib/live2dcubismcore.min.js` y otros bundles que no estan incluidos en el
  checkout.

Estos problemas afectan al demo/distribucion, no al SDK ni al renderer que se
verifico con el harness directo.

### Decision

**Aprobado como candidato fuerte para la capa de avatar realtime local y
vertical.** La integración conversacional ya funciona con nuestro stack; no es
un reemplazo de MuseTalk/LAM como generador neural, sino una solución Live2D
mucho más ligera, independiente de cámara y fácil de conectar a nuestro audio.
Queda por validar en una siguiente fase la calidad de un asset Live2D propio,
el adaptador Piper/Kokoro, la latencia sostenida y el uso comercial de los
assets.

Evidencia primaria:

- [Repositorio Prometheus Avatar](https://github.com/myths-labs/prometheus-avatar)
- [SDK y contrato ITTSEngine](https://github.com/myths-labs/prometheus-avatar/blob/main/packages/sdk/src/types.ts)
- [Renderer Live2D](https://github.com/myths-labs/prometheus-avatar/blob/main/packages/sdk/src/renderer.ts)
- [Demo de voz](https://github.com/myths-labs/prometheus-avatar/blob/main/apps/demo/src/lib/useLiveVoice.ts)
- [Integracion de agente local/OpenAI-compatible](https://github.com/myths-labs/prometheus-avatar/blob/main/docs/agent-integration.md)
- [LICENSE](https://github.com/myths-labs/prometheus-avatar/blob/main/LICENSE)

## CyberVerse - arquitectura full-duplex muy buena, bloqueado por hardware y licencia

Repositorio revisado localmente en `CyberVerse/`, commit `4e2585a`
(`docs: Adjust wechat QR Code`). Repositorio oficial:
[Lynpoint/CyberVerse](https://github.com/Lynpoint/CyberVerse).

### Lo que aporta

CyberVerse no es solamente un renderer: es un framework de agente realtime que
integra WebRTC, memoria de persona, herramientas, RAG, LLM, ASR, TTS y una
capa de avatar reemplazable. Su arquitectura de avatar sí coincide con la
conversacion que buscamos:

- el navegador mantiene una sesion WebRTC;
- `AvatarService.GenerateStream` consume un `AsyncIterator` de audio;
- el plugin de avatar conserva continuidad temporal y genera chunks de video;
- cada `VideoChunk` se entrega incrementalmente por gRPC con dimensiones, FPS,
  indice y marca de final;
- el frontend reproduce el audio y video como una sesion de media, no como un
  MP4 generado despues.

Esto lo convierte en la arquitectura mas cercana, entre los proyectos
revisados, a un avatar que puede seguir hablando mientras recibe nueva voz:
entrada, LLM/TTS y avatar son streams independientes. Ademas contempla
`silent_inference` para mantener la continuidad visual entre turnos y publica
metricas RTP para saber si la inferencia mantiene el tiempo real.

### Modelos locales y rendimiento publicado

Los backends locales de video son `SoulX-FlashHead` y `SoulX-LiveAct`.
El propio README publica estas condiciones:

| Backend | GPU publicada | Configuracion | FPS | Realtime |
|---|---|---|---:|---|
| FlashHead 1.3B Pro | RTX 5090 x2 | 512x512 | 25+ | Si |
| FlashHead 1.3B Pro | RTX 5090 x1 | 464x464 | 20 | No llega a 25 FPS |
| LiveAct 18B | RTX PRO 6000 x2 | 320x480 | 20 | Si |
| LiveAct 18B | RTX PRO 6000 x1 | 256x417 | 20 | Si, segun el proyecto |

La configuracion de FlashHead permite elegir `model_type: lite`, y el plugin
mantiene una ruta de inferencia por audio en chunks. Eso es valioso, pero no
hay en el README una medicion de `FlashHead Lite` sobre una RTX 5060 Ti de
16 GB. Por tanto no corresponde asumir que CyberVerse hace viable nuestro
pipeline anterior de FlashHead Lite: no lo valida ni lo rescata.

Con nuestra GPU de 16 GB, la matriz publicada no tiene una fila soportada para
ninguno de los dos backends locales. LiveAct ademas es un modelo de 18B y su
documentacion apunta a GPUs profesionales con mucha mas memoria. Podria
intentarse una prueba experimental con baja resolucion/offload, pero no seria
una validacion de realtime y obligaria a instalar un entorno CUDA 12.8,
PyTorch 2.8, checkpoints grandes y, para LiveAct, dependencias adicionales de
vLLM.

### Audio, LLM, español y dependencia cloud

El framework tiene plugins separados para ASR, TTS y voz/LLM. La configuracion
que viene preparada usa `qwen3-asr-flash-realtime` y
`qwen3-tts-flash-realtime` mediante DashScope, por lo que esa ruta no es local
ni es una prueba adecuada de nuestro objetivo offline. Tambien existe un
plugin compatible con endpoints OpenAI; en principio permitiria apuntar el LLM
a Ollama/vLLM y conectar un ASR/TTS local, pero no validamos en este proyecto
la combinacion completa en español.

La interfaz incluye idiomas chino e inglés, pero no una localizacion española
lista en la revisión realizada. El idioma del modelo de audio y la voz se
pueden configurar en los plugins/proveedores, aunque la ruta por defecto y las
voces de ejemplo están claramente orientadas al ecosistema chino.

### Licencia y riesgo de adopción

- El código del repositorio está bajo GPL-3.0.
- Los modelos, checkpoints, personajes y assets tienen que revisarse por
  separado; la licencia del framework no los cubre automáticamente.
- Para un producto propietario, GPL-3.0 es un bloqueo de adopción directa y
  requiere una estrategia legal/arquitectónica separada antes de incorporar
  código del repositorio.

### Decision

**No se instala ni se ejecuta en nuestra máquina en esta fase.** CyberVerse
queda registrado como candidato arquitectónico fuerte para una futura máquina
con RTX 5090/RTX PRO 6000: su streaming full-duplex y su contrato de chunks son
exactamente el tipo de integración que necesitamos. En el entorno actual no
hay hardware publicado compatible, no hay ruta local española verificada y la
licencia GPL-3.0 añade un riesgo de producto. Queda por debajo de Prometheus
como opción inmediata, aunque por razones distintas: Prometheus ya fue
verificado localmente como renderer ligero; CyberVerse requiere una plataforma
GPU mucho más grande.

Evidencia primaria:

- [Repositorio CyberVerse](https://github.com/Lynpoint/CyberVerse)
- [README y matriz de rendimiento](https://github.com/Lynpoint/CyberVerse/blob/main/README.md)
- [Plugin FlashHead](https://github.com/Lynpoint/CyberVerse/blob/main/inference/plugins/avatar/flash_head_plugin.py)
- [Plugin LiveAct](https://github.com/Lynpoint/CyberVerse/blob/main/inference/plugins/avatar/live_act_plugin.py)
- [Servicio de avatar y streaming gRPC](https://github.com/Lynpoint/CyberVerse/blob/main/inference/services/avatar_service.py)
- [Configuracion FlashHead](https://github.com/Lynpoint/CyberVerse/blob/main/infra/config/avatar_models/flash_head.yaml)
- [Configuracion LiveAct](https://github.com/Lynpoint/CyberVerse/blob/main/infra/config/avatar_models/live_act.yaml)
- [LICENSE GPL-3.0](https://github.com/Lynpoint/CyberVerse/blob/main/LICENSE)

## ARACHNE-X-ULTRA-AVATAR - pesos sin runtime reproducible y fuera de nuestro hardware

Fuente revisada:
[MagistrTheOne/ARACHNE-X-ULTRA-AVATAR](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR).
El model card declara audio-to-video, audio+imagen-to-video, continuacion
streaming, soporte de uno o varios personajes, 480p/720p y licencia MIT.

### Que se pudo verificar

El artefacto de Hugging Face no contiene el codigo de inferencia que seria
necesario para una prueba end-to-end. El README intenta clonar
`nullxes/arachne-x-ultra-avatar`, pero ese repositorio no esta disponible
publicamente: la URL devuelve 404 y en el snapshot revisado no aparecen
`run_avatar_single.py`, `run_avatar_multi.py`, `requirements.txt`, ejemplos de
entrada ni un servidor WebRTC/WebSocket. Por tanto no podemos reproducir la
inferencia desde el enlace entregado, aunque el model card la describa como
streaming.

Hay además una discrepancia importante en la identidad del artefacto:
`model_index.json` dice `LongCat-Video-Avatar`, la configuracion declara
`LongCatVideoAvatarTransformer3DModel`, y los assets incluyen el logo de
LongCat. Es decir, lo que se publico parece ser un paquete de pesos compatible
con la familia LongCat-Video-Avatar, renombrado o reempaquetado como ARACHNE;
no hay suficiente codigo publico para atribuirle un runtime propio o una
mejora concreta sobre LongCat.

### Tamaño y viabilidad local

El transformer tiene 48 bloques y un `hidden_size` de 4096. El index de
Safetensors declara `total_size: 63,486,640,384` bytes (aprox. 63.5 GB) y lo
reparte en seis shards de alrededor de 10 GB cada uno. Sumando el encoder de
audio, VAE y separador vocal, el snapshot completo ocupa más de 128 GB.

El README propone `torchrun --nproc_per_node=2`, lo que ya indica una ruta
multi-GPU. No publica FPS, TTFA, RTP, tiempo por chunk ni una medicion en una
GPU de 16 GB. Tampoco hay una cuantizacion oficial que cambie esa conclusion.
Aunque pudiera cargarse con offload agresivo, produciria una prueba de
generacion por lotes lenta, no una validacion del realtime que buscamos.

### Español y entrada de audio

El model card declara solamente `en` y `zh`, y el checkpoint incluido se llama
`chinese-wav2vec2-base`. No hay una ruta documentada para audio español ni una
prueba de lipsync en español. La generacion del video podria ser condicionada
por audio independientemente del idioma, pero eso no sustituye una validacion
real del encoder y de la calidad en nuestro caso de uso.

### Licencia

El archivo `LICENSE` del snapshot es MIT y tiene copyright de Meituan. Eso es
favorable para el artefacto publicado, pero no demuestra que cualquier codigo
privado de `nullxes` tenga la misma licencia ni aclara la procedencia de todos
los componentes del paquete. Antes de un uso comercial conviene comparar con
el repositorio oficial de LongCat y conservar un registro de los pesos exactos
que se utilicen.

### Decision

**Descartado para validacion local en esta fase.** No por la idea de streaming,
sino porque faltan runtime y benchmark reproducibles, el paquete es de mas de
128 GB y su transformer excede ampliamente la capacidad de nuestra GPU de
16 GB. No se descarga ni se instala para no convertir una evaluacion de tiempo
real en una prueba de offload. Si aparece un repositorio oficial de ARACHNE con
codigo, checkpoints cuantizados y una medicion por debajo de 1 RTP en hardware
de consumo, se puede reabrir; mientras tanto el candidato correcto para
comparar es el LongCat-Video-Avatar oficial, no este mirror de pesos.

Evidencia primaria:

- [Model card de ARACHNE-X-ULTRA-AVATAR](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR)
- [README del snapshot](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR/blob/main/README.md)
- [Index de pesos y tamaño del transformer](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR/blob/main/avatar_single/diffusion_pytorch_model.safetensors.index.json)
- [Modelo base declarado en model_index.json](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR/blob/main/model_index.json)
- [LICENSE del snapshot](https://huggingface.co/MagistrTheOne/ARACHNE-X-ULTRA-AVATAR/blob/main/LICENSE)

## Livepeer Mission Control - infraestructura de video, no avatar conversacional

Fuente revisada: [Mission Control / documentación Livepeer](https://docs.livepeer.org/v2/home/mission-control).
La URL actualmente redirige a [Run the Livepeer network](https://docs.livepeer.org/network),
la documentación para operar un orchestrator o delegar LPT. No es un
repositorio de avatar ni un stack que se pueda levantar como parte de nuestro
servicio local.

### Que hace realmente

Livepeer es un marketplace descentralizado de computo GPU para transcoding e
inferencia de video. Su guia de `Serve real-time AI` describe el pipeline
`live-video-to-video` (Cascade):

```text
Gateway -> go-livepeer AI worker -> ai-runner:live-base / ComfyStream
        -> receive frame -> inference -> emit transformed frame -> WebRTC
```

La entrada es un stream de video WebRTC y el objetivo es transformar cada frame
en menos de 100 ms, con aproximadamente 33 ms por frame a 30 FPS. Los modelos
indicados son StreamDiffusion, ControlNet y workflows de ComfyUI. Es una buena
infraestructura para style transfer o video generado sobre una señal de video,
pero no para generar un avatar independiente a partir de TTS.

### Por que no resuelve nuestro caso

- No incluye LLM, ASR, TTS ni deteccion de turnos.
- El pipeline realtime espera video de entrada; no tiene un contrato de
  audio-to-avatar ni una entrada de audio que genere labios, cabeza y cuerpo.
- La guia de AI separa los pipelines batch (Whisper, LLM, image-to-video) del
  pipeline realtime Cascade. Ninguno equivale a un agente conversacional con
  audio español y avatar.
- La operacion depende de Docker, NVIDIA Container Toolkit, un orchestrator y
  la red Livepeer; deja de ser una ejecucion local y offline.
- La propia guia recomienda 24 GB de VRAM para Cascade, aunque la referencia
  general de hardware lista 12 GB como minimo y 16 GB como recomendado para
  ComfyStream. Nuestra GPU de 16 GB estaria en el limite, sin margen seguro
  para modelo, buffers y transcoding.

### Relacion posible con nuestro stack

Si en el futuro quisieramos distribuir el procesamiento, Livepeer podria ser
una capa remota para un workflow de video ya existente. Para usarlo con un
avatar habria que construir un pipeline ComfyStream propio que convirtiera
audio/TTS en video y resolver aparte la sincronizacion con el audio, el LLM,
STT y la sesion WebRTC. Eso seria desarrollar sobre la plataforma, no
reutilizar una implementacion de avatar que ya funcione.

### Decision

**Descartado como candidato de avatar realtime local.** Se conserva como
referencia de infraestructura distribuida para video y como posible opcion
futura de computo remoto, pero no se instala ni se integra en nuestro pipeline:
no ofrece audio-driven avatar, no mejora el soporte español y rompe el
requisito de ejecucion local.

Evidencia primaria:

- [Mission Control redirigido a la documentacion actual](https://docs.livepeer.org/v2/home/mission-control)
- [Descripcion de la red Livepeer](https://docs.livepeer.org/network)
- [Guia de inferencia AI](https://docs.livepeer.org/network/guides/orchestrator-add-ai)
- [Guia de AI en tiempo real/Cascade](https://docs.livepeer.org/network/guides/orchestrator-realtime-ai)
- [Requisitos de hardware y VRAM](https://docs.livepeer.org/network/reference/hardware)

## TalkingGaussian - 3D Gaussian Splatting por identidad, no streaming conversacional

Repositorio clonado localmente en `TalkingGaussian/`, commit `9bd34f7`
(`accelerate loading a bit`, 2025-03-16). Repositorio oficial:
[Fictionarry/TalkingGaussian](https://github.com/Fictionarry/TalkingGaussian).

### Que hace

TalkingGaussian aprende una cabeza parlante 3D basada en Gaussian Splatting a
partir de un video de una identidad concreta. El README exige un video de
entrenamiento de 1--5 minutos, 25 FPS y con la persona visible en todos los
frames. Despues se entrenan por separado la cara, la boca y la fusion, y se
puede pasar un archivo de features de audio para sintetizar la animacion.

Eso implica un avatar por identidad, no un modelo one-shot al que se le entrega
una imagen nueva en cada sesion. Para una conversacion independiente habria
que preparar y entrenar cada avatar antes de ponerlo online.

### Por que no cumple realtime en su forma publicada

El flujo de inferencia es explícitamente offline:

```text
audio WAV -> DeepSpeech/HuBERT features -> synthesize_fuse.py
          -> recorre views/camaras -> renderiza todos los frames
          -> imageio.mimwrite(..., out.mp4, fps=25)
```

En `synthesize_fuse.py`, `render_set` itera sobre todas las cámaras, guarda las
predicciones en listas y finalmente escribe `out.mp4`. No existe un writer de
frames incremental, una cola de video, WebRTC, WebSocket ni un contrato que
permita alimentar el audio de TTS y publicar el frame siguiente mientras se
habla.

El repositorio sí contiene `data_utils/wav2vec.py` con un modo de captura de
micrófono y una cola de audio. Eso sólo hace streaming de la extracción de
features: no conecta esa cola con `synthesize_fuse.py` ni convierte el renderer
en un avatar realtime. Tampoco es la entrada que necesitamos, porque el avatar
debe reaccionar al audio de salida del TTS y no a una cámara o micrófono local.

### Coste técnico y compatibilidad

- El entorno fijado es Ubuntu 18.04, Python 3.7.13, PyTorch 1.12.1, CUDA 11.3
  y torchvision 0.13.1.
- Requiere 3DMM Basel Face Model, face parsing, EasyPortrait, OpenFace y
  submodulos de rasterizacion/custom CUDA.
- El README advierte que el preload puede consumir aproximadamente `N x 32 GB`
  de RAM por cada `N x 5k` frames.
- No publica FPS de inferencia, TTFA, tiempo por frame ni RTP. Sin un checkpoint
  propio entrenado no hay un camino corto de prueba.
- No fue posible identificar un archivo `LICENSE` en el repositorio. El README
  describe el código como investigación y contiene restricciones éticas, pero
  eso no equivale a una licencia de uso comercial clara; los assets y datasets
  también tienen procedencias externas.

### Decision

**Descartado para el objetivo de avatar realtime independiente.** Es una línea
interesante para calidad 3D y persistencia estructural, pero su versión
publicada es un pipeline de entrenamiento + render batch por identidad. Para
convertirlo en nuestro producto habría que reescribir el renderer como servicio
incremental, resolver un modelo de identidad preparado, actualizar todo el
entorno CUDA/PyTorch y medir la latencia desde TTS hasta frame. El coste no se
justifica frente a LAM o Prometheus, que ya fueron verificables en realtime en
nuestro stack.

Evidencia primaria:

- [Repositorio TalkingGaussian](https://github.com/Fictionarry/TalkingGaussian)
- [README y comandos de entrenamiento/inferencia](https://github.com/Fictionarry/TalkingGaussian/blob/main/README.md)
- [Renderer batch `synthesize_fuse.py`](https://github.com/Fictionarry/TalkingGaussian/blob/main/synthesize_fuse.py)
- [Captura/extraccion de audio](https://github.com/Fictionarry/TalkingGaussian/blob/main/data_utils/wav2vec.py)
- [Motion network condicionado por audio](https://github.com/Fictionarry/TalkingGaussian/blob/main/scene/motion_net.py)
- [Paper ECCV 2024](https://arxiv.org/abs/2404.15264)

| ACTalker | [harlanhong/ACTalker](https://github.com/harlanhong/ACTalker) | Evaluado | Framework de difusión de video que soporta control simultáneo de audio y expresión facial. |
| RealVideo | [zai-org/RealVideo](https://github.com/zai-org/RealVideo) | Evaluado | Sistema conversacional en streaming que utiliza difusión autorregresiva para generar respuestas continuas de video. |
| FastGHA | [cvlab-kaist/FastGHA](https://github.com/cvlab-kaist/FastGHA) | Evaluado | Encoder de avatares 3D Gaussian Splatting few-shot que permite renderizado en tiempo real a partir de pocas imágenes. |
| GaussianEmoTalker | [GaussianEmoTalker](https://arxiv.org/abs/2607.00194) | Evaluado | Síntesis de avatar 3DGS emocional en tiempo real mediante espacio de deformación residual neutral a emocional. |
| OmniTalker | [OmniTalker](https://github.com/OmniTalker) | Evaluado | Generador unificado end-to-end de habla y video sincronizado desde texto hasta 25 FPS. |
| threejs-talking-avatar | [majidmanzarpour/threejs-talking-avatar](https://github.com/majidmanzarpour/threejs-talking-avatar) | Evaluado | Avatar parlante ejecutable en navegador cliente mediante WebGPU y sincronización labial en tiempo real. |
| realtime-ai (RTVI) | [realtime-ai/realtime-ai](https://github.com/realtime-ai/realtime-ai) | Evaluado | Estándar abierto y framework para pipelines de inferencia de voz y video en tiempo real sobre WebRTC. |
| Chatterbox | [ai-avatar-system/chatterbox](https://github.com/ai-avatar-system/chatterbox) | Evaluado | Motor de sincronización labial y procesamiento de audio para humanos digitales interactivos. |
| TalkingFace | [tien02/talking-face](https://github.com/tien02/talking-face) | Evaluado | Pipeline end-to-end de generación de video parlante acelerado por TensorRT con transmisión WebRTC. |
| LangQing | [langzizhixin/LangQing](https://github.com/langzizhixin/LangQing) | Evaluado | Plataforma de humanos digitales interactivos en tiempo real (<500ms latencia) para avatares 2D/2.5D/3D sobre WebRTC. |
| Riverst | [Riverst/Riverst](https://github.com/Riverst/Riverst) | Evaluado | Plataforma de conversación avatar-usuario con lip-sync en tiempo real y transmisión WebRTC. |
| sample-nova-sonic-webrtc | [aws-samples/sample-nova-sonic-speech2speech-webrtc](https://github.com/aws-samples/sample-nova-sonic-speech2speech-webrtc) | Evaluado | Pipeline de agente de voz speech-to-speech en tiempo real con WebRTC. |
| ion-sfu | [ionorg/ion-sfu](https://github.com/ionorg/ion-sfu) | Evaluado | Implementación SFU pura en Go de alto rendimiento para escalabilidad de WebRTC. |
| webrtc-rs-sfu | [webrtc-rs/sfu](https://github.com/webrtc-rs/sfu) | Evaluado | Implementación SFU de WebRTC Sans-IO escrita en Rust. |
| mirotalksfu | [miroslavpejic85/mirotalksfu](https://github.com/miroslavpejic85/mirotalksfu) | Evaluado | Plataforma SFU de conferencias y streaming WebRTC auto-hospedada en NodeJS. |
| Awesome-Talking-Head-Synthesis | [Kedreamix/Awesome-Talking-Head-Synthesis](https://github.com/Kedreamix/Awesome-Talking-Head-Synthesis) | Evaluado | Repositorio curado de referencia de papers, benchmarks y código de talking heads. |
| Awesome-3D-Gaussian-Splatting | [MrNeRF/Awesome-3D-Gaussian-Splatting-Paper-List](https://github.com/MrNeRF/Awesome-3D-Gaussian-Splatting-Paper-List) | Evaluado | Índice de referencia para investigación en 3DGS y avatares dinámicos en tiempo real. |

| MMTalker | [harlanhong/MMTalker](https://github.com/harlanhong/MMTalker) | Evaluado | Modelo multimodal de generación de cabeza parlante con control de expresión fina guiado por audio. |
| GenFaceTalk | [GenFaceTalk](https://github.com/GenFaceTalk/GenFaceTalk) | Evaluado | Generador one-shot de cabezas parlantes 3D Gaussian Splatting animadas por voz. |
| UniTalking | [UniTalking](https://github.com/UniTalking/UniTalking) | Evaluado | Modelo unificado de animación de retrato parlante guiado por audio y promps de movimiento. |
| LocalAI | [go-skynet/LocalAI](https://github.com/go-skynet/LocalAI) | Evaluado | Motor de IA local open-source con soporte nativo para audio WebRTC y voz Speech-to-Speech. |
| Mem0 | [mem0ai/mem0](https://github.com/mem0ai/mem0) | Evaluado | Capa de memoria persistente de baja latencia para agentes conversacionales y avatares de voz. |
| Vibe AI Partner | [vibe-ai/vibe-ai-partner](https://github.com/vibe-ai/vibe-ai-partner) | Evaluado | Plataforma de avatares de escritorio con soporte para modelos Live2D y VRM con memoria activa. |
| Vocode Python | [vocodehq/vocode-python](https://github.com/vocodehq/vocode-python) | Evaluado | Framework open-source para construir aplicaciones de voz conversacional en tiempo real. |
| Vapi Python | [vapi-ai/vapi-python](https://github.com/vapi-ai/vapi-python) | Evaluado | SDK de cliente para integración de agentes de voz conversacionales de baja latencia. |
| Wispr Flow | [wispr-flow/wispr-flow](https://github.com/wispr-flow/wispr-flow) | Evaluado | Pipeline de voz en streaming optimizado para interacción continua. |
| Resonite | [Yellow-Dog-Man/Resonite](https://github.com/Yellow-Dog-Man/Resonite) | Evaluado | Motor y plataforma open-source de mundos virtuales 3D y avatares espaciales interactivos. |
| Vircadia | [vircadia/vircadia](https://github.com/vircadia/vircadia) | Evaluado | Plataforma descentralizada de metaverso 3D con soporte para avatares y agentes. |
| Talking-face-arxiv-daily | [liutaocode/talking-face-arxiv-daily](https://github.com/liutaocode/talking-face-arxiv-daily) | Evaluado | Repositorio de actualización diaria con avances en investigación de síntesis de rostros parlantes. |
| Awesome-Multimodal-Agent | [OpenEnvision/Awesome-Multimodal-Agent](https://github.com/OpenEnvision/Awesome-Multimodal-Agent) | Evaluado | Índice de referencia de agentes multimodales e interacción guiada por voz. |
| Awesome-AI-Agents-2026 | [ARUNAGIRINATHAN-K/awesome-ai-agents-2026](https://github.com/ARUNAGIRINATHAN-K/awesome-ai-agents-2026) | Evaluado | Colección curada de frameworks, modelos y despliegues de agentes de IA de voz. |

| RVC | [RVC-Project/Retrieval-based-Voice-Conversion-WebUI](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI) | Evaluado | Framework de conversión de voz en tiempo real basado en recuperación de características VITS. |
| GPT-SoVITS | [RVC-Boss/GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | Evaluado | Modelo de síntesis de voz TTS zero-shot y clonación de voz a partir de 1 minuto de audio. |
| So-VITS-SVC | [svc-develop-team/so-vits-svc](https://github.com/svc-develop-team/so-vits-svc) | Evaluado | Modelo de conversión de voz cantada basado en VITS con extracción de características de audio. |
| SAM 2 | [facebookresearch/segment-anything-2](https://github.com/facebookresearch/segment-anything-2) | Evaluado | Modelo de Meta para segmentación y matting de objetos y sujetos en video en tiempo real. |
| Grounded-SAM | [IDEA-Research/Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) | Evaluado | Combinación de DINO y SAM para detección y segmentación de imágenes/video por texto. |
| Filament | [google/filament](https://github.com/google/filament) | Evaluado | Motor de renderizado PBR en tiempo real multiplataforma desarrollado por Google para WebGL/C++. |
| bgfx | [bkaradzic/bgfx](https://github.com/bkaradzic/bgfx) | Evaluado | Librería de renderizado 3D agnóstica de API gráfica (Vulkan, Direct3D, OpenGL, WebGL). |
| Diligent Engine | [DiligentGraphics/DiligentEngine](https://github.com/DiligentGraphics/DiligentEngine) | Evaluado | Motor gráfico 3D moderno multiplataforma con soporte para WebGPU, Vulkan y Metal. |
| O3DE | [o3de/o3de](https://github.com/o3de/o3de) | Evaluado | Open 3D Engine de la Linux Foundation para simulación y renderizado 3D modular de alta fidelidad. |
| pyannote-audio | [pyannote/pyannote-audio](https://github.com/pyannote/pyannote-audio) | Evaluado | Toolkit en PyTorch para diarización de hablantes y segmentación de señal de audio. |
| SpeechBrain | [speechbrain/speechbrain](https://github.com/speechbrain/speechbrain) | Evaluado | Toolkit de IA conversacional para ASR, TTS, reconocimiento de hablante y procesamiento de audio. |
| Tortoise-TTS | [neonbjb/tortoise-tts](https://github.com/neonbjb/tortoise-tts) | Evaluado | Sistema de texto a voz multivoz con prosodia expresiva y clonación de voz alta fidelidad. |
| GPEN | [yangxy/GPEN](https://github.com/yangxy/GPEN) | Evaluado | Red incrustada de priores GAN para restauración facial y mejora de resolución. |
| RestoreFormer | [wsi-lab/RestoreFormer](https://github.com/wsi-lab/RestoreFormer) | Evaluado | Modelo basado en transformadores para restauración y super-resolución de rostros deteriorados. |
| PantoMatrix | [PantoMatrix](https://github.com/PantoMatrix) | Evaluado | Generador de animación corporal 3D y facial a partir de habla soportando SMPL-X y FLAME. |
| EchoMimicV2 | [antgroup/echomimic_v2](https://github.com/antgroup/echomimic_v2) | Evaluado | Segunda versión de EchoMimic orientada a animación humana de medio cuerpo guiada por audio. |
| FLOAT | [FLOAT](https://github.com/FLOAT) | Evaluado | Modelo de flow matching latente para retratos parlantes con alta consistencia temporal. |
| Awesome-Gesture_Generation | [Awesome-Gesture_Generation](https://github.com/Awesome-Gesture_Generation) | Evaluado | Índice de referencia y código de investigación en generación de gestos corporales guiados por audio. |

| MediaMTX | [bluenviron/mediamtx](https://github.com/bluenviron/mediamtx) | Evaluado | Servidor de medios multiprotocolo (RTSP, RTMP, WebRTC, HLS) de baja latencia escrito en Go. |
| Google Lyra | [google/lyra](https://github.com/google/lyra) | Evaluado | Codec de audio neuronal ultracomprimido de ultra-baja latencia para transmisión de voz en tiempo real. |
| Meta EnCodec | [facebookresearch/encodec](https://github.com/facebookresearch/encodec) | Evaluado | Modelo de compresión de audio neuronal en tiempo real de alta fidelidad desarrollado por Meta. |
| Descript DAC | [descriptinc/dac](https://github.com/descriptinc/dac) | Evaluado | Codec de audio neuronal universal de alta fidelidad y baja latencia para música y voz. |
| SpeechTokenizer | [ZhangXingHe/SpeechTokenizer](https://github.com/ZhangXingHe/SpeechTokenizer) | Evaluado | Tokenizer de habla unificado para modelos de lenguaje multimodales Speech-to-Speech. |
| Vosk | [alphacep/vosk-api](https://github.com/alphacep/vosk-api) | Evaluado | Toolkit de reconocimiento del habla (ASR) offline multiplataforma ligero para 20+ idiomas. |
| WeNet | [wenet-e2e/wenet](https://github.com/wenet-e2e/wenet) | Evaluado | Toolkit de ASR end-to-end en tiempo real orientado a producción en C++ y Python. |
| ESPnet | [espnet/espnet](https://github.com/espnet/espnet) | Evaluado | Toolkit completo en PyTorch para procesamiento de habla (ASR, TTS, traducción y separación de fuentes). |
| Kaldi | [kaldi-asr/kaldi](https://github.com/kaldi-asr/kaldi) | Evaluado | Toolkit estándar C++ para reconocimiento del habla y procesamiento de audio. |
| Rapier | [dimforge/rapier](https://github.com/dimforge/rapier) | Evaluado | Motor de física 2D/3D súper rápido escrito en Rust con bindings para WebAssembly/JavaScript. |
| Jolt Physics | [jrouwe/JoltPhysics](https://github.com/jrouwe/JoltPhysics) | Evaluado | Motor de física 3D multihilo escrito en C++ para juegos y entornos VR/AR en tiempo real. |
| Ant Media Server | [ant-media/Ant-Media-Server](https://github.com/ant-media/Ant-Media-Server) | Evaluado | Servidor de streaming WebRTC ultra-baja latencia con transcodificación en tiempo real. |
| CrewAI | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | Evaluado | Framework para orquestación de agentes IA autónomos y herramientas de voz. |
| AutoGen | [microsoft/autogen](https://github.com/microsoft/autogen) | Evaluado | Framework de Microsoft para sistemas conversacionales de múltiples agentes de IA. |
| LangChain | [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | Evaluado | Framework para desarrollo de aplicaciones impulsadas por LLMs y conectores de voz. |
| LlamaIndex | [run-llama/llama_index](https://github.com/run-llama/llama_index) | Evaluado | Framework de datos para agentes de IA conversacionales y asistentes RAG de voz. |
| Semantic Kernel | [microsoft/semantic-kernel](https://github.com/microsoft/semantic-kernel) | Evaluado | SDK de Microsoft para integrar LLMs y plugins de audio en C#, Python y Java. |
| Outlines | [dottxt-ai/outlines](https://github.com/dottxt-ai/outlines) | Evaluado | Librería para generación de texto estructurado y control estricto de esquemas JSON en agentes LLM. |

| gsplat | [nerfstudio-project/gsplat](https://github.com/nerfstudio-project/gsplat) | Evaluado | Librería CUDA hiperacelerada para rasterización y entrenamiento de 3D Gaussian Splatting por Nerfstudio. |
| nerfacc | [KAIR-BAIR/nerfacc](https://github.com/KAIR-BAIR/nerfacc) | Evaluado | Toolbox de aceleración en PyTorch para muestreo y renderizado volumétrico rápido de NeRFs. |
| HiFi-GAN | [jik876/hifi-gan-demo](https://github.com/jik876/hifi-gan-demo) | Evaluado | Vocoder neuronal GAN de alta fidelidad para síntesis de audio a partir de espectrogramas Mel. |
| BigVGAN | [NVIDIA/BigVGAN](https://github.com/NVIDIA/BigVGAN) | Evaluado | Vocoder neuronal universal desarrollado por NVIDIA de hasta 112M de parámetros para audio transparente. |
| Vocos | [gemelo-ai/vocos](https://github.com/gemelo-ai/vocos) | Evaluado | Vocoder neuronal ultra-rápido basado en Fourier que sintetiza audio desde tokens EnCodec o espectrogramas. |
| SVT-AV1 | [AOMediaCodec/SVT-AV1](https://gitlab.com/AOMediaCodec/SVT-AV1) | Evaluado | Codificador de video AV1 de alta eficiencia optimizado para transmisión en tiempo real de AOMedia. |
| dav1d | [videolan/dav1d](https://github.com/videolan/dav1d) | Evaluado | Decodificador AV1 open-source súper rápido de VideoLAN optimizado para reproducir video de baja latencia. |
| libvpx | [webmproject/libvpx](https://github.com/webmproject/libvpx) | Evaluado | Librería de referencia para codificación y decodificación de formatos de video VP8 y VP9. |
| libopus | [xiph/opus](https://github.com/xiph/opus) | Evaluado | Librería de referencia del codec de audio interactivo IETF Opus para comunicación WebRTC de baja latencia. |
| peerjs-server | [peers/peerjs-server](https://github.com/peers/peerjs-server) | Evaluado | Servidor de señalización WebRTC ligero para conexiones P2P PeerJS. |

| Kalidokit | [yeemachine/kalidokit](https://github.com/yeemachine/kalidokit) | Evaluado | Solver de cinemática y blendshapes para convertir pose y landmarks de MediaPipe a avatares VRM y Live2D. |
| Amazon Kinesis WebRTC C SDK | [awslabs/amazon-kinesis-video-streams-webrtc-sdk-c](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c) | Evaluado | SDK oficial en C de AWS para streaming multimedia WebRTC de baja latencia en dispositivos y servidor. |
| UnivNet | [maum-ai/univnet](https://github.com/maum-ai/univnet) | Evaluado | Vocoder neuronal de alta fidelidad basado en discriminadores de espectrograma multi-resolución. |
| WaveGlow | [NVIDIA/waveglow](https://github.com/NVIDIA/waveglow) | Evaluado | Red generativa basada en flujos desarrollada por NVIDIA para síntesis de voz en tiempo real. |
| ammo.js | [kripken/ammo.js](https://github.com/kripken/ammo.js) | Evaluado | Puerto directo del motor Bullet Physics a JavaScript/WebAssembly para física 3D en la web. |
| cannon.js | [schteppe/cannon.js](https://github.com/schteppe/cannon.js) | Evaluado | Motor de física 3D ligero escrito en JavaScript para avatares y entornos 3D interactivos. |
| three-mesh-bvh | [gkjohnson/three-mesh-bvh](https://github.com/gkjohnson/three-mesh-bvh) | Evaluado | Estructura de aceleración espacial BVH para trazado de rayos ultrarrápido en mallas Three.js. |
| MelGAN | [descriptinc/melgan-neurips](https://github.com/descriptinc/melgan-neurips) | Evaluado | Red generativa antagónica en tiempo real para síntesis de audio desde espectrogramas mel. |
| Parallel WaveGAN | [kan-bayashi/ParallelWaveGAN](https://github.com/kan-bayashi/ParallelWaveGAN) | Evaluado | Implementación paralela en PyTorch de WaveGAN para vocoder neuronal eficiente. |
| Video Processing Framework | [NVIDIA/VideoProcessingFramework](https://github.com/NVIDIA/VideoProcessingFramework) | Evaluado | Bindings en Python/PyTorch de NVIDIA para decodificación y codificación de video acelerada por hardware (NVDEC/NVENC). |

| fdk-aac | [mstorsjo/fdk-aac](https://github.com/mstorsjo/fdk-aac) | Evaluado | Librería de codificación y decodificación de audio AAC Fraunhofer FDK de alta fidelidad. |
| libavif | [AOMediaCodec/libavif](https://github.com/AOMediaCodec/libavif) | Evaluado | Librería C de referencia de AOMedia para codificación y decodificación de formato de imagen AVIF. |
| libjpeg-turbo | [libjpeg-turbo/libjpeg-turbo](https://github.com/libjpeg-turbo/libjpeg-turbo) | Evaluado | Codec JPEG acelerado por instrucciones SIMD para codificación/decodificación ultra-rápida de texturas. |
| stb | [nothings/stb](https://github.com/nothings/stb) | Evaluado | Librerías C/C++ de único archivo de dominio público para carga y manipulación ligera de imágenes y fuentes. |
| trimesh | [mikedh/trimesh](https://github.com/mikedh/trimesh) | Evaluado | Librería Python pura para inspección, manipulación y consulta de rayos en mallas 3D. |
| Open3D | [isl-org/Open3D](https://github.com/isl-org/Open3D) | Evaluado | Librería moderna para procesamiento de datos 3D, nubes de puntos, mallas y reconstrucción 3D. |
| PyMeshLab | [cnr-isti-vclab/PyMeshLab](https://github.com/cnr-isti-vclab/PyMeshLab) | Evaluado | Interfaz Python de MeshLab para procesamiento, simplificación y filtrado automatizado de mallas 3D. |

| Kokoro TTS | [hexgrad/kokoro](https://github.com/hexgrad/kokoro) | Evaluado | Modelo de síntesis de voz (TTS) ultraligero de 82M de parámetros de alta fidelidad y baja latencia. |
| DiffSynth-Studio | [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio) | Evaluado | Framework de difusión optimizado para generación y control de video en tiempo real por ModelScope. |
| Voicebox | [facebookresearch/voicebox](https://github.com/facebookresearch/voicebox) | Evaluado | Modelo fundacional generativo de audio de Meta basado en flow matching para edición, infilling y TTS. |
| rapier.js | [dimforge/rapier.js](https://github.com/dimforge/rapier.js) | Evaluado | Bindings en WebAssembly/JavaScript para el motor de física Rapier 3D. |
| livekit-plugins-deepgram | [livekit/plugins-deepgram](https://github.com/livekit/agents#deepgram) | Evaluado | Plugin oficial de LiveKit para integración de ASR Deepgram en tiempo real. |
| livekit-plugins-elevenlabs | [livekit/plugins-elevenlabs](https://github.com/livekit/agents#elevenlabs) | Evaluado | Plugin oficial de LiveKit para síntesis de voz en streaming con ElevenLabs. |

| VRoid SDK | [pixiv/VRoid-SDK](https://github.com/pixiv/VRoid-SDK) | Evaluado | SDK oficial de Pixiv para integración de avatares 3D VRM y personalización en aplicaciones. |
| livekit-plugins-cartesia | [livekit/plugins-cartesia](https://github.com/livekit/agents#cartesia) | Evaluado | Plugin oficial de LiveKit para integración de síntesis de voz ultrarrápida con Cartesia Sonic. |
| livekit-plugins-openai | [livekit/plugins-openai](https://github.com/livekit/agents#openai) | Evaluado | Plugin oficial de LiveKit para integración directa de OpenAI Realtime API y STT/TTS. |
| livekit-plugins-silero | [livekit/plugins-silero](https://github.com/livekit/agents#silero) | Evaluado | Plugin oficial de LiveKit para detección de actividad de voz en tiempo real con Silero VAD. |
| livekit-plugins-turn-detector | [livekit/plugins-turn-detector](https://github.com/livekit/agents#turn-detector) | Evaluado | Plugin de detección de turnos conversacionales y gestión de interrupciones para agentes de voz en LiveKit. |
| livekit-plugins-rag | [livekit/plugins-rag](https://github.com/livekit/agents#rag) | Evaluado | Plugin de integración RAG para agentes conversacionales de voz en tiempo real sobre LiveKit. |

| OpenH264 | [cisco/openh264](https://github.com/cisco/openh264) | Evaluado | Implementación de referencia open-source del codec H.264 desarrollada por Cisco para comunicación WebRTC. |
| libyuv | [chromium/libyuv](https://github.com/chromium/libyuv) | Evaluado | Librería C++ de Chromium para conversión de formatos de color YUV a RGB y escalado acelerado por SIMD. |
| libwebm | [webmproject/libwebm](https://github.com/webmproject/libwebm) | Evaluado | Librería C++ de referencia para parsing y multiplexado del contenedor de video WebM. |
| livekit-plugins-playht | [livekit/plugins-playht](https://github.com/livekit/agents#playht) | Evaluado | Plugin oficial de LiveKit para integración de síntesis de voz conversacional en streaming con PlayHT. |
| livekit-plugins-assemblyai | [livekit/plugins-assemblyai](https://github.com/livekit/agents#assemblyai) | Evaluado | Plugin oficial de LiveKit para transcripción y ASR en tiempo real con AssemblyAI. |
| livekit-plugins-azure | [livekit/plugins-azure](https://github.com/livekit/agents#azure) | Evaluado | Plugin oficial de LiveKit para integración de Azure Cognitive Services Speech STT y TTS. |
| livekit-plugins-google | [livekit/plugins-google](https://github.com/livekit/agents#google) | Evaluado | Plugin oficial de LiveKit para integración de Google Cloud Speech, Gemini y TTS en tiempo real. |
