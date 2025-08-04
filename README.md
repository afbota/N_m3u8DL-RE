# N_m3u8DL-RE

A fork of nilaoda's [N_m3u8DL-RE](https://github.com/nilaoda/N_m3u8DL-RE) aim to bring quality of life improvements.

Cross-platform DASH/HLS/MSS download tool. Supports on-demand and live streaming (DASH/HLS).

[![img](https://img.shields.io/github/last-commit/voldemort2826/N_m3u8DL-RE?label=Last%20Commit)](https://github.com/voldemort2826/N_m3u8DL-RE)  [![img](https://img.shields.io/github/license/voldemort2826/N_m3u8DL-RE?label=License)](https://github.com/voldemort2826/N_m3u8DL-RE)

> [!WARNING]
> If you encounter a bug, please first confirm that:
>
> - you have downloaded the latest version
> - you have checked the [Issues](https://github.com/voldemort2826/N_m3u8DL-RE/issues) section to see if someone else has encountered a similar problem
>
> If not, feel free to open a new issue.

## Command line parameters

```text
Description:
  N_m3u8DL-RE (Beta) build xxx

Usage:
  N_m3u8DL-RE <input> [options]

Arguments:
  <input>  Input Url or File

Options:
  --tmp-dir <tmp-dir>                                     Set temporary file directory
  --save-dir <save-dir>                                   Set output directory
  --save-name <save-name>                                 Set output filename
  --base-url <base-url>                                   Set BaseURL
  --thread-count <number>                                 Set download thread count [default: based on the number of CPU cores]
  --download-retry-count <number>                         The number of retries when download segment error [default: 3]
  --http-request-timeout <seconds>                        Timeout duration for HTTP requests (in seconds) [default: 100]
  --force-ansi-console                                    Force assuming the terminal is ANSI-compatible and interactive
  --no-ansi-color                                         Remove ANSI colors
  --auto-select                                           Automatically selects the best tracks of all types [default:
                                                          False]
  --skip-merge                                            Skip segments merge [default: False]
  --skip-download                                         Skip download [default: False]
  --check-segments-count                                  Check if the actual number of segments downloaded matches the
                                                          expected number [default: True]
  --binary-merge                                          Binary merge [default: False]
  --use-ffmpeg-concat-demuxer                             When merging with ffmpeg, use the concat demuxer instead of
                                                          the concat protocol [default: False]
  --del-after-done                                        Delete temporary files when done [default: True]
  --no-date-info                                          Date information is not written during muxing [default: False]
  --no-log                                                Disable log file output [default: False]
  --write-meta-json                                       Write meta json after parsed [default: True]
  --append-url-params                                     Add Params of input Url to segments, useful for some
                                                          websites, such as kakao.com [default: False]
  -mt, --concurrent-download                              Concurrently download the selected audio, video and subtitles
                                                          [default: False]
  -H, --header <header>                                   Pass custom header(s) to server, Example:
                                                          -H "Cookie: mycookie" -H "User-Agent: iOS"
  --sub-only                                              Select only subtitle tracks [default: False]
  --sub-format <SRT|VTT>                                  Subtitle output format [default: SRT]
  --auto-subtitle-fix                                     Automatically fix subtitles [default: True]
  --ffmpeg-binary-path <PATH>                             Full path to the ffmpeg binary, like C:\Tools\ffmpeg.exe
  --log-level <DEBUG|ERROR|INFO|OFF|WARN>                 Set log level [default: INFO]
  --ui-language <en-US|zh-CN|zh-TW>                       Set UI language
  --urlprocessor-args <urlprocessor-args>                 Give these arguments to the URL Processors.
  --key <key>                                             Set decryption key(s) to mp4decrypt/shaka-packager/ffmpeg.
                                                          format:
                                                          --key KID1:KEY1 --key KID2:KEY2
                                                          or use --key KEY if all tracks share the same key.
  --key-text-file <key-text-file>                         Set the kid-key file, the program will search the KEY with
                                                          KID from the file.(Very large file are not recommended)
  --decryption-engine <FFMPEG|MP4DECRYPT|SHAKA_PACKAGER>  Set the third-party program used for decryption [default:
                                                          MP4DECRYPT]
  --decryption-binary-path <PATH>                         Full path to the tool used for MP4 decryption, like
                                                          C:\Tools\mp4decrypt.exe
  --mp4-real-time-decryption                              Decrypt MP4 segments in real time [default: False]
  -R, --max-speed <SPEED>                                 Set speed limit, Mbps or Kbps, for example: 15M 100K.
  -M, --mux-after-done <OPTIONS>                          When all works is done, try to mux the downloaded streams.
                                                          Use "--morehelp mux-after-done" for more details
  --custom-hls-method <METHOD>                            Set HLS encryption method
                                                          (AES_128|AES_128_ECB|CENC|CHACHA20|NONE|SAMPLE_AES|SAMPLE_AES_
                                                          CTR|UNKNOWN)
  --custom-hls-key <FILE|HEX|BASE64>                      Set the HLS decryption key. Can be file, HEX or Base64
  --custom-hls-iv <FILE|HEX|BASE64>                       Set the HLS decryption iv. Can be file, HEX or Base64
  --use-system-proxy                                      Use system default proxy [default: True]
  --custom-proxy <URL>                                    Set web request proxy, like http://127.0.0.1:8888
  --custom-range <RANGE>                                  Download only part of the segments. Use "--morehelp
                                                          custom-range" for more details
  --task-start-at <yyyyMMddHHmmss>                        Task execution will not start before this time
  --live-perform-as-vod                                   Download live streams as vod [default: False]
  --live-real-time-merge                                  Real-time merge into file when recording live [default: False]
  --live-keep-segments                                    Keep segments when recording a live (liveRealTimeMerge
                                                          enabled) [default: True]
  --live-pipe-mux                                         Real-time muxing to TS file through pipeline + ffmpeg
                                                          (liveRealTimeMerge enabled) [default: False]
  --live-fix-vtt-by-audio                                 Correct VTT sub by reading the start time of the audio file
                                                          [default: False]
  --live-record-limit <HH:mm:ss>                          Recording time limit when recording live
  --live-wait-time <SEC>                                  Manually set the live playlist refresh interval
  --live-take-count <NUM>                                 Manually set the number of segments downloaded for the first
                                                          time when recording live [default: 16]
  --mux-import <OPTIONS>                                  When MuxAfterDone enabled, allow to import local media files.
                                                          Use "--morehelp mux-import" for more details
  -sv, --select-video <OPTIONS>                           Select video streams by regular expressions. Use "--morehelp
                                                          select-video" for more details
  -sa, --select-audio <OPTIONS>                           Select audio streams by regular expressions. Use "--morehelp
                                                          select-audio" for more details
  -ss, --select-subtitle <OPTIONS>                        Select subtitle streams by regular expressions. Use
                                                          "--morehelp select-subtitle" for more details
  -dv, --drop-video <OPTIONS>                             Drop video streams by regular expressions.
  -da, --drop-audio <OPTIONS>                             Drop audio streams by regular expressions.
  -ds, --drop-subtitle <OPTIONS>                          Drop subtitle streams by regular expressions.
  --ad-keyword <REG>                                      Set URL keywords (regular expressions) for AD segments
  --disable-update-check                                  Disable version update check [default: False]
  --allow-hls-multi-ext-map                               Allow multiple #EXT-X-MAP in HLS (experimental) [default:
                                                          False]
  --morehelp <OPTION>                                     Set more help info about one option
  --version                                               Show version information
  -?, -h, --help                                          Show help and usage information
```

<details>
<summary>Click to view "More Help" section</summary>

```text
More Help:

  --mux-after-done

When all works are done, try to mux the separated audio and video. You can specify the following parameters:

* format=FORMAT: specify the mux container (mkv, mp4)
* muxer=MUXER: specify the mux program (ffmpeg, mkvmerge) (default: ffmpeg)
* bin_path=PATH: specify the program path (default: auto-find)
* skip_sub=BOOL: whether to ignore subtitle files (default: false)
* keep=BOOL: whether to keep the file after muxing (true, false) (default: false)

Examples:
# mux to mp4 container
-M format=mp4
# use mkvmerge, auto-find program
-M format=mkv:muxer=mkvmerge
# use mkvmerge, custom program path
-M format=mkv:muxer=mkvmerge:bin_path="C\:\Program Files\MKVToolNix\mkvmerge.exe"
```

```text
More Help:

  --mux-import

When MuxAfterDone enabled, allow to import local media files. OPTIONS is a colon separated list of:

* path=PATH: set file path
* lang=CODE: set media language code (not required)
* name=NAME: set description (not required)

Examples:
# import subtitle
--mux-import path=en-US.srt:lang=eng:name="English (Original)"
# import audio and subtitle
--mux-import path="D\:\media\atmos.m4a":lang=eng:name="English Description Audio" --mux-import path="D\:\media\eng.vtt":lang=eng:name="English (Description)"
```

```text
More Help:

  --select-video

Select video streams by regular expressions. OPTIONS is a colon separated list of:

id=REGEX:lang=REGEX:name=REGEX:codecs=REGEX:res=REGEX:frame=REGEX
segsMin=number:segsMax=number:ch=REGEX:range=REGEX:url=REGEX
plistDurMin=hms:plistDurMax=hms:bwMin=int:bwMax=int:role=string:for=FOR

* for=FOR: Select type. best[number], worst[number], all (Default: best)

Examples:
# select best video
-sv best
# select 4K+HEVC video
-sv res="3840*":codecs=hvc1:for=best
# Select best video with duration longer than 1 hour 20 minutes 30 seconds
-sv plistDurMin="1h20m30s":for=best
-sv role="main":for=best
# Select video with bandwidth between 800Kbps and 1Mbps
-sv bwMin=800:bwMax=1000
```

```text
More Help:

  --select-audio

Select audio streams by regular expressions. ref --select-video

Examples:
# select all
-sa all
# select best eng audio
-sa lang=en:for=best
# select best 2, and language is ja or en
-sa lang="ja|en":for=best2
-sa role="main":for=best
```

```text
More Help:

  --select-subtitle

Select subtitle streams by regular expressions. ref --select-video

Examples:
# select all subs
-ss all
# select all subs containing "English"
-ss name="English":for=all
```

```text
More Help:

  --custom-range

Download only part of the segments when downloading vod content.

Examples:
# Download [0,10], a total of 11 segments
--custom-range 0-10
# Download subsequent segments starting from index 10
--custom-range 10-
# Download the first 100 segments
--custom-range -99
# Download content from the 05:00 to 20:00
--custom-range 05:00-20:00
```

</details>

## Screenshots

### On-demand

![RE1](img/RE.gif)

Can also download in parallel and automatically mix streams

![RE2](img/RE2.gif)

### Live

Record TS live source:

[click to show gif](http://pan.iqiyi.com/file/paopao/W0LfmaMRvuA--uCdOpZ1cldM5JCVhMfIm7KFqr4oKCz80jLn0bBb-9PWmeCFZ-qHpAaQydQ1zk-CHYT_UbRLtw.gif)

Record MPD live source:

[click to show gif](http://pan.iqiyi.com/file/paopao/nmAV5MOh0yIyHhnxdgM_6th_p2nqrFsM4k-o3cUPwUa8Eh8QOU4uyPkLa_BlBrMa3GBnKWSk8rOaUwbsjKN14g.gif)

During recording, use ffmpeg to mix audio and video in real time

```bash
ffmpeg -readrate 1 -i 2022-09-21_19-54-42_V.mp4 -i 2022-09-21_19-54-42_V.chi.m4a -c copy 2022-09-21_19-54-42_V.ts
```

From v0.1.5, you can try to enable `live-pipe-mux` instead of the above command

> [!NOTE]
> If the network environment is not stable, do not enable `live-pipe-mux`. The data read in the pipeline is handled by ffmpeg, and it is easy to lose live data in some environments.

From v0.1.8, you can set the environment variable `RE_LIVE_PIPE_OPTIONS` to change some options of ffmpeg when `live-pipe-mux` is enabled: <https://github.com/nilaoda/N_m3u8DL-RE/issues/162#issuecomment-1592462532>

## Credits

- [@nilaoda](https://github.com/nilaoda): original author
- All contributors in [@nilaoda/N_m3u8DL-RE](https://github.com/nilaoda/N_m3u8DL-RE/graphs/contributors)
