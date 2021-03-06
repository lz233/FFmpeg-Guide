# FFmpeg Guide

## 序言

### 这份指南的由来

我平常总能在群组中看到使用某工厂进行转码的人，这时候我都很想让他们使用 ffmpeg。但是迫于上手繁琐等原因，他们一般都不愿尝试，于是便有了这份指南。

### 这份指南适合谁

这份指南面向有一定命令行基础，想要快速上手，掌握 ffmpeg 基本用法的用户。

对于高级的用法，本指南可能不会有太多叙述。

### 许可

本指南在 [Apache License 2.0](https://github.com/lz233/FFmpeg-Guide/blob/master/LICENSE) 下进行许可。

## 安装与部署

本节会介绍在大多数常见操作系统上安装与部署 ffmpeg 的方式。在部署完毕后，后续章节会主要在Windows下进行演示。其他平台下的使用方式与在Windows下使用几乎无异。

### Microsoft Windows

#### 获取二进制文件

1. 在 [Zeranoe](https://ffmpeg.zeranoe.com/builds/) (https://ffmpeg.zeranoe.com/builds/) 中选择你需要获取的分支，下载其二进制文件。
2. 转到控制面板-系统和安全-系统-高级系统设置-高级-环境变量，在Path变量中添加 ffmpeg 二进制文件的目录。例如`C:\Users\24843\Documents\exe\ffmpeg`
3. 使用 CMD/Windows PowerShell/Windows Termainal，键入`ffmpeg`。如果控制台的输出像这样的话，即安装完毕。
`ffmpeg version 4.2 Copyright (c) 2000-2019 the FFmpeg developers`

#### 从源码编译

待完成……

### GNU/Linux

#### 通过命令行部署

大多数 Linux 发行版都有强大的包管理系统，只需一行命令便能部署 ffmpeg。

- Debian 系

`sudo apt install ffmpeg`

- 红帽系

根据发行版的不同，可能有以下安装方式。

`yum install ffmpeg`

`dnf install ffmpeg`

- Arch 系

`pacman -S ffmpeg`

使用终端，键入`ffmpeg`，如果终端的输出像这样的话，即安装完毕。

`ffmpeg version 4.2 Copyright (c) 2000-2019 the FFmpeg developers`

#### 获取二进制文件

待完成……

#### 从源码编译

待完成……

### Apple Mac OS

#### 通过命令行部署

在终端键入`brew install ffmpeg`即可部署。完成后键入`ffmpeg`，如果终端的输出像这样的话，即安装完毕。

`ffmpeg version 4.2 Copyright (c) 2000-2019 the FFmpeg developers`

#### 获取二进制文件

待完成……

#### 从源码编译

待完成……

### Apple iOS/iPad OS

#### 从Cydia部署

在 Cydia 或其他包管理器中搜索 ffmpeg，应该会出现相应的包，安装即可。完成后在终端键入`ffmpeg`，如果终端的输出像这样的话，即安装完毕。

`ffmpeg version 4.2 Copyright (c) 2000-2019 the FFmpeg developers`

### Android

#### 从 Google Play Store 获取

Google Play Store 有很多类似的应用，比如 [FFmpegui](https://play.google.com/store/apps/details?id=org.ffmpeg.gui)、[FFmpegMediaEncoder](https://play.google.com/store/apps/details?id=com.silentlexx.ffmpeggui)。或者，也可以在 [NeoTerm](https://www.coolapk.com/apk/io.neoterm)、[Termux](https://play.google.com/store/apps/details?id=com.termux) 内安装 ffmpeg，安装方式与上文 GNU/Linux 的方式几乎无异。

## 开始工作之前

### 了解当前 ffmpeg 支持的文件格式与编码器

如果你在桌面操作系统上使用 ffmpeg，那么你获取到的一般是最新版本。但如果你在移动平台上使用，则不然，因为这些发行版本一般不由官方维护。因此，你需要检查当前 ffmpeg 所支持的文件格式与编码器。

要了解当前 ffmpeg 支持的文件格式，请键入`ffmpeg -formats`。它的输出大致如下：

```bash
File formats:
 D. = Demuxing supported
 .E = Muxing supported
 --
 D  3dostr          3DO STR
  E 3g2             3GP2 (3GPP2 file format)
  E 3gp             3GP (3GPP file format)
 D  4xm             4X Technologies
  E a64             a64 - video for Commodore 64
 D  aa              Audible AA format files
 D  aac             raw ADTS AAC (Advanced Audio Coding)
 DE ac3             raw AC-3
 D  acm             Interplay ACM
 D  act             ACT Voice file format
 D  adf             Artworx Data Format
 D  adp             ADP
 D  ads             Sony PS2 ADS
  E adts            ADTS AAC (Advanced Audio Coding)
 DE adx             CRI ADX
 D  aea             MD STUDIO audio
 D  afc             AFC
 DE aiff            Audio IFF
 D  aix             CRI AIX
 DE alaw            PCM A-law
 D  alias_pix       Alias/Wavefront PIX image
 DE amr             3GPP AMR
 D  amrnb           raw AMR-NB
 D  amrwb           raw AMR-WB
 D  anm             Deluxe Paint Animation
 D  apc             CRYO APC
 D  ape             Monkey's Audio
 DE apng            Animated Portable Network Graphics
 DE aptx            raw aptX (Audio Processing Technology for Bluetooth)
 DE aptx_hd         raw aptX HD (Audio Processing Technology for Bluetooth)
 D  aqtitle         AQTitle subtitles
 DE asf             ASF (Advanced / Active Streaming Format)
 D  asf_o           ASF (Advanced / Active Streaming Format)
  E asf_stream      ASF (Advanced / Active Streaming Format)
 DE ass             SSA (SubStation Alpha) subtitle
 DE ast             AST (Audio Stream)
 DE au              Sun AU
 DE avi             AVI (Audio Video Interleaved)
 D  avisynth        AviSynth script
  E avm2            SWF (ShockWave Flash) (AVM2)
 D  avr             AVR (Audio Visual Research)
 D  avs             Argonaut Games Creature Shock
 DE avs2            raw AVS2-P2/IEEE1857.4 video
 D  bethsoftvid     Bethesda Softworks VID
 D  bfi             Brute Force & Ignorance
 D  bfstm           BFSTM (Binary Cafe Stream)
 D  bin             Binary text
 D  bink            Bink
 DE bit             G.729 BIT file format
 D  bmp_pipe        piped bmp sequence
 D  bmv             Discworld II BMV
 D  boa             Black Ops Audio
 D  brender_pix     BRender PIX image
 D  brstm           BRSTM (Binary Revolution Stream)
 D  c93             Interplay C93
 DE caf             Apple CAF (Core Audio Format)
 DE cavsvideo       raw Chinese AVS (Audio Video Standard) video
 D  cdg             CD Graphics
 D  cdxl            Commodore CDXL video
 D  cine            Phantom Cine
 DE codec2          codec2 .c2 muxer
 DE codec2raw       raw codec2 muxer
 D  concat          Virtual concatenation script
  E crc             CRC testing
 DE dash            DASH Muxer
 DE data            raw data
 DE daud            D-Cinema audio
 D  dcstr           Sega DC STR
 D  dds_pipe        piped dds sequence
 D  dfa             Chronomaster DFA
 D  dhav            Video DAV
 DE dirac           raw Dirac
 DE dnxhd           raw DNxHD (SMPTE VC-3)
 D  dpx_pipe        piped dpx sequence
 D  dsf             DSD Stream File (DSF)
 D  dshow           DirectShow capture
 D  dsicin          Delphine Software International CIN
 D  dss             Digital Speech Standard (DSS)
 DE dts             raw DTS
 D  dtshd           raw DTS-HD
 DE dv              DV (Digital Video)
 D  dvbsub          raw dvbsub
 D  dvbtxt          dvbtxt
  E dvd             MPEG-2 PS (DVD VOB)
 D  dxa             DXA
 D  ea              Electronic Arts Multimedia
 D  ea_cdata        Electronic Arts cdata
 DE eac3            raw E-AC-3
 D  epaf            Ensoniq Paris Audio File
 D  exr_pipe        piped exr sequence
 DE f32be           PCM 32-bit floating-point big-endian
 DE f32le           PCM 32-bit floating-point little-endian
  E f4v             F4V Adobe Flash Video
 DE f64be           PCM 64-bit floating-point big-endian
 DE f64le           PCM 64-bit floating-point little-endian
 DE ffmetadata      FFmpeg metadata in text
  E fifo            FIFO queue pseudo-muxer
  E fifo_test       Fifo test muxer
 DE film_cpk        Sega FILM / CPK
 DE filmstrip       Adobe Filmstrip
 DE fits            Flexible Image Transport System
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation
 DE flv             FLV (Flash Video)
  E framecrc        framecrc testing
  E framehash       Per-frame hash testing
  E framemd5        Per-frame MD5 testing
 D  frm             Megalux Frame
 D  fsb             FMOD Sample Bank
 DE g722            raw G.722
 DE g723_1          raw G.723.1
 DE g726            raw big-endian G.726 ("left-justified")
 DE g726le          raw little-endian G.726 ("right-justified")
 D  g729            G.729 raw format demuxer
 D  gdigrab         GDI API Windows frame grabber
 D  gdv             Gremlin Digital Video
 D  genh            GENeric Header
 DE gif             CompuServe Graphics Interchange Format (GIF)
 D  gif_pipe        piped gif sequence
 DE gsm             raw GSM
 DE gxf             GXF (General eXchange Format)
 DE h261            raw H.261
 DE h263            raw H.263
 DE h264            raw H.264 video
  E hash            Hash testing
 D  hcom            Macintosh HCOM
  E hds             HDS Muxer
 DE hevc            raw HEVC video
 DE hls             Apple HTTP Live Streaming
 D  hnm             Cryo HNM v4
 DE ico             Microsoft Windows ICO
 D  idcin           id Cinematic
 D  idf             iCE Draw File
 D  iff             IFF (Interchange File Format)
 D  ifv             IFV CCTV DVR
 DE ilbc            iLBC storage
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       raw Ingenient MJPEG
 D  ipmovie         Interplay MVE
  E ipod            iPod H.264 MP4 (MPEG-4 Part 14)
 DE ircam           Berkeley/IRCAM/CARL Sound Format
  E ismv            ISMV/ISMA (Smooth Streaming)
 D  iss             Funcom ISS
 D  iv8             IndigoVision 8000 video
 DE ivf             On2 IVF
 D  ivr             IVR (Internet Video Recording)
 D  j2k_pipe        piped j2k sequence
 DE jacosub         JACOsub subtitle format
 D  jpeg_pipe       piped jpeg sequence
 D  jpegls_pipe     piped jpegls sequence
 D  jv              Bitmap Brothers JV
 D  kux             KUX (YouKu)
  E latm            LOAS/LATM
 D  lavfi           Libavfilter virtual input device
 D  libopenmpt      Tracker formats (libopenmpt)
 D  live_flv        live RTMP FLV (Flash Video)
 D  lmlm4           raw lmlm4
 D  loas            LOAS AudioSyncStream
 DE lrc             LRC lyrics
 D  lvf             LVF
 D  lxf             VR native stream (LXF)
 DE m4v             raw MPEG-4 video
  E matroska        Matroska
 D  matroska,webm   Matroska / WebM
  E md5             MD5 testing
 D  mgsts           Metal Gear Solid: The Twin Snakes
 DE microdvd        MicroDVD subtitle format
 DE mjpeg           raw MJPEG video
 D  mjpeg_2000      raw MJPEG 2000 video
  E mkvtimestamp_v2 extract pts as timecode v2 format, as defined by mkvtoolnix
 DE mlp             raw MLP
 D  mlv             Magic Lantern Video (MLV)
 D  mm              American Laser Games MM
 DE mmf             Yamaha SMAF
  E mov             QuickTime / MOV
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime / MOV
  E mp2             MP2 (MPEG audio layer 2)
 DE mp3             MP3 (MPEG audio layer 3)
  E mp4             MP4 (MPEG-4 Part 14)
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 Systems / MPEG program stream
  E mpeg1video      raw MPEG-1 video
  E mpeg2video      raw MPEG-2 video
 DE mpegts          MPEG-TS (MPEG-2 Transport Stream)
 D  mpegtsraw       raw MPEG-TS (MPEG-2 Transport Stream)
 D  mpegvideo       raw MPEG video
 DE mpjpeg          MIME multipart JPEG
 D  mpl2            MPL2 subtitles
 D  mpsub           MPlayer subtitles
 D  msf             Sony PS3 MSF
 D  msnwctcp        MSN TCP Webcam stream
 D  mtaf            Konami PS2 MTAF
 D  mtv             MTV
 DE mulaw           PCM mu-law
 D  musx            Eurocom MUSX
 D  mv              Silicon Graphics Movie
 D  mvi             Motion Pixels MVI
 DE mxf             MXF (Material eXchange Format)
  E mxf_d10         MXF (Material eXchange Format) D-10 Mapping
  E mxf_opatom      MXF (Material eXchange Format) Operational Pattern Atom
 D  mxg             MxPEG clip
 D  nc              NC camera feed
 D  nistsphere      NIST SPeech HEader REsources
 D  nsp             Computerized Speech Lab NSP
 D  nsv             Nullsoft Streaming Video
  E null            raw null video
 DE nut             NUT
 D  nuv             NuppelVideo
  E oga             Ogg Audio
 DE ogg             Ogg
  E ogv             Ogg Video
 DE oma             Sony OpenMG audio
  E opus            Ogg Opus
 D  paf             Amazing Studio Packed Animation File
 D  pam_pipe        piped pam sequence
 D  pbm_pipe        piped pbm sequence
 D  pcx_pipe        piped pcx sequence
 D  pgm_pipe        piped pgm sequence
 D  pgmyuv_pipe     piped pgmyuv sequence
 D  pictor_pipe     piped pictor sequence
 D  pjs             PJS (Phoenix Japanimation Society) subtitles
 D  pmp             Playstation Portable PMP
 D  png_pipe        piped png sequence
 D  ppm_pipe        piped ppm sequence
 D  psd_pipe        piped psd sequence
  E psp             PSP MP4 (MPEG-4 Part 14)
 D  psxstr          Sony Playstation STR
 D  pva             TechnoTrend PVA
 D  pvf             PVF (Portable Voice Format)
 D  qcp             QCP
 D  qdraw_pipe      piped qdraw sequence
 D  r3d             REDCODE R3D
 DE rawvideo        raw video
 D  realtext        RealText subtitle format
 D  redspark        RedSpark
 D  rl2             RL2
 DE rm              RealMedia
 DE roq             raw id RoQ
 D  rpl             RPL / ARMovie
 D  rsd             GameCube RSD
 DE rso             Lego Mindstorms RSO
 DE rtp             RTP output
  E rtp_mpegts      RTP/mpegts output format
 DE rtsp            RTSP output
 DE s16be           PCM signed 16-bit big-endian
 DE s16le           PCM signed 16-bit little-endian
 DE s24be           PCM signed 24-bit big-endian
 DE s24le           PCM signed 24-bit little-endian
 DE s32be           PCM signed 32-bit big-endian
 DE s32le           PCM signed 32-bit little-endian
 D  s337m           SMPTE 337M
 DE s8              PCM signed 8-bit
 D  sami            SAMI subtitle format
 DE sap             SAP output
 DE sbc             raw SBC
 D  sbg             SBaGen binaural beats script
 DE scc             Scenarist Closed Captions
  E sdl,sdl2        SDL2 output device
 D  sdp             SDP
 D  sdr2            SDR2
 D  sds             MIDI Sample Dump Standard
 D  sdx             Sample Dump eXchange
  E segment         segment
 D  ser             SER (Simple uncompressed video format for astronomical capturing)
 D  sgi_pipe        piped sgi sequence
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
  E singlejpeg      JPEG single image
 D  sln             Asterisk raw pcm
 DE smjpeg          Loki SDL MJPEG
 D  smk             Smacker
  E smoothstreaming Smooth Streaming Muxer
 D  smush           LucasArts Smush
 D  sol             Sierra SOL
 DE sox             SoX native
 DE spdif           IEC 61937 (used on S/PDIF - IEC958)
  E spx             Ogg Speex
 DE srt             SubRip subtitle
 D  stl             Spruce subtitle format
  E stream_segment,ssegment streaming segment muxer
 D  subviewer       SubViewer subtitle format
 D  subviewer1      SubViewer v1 subtitle format
 D  sunrast_pipe    piped sunrast sequence
 DE sup             raw HDMV Presentation Graphic Stream subtitles
 D  svag            Konami PS2 SVAG
  E svcd            MPEG-2 PS (SVCD)
 D  svg_pipe        piped svg sequence
 DE swf             SWF (ShockWave Flash)
 D  tak             raw TAK
 D  tedcaptions     TED Talks captions
  E tee             Multiple muxer tee
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ
 D  tiff_pipe       piped tiff sequence
 D  tmv             8088flex TMV
 DE truehd          raw TrueHD
 DE tta             TTA (True Audio)
 D  tty             Tele-typewriter
 D  txd             Renderware TeXture Dictionary
 D  ty              TiVo TY Stream
 DE u16be           PCM unsigned 16-bit big-endian
 DE u16le           PCM unsigned 16-bit little-endian
 DE u24be           PCM unsigned 24-bit big-endian
 DE u24le           PCM unsigned 24-bit little-endian
 DE u32be           PCM unsigned 32-bit big-endian
 DE u32le           PCM unsigned 32-bit little-endian
 DE u8              PCM unsigned 8-bit
  E uncodedframecrc uncoded framecrc testing
 D  v210            Uncompressed 4:2:2 10-bit
 D  v210x           Uncompressed 4:2:2 10-bit
 D  vag             Sony PS2 VAG
 DE vc1             raw VC-1 video
 DE vc1test         VC-1 test bitstream
  E vcd             MPEG-1 Systems / MPEG program stream (VCD)
 D  vfwcap          VfW video capture
 DE vidc            PCM Archimedes VIDC
 D  vividas         Vividas VIV
 D  vivo            Vivo
 D  vmd             Sierra VMD
  E vob             MPEG-2 PS (VOB)
 D  vobsub          VobSub subtitle format
 DE voc             Creative Voice
 D  vpk             Sony PS2 VPK
 D  vplayer         VPlayer subtitles
 D  vqf             Nippon Telegraph and Telephone Corporation (NTT) TwinVQ
 DE w64             Sony Wave64
 DE wav             WAV / WAVE (Waveform Audio)
 D  wc3movie        Wing Commander III movie
  E webm            WebM
  E webm_chunk      WebM Chunk Muxer
 DE webm_dash_manifest WebM DASH Manifest
  E webp            WebP
 D  webp_pipe       piped webp sequence
 DE webvtt          WebVTT subtitle
 D  wsaud           Westwood Studios audio
 D  wsd             Wideband Single-bit Data (WSD)
 D  wsvqa           Westwood Studios VQA
 DE wtv             Windows Television (WTV)
 DE wv              raw WavPack
 D  wve             Psion 3 audio
 D  xa              Maxis XA
 D  xbin            eXtended BINary text (XBIN)
 D  xmv             Microsoft XMV
 D  xpm_pipe        piped xpm sequence
 D  xvag            Sony PS3 XVAG
 D  xwd_pipe        piped xwd sequence
 D  xwma            Microsoft xWMA
 D  yop             Psygnosis YOP
 DE yuv4mpegpipe    YUV4MPEG pipe
```

### 尝试转换第一个文件

使用ffmpeg进行文件转换很简单，键入以下一行命令就能完成操作。

`ffmpeg -i [input] [ouput]`

在部分系统上，你可以尝试将文件拖入命令行窗口来自动填充命令。

## 转换时可以干的事情

## 小技巧

### ffmpeg 还能做更多

除了音视频之外，ffmpeg 还能转换图片，并且一般支持ico/webp/png/gif/jpg等多种格式。例如将视频转换为gif：

`
ffmpeg -i input.mp4 output.gif
`