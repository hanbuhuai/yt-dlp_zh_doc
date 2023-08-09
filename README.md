yt-dlp是基于现已停用的youtube-dlc的一个分支，主要关注于添加新功能和补丁，同时与原始项目保持更新。 [ youtube-dl ](https://github.com/ytdl-org/youtube-dl) [ youtube-dlc ](https://github.com/blackjack4494/yt-dlc)

<!--MANPAGE: MOVE "USAGE AND OPTIONS" SECTION HERE MANPAGE: BEGIN EXCLUDED SECTION >

  * 新功能 
    * 默认行为的差异 
  * 安装 
  * 更新 
  * 发布文件 
    * 推荐 
    * 替代方案 
    * 杂项 
  * 依赖项 
    * 强烈推荐 
    * 网络 
    * 元数据 
    * 杂项 
    * 已弃用 
  * 编译 
    * 独立的PyInstaller构建 
    * 平台无关的二进制文件（UNIX） 
    * 独立的Py2Exe构建（Windows） 
    * 相关脚本 
    * 分叉项目 
  * 使用和选项 
  * 通用选项： 
  * 网络选项： 
  * 地理限制： 
  * 视频选择： 
  * 下载选项： 
  * 文件系统选项： 
  * 缩略图选项： 
  * Internet快捷方式选项： 
  * 冗长和模拟选项： 
  * 解决方法： 
  * 视频格式选项： 
  * 字幕选项： 
  * 身份验证选项： 
  * 后处理选项： 
  * SponsorBlock选项： 
  * 提取器选项： 
  * 配置 
    * 配置文件编码 
    * 使用netrc进行身份验证 
    * 关于环境变量的注意事项 
  * 输出模板 
    * 输出模板示例 
  * 格式选择 
  * 过滤格式 
  * 排序格式 
  * 格式选择示例 
  * 修改元数据 
  * 修改元数据示例 
  * 提取器参数 
    * youtube 
    * youtubetab（YouTube播放列表，频道，订阅等） 
    * 通用 
    * funimation 
    * crunchyrollbeta（Crunchyroll） 
    * vikichannel 
    * niconico 
    * youtubewebarchive 
    * gamejolt 
    * hotstar 
    * tiktok 
    * rokfinchannel 
    * twitter 
    * stacommu，wrestleuniverse 
    * twitch 
    * nhkradirulive（NHK らじる★らじる LIVE） 
  * 插件 
  * 安装插件 
  * 开发插件 
  * 嵌入YT-DLP 
  * 嵌入示例 
    * 提取信息 
    * 使用info-json下载 
    * 提取音频 
    * 过滤视频 
    * 添加日志记录器和进度钩子 
    * 添加自定义后处理器 
    * 使用自定义格式选择器 
  * 废弃选项 
    * 几乎冗余的选项 
    * 冗余选项 
    * 不推荐使用 
    * 开发者选项 
    * 旧别名 
    * Sponskrub 选项 
    * 不再支持 
    * 已移除 
  * 贡献 
  * 维基 

<!--MANPAGE: END EXCLUDED SECTION -->

#  新功能 

  * Forked from [ **yt-dlc@f9401f2** ](https://github.com/blackjack4494/yt-dlc/commit/f9401f2a91987068139c5f757b12fc711d4c0cee) and merged with [ **youtube-dl@42f2d4** ](https://github.com/ytdl-org/youtube-dl/commit/07af47960f3bb262ead02490ce65c8c45c01741e) ( [ exceptions ](https://github.com/yt-dlp/yt-dlp/issues/21) ) 

  * ** SponsorBlock Integration  ** : 您可以利用 [ SponsorBlock ](https://sponsor.ajay.app) API 标记/删除 YouTube 视频中的赞助部分 

  * ** Format Sorting  ** : 默认的格式排序选项已更改，现在更倾向于选择更高分辨率和更好的编解码器，而不仅仅是使用更大的比特率。此外，您现在可以使用 ` -S ` 指定排序顺序。这比仅使用 ` --format ` 更容易选择格式（  示例  ） 

  * **Merged with animelover1984/youtube-dl** : 您可以获得来自 [ animelover1984/youtube-dl ](https://github.com/animelover1984/youtube-dl) 的大多数功能和改进，包括 ` --write-comments ` 、 ` BiliBiliSearch ` 、 ` BilibiliChannel ` ，在 mp4/ogg/opus 中嵌入缩略图，播放列表 infojson 等。请注意，NicoNico 直播不可用。有关详细信息，请参阅 [ #31 ](https://github.com/yt-dlp/yt-dlp/pull/31) 。 

  * **YouTube 改进** ： 

    * 支持剪辑、故事（ ` ytstories:<channel UCID> ` ）、搜索（包括过滤器） ***** 、YouTube 音乐搜索、特定频道搜索、搜索前缀（ ` ytsearch: ` 、 ` ytsearchdate: ` ） ***** 、混合和订阅源（ ` :ytfav ` 、 ` :ytwatchlater ` 、 ` :ytsubs ` 、 ` :ythistory ` 、 ` :ytrec ` 、 ` :ytnotif ` ） 
    * 修复了基于 n-sig 的限流问题 *****
    * 支持一些（但不是全部）需要年龄验证的内容，无需使用 cookies 
    * 使用 ` --live-from-start ` 从开始下载直播流（ _实验性的_ ） 
    * 当提供高级 cookies 时，从 YouTube Music 提取 ` 255kbps ` 音频（如果可用） 
    * 频道 URL 下载频道的所有上传内容，包括短视频和直播 
  * **来自浏览器的 Cookies** ：可以使用 ` --cookies-from-browser BROWSER[+KEYRING][:PROFILE][::CONTAINER] ` 自动提取所有主要网络浏览器的 Cookies 

  * **下载时间范围** ：可以根据时间戳或章节部分下载视频，使用 ` --download-sections `

  * **按章节拆分视频** ：可以根据章节将视频拆分为多个文件，使用 ` --split-chapters `

  * **多线程片段下载** ：可以并行下载m3u8/mpd视频的多个片段。使用 ` --concurrent-fragments ` （ ` -N ` ）选项设置线程数 

  * **使用Aria2c下载HLS/DASH** ：可以使用 ` aria2c ` 作为DASH（mpd）和HLS（m3u8）格式的外部下载器 

  * **新的和修复的提取器** ：添加了许多新的提取器，并修复了许多现有的提取器。请参阅 [ 更新日志 ](Changelog.md) 或 [ 支持的站点列表 ](supportedsites.md)

  * **新的MSO** ：Philo、Spectrum、SlingTV、Cablevision、RCN等 

  * **从清单中提取字幕** ：可以从流媒体清单中提取字幕。详见 [ commit/be6202f ](https://github.com/yt-dlp/yt-dlp/commit/be6202f12b97858b9d716e608394b51065d0419f)

  * **多个路径和输出模板** ：可以为不同类型的文件提供不同的  输出模板  和下载路径。还可以使用 ` --paths ` （ ` -P ` ）设置中间文件下载的临时路径 

  * **可移植配置** ：配置文件会自动从主目录和根目录加载。详见  配置说明 

  * **输出模板改进** ：输出模板现在可以具有日期时间格式、数字偏移、对象遍历等功能。详见  输出模板说明  。还可以通过 ` --parse-metadata ` 和 ` --replace-in-metadata ` 进行更高级的操作 

  * **其他新选项** ：添加了许多新选项，例如 ` --alias ` 、 ` --print ` 、 ` --concat-playlist ` 、 ` --wait-for-video ` 、 ` --retry-sleep ` 、 ` --sleep-requests ` 、 ` --convert-thumbnails ` 、 ` --force-download-archive ` 、 ` --force-overwrites ` 、 ` --break-match-filter ` 等等 

  * **改进** ：在 ` --format ` / ` --match-filter ` 中支持正则表达式和其他运算符，支持多个 ` --postprocessor-args ` 和 ` --downloader-args ` ，更快的存档检查，更多的  格式选择选项  ，合并多个视频/音频，多个 ` --config-locations ` ，不同阶段的 ` --exec ` 等等 

  * **插件** ：可以从外部文件加载提取器和后处理器。详见  插件  了解详情 

  * **自动更新程序** ：可以使用 ` yt-dlp -U ` 进行更新，如果需要可以使用 ` --update-to ` 进行降级 

  * **每夜构建版本** ：  自动化每夜构建版本  可以使用 ` --update-to nightly ` 使用 




查看 [ 更新日志 ](Changelog.md) 或 [ 提交记录 ](https://github.com/yt-dlp/yt-dlp/commits) 获取完整的变更列表 

带有 ***** 标记的功能已经被回溯到youtube-dl 

###  默认行为的差异 

yt-dlp的一些默认选项与youtube-dl和youtube-dlc不同： 

  * yt-dlp仅支持  Python 3.7+  ，并且 _可能_ 会移除对更多版本的支持，因为它们 [ 已经过时 ](https://devguide.python.org/versions/#python-release-cycle) ；而 [ youtube-dl仍然支持Python 2.6+和3.2+ ](https://github.com/ytdl-org/youtube-dl/issues/30568#issue-1118238743)
  * 选项 ` --auto-number ` （ ` -A ` ）， ` --title ` （ ` -t ` ）和 ` --literal ` （ ` -l ` ）不再起作用。详见  已移除的选项 
  * 不再支持 ` avconv ` 作为 ` ffmpeg ` 的替代方案 
  * yt-dlp将配置文件存储在与youtube-dl略有不同的位置。详见  配置  以获取正确位置的列表 
  * 默认的  输出模板  是 ` %(title)s [%(id)s].%(ext)s ` 。这个更改没有真正的原因。这个更改是在yt-dlp公开之前进行的，现在没有计划改回 ` %(title)s-%(id)s.%(ext)s ` 。而是可以使用 ` --compat-options filename `
  * 默认的  格式排序  与youtube-dl不同，它更喜欢更高分辨率和更好的编解码器，而不是更高的比特率。您可以使用 ` --format-sort ` 选项来更改为您喜欢的任何顺序，或者使用 ` --compat-options format-sort ` 来使用youtube-dl的排序顺序 
  * 默认的格式选择器是 ` bv*+ba/b ` 。这意味着如果找到了一个比最佳的仅视频格式更好的视频+音频格式，将优先选择前者。使用 ` -f bv+ba/b ` 或 ` --compat-options format-spec ` 来恢复默认设置 
  * 与youtube-dlc不同，yt-dlp默认情况下不允许将多个音频/视频流合并为一个文件（因为这与使用 ` -f bv*+ba ` 冲突）。如果需要，必须使用 ` --audio-multistreams ` 和 ` --video-multistreams ` 启用此功能。您还可以使用 ` --compat-options multistreams ` 启用两者 
  * 默认情况下启用 ` --no-abort-on-error ` 。使用 ` --abort-on-error ` 或 ` --compat-options abort-on-error ` 来在出现错误时中止 
  * 在编写元数据文件（如缩略图、描述或infojson）时，也会为播放列表编写相同的信息（如果有）。使用 ` --no-write-playlist-metafiles ` 或 ` --compat-options no-playlist-metafiles ` 来不写入这些文件 
  * ` --add-metadata ` 附加元数据到mkv文件中，除了在使用 ` --write-info-json ` 时写入元数据。使用 ` --no-embed-info-json ` 或 ` --compat-options no-attach-info-json ` 来恢复默认设置 
  * 使用 ` --add-metadata ` 与youtube-dl相比，一些元数据被嵌入到不同的字段中。最显著的是， ` comment ` 字段包含 ` webpage_url ` ， ` synopsis ` 包含 ` description ` 。您可以使用  \--parse-metadata  来修改这个设置，或者使用 ` --compat-options embed-metadata ` 来恢复默认设置 
  * 在使用 ` --playlist-reverse ` 和 ` --playlist-items ` 等选项时， ` playlist_index ` 的行为不同。详细信息请参见 [ #302 ](https://github.com/yt-dlp/yt-dlp/issues/302) 。如果您想保留早期的行为，可以使用 ` --compat-options playlist-index `
  * ` -F ` 的输出以一种新的格式列出。使用 ` --compat-options list-formats ` 来恢复默认设置 
  * 直播聊天（如果可用）被视为字幕。使用 ` --sub-langs all,-live_chat ` 下载除了直播聊天之外的所有字幕。您还可以使用 ` --compat-options no-live-chat ` 来阻止下载任何直播聊天/弹幕 
  * YouTube频道URL下载频道的所有上传视频。要仅下载特定标签中的视频，请传递该标签的URL。如果频道没有显示请求的标签，将引发错误。此外， ` /live ` 的URL如果没有直播视频将引发错误，而不是静默下载整个频道。您可以使用 ` --compat-options no-youtube-channel-redirect ` 来恢复所有这些重定向 
  * YouTube播放列表中也列出了不可用的视频。使用 ` --compat-options no-youtube-unavailable-videos ` 来移除这些视频 
  * 从YouTube提取的上传日期是UTC时间 [ 如果可用 ](https://github.com/yt-dlp/yt-dlp/blob/89e4d86171c7b7c997c77d4714542e0383bf0db0/yt_dlp/extractor/youtube.py#L3898-L3900) 。使用 ` --compat-options no-youtube-prefer-utc-upload-date ` 来优先使用非UTC上传日期 
  * 如果使用ffmpeg作为下载器，当可能时，格式的下载和合并将在一步完成。使用 ` --compat-options no-direct-merge ` 来恢复默认设置 
  * 在mp4中嵌入缩略图时，如果可能，使用mutagen。使用 ` --compat-options embed-thumbnail-atomicparsley ` 强制使用AtomicParsley 
  * 默认情况下，从infojson中删除一些内部元数据，如文件名。使用 ` --no-clean-infojson ` 或 ` --compat-options no-clean-infojson ` 来恢复默认设置 
  * 当使用 ` --embed-subs ` 和 ` --write-subs ` 一起使用时，字幕将被写入磁盘并嵌入到媒体文件中。您可以只使用 ` --embed-subs ` 来嵌入字幕并自动删除单独的文件。有关更多信息，请参见 [ #630 (评论) ](https://github.com/yt-dlp/yt-dlp/issues/630#issuecomment-893659460) 。 ` --compat-options no-keep-subs ` 可用于恢复此操作 
  * 如果安装了 ` certifi ` ，将使用它作为SSL根证书。如果您想使用系统证书（例如自签名证书），请使用 ` --compat-options no-certifi `
  * yt-dlp对文件名中的无效字符进行的清理与youtube-dl不同/更智能。您可以使用 ` --compat-options filename-sanitization ` 来恢复到youtube-dl的行为 
  * yt-dlp尝试将外部下载器的输出解析为标准进度输出（目前已实现： [ ~~aria2c~~ ](https://github.com/yt-dlp/yt-dlp/issues/5931) ）。您可以使用 ` --compat-options no-external-downloader-progress ` 来获取下载器的原始输出 
  * yt-dlp版本在2021.09.01和2023.01.02之间应用 ` --match-filter ` 到嵌套播放列表。这是 [ 8f18ac ](https://github.com/yt-dlp/yt-dlp/commit/8f18aca8717bb0dd49054555af8d386e5eda3a88) 的意外副作用，并在 [ d7b460 ](https://github.com/yt-dlp/yt-dlp/commit/d7b460d0e5fc710950582baed2e3fc616ed98a80) 中修复。使用 ` --compat-options playlist-match-filter ` 来恢复此操作 



为了方便使用，还有一些兼容选项可用： 

  * ` --compat-options all ` ：使用所有兼容选项（请勿使用） 
  * ` --compat-options youtube-dl ` ：与 ` --compat-options all,-multistreams,-playlist-match-filter ` 相同 
  * ` --compat-options youtube-dlc ` ：与 ` --compat-options all,-no-live-chat,-no-youtube-channel-redirect,-playlist-match-filter ` 相同 
  * ` --compat-options 2021 ` ：与 ` --compat-options 2022,no-certifi,filename-sanitization,no-youtube-prefer-utc-upload-date ` 相同 
  * ` --compat-options 2022 ` ：与 ` --compat-options playlist-match-filter,no-external-downloader-progress ` 相同。使用此选项启用所有未来的兼容选项 



#  安装 

MANPAGE: BEGIN EXCLUDED SECTION 

[ ![Windows](https://img.shields.io/badge/-Windows_x64-blue.svg?style=for-the-badge&logo=windows) ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe) [ ![Unix](https://img.shields.io/badge/-Linux/BSD-red.svg?style=for-the-badge&logo=linux) ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp) [ ![MacOS](https://img.shields.io/badge/-MacOS-lightblue.svg?style=for-the-badge&logo=apple) ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos) [ ![PyPi](https://img.shields.io/badge/-PyPi-blue.svg?logo=pypi&labelColor=555555&style=for-the-badge) ](https://pypi.org/project/yt-dlp) [ ![Source Tarball](https://img.shields.io/badge/-Source_tar-green.svg?style=for-the-badge) ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.tar.gz) ![Other variants](https://img.shields.io/badge/-Other-grey.svg?style=for-the-badge) [ ![All versions](https://img.shields.io/badge/-All_Versions-lightgrey.svg?style=for-the-badge) ](https://github.com/yt-dlp/yt-dlp/releases)

MANPAGE: END EXCLUDED SECTION 

您可以使用以下方式安装yt-dlp：  二进制文件  、 [ pip ](https://pypi.org/project/yt-dlp) 或使用第三方软件包管理器。详细说明请参见 [ wiki ](https://github.com/yt-dlp/yt-dlp/wiki/Installation)

##  更新 

如果您使用的是  发行版的二进制文件  ，可以使用 ` yt-dlp -U ` 进行更新 

如果您使用的是pip安装的，只需重新运行安装程序时使用的相同命令即可 [ 安装pip ](https://github.com/yt-dlp/yt-dlp/wiki/Installation#with-pip)

对于其他第三方软件包管理器，请参考 [ wiki ](https://github.com/yt-dlp/yt-dlp/wiki/Installation#third-party-package-managers) 或查阅其文档 

目前有两个二进制发行渠道， ` stable ` 和 ` nightly ` 。 ` stable ` 是默认渠道，其中的更改已经由夜间渠道的用户测试过。 夜间渠道在每次推送到主分支后构建发布，将具有最新的修复和添加功能，但也存在更多的回归风险。它们可以在  [ 自己的仓库 ](https://github.com/yt-dlp/yt-dlp-nightly-builds/releases) 中找到。 

使用 ` --update ` / ` -U ` 时，发行版二进制文件只会更新到当前渠道。 当有新版本可用时，可以使用 ` --update-to CHANNEL ` 切换到其他渠道。 还可以使用 ` --update-to [CHANNEL@]TAG ` 升级或降级到特定渠道的标签。 

您还可以使用 ` --update-to <repository> ` ( ` <owner>/<repository> ` ) 来更新到完全不同的仓库中的渠道。但是，请注意要更新到哪个仓库，不同仓库的二进制文件没有进行验证。 

示例用法： * ` yt-dlp --update-to nightly ` 切换到 ` nightly ` 渠道并更新到最新版本 * ` yt-dlp --update-to stable@2023.02.17 ` 升级/降级到 ` stable ` 渠道的标签 ` 2023.02.17 ` * ` yt-dlp --update-to 2023.01.06 ` 升级/降级到标签 ` 2023.01.06 ` （如果当前渠道存在该标签） * ` yt-dlp --update-to example/yt-dlp@2023.03.01 ` 升级/降级到 ` example/yt-dlp ` 仓库中的发布，标签为 ` 2023.03.01 `

MANPAGE: BEGIN EXCLUDED SECTION 

##  发布文件 

####  推荐 

文件  |  描述   
---|---  
[ yt-dlp ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp) |  平台无关 [ zipimport ](https://docs.python.org/3/library/zipimport.html) 二进制文件。需要Python（推荐用于 **Linux/BSD** ）   
[ yt-dlp.exe ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe) |  Windows（Win7 SP1+）独立x64二进制文件（推荐用于 **Windows** ）   
[ yt-dlp_macos ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos) |  通用MacOS（10.15+）独立可执行文件（推荐用于 **MacOS** ）   
  
####  替代方案 

文件  |  描述   
---|---  
[ yt-dlp_x86.exe ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_x86.exe) |  Windows（Vista SP2+）独立x86（32位）二进制文件   
[ yt-dlp_min.exe ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_min.exe) |  Windows（Win7 SP1+）使用 ` py2exe ` 构建的独立x64二进制文件   
（  不推荐使用  ）   
[ yt-dlp_linux ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_linux) |  Linux独立x64二进制文件   
[ yt-dlp_linux.zip ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_linux.zip) |  未打包的Linux可执行文件（无自动更新）   
[ yt-dlp_linux_armv7l ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_linux_armv7l) |  Linux独立armv7l（32位）二进制文件   
[ yt-dlp_linux_aarch64 ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_linux_aarch64) |  Linux独立aarch64（64位）二进制文件   
[ yt-dlp_win.zip ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_win.zip) |  未打包的Windows可执行文件（无自动更新）   
[ yt-dlp_macos.zip ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos.zip) |  未打包的MacOS（10.15+）可执行文件（无自动更新）   
[ yt-dlp_macos_legacy ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos_legacy) |  MacOS（10.9+）独立x64可执行文件   
  
####  杂项 

文件  |  描述   
---|---  
[ yt-dlp.tar.gz ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.tar.gz) |  源代码压缩包   
[ SHA2-512SUMS ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/SHA2-512SUMS) |  GNU风格的SHA512校验和   
[ SHA2-512SUMS.sig ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/SHA2-512SUMS.sig) |  用于SHA512校验和的GPG签名文件   
[ SHA2-256SUMS ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/SHA2-256SUMS) |  GNU风格的SHA256校验和   
[ SHA2-256SUMS.sig ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/SHA2-256SUMS.sig) |  用于SHA256校验和的GPG签名文件   
  
可用于验证GPG签名的公钥 [ 在这里 ](https://github.com/yt-dlp/yt-dlp/blob/master/public.key) 示例用法： 
    
    
    curl -L https://github.com/yt-dlp/yt-dlp/raw/master/public.key | gpg --import
    gpg --verify SHA2-256SUMS.sig SHA2-256SUMS
    gpg --verify SHA2-512SUMS.sig SHA2-512SUMS
    

MANPAGE: END EXCLUDED SECTION 

**注意** ：manpages、shell自动补全文件等可在 [ 源代码压缩包 ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.tar.gz) 中找到。 

##  依赖项 

支持Python版本3.7+（包括CPython和PyPy）。其他版本和实现可能工作不正常。 

Python 3.5+ uses VC++14 and it is already embedded in the binary created  On windows, [Microsoft Visual C++ 2010 SP1 Redistributable Package (x86)](https://download.microsoft.com/download/1/6/5/165255E7-1014-4D0A-B094-B6A430A6BFFC/vcredist_x86.exe) is also necessary to run yt-dlp. You probably already have this, but if the executable throws an error due to missing `MSVCR100.dll` you need to install it manually. 

虽然所有其他依赖项都是可选的， ` ffmpeg ` 和 ` ffprobe ` 是强烈推荐的 

###  强烈推荐 

  * [ **ffmpeg** 和 **ffprobe** ](https://www.ffmpeg.org) \- 用于  合并单独的视频和音频文件  以及各种  后处理  任务。许可证 [ 取决于构建 ](https://www.ffmpeg.org/legal.html)

使用yt-dlp时，ffmpeg存在一些导致各种问题的错误。由于ffmpeg是如此重要的依赖项，我们提供了带有一些问题修补程序的 [ 自定义构建版本 ](https://github.com/yt-dlp/FFmpeg-Builds#ffmpeg-static-auto-builds) ，位于 [ yt-dlp/FFmpeg-Builds ](https://github.com/yt-dlp/FFmpeg-Builds) 。有关这些构建解决的具体问题的详细信息，请参阅 [ 自述文件 ](https://github.com/yt-dlp/FFmpeg-Builds#patches-applied)

**重要提示** ：您需要的是ffmpeg _二进制文件_ ，而不是同名的 **python包** [ 。 ](https://pypi.org/project/ffmpeg)




###  网络 

  * [ **certifi** ](https://github.com/certifi/python-certifi) * - 提供Mozilla的根证书包。根据 [ MPLv2 ](https://github.com/certifi/python-certifi/blob/master/LICENSE) 许可 
  * [ **brotli** ](https://github.com/google/brotli) * 或 [ **brotlicffi** ](https://github.com/python-hyper/brotlicffi) \- [ Brotli ](https://en.wikipedia.org/wiki/Brotli) 内容编码支持。两者均根据MIT许可  [ 1 ](https://github.com/google/brotli/blob/master/LICENSE) [ 2 ](https://github.com/python-hyper/brotlicffi/blob/master/LICENSE)
  * [ **websockets** ](https://github.com/aaugustin/websockets) * - 用于通过websocket下载。根据 [ BSD-3-Clause ](https://github.com/aaugustin/websockets/blob/main/LICENSE) 许可 



###  元数据 

  * [ **mutagen** ](https://github.com/quodlibet/mutagen) * - 用于某些格式中的 ` --embed-thumbnail ` 。根据 [ GPLv2+ ](https://github.com/quodlibet/mutagen/blob/master/COPYING) 许可 
  * [ **AtomicParsley** ](https://github.com/wez/atomicparsley) \- 用于 ` --embed-thumbnail ` 在 ` mp4 ` / ` m4a ` 文件中，当 ` mutagen ` / ` ffmpeg ` 无法使用时。根据 [ GPLv2+ ](https://github.com/wez/atomicparsley/blob/master/COPYING) 许可 
  * [ **xattr** ](https://github.com/xattr/xattr) , [ **pyxattr** ](https://github.com/iustin/pyxattr) 或 [ **setfattr** ](http://savannah.nongnu.org/projects/attr) \- 用于在 **Linux** 上写入 xattr 元数据 ( ` --xattr ` )。分别根据 [ MIT ](https://github.com/xattr/xattr/blob/master/LICENSE.txt) , [ LGPL2.1 ](https://github.com/iustin/pyxattr/blob/master/COPYING) 和 [ GPLv2+ ](http://git.savannah.nongnu.org/cgit/attr.git/tree/doc/COPYING) 许可 



###  杂项 

  * [ **pycryptodomex** ](https://github.com/Legrandin/pycryptodome) * - 用于解密 AES-128 HLS 流和其他各种数据。根据 [ BSD-2-Clause ](https://github.com/Legrandin/pycryptodome/blob/master/LICENSE.rst) 许可 
  * [ **phantomjs** ](https://github.com/ariya/phantomjs) \- 用于需要运行 JavaScript 的提取器。根据 [ BSD-3-Clause ](https://github.com/ariya/phantomjs/blob/master/LICENSE.BSD) 许可 
  * [ **secretstorage** ](https://github.com/mitya57/secretstorage) \- 用于 ` --cookies-from-browser ` 访问 **Gnome** 钥匙链，同时解密 **Chromium** -based 浏览器上的 cookie。根据 [ BSD-3-Clause ](https://github.com/mitya57/secretstorage/blob/master/LICENSE) 许可 
  * 任何你想要与 ` --downloader ` 一起使用的外部下载器 



###  已弃用 

  * [ **avconv** 和 **avprobe** ](https://www.libav.org) \- 现在已经被弃用，是ffmpeg的替代品。许可证 [ 取决于构建 ](https://libav.org/legal)
  * [ **sponskrub** ](https://github.com/faissaloo/SponSkrub) \- 用于使用现在已经被弃用的 **sponskrub选项** 。许可证为 [ GPLv3+ ](https://github.com/faissaloo/SponSkrub/blob/master/LICENCE.md)
  * [ **rtmpdump** ](http://rtmpdump.mplayerhq.hu) \- 用于下载 ` rtmp ` 流。也可以使用ffmpeg并使用 ` --downloader ffmpeg ` 。许可证为 [ GPLv2+ ](http://rtmpdump.mplayerhq.hu)
  * [ **mplayer** ](http://mplayerhq.hu/design7/info.html) 或 [ **mpv** ](https://mpv.io) \- 用于下载 ` rstp ` / ` mms ` 流。也可以使用ffmpeg并使用 ` --downloader ffmpeg ` 。许可证为 [ GPLv2+ ](https://github.com/mpv-player/mpv/blob/master/Copyright)



要使用或重新分发这些依赖项，您必须同意它们各自的许可条款。 

独立发布的二进制文件是使用Python解释器和标有 ***** 的软件包构建的。 

如果您没有进行所需任务的必要依赖项，yt-dlp将会警告您。所有当前可用的依赖项都可以在 ` --verbose ` 输出的顶部看到。 

##  编译 

###  独立的PyInstaller构建 

要构建独立的可执行文件，您必须安装Python和 ` pyinstaller ` （如果需要，还需要yt-dlp的任何  可选依赖项  ）。安装所有必要的依赖项后，只需运行 ` pyinst.py ` 。可执行文件将根据使用的Python的架构（x86/ARM，32/64位）进行构建。 
    
    
    python3 -m pip install -U pyinstaller -r requirements.txt
    python3 devscripts/make_lazy_extractors.py
    python3 pyinst.py
    

在某些系统上，您可能需要使用 ` py ` 或 ` python ` 而不是 ` python3 ` 。 

` pyinst.py ` 接受可以传递给 ` pyinstaller ` 的任何参数，例如 ` --onefile/-F ` 或 ` --onedir/-D ` ，更多信息 [ 在这里 ](https://pyinstaller.org/en/stable/usage.html#what-to-generate) 。 

**注意** ：Pyinstaller版本低于4.4 [ 不支持 ](https://github.com/pyinstaller/pyinstaller#requirements-and-tested-platforms) 从Windows商店安装的Python，而不使用虚拟环境。 

**重要** ：直接运行 ` pyinstaller ` 而 **不使用** ` pyinst.py ` 是 **不** 受官方支持的。这可能或可能不会正常工作。 

###  平台无关的二进制文件（UNIX） 

您将需要以下构建工具 ` python ` （3.7+）， ` zip ` ， ` make ` （GNU）， ` pandoc ` * 和 ` pytest ` *。 

安装完这些工具后，只需运行 ` make ` 。 

您也可以运行 ` make yt-dlp ` ，只编译二进制文件而不更新任何其他文件。（标有 ***** 的构建工具不需要） 

###  独立的Py2Exe构建（Windows） 

虽然我们提供了使用 [ py2exe ](https://www.py2exe.org) 构建的选项，但建议使用  PyInstaller  构建，因为py2exe构建 **无法包含` pycryptodomex ` / ` certifi ` ，并且需要目标计算机上的VC++14 ** 来运行。 

如果您仍然希望构建它，请安装Python和py2exe，然后只需运行 ` setup.py py2exe `
    
    
    py -m pip install -U py2exe -r requirements.txt
    py devscripts/make_lazy_extractors.py
    py setup.py py2exe
    

###  相关脚本 

  * **` devscripts/update-version.py ` ** \- 根据当前日期更新版本号。 
  * **` devscripts/set-variant.py ` ** \- 设置可执行文件的构建变体。 
  * **` devscripts/make_changelog.py ` ** \- 使用简短的提交消息创建一个markdown格式的changelog，并更新 ` CONTRIBUTORS ` 文件。 
  * **` devscripts/make_lazy_extractors.py ` ** \- 创建延迟提取器。在构建二进制文件（任何变体）之前运行此命令将提高其启动性能。如果您希望强制禁用延迟提取器加载，请设置环境变量 ` YTDLP_NO_LAZY_EXTRACTORS=1 ` 。 



注意：查看它们的 ` --help ` 以获取更多信息。 

###  分叉项目 

如果您在GitHub上分叉了该项目，您可以运行您的分叉的 [ 构建工作流程 ](.github/workflows/build.yml) ，自动构建所选版本作为构件。或者，您可以运行 [ 发布工作流程 ](.github/workflows/release.yml) 或启用 [ 每夜工作流程 ](.github/workflows/release-nightly.yml) 创建完整的（预）发布。 

#  用法和选项 

MANPAGE: BEGIN EXCLUDED SECTION 
    
    
    yt-dlp [OPTIONS] [--] URL [URL...]
    

` Ctrl+F ` 是你的好朋友 :D 

MANPAGE: END EXCLUDED SECTION Auto generated 

##  通用选项： 
    
    
    -h, --help                      Print this help text and exit
    --version                       Print program version and exit
    -U, --update                    Update this program to the latest version
    --no-update                     Do not check for updates (default)
    --update-to [CHANNEL]@[TAG]     Upgrade/downgrade to a specific version.
                                    CHANNEL can be a repository as well. CHANNEL
                                    and TAG default to "stable" and "latest"
                                    respectively if omitted; See "UPDATE" for
                                    details. Supported channels: stable, nightly
    -i, --ignore-errors             Ignore download and postprocessing errors.
                                    The download will be considered successful
                                    even if the postprocessing fails
    --no-abort-on-error             Continue with next video on download errors;
                                    e.g. to skip unavailable videos in a
                                    playlist (default)
    --abort-on-error                Abort downloading of further videos if an
                                    error occurs (Alias: --no-ignore-errors)
    --dump-user-agent               Display the current user-agent and exit
    --list-extractors               List all supported extractors and exit
    --extractor-descriptions        Output descriptions of all supported
                                    extractors and exit
    --use-extractors NAMES          Extractor names to use separated by commas.
                                    You can also use regexes, "all", "default"
                                    and "end" (end URL matching); e.g. --ies
                                    "holodex.*,end,youtube". Prefix the name
                                    with a "-" to exclude it, e.g. --ies
                                    default,-generic. Use --list-extractors for
                                    a list of extractor names. (Alias: --ies)
    --default-search PREFIX         Use this prefix for unqualified URLs. E.g.
                                    "gvsearch2:python" downloads two videos from
                                    google videos for the search term "python".
                                    Use the value "auto" to let yt-dlp guess
                                    ("auto_warning" to emit a warning when
                                    guessing). "error" just throws an error. The
                                    default value "fixup_error" repairs broken
                                    URLs, but emits an error if this is not
                                    possible instead of searching
    --ignore-config                 Don't load any more configuration files
                                    except those given by --config-locations.
                                    For backward compatibility, if this option
                                    is found inside the system configuration
                                    file, the user configuration is not loaded.
                                    (Alias: --no-config)
    --no-config-locations           Do not load any custom configuration files
                                    (default). When given inside a configuration
                                    file, ignore all previous --config-locations
                                    defined in the current file
    --config-locations PATH         Location of the main configuration file;
                                    either the path to the config or its
                                    containing directory ("-" for stdin). Can be
                                    used multiple times and inside other
                                    configuration files
    --flat-playlist                 Do not extract the videos of a playlist,
                                    only list them
    --no-flat-playlist              Fully extract the videos of a playlist
                                    (default)
    --live-from-start               Download livestreams from the start.
                                    Currently only supported for YouTube
                                    (Experimental)
    --no-live-from-start            Download livestreams from the current time
                                    (default)
    --wait-for-video MIN[-MAX]      Wait for scheduled streams to become
                                    available. Pass the minimum number of
                                    seconds (or range) to wait between retries
    --no-wait-for-video             Do not wait for scheduled streams (default)
    --mark-watched                  Mark videos watched (even with --simulate)
    --no-mark-watched               Do not mark videos watched (default)
    --color [STREAM:]POLICY         Whether to emit color codes in output,
                                    optionally prefixed by the STREAM (stdout or
                                    stderr) to apply the setting to. Can be one
                                    of "always", "auto" (default), "never", or
                                    "no_color" (use non color terminal
                                    sequences). Can be used multiple times
    --compat-options OPTS           Options that can help keep compatibility
                                    with youtube-dl or youtube-dlc
                                    configurations by reverting some of the
                                    changes made in yt-dlp. See "Differences in
                                    default behavior" for details
    --alias ALIASES OPTIONS         Create aliases for an option string. Unless
                                    an alias starts with a dash "-", it is
                                    prefixed with "--". Arguments are parsed
                                    according to the Python string formatting
                                    mini-language. E.g. --alias get-audio,-X
                                    "-S=aext:{0},abr -x --audio-format {0}"
                                    creates options "--get-audio" and "-X" that
                                    takes an argument (ARG0) and expands to
                                    "-S=aext:ARG0,abr -x --audio-format ARG0".
                                    All defined aliases are listed in the --help
                                    output. Alias options can trigger more
                                    aliases; so be careful tocompat-options OPTS           Options that can help keep compatibility
                                    with youtube-dl or youtube-dlc
                                    configurations by reverting some of the
                                    changes made in yt-dlp. See "Differences in
                                    default behavior" for details
    --alias ALIASES OPTIONS         Create aliases for an option string. Unless
                                    an alias starts with a dash "-", it is
                                    prefixed with "--". Arguments are parsed
                                    according to the Python string formatting
                                    mini-language. E.g. --alias get-audio,-X
                                    "-S=aext:{0},abr -x --audio-format {0}"
                                    creates options "--get-audio" and "-X" that
                                    takes an argument (ARG0) and expands to
                                    "-S=aext:ARG0,abr -x --audio-format ARG0".
                                    All defined aliases are listed in the --help
                                    output. Alias options can trigger more
                                    aliases; so be careful to avoid defining
                                    recursive options. As a safety measure, each
                                    alias may be triggered a maximum of 100
                                    times. This option can be used multiple times
    

##  网络选项： 
    
    
    --proxy URL                     使用指定的HTTP/HTTPS/SOCKS代理。要启用SOCKS代理，请指定正确的方案，
                                    例如 socks5://user:pass@127.0.0.1:1080/。
                                    传入一个空字符串 (--proxy "") 进行直接连接
    --socket-timeout SECONDS        在放弃之前等待的时间，以秒为单位
    --source-address IP             绑定到的客户端IP地址
    -4, --force-ipv4                所有连接都通过IPv4进行
    -6, --force-ipv6                所有连接都通过IPv6进行
    --enable-file-urls              启用 file:// URLs。出于安全原因，默认情况下禁用此功能。
    

##  地理限制： 
    
    
    --geo-verification-proxy URL    使用此代理验证某些地理限制网站的IP地址。实际下载时使用 --proxy 指定的默认代理（如果选项不存在，则不使用代理）
    --xff VALUE                     如何伪造 X-Forwarded-For HTTP 头以尝试绕过地理限制。可以是 "default"（仅在已知有用时），"never"，一个 CIDR 表示的 IP 块，或者一个两字母的 ISO 3166-2 国家代码
    

##  视频选择： 
    
    
    -I, --playlist-items ITEM_SPEC  逗号分隔的项目的播放列表索引
                                    要下载。您可以使用“[START]:[STOP][:STEP]”指定范围。为了向后
                                    兼容，也支持START-STOP。
                                    使用负索引从右边计数
                                    和负STEP以相反的顺序下载
                                    例如，“-I 1:3,7,-5::2”用于
                                    大小为15的播放列表将下载项目
                                    在索引1,2,3,7,11,13,15处
    --min-filesize SIZE             如果文件大小小于
                                    SIZE，则中止下载，例如50k或44.6M
    --max-filesize SIZE             如果文件大小大于
                                    SIZE，则中止下载，例如50k或44.6M
    --date DATE                     仅下载在此日期上传的视频。
                                    日期可以是“YYYYMMDD”或格式为
                                    [now|today|yesterday][-N[day|week|month|year]]。
                                    例如，“--date today-2weeks”仅下载
                                    两周前同一天上传的视频
    --datebefore DATE               仅下载在此日期之前或上传的视频。接受的日期格式与--date相同
    --dateafter DATE                仅下载在此日期之后或上传的视频。接受的日期格式与--date相同
    --match-filters FILTER          通用视频过滤器。可以使用“OUTPUT TEMPLATE”字段与数字或
                                    字符串进行比较，使用“Filtering Formats”中定义的运算符。
                                    如果字段存在，也可以简单地指定要匹配的字段，使用“!field”检查字段
                                    是否不存在，并使用“&”检查多个条件。如果多次使用，
                                    如果满足至少一个条件，则过滤器匹配。例如，--match-filter
                                    !is_live --match-filter "like_count>?100 &
                                    description~='(?i)\bcats \& dogs\b'"仅匹配
                                    不是直播的视频或那些
                                    具有超过100个赞（或赞字段不可用）并且还具有
                                    包含短语“cats &
                                    dogs”的描述（不区分大小写）。使用“--match-filter -”来
                                    交互式地询问是否下载每个
                                    视频
    --no-match-filters              不使用任何--match-filter（默认）
    --break-match-filters FILTER    与“--match-filters”相同，但在拒绝视频时停止
                                    下载过程
    --no-break-match-filters        不使用任何--break-match-filters（默认）
    --no-playlist                   如果URL引用
                                    视频和播放列表，则仅下载视频
    --yes-playlist                  如果URL引用
                                    视频和播放列表，则下载播放列表
    --age-limit YEARS               仅下载适合给定年龄的视频
    --download-archive FILE         仅下载未列在
                                    存档文件中的视频。将所有的ID
                                    下载的视频
    --no-download-archive           不使用存档文件（默认）
    --max-downloads NUMBER          下载NUMBER个文件后中止
    --break-on-existing             遇到时停止下载过程
                                    存档中存在的文件
    --break-per-input               改变--max-downloads，--break-on-existing，
                                    --break-match-filter和autonumber以
                                    每个输入URL重置
    --no-break-per-input            --break-on-existing和类似选项
                                    终止整个下载队列
    --skip-playlist-after-errors N  允许的失败次数，直到剩下的
                                    播放列表被跳过
    

##  下载选项： 
    
    
    -N, --concurrent-fragments N    Number of fragments of a dash/hlsnative
                                    video that should be downloaded concurrently
                                    (default is 1)
    -r, --limit-rate RATE           Maximum download rate in bytes per second,
                                    e.g. 50K or 4.2M
    --throttled-rate RATE           Minimum download rate in bytes per second
                                    below which throttling is assumed and the
                                    video data is re-extracted, e.g. 100K
    -R, --retries RETRIES           Number of retries (default is 10), or
                                    "infinite"
    --file-access-retries RETRIES   Number of times to retry on file access
                                    error (default is 3), or "infinite"
    --fragment-retries RETRIES      Number of retries for a fragment (default is
                                    10), or "infinite" (DASH, hlsnative and ISM)
    --retry-sleep [TYPE:]EXPR       Time to sleep between retries in seconds
                                    (optionally) prefixed by the type of retry
                                    (http (default), fragment, file_access,
                                    extractor) to apply the sleep to. EXPR can
                                    be a number, linear=START[:END[:STEP=1]] or
                                    exp=START[:END[:BASE=2]]. This option can be
                                    used multiple times to set the sleep for the
                                    different retry types, e.g. --retry-sleep
                                    linear=1::2 --retry-sleep fragment:exp=1:20
    --skip-unavailable-fragments    Skip unavailable fragments for DASH,
                                    hlsnative and ISM downloads (default)
                                    (Alias: --no-abort-on-unavailable-fragments)
    --abort-on-unavailable-fragments
                                    Abort download if a fragment is unavailable
                                    (Alias: --no-skip-unavailable-fragments)
    --keep-fragments                Keep downloaded fragments on disk after
                                    downloading is finished
    --no-keep-fragments             Delete downloaded fragments after
                                    downloading is finished (default)
    --buffer-size SIZE              Size of download buffer, e.g. 1024 or 16K
                                    (default is 1024)
    --resize-buffer                 The buffer size is automatically resized
                                    from an initial value of --buffer-size
                                    (default)
    --no-resize-buffer              Do not automatically adjust the buffer size
    --http-chunk-size SIZE          Size of a chunk for chunk-based HTTP
                                    downloading, e.g. 10485760 or 10M (default
                                    is disabled). May be useful for bypassing
                                    bandwidth throttling imposed by a webserver
                                    (experimental)
    --playlist-random               Download playlist videos in random order
    --lazy-playlist                 Process entries in the playlist as they are
                                    received. This disables n_entries,
                                    --playlist-random and --playlist-reverse
    --no-lazy-playlist              Process videos in the playlist only after
                                    the entire playlist is parsed (default)
    --xattr-set-filesize            Set file xattribute ytdl.filesize with
                                    expected file size
    --hls-use-mpegts                Use the mpegts container for HLS videos;
                                    allowing some players to play the video
                                    while downloading, and reducing the chance
                                    of file corruption if download is
                                    interrupted. This is enabled by default for
                                    live streams
    --no-hls-use-mpegts             Do not use the mpegts container for HLS
                                    videos. This is default when not downloading
                                    live streams
    --download-sections REGEX       Download only chapters that match the
                                    regular expression. A "*" prefix denotes
                                    time-range instead of chapter. Negative
                                    timestamps are calculated from the end.
                                    "*from-url" can be used to download between
                                    the "start_time" and "end_time" extracted
                                    from the URL. Needs ffmpeg. This option can
                                    be used multiple times to download multiple
                                    sections, e.g. --download-sections
                                    "*10:15-inf" --download-sections "intro"
    --downloader [PROTO:]NAME       Name or path of the external downloader to
                                    use (optionally) prefixed by the protocols
                                    (http, ftp, m3u8, dash, rstp, rtmp, mms) to
                                    use it for. Currently supports native,
                                    aria2c, avconv, axel, curl, ffmpeg, httpie,
                                    wget. You can use this option multiple times
                                    to set different downloaders for different
                                    protocols. E.g. --downloader aria2c
                                    --downloader "dash,m3u8:native" will use
                                    aria2c for http/ftp downloads, and the
                                    native downloader for dash/m3u8 downloads
                                    (Alias: --external-downloader)
    --downloader-args NAME:ARGS     Give to download multiple
                                    sections, e.g. --download-sections
                                    "*10:15-inf" --download-sections "intro"
    --downloader [PROTO:]NAME       Name or path of the external downloader to
                                    use (optionally) prefixed by the protocols
                                    (http, ftp, m3u8, dash, rstp, rtmp, mms) to
                                    use it for. Currently supports native,
                                    aria2c, avconv, axel, curl, ffmpeg, httpie,
                                    wget. You can use this option multiple times
                                    to set different downloaders for different
                                    protocols. E.g. --downloader aria2c
                                    --downloader "dash,m3u8:native" will use
                                    aria2c for http/ftp downloads, and the
                                    native downloader for dash/m3u8 downloads
                                    (Alias: --external-downloader)
    --downloader-args NAME:ARGS     Give these arguments to the external
                                    downloader. Specify the downloader name and
                                    the arguments separated by a colon ":". For
                                    ffmpeg, arguments can be passed to different
                                    positions using the same syntax as
                                    --postprocessor-args. You can use this
                                    option multiple times to give different
                                    arguments to different downloaders (Alias:
                                    --external-downloader-args)
    

##  文件系统选项： 
    
    
    -a, --batch-file FILE           File containing URLs to download ("-" for
                                    stdin), one URL per line. Lines starting
                                    with "#", ";" or "]" are considered as
                                    comments and ignored
    --no-batch-file                 Do not read URLs from batch file (default)
    -P, --paths [TYPES:]PATH        The paths where the files should be
                                    downloaded. Specify the type of file and the
                                    path separated by a colon ":". All the same
                                    TYPES as --output are supported.
                                    Additionally, you can also provide "home"
                                    (default) and "temp" paths. All intermediary
                                    files are first downloaded to the temp path
                                    and then the final files are moved over to
                                    the home path after download is finished.
                                    This option is ignored if --output is an
                                    absolute path
    -o, --output [TYPES:]TEMPLATE   Output filename template; see "OUTPUT
                                    TEMPLATE" for details
    --output-na-placeholder TEXT    Placeholder for unavailable fields in
                                    "OUTPUT TEMPLATE" (default: "NA")
    --restrict-filenames            Restrict filenames to only ASCII characters,
                                    and avoid "&" and spaces in filenames
    --no-restrict-filenames         Allow Unicode characters, "&" and spaces in
                                    filenames (default)
    --windows-filenames             Force filenames to be Windows-compatible
    --no-windows-filenames          Make filenames Windows-compatible only if
                                    using Windows (default)
    --trim-filenames LENGTH         Limit the filename length (excluding
                                    extension) to the specified number of
                                    characters
    -w, --no-overwrites             Do not overwrite any files
    --force-overwrites              Overwrite all video and metadata files. This
                                    option includes --no-continue
    --no-force-overwrites           Do not overwrite the video, but overwrite
                                    related files (default)
    -c, --continue                  Resume partially downloaded files/fragments
                                    (default)
    --no-continue                   Do not resume partially downloaded
                                    fragments. If the file is not fragmented,
                                    restart download of the entire file
    --part                          Use .part files instead of writing directly
                                    into output file (default)
    --no-part                       Do not use .part files - write directly into
                                    output file
    --mtime                         Use the Last-modified header to set the file
                                    modification time (default)
    --no-mtime                      Do not use the Last-modified header to set
                                    the file modification time
    --write-description             Write video description to a .description file
    --no-write-description          Do not write video description (default)
    --write-info-json               Write video metadata to a .info.json file
                                    (this may contain personal information)
    --no-write-info-json            Do not write video metadata (default)
    --write-playlist-metafiles      Write playlist metadata in addition to the
                                    video metadata when using --write-info-json,
                                    --write-description etc. (default)
    --no-write-playlist-metafiles   Do not write playlist metadata when using
                                    --write-info-json, --write-description etc.
    --clean-info-json               Remove some internal metadata such as
                                    filenames from the infojson (default)
    --no-clean-info-json            Write all fields to the infojson
    --write-comments                Retrieve video comments to be placed in the
                                    infojson. The comments are fetched even
                                    without this option if the extraction is
                                    known to be quick (Alias: --get-comments)
    --no-write-comments             Do not retrieve video comments unless the
                                    extraction is known to be quick (Alias:
                                    --no-get-comments)
    --load-info-json FILE           JSON file containing the video information
                                    (created with the "--write-info-json" option)
    --cookies FILE                  Netscape formatted file to read cookies from
                                    and dump cookie jar in
    --no-cookies                    Do not read/dump cookies from/to file
                                    (default)
    --cookies-from-browser BROWSER[+KEYRING][:PROFILE][::CONTAINER]
                                    The name of the browser to load cookies
                                    from. Currently supported browsers are:
                                    brave, chrome, chromium, edge, firefox,
                                    opera, safari, vivaldi. Optionally, the
                                    KEYRING used for decrypting Chromium cookies
                                    on Linux, the name/path of the PROFILE to
                                    load cookies from, and the CONTAINER name
                                    (if Firefox) ("none" for no container) can
                                    be given with their respective seperators.
                                    By default, all containers of the most
                                    recently accessed profile are used.
                                    Currently supported keyrings are: basictext,
                                    gnomekeyring, kwallet, kwallet5, kwallet6
    --no-cookies-from-browser       Do not load cookies from browser (default)
    --cache-dir DIR                 Location in the filesystem where yt-dlp can
                                    store some downloaded information (such as
                                    client ids and signatures) permanently. By
                                    default ${XDG_CACHE_HOME}/yt-dlp
    -- to load cookies
                                    from. Currently supported browsers are:
                                    brave, chrome, chromium, edge, firefox,
                                    opera, safari, vivaldi. Optionally, the
                                    KEYRING used for decrypting Chromium cookies
                                    on Linux, the name/path of the PROFILE to
                                    load cookies from, and the CONTAINER name
                                    (if Firefox) ("none" for no container) can
                                    be given with their respective seperators.
                                    By default, all containers of the most
                                    recently accessed profile are used.
                                    Currently supported keyrings are: basictext,
                                    gnomekeyring, kwallet, kwallet5, kwallet6
    --no-cookies-from-browser       Do not load cookies from browser (default)
    --cache-dir DIR                 Location in the filesystem where yt-dlp can
                                    store some downloaded information (such as
                                    client ids and signatures) permanently. By
                                    default ${XDG_CACHE_HOME}/yt-dlp
    --no-cache-dir                  Disable filesystem caching
    --rm-cache-dir                  Delete all filesystem cache files
    

##  缩略图选项： 
    
    
    --write-thumbnail               将缩略图写入磁盘
    --no-write-thumbnail            不将缩略图写入磁盘（默认）
    --write-all-thumbnails          将所有缩略图格式写入磁盘
    --list-thumbnails               列出每个视频的可用缩略图。
                                    除非使用--no-simulate，否则模拟
    

##  互联网快捷方式选项： 
    
    
    --write-link                    根据当前平台写入互联网快捷方式文件（.url、.webloc或.desktop）。URL可能会被操作系统缓存
    --write-url-link                写入.url Windows互联网快捷方式。操作系统根据文件路径缓存URL
    --write-webloc-link             写入.webloc macOS互联网快捷方式
    --write-desktop-link            写入.desktop Linux互联网快捷方式
    

##  详细和模拟选项： 
    
    
    -q, --quiet                     激活静默模式。如果与--verbose一起使用，将日志打印到stderr
    --no-quiet                      取消静默模式。（默认）
    --no-warnings                   忽略警告
    -s, --simulate                  不下载视频，也不将任何内容写入磁盘
    --no-simulate                   即使使用打印/列出选项，也下载视频
    --ignore-no-formats-error       忽略“没有视频格式”错误。即使视频实际上不可下载，也可用于提取元数据
                                    （实验性）
    --no-ignore-no-formats-error    当找不到可下载的视频格式时抛出错误（默认）
    --skip-download                 不下载视频，但写入所有相关文件（别名：--no-download）
    -O, --print [WHEN:]TEMPLATE     要打印到屏幕的字段名称或输出模板，可选地以when为前缀打印，用冒号分隔。支持的
                                    "WHEN"的值与--use-postprocessor相同（默认：video）。
                                    意味着--quiet。除非使用--no-simulate或后续阶段的WHEN，否则意味着--simulate。
                                    此选项可以多次使用
    --print-to-file [WHEN:]TEMPLATE FILE
                                    将给定的模板追加到文件中。WHEN和TEMPLATE的值与--print相同。FILE使用与输出模板相同的语法。
                                    此选项可以多次使用
    -j, --dump-json                 静默模式，但为每个视频打印JSON信息。除非使用--no-simulate，否则模拟。
                                    有关可用键的描述，请参见“输出模板”
    -J, --dump-single-json          静默模式，但为每个传递的URL或infojson打印JSON信息。除非使用--no-simulate，否则模拟。
                                    如果URL引用播放列表，则整个播放列表信息将以单行形式转储
    --force-write-archive           强制写入下载存档条目，只要没有错误发生，即使使用-s或其他模拟选项（别名：
                                    --force-download-archive）
    --newline                       将进度条输出为新行
    --no-progress                   不打印进度条
    --progress                      显示进度条，即使在静默模式下也是如此
    --console-title                 在控制台标题栏中显示进度
    --progress-template [TYPES:]TEMPLATE
                                    进度输出的模板，可选地以“download:”（默认）、“download-title:”（控制台标题）、
                                    “postprocess:”或“postprocess-title:”为前缀。视频的字段可以在“info”键下访问，
                                    进度属性可以在“progress”键下访问。例如--console-title --progress-template
                                    “download-title:%(info.id)s-%(progress.eta)s”
    -v, --verbose                   打印各种调试信息
    --dump-pages                    打印以base64编码的下载页面以调试问题（非常详细）
    --write-pages                   将下载的中间页面写入当前目录中的文件以调试问题
    --print-traffic                 显示发送和接收的HTTP流量
    

##  解决方法： 
    
    
    --encoding ENCODING             强制指定编码（实验性）
    --legacy-server-connect         显式允许与不支持RFC 5746安全重协商的服务器进行HTTPS连接
    --no-check-certificates         禁止HTTPS证书验证
    --prefer-insecure               使用未加密的连接检索有关视频的信息（目前仅支持YouTube）
    --add-headers FIELD:VALUE       指定自定义的HTTP头和其值，用冒号“:”分隔。可以多次使用此选项
    --bidi-workaround               解决不支持双向文本支持的终端问题。需要在PATH中有bidiv或fribidi可执行文件
    --sleep-requests SECONDS        在数据提取期间每个请求之间休眠的秒数
    --sleep-interval SECONDS        在每次下载之前休眠的秒数。与--max-sleep-interval一起使用时，这是最小休眠时间（别名：--min-sleep-interval）
    --max-sleep-interval SECONDS    最大休眠秒数。只能与--min-sleep-interval一起使用
    --sleep-subtitles SECONDS       在每个字幕下载之前休眠的秒数
    

##  视频格式选项： 
    
    
    -f, --format FORMAT             视频格式代码，请参阅“格式选择”以获取更多详细信息
    -S, --format-sort SORTORDER     按给定的字段对格式进行排序，请参阅“排序格式”以获取更多详细信息
    --format-sort-force             强制用户指定的排序顺序优先于所有字段，请参阅“排序格式”以获取更多详细信息（别名：--S-force）
    --no-format-sort-force          某些字段优先于用户指定的排序顺序（默认）
    --video-multistreams            允许将多个视频流合并为单个文件
    --no-video-multistreams         每个输出文件只下载一个视频流（默认）
    --audio-multistreams            允许将多个音频流合并为单个文件
    --no-audio-multistreams         每个输出文件只下载一个音频流（默认）
    --prefer-free-formats           优先选择具有免费容器的视频格式，而不考虑质量相同的非免费容器。与“-S ext”一起使用，严格优先选择免费容器
    --no-prefer-free-formats        不对免费容器给予任何特殊偏好（默认）
    --check-formats                 确保仅从实际可下载的格式中选择格式
    --check-all-formats             检查所有格式是否实际可下载
    --no-check-formats              不检查格式是否实际可下载
    -F, --list-formats              列出每个视频的可用格式。除非使用--no-simulate，否则模拟
    --merge-output-format FORMAT    合并格式时可以使用的容器，用“/”分隔，例如“mp4/mkv”。如果不需要合并，则忽略（当前支持：avi、flv、mkv、mov、mp4、webm）
    

##  字幕选项： 
    
    
    --write-subs                    写入字幕文件
    --no-write-subs                 不写入字幕文件（默认）
    --write-auto-subs               写入自动生成的字幕文件（别名：--write-automatic-subs）
    --no-write-auto-subs            不写入自动生成的字幕（默认）（别名：--no-write-automatic-subs）
    --list-subs                     列出每个视频的可用字幕。除非使用--no-simulate，否则模拟
    --sub-format FORMAT             字幕格式；接受格式偏好，例如“srt”或“ass/srt/best”
    --sub-langs LANGS               要下载的字幕的语言（可以是正则表达式）或用逗号分隔的“all”，例如--sub-langs“en.*,ja”。您可以在语言代码前加“-”以将其排除在请求的语言之外，例如--sub-langs all,-live_chat。使用--list-subs获取可用语言标签的列表
    

##  身份验证选项： 
    
    
    -u，--用户名USERNAME         使用此帐户ID登录
    -p，--密码PASSWORD         帐户密码。如果不提供此选项，yt-dlp将会交互式询问
    -2，--双因素TWOFACTOR       双因素身份验证代码
    -n，--netrc                     使用.netrc身份验证数据
    --netrc-location PATH           .netrc身份验证数据的位置；可以是路径或其所在的目录。
                                    默认为~/.netrc
    --netrc-cmd NETRC_CMD           执行的命令以获取提取器的凭据。
    --video-password PASSWORD       视频密码（vimeo，youku）
    --ap-mso MSO                    Adobe Pass多系统运营商（电视提供商）标识符，使用--ap-list-mso获取
                                    可用的MSO列表
    --ap-username USERNAME          多系统运营商帐户登录
    --ap-password PASSWORD          多系统运营商帐户密码。如果不提供此选项，yt-dlp将会交互式询问
    --ap-list-mso                   列出所有支持的多系统运营商
    --client-certificate CERTFILE   PEM格式的客户端证书文件路径。可以包含私钥
    --client-certificate-key KEYFILE
                                    客户端证书的私钥文件路径
    --client-certificate-password PASSWORD
                                    客户端证书私钥的密码，如果已加密。如果未提供，并且密钥
                                    已加密，yt-dlp将会交互式询问
    

##  后处理选项： 
    
    
    -x, --extract-audio             Convert video files to audio-only files
                                    (requires ffmpeg and ffprobe)
    --audio-format FORMAT           Format to convert the audio to when -x is
                                    used. (currently supported: best (default),
                                    aac, alac, flac, m4a, mp3, opus, vorbis,
                                    wav). You can specify multiple rules using
                                    similar syntax as --remux-video
    --audio-quality QUALITY         Specify ffmpeg audio quality to use when
                                    converting the audio with -x. Insert a value
                                    between 0 (best) and 10 (worst) for VBR or a
                                    specific bitrate like 128K (default 5)
    --remux-video FORMAT            Remux the video into another container if
                                    necessary (currently supported: avi, flv,
                                    gif, mkv, mov, mp4, webm, aac, aiff, alac,
                                    flac, m4a, mka, mp3, ogg, opus, vorbis,
                                    wav). If target container does not support
                                    the video/audio codec, remuxing will fail.
                                    You can specify multiple rules; e.g.
                                    "aac>m4a/mov>mp4/mkv" will remux aac to m4a,
                                    mov to mp4 and anything else to mkv
    --recode-video FORMAT           Re-encode the video into another format if
                                    necessary. The syntax and supported formats
                                    are the same as --remux-video
    --postprocessor-args NAME:ARGS  Give these arguments to the postprocessors.
                                    Specify the postprocessor/executable name
                                    and the arguments separated by a colon ":"
                                    to give the argument to the specified
                                    postprocessor/executable. Supported PP are:
                                    Merger, ModifyChapters, SplitChapters,
                                    ExtractAudio, VideoRemuxer, VideoConvertor,
                                    Metadata, EmbedSubtitle, EmbedThumbnail,
                                    SubtitlesConvertor, ThumbnailsConvertor,
                                    FixupStretched, FixupM4a, FixupM3u8,
                                    FixupTimestamp and FixupDuration. The
                                    supported executables are: AtomicParsley,
                                    FFmpeg and FFprobe. You can also specify
                                    "PP+EXE:ARGS" to give the arguments to the
                                    specified executable only when being used by
                                    the specified postprocessor. Additionally,
                                    for ffmpeg/ffprobe, "_i"/"_o" can be
                                    appended to the prefix optionally followed
                                    by a number to pass the argument before the
                                    specified input/output file, e.g. --ppa
                                    "Merger+ffmpeg_i1:-v quiet". You can use
                                    this option multiple times to give different
                                    arguments to different postprocessors.
                                    (Alias: --ppa)
    -k, --keep-video                Keep the intermediate video file on disk
                                    after post-processing
    --no-keep-video                 Delete the intermediate video file after
                                    post-processing (default)
    --post-overwrites               Overwrite post-processed files (default)
    --no-post-overwrites            Do not overwrite post-processed files
    --embed-subs                    Embed subtitles in the video (only for mp4,
                                    webm and mkv videos)
    --no-embed-subs                 Do not embed subtitles (default)
    --embed-thumbnail               Embed thumbnail in the video as cover art
    --no-embed-thumbnail            Do not embed thumbnail (default)
    --embed-metadata                Embed metadata to the video file. Also
                                    embeds chapters/infojson if present unless
                                    --no-embed-chapters/--no-embed-info-json are
                                    used (Alias: --add-metadata)
    --no-embed-metadata             Do not add metadata to file (default)
                                    (Alias: --no-add-metadata)
    --embed-chapters                Add chapter markers to the video file
                                    (Alias: --add-chapters)
    --no-embed-chapters             Do not add chapter markers (default) (Alias:
                                    --no-add-chapters)
    --embed-info-json               Embed the infojson as an attachment to
                                    mkv/mka video files
    --no-embed-info-json            Do not embed the infojson as an attachment
                                    to the video file
    --parse-metadata [WHEN:]FROM:TO
                                    Parse additional metadata like title/artist
                                    from other fields; see "MODIFYING METADATA"
                                    for details. Supported values of "WHEN" are
                                    the same as that of --use-postprocessor
                                    (default: pre_process)
    --replace-in-metadata [WHEN:]FIELDS REGEX REPLACE
                                    Replace text in a metadata field using the
                                    given regex. This option can be used
                                    multiple times. Supported values of "WHEN"
                                    are the same as that of --use-postprocessor
                                    (default: pre_process)
    --xattrs                        Write metadataembed-chapters             Do not add chapter markers (default) (Alias:
                                    --no-add-chapters)
    --embed-info-json               Embed the infojson as an attachment to
                                    mkv/mka video files
    --no-embed-info-json            Do not embed the infojson as an attachment
                                    to the video file
    --parse-metadata [WHEN:]FROM:TO
                                    Parse additional metadata like title/artist
                                    from other fields; see "MODIFYING METADATA"
                                    for details. Supported values of "WHEN" are
                                    the same as that of --use-postprocessor
                                    (default: pre_process)
    --replace-in-metadata [WHEN:]FIELDS REGEX REPLACE
                                    Replace text in a metadata field using the
                                    given regex. This option can be used
                                    multiple times. Supported values of "WHEN"
                                    are the same as that of --use-postprocessor
                                    (default: pre_process)
    --xattrs                        Write metadata to the video file's xattrs
                                    (using dublin core and xdg standards)
    --concat-playlist POLICY        Concatenate videos in a playlist. One of
                                    "never", "always", or "multi_video"
                                    (default; only when the videos form a single
                                    show). All the video files must have same
                                    codecs and number of streams to be
                                    concatable. The "pl_video:" prefix can be
                                    used with "--paths" and "--output" to set
                                    the output filename for the concatenated
                                    files. See "OUTPUT TEMPLATE" for details
    --fixup POLICY                  Automatically correct known faults of the
                                    file. One of never (do nothing), warn (only
                                    emit a warning), detect_or_warn (the
                                    default; fix file if we can, warn
                                    otherwise), force (try fixing even if file
                                    already exists)
    --ffmpeg-location PATH          Location of the ffmpeg binary; either the
                                    path to the binary or its containing directory
    --exec [WHEN:]CMD               Execute a command, optionally prefixed with
                                    when to execute it, separated by a ":".
                                    Supported values of "WHEN" are the same as
                                    that of --use-postprocessor (default:
                                    after_move). Same syntax as the output
                                    template can be used to pass any field as
                                    arguments to the command. If no fields are
                                    passed, %(filepath,_filename|)q is appended
                                    to the end of the command. This option can
                                    be used multiple times
    --no-exec                       Remove any previously defined --exec
    --convert-subs FORMAT           Convert the subtitles to another format
                                    (currently supported: ass, lrc, srt, vtt)
                                    (Alias: --convert-subtitles)
    --convert-thumbnails FORMAT     Convert the thumbnails to another format
                                    (currently supported: jpg, png, webp). You
                                    can specify multiple rules using similar
                                    syntax as --remux-video
    --split-chapters                Split video into multiple files based on
                                    internal chapters. The "chapter:" prefix can
                                    be used with "--paths" and "--output" to set
                                    the output filename for the split files. See
                                    "OUTPUT TEMPLATE" for details
    --no-split-chapters             Do not split video based on chapters (default)
    --remove-chapters REGEX         Remove chapters whose title matches the
                                    given regular expression. The syntax is the
                                    same as --download-sections. This option can
                                    be used multiple times
    --no-remove-chapters            Do not remove any chapters from the file
                                    (default)
    --force-keyframes-at-cuts       Force keyframes at cuts when
                                    downloading/splitting/removing sections.
                                    This is slow due to needing a re-encode, but
                                    the resulting video may have fewer artifacts
                                    around the cuts
    --no-force-keyframes-at-cuts    Do not force keyframes around the chapters
                                    when cutting/splitting (default)
    --use-postprocessor NAME[:ARGS]
                                    The (case sensitive) name of plugin
                                    postprocessors to be enabled, and
                                    (optionally) arguments to be passed to it,
                                    separated by a colon ":". ARGS are a
                                    semicolon ";" delimited list of NAME=VALUE.
                                    The "when" argument determines when the
                                    postprocessor is invoked. It can be one of
                                    "pre_process" (after video extraction),
                                    "after_filter" (after video passes filter),
                                    "video" (after --format; before
                                    --print/--output), "before_dl" (before each
                                    video download), "post_process" (after each
                                    video download; default), "after_move"
                                    (after moving video file to it's final
                                    locations), "after_video" (after downloading
                                    and processing all formats of a video), or
                                    "playlist" (at end of playlist)./splitting (default)
    --use-postprocessor NAME[:ARGS]
                                    The (case sensitive) name of plugin
                                    postprocessors to be enabled, and
                                    (optionally) arguments to be passed to it,
                                    separated by a colon ":". ARGS are a
                                    semicolon ";" delimited list of NAME=VALUE.
                                    The "when" argument determines when the
                                    postprocessor is invoked. It can be one of
                                    "pre_process" (after video extraction),
                                    "after_filter" (after video passes filter),
                                    "video" (after --format; before
                                    --print/--output), "before_dl" (before each
                                    video download), "post_process" (after each
                                    video download; default), "after_move"
                                    (after moving video file to it's final
                                    locations), "after_video" (after downloading
                                    and processing all formats of a video), or
                                    "playlist" (at end of playlist). This option
                                    can be used multiple times to add different
                                    postprocessors
    

##  SponsorBlock选项： 

使用 [ SponsorBlock API ](https://sponsor.ajay.app) 为下载的YouTube视频创建章节条目，或删除各种片段（赞助商、介绍等） 
    
    
    --sponsorblock-mark CATS        要为之创建章节的SponsorBlock类别，用逗号分隔。可用的类别有sponsor、intro、outro、selfpromo、preview、filler、interaction、music_offtopic、poi_highlight、chapter、all和default（=all）。您可以在类别前加"-"来排除它。有关类别的描述，请参见[1]。例如：--sponsorblock-mark all,-preview
                                    [1] https://wiki.sponsor.ajay.app/w/Segment_Categories
    --sponsorblock-remove CATS      要从视频文件中删除的SponsorBlock类别，用逗号分隔。如果一个类别在mark和remove中都存在，则remove优先。语法和可用的类别与--sponsorblock-mark相同，只是"default"指的是"all,-filler"，poi_highlight和chapter不可用
    --sponsorblock-chapter-title TEMPLATE
                                    用于由--sponsorblock-mark创建的SponsorBlock章节标题的输出模板。唯一可用的字段是start_time、end_time、category、categories、name、category_names。默认为"[SponsorBlock]: %(category_names)l"
    --no-sponsorblock               禁用--sponsorblock-mark和--sponsorblock-remove
    --sponsorblock-api URL          SponsorBlock API位置，默认为https://sponsor.ajay.app
    

##  提取器选项： 
    
    
    --extractor-retries RETRIES     已知提取器错误的重试次数（默认为3），或者"infinite"
    --allow-dynamic-mpd             处理动态DASH清单（默认）（别名：--no-ignore-dynamic-mpd）
    --ignore-dynamic-mpd            不处理动态DASH清单（别名：--no-allow-dynamic-mpd）
    --hls-split-discontinuity       在不连续点（如广告中断）处将HLS播放列表拆分为不同的格式
    --no-hls-split-discontinuity    不在不连续点（如广告中断）处将HLS播放列表拆分为不同的格式（默认）
    --extractor-args IE_KEY:ARGS    将ARGS参数传递给IE_KEY提取器。有关详细信息，请参见"EXTRACTOR ARGUMENTS"。您可以多次使用此选项为不同的提取器提供参数
    

#  配置 

您可以通过将任何支持的命令行选项放入配置文件中来配置yt-dlp。配置文件从以下位置加载： 

  1. **主要配置** ： 
    * 给定的文件为 ` --config-location `
  2. **便携式配置** ：（推荐用于便携式安装） 
    * 如果使用二进制文件， ` yt-dlp.conf ` 与二进制文件放在同一目录下 
    * 如果从源代码运行， ` yt-dlp.conf ` 在 ` yt_dlp ` 的父目录中 
  3. **主目录配置** ： 
    * ` yt-dlp.conf ` 在由 ` -P ` 给出的主目录中 
    * 如果未给出 ` -P ` ，则在当前目录中搜索 
  4. **用户配置** ： 

    * ` ${XDG_CONFIG_HOME}/yt-dlp.conf `
    * ` ${XDG_CONFIG_HOME}/yt-dlp/config ` （在Linux/macOS上推荐） 
    * ` ${XDG_CONFIG_HOME}/yt-dlp/config.txt `
    * ` ${APPDATA}/yt-dlp.conf `
    * ` ${APPDATA}/yt-dlp/config ` （在Windows上推荐） 
    * ` ${APPDATA}/yt-dlp/config.txt `
    * ` ~/yt-dlp.conf `
    * ` ~/yt-dlp.conf.txt `
    * ` ~/.yt-dlp/config `
    * ` ~/.yt-dlp/config.txt `

另请参阅：  关于环境变量的说明  1\. **系统配置** ： * ` /etc/yt-dlp.conf ` * ` /etc/yt-dlp/config ` * ` /etc/yt-dlp/config.txt `




例如，使用以下配置文件，yt-dlp将始终提取音频，不复制修改时间，使用代理，并将所有视频保存在您的主目录下的 ` YouTube ` 目录中： 
    
    
    # 以#开头的行是注释
    
    # 始终提取音频
    -x
    
    # 不复制修改时间
    --no-mtime
    
    # 使用此代理
    --proxy 127.0.0.1:3128
    
    # 将所有视频保存在您的主目录下的YouTube目录中
    -o ~/YouTube/%(title)s.%(ext)s
    

**注意** ：配置文件中的选项与常规命令行调用中使用的选项（开关）相同；因此， **不能有空格** 在 ` - ` 或 ` -- ` 之后，例如 ` -o ` 或 ` --proxy ` ，但不能是 ` - o ` 或 ` -- proxy ` 。在必要时，它们也必须像UNIX shell一样用引号引起来。 

如果您想要在特定的yt-dlp运行中禁用所有配置文件，可以使用 ` --ignore-config ` 。如果任何配置文件中存在 ` --ignore-config ` ，则不会加载其他配置。例如，在便携式配置文件中使用该选项会阻止加载主目录、用户和系统配置。此外，（为了向后兼容）如果在系统配置文件中找到 ` --ignore-config ` ，则不会加载用户配置。 

###  配置文件编码 

配置文件根据UTF BOM（如果存在）进行解码，否则使用系统区域设置的编码进行解码。 

如果您希望以不同的方式解码文件，请在文件开头添加 ` # coding: ENCODING ` （例如 ` # coding: shift-jis ` ）。之前不能有任何字符，包括空格或BOM。 

###  使用netrc进行身份验证 

您还可以为支持身份验证的提取器配置自动凭据存储（通过使用 ` --username ` 和 ` --password ` 提供登录和密码），以便不必在每次yt-dlp执行时将凭据作为命令行参数传递，并防止在shell命令历史记录中跟踪明文密码。您可以在每个提取器的基础上使用 [ ` .netrc ` 文件 ](https://stackoverflow.com/tags/.netrc/info) 来实现这一点。为此，您需要在 ` --netrc-location ` 中创建一个 ` .netrc ` 文件，并将权限限制为只读/写您自己： 
    
    
    touch ${HOME}/.netrc
    chmod a-rwx,u+rw ${HOME}/.netrc
    

然后，您可以按以下格式为提取器添加凭据，其中 _extractor_ 是小写的提取器名称： 
    
    
    machine <extractor> login <username> password <password>
    

例如： 
    
    
    machine youtube login myaccount@gmail.com password my_youtube_password
    machine twitch login my_twitch_account_name password my_twitch_password
    

要激活使用 ` .netrc ` 文件进行身份验证，您应该将 ` --netrc ` 传递给yt-dlp或将其放置在  配置文件  中。 

.netrc文件的默认位置是 ` ~ ` （见下文）。 

作为使用 ` .netrc ` 文件的替代方法，该方法的缺点是将密码保存在明文文件中，您可以配置自定义的shell命令来提供提取器的凭据。通过提供 ` --netrc-cmd ` 参数来完成此操作，它应该以netrc格式输出凭据，并在成功时返回 ` 0 ` ，其他值将被视为错误。 命令中的 ` {} ` 将被替换为提取器的名称，以便选择正确的凭据。 

例如，要使用加密的 ` .netrc ` 文件存储为 ` .authinfo.gpg `
    
    
    yt-dlp --netrc-cmd 'gpg --decrypt ~/.authinfo.gpg' https://www.youtube.com/watch?v=BaW_jenozKc
    

###  关于环境变量的注意事项 

  * 环境变量通常以UNIX上的 ` ${VARIABLE} ` / ` $VARIABLE ` 或Windows上的 ` %VARIABLE% ` 的形式指定；但在本文档中始终显示为 ` ${VARIABLE} `
  * yt-dlp还允许在Windows上使用类UNIX风格的变量作为路径选项；例如 ` --output ` 、 ` --config-location `
  * 如果未设置， ` ${XDG_CONFIG_HOME} ` 默认为 ` ~/.config ` ， ` ${XDG_CACHE_HOME} ` 默认为 ` ~/.cache `
  * 在Windows上， ` ~ ` 指向 ` ${HOME} ` （如果存在）；否则指向 ` ${USERPROFILE} ` 或 ` ${HOMEDRIVE}${HOMEPATH} `
  * 在Windows上， ` ${USERPROFILE} ` 通常指向 ` C:\Users\<user name> ` ， ` ${APPDATA} ` 指向 ` ${USERPROFILE}\AppData\Roaming `



#  输出模板 

使用 ` -o ` 选项指定输出文件名的模板，使用 ` -P ` 选项指定每种类型文件应保存到的路径。 

MANPAGE: BEGIN EXCLUDED SECTION 

**简而言之：** 将我导航到示例  . 

MANPAGE: END EXCLUDED SECTION 

` -o ` 的最简单用法是在下载单个文件时不设置任何模板参数，例如： ` yt-dlp -o funny_video.flv "https://some/video" ` （像这样硬编码文件扩展名是 **不推荐的** ，可能会破坏一些后处理）。 

但它也可以包含一些特殊序列，这些序列在下载每个视频时会被替换。这些特殊序列可以按照 [ Python字符串格式化操作 ](https://docs.python.org/3/library/stdtypes.html#printf-style-string-formatting) 进行格式化，例如： ` %(NAME)s ` 或者 ` %(NAME)05d ` 。需要澄清的是，这是一个百分号后跟括号中的名称，然后是格式化操作。 

字段名称本身（括号内的部分）也可以有一些特殊的格式化： 

  1. **对象遍历** ：可以使用点 ` . ` 分隔符遍历元数据中的字典和列表；例如 ` %(tags.0)s ` 、 ` %(subtitles.en.-1.ext)s ` 。可以使用冒号 ` : ` 进行Python切片；例如 ` %(id.3:7:-1)s ` 、 ` %(formats.:.format_id)s ` 。花括号 ` {} ` 可以用于构建只包含特定键的字典；例如 ` %(formats.:.{format_id,height})#j ` 。空字段名 ` %()s ` 表示整个infodict；例如 ` %(.{id,title})s ` 。请注意，使用此方法可用的所有字段未在下面列出。使用 ` -j ` 查看这些字段 

  2. **加法** ：可以使用 ` + ` 和 ` - ` 进行数字字段的加法和减法运算；例如 ` %(playlist_index+10)03d ` 、 ` %(n_entries+1-playlist_index)d `

  3. **日期/时间格式化** ：可以使用 [ strftime格式化 ](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes) 将日期/时间字段格式化，通过使用 ` > ` 将其与字段名分隔开；例如 ` %(duration>%H-%M-%S)s ` 、 ` %(upload_date>%Y-%m-%d)s ` 、 ` %(epoch-3600>%H-%M-%S)s `

  4. **替代字段** ：可以使用逗号 ` , ` 分隔指定替代字段；例如 ` %(release_date>%Y,upload_date>%Y|Unknown)s `

  5. **替换值** ：可以使用 ` & ` 分隔符指定替换值，根据 [ ` str.format ` 迷你语言 ](https://docs.python.org/3/library/string.html#format-specification-mini-language) 。如果字段 _不是_ 空的，将使用此替换值而不是实际字段内容。这是在考虑替代字段之后进行的；因此，如果 _任何_ 替代字段 _不是_ 空的，将使用替换值。例如 ` %(chapters&has chapters|no chapters)s ` 、 ` %(title&TITLE={:>20}|NO TITLE)s `

  6. **默认值** ：可以使用竖线 ` | ` 分隔符指定字段为空时的字面默认值。这将覆盖 ` --output-na-placeholder ` 。例如 ` %(uploader|Unknown)s `

  7. **更多转换** ：除了常规的格式类型 ` diouxXeEfFgGcrs ` ，yt-dlp还支持转换为 ` B ` = **B** ytes， ` j ` = **j** son（标志 ` # ` 用于漂亮打印， ` + ` 用于Unicode）， ` h ` = HTML转义， ` l ` = 逗号分隔的 **l** ist（标志 ` # ` 用于换行分隔）， ` q ` = 终端上引用的字符串（标志 ` # ` 用于将列表拆分为不同的参数）， ` D ` = 添加 **D** ecimal后缀（例如10M）（标志 ` # ` 使用1024作为因子），以及 ` S ` = **S** 作为文件名进行清理（标志 ` # ` 限制） 

  8. **Unicode规范化** ：格式类型 ` U ` 可用于NFC [ Unicode规范化 ](https://docs.python.org/3/library/unicodedata.html#unicodedata.normalize) 。备用形式标志（ ` # ` ）将规范化更改为NFD，转换标志 ` + ` 可用于NFKC/NFKD兼容等价规范化。例如 ` %(title)+.100U ` 是NFKC 




总结一下，字段的一般语法如下： 
    
    
    %(name[.keys][addition][>strf][,alternate][&replacement][|default])[flags][width][.precision][length]type
    

此外，您可以通过指定文件类型后跟由冒号分隔的模板，为各种元数据文件单独设置不同的输出模板 ` : ` 。支持的不同文件类型有 ` subtitle ` 、 ` thumbnail ` 、 ` description ` 、 ` annotation ` (已弃用)、 ` infojson ` 、 ` link ` 、 ` pl_thumbnail ` 、 ` pl_description ` 、 ` pl_infojson ` 、 ` chapter ` 、 ` pl_video ` 。例如， ` -o "%(title)s.%(ext)s" -o "thumbnail:%(title)s\%(title)s.%(ext)s" ` 将把缩略图放在与视频同名的文件夹中。如果任何模板为空，则不会写入该类型的文件。例如， ` --write-thumbnail -o "thumbnail:" ` 将仅为播放列表写入缩略图，而不会为视频写入缩略图。 

**注意** ：由于后处理（即合并等），实际输出的文件名可能会有所不同。使用 ` --print after_move:filepath ` 来获取所有后处理完成后的名称。 

可用字段为： 

  * ` id ` (字符串): 视频标识符 
  * ` title ` (字符串): 视频标题 
  * ` fulltitle ` (字符串): 忽略直播时间戳和通用标题的视频标题 
  * ` ext ` (字符串): 视频文件扩展名 
  * ` alt_title ` (字符串): 视频的第二标题 
  * ` description ` (字符串): 视频的描述 
  * ` display_id ` (字符串): 视频的替代标识符 
  * ` uploader ` (字符串): 视频上传者的全名 
  * ` license ` (字符串): 视频所属的许可证名称 
  * ` creator ` (字符串): 视频的创建者 
  * ` timestamp ` (数值): 视频可用的UNIX时间戳 
  * ` upload_date ` (字符串): 视频上传日期（UTC）（YYYYMMDD） 
  * ` release_timestamp ` (数值): 视频发布的UNIX时间戳 
  * ` release_date ` (字符串): 视频发布日期（UTC）（YYYYMMDD） 
  * ` modified_timestamp ` (数值): 视频最后修改的UNIX时间戳 
  * ` modified_date ` (字符串): 视频最后修改日期（UTC）（YYYYMMDD） 
  * ` uploader_id ` (字符串): 视频上传者的昵称或ID 
  * ` channel ` (字符串): 视频上传的频道的全名 
  * ` channel_id ` (字符串): 频道的ID 
  * ` channel_follower_count ` (数值): 频道的关注者数量 
  * ` channel_is_verified ` (布尔值): 频道在平台上是否已验证 
  * ` location ` (字符串): 视频拍摄的物理位置 
  * ` duration ` (数值): 视频的长度（秒） 
  * ` duration_string ` (字符串): 视频的长度（HH:mm:ss） 
  * ` view_count ` (数值): 在平台上观看视频的用户数量 
  * ` concurrent_view_count ` (数值): 当前正在观看视频的用户数量 
  * ` like_count ` (数值): 视频的正面评级数量 
  * ` dislike_count ` (数值): 视频的负面评级数量 
  * ` repost_count ` (数值): 视频的转发数量 
  * ` average_rating ` (数值): 用户给出的平均评级，所使用的刻度取决于网页 
  * ` comment_count ` (数值): 视频的评论数量（对于某些提取器，评论仅在最后下载，因此无法使用此字段） 
  * ` age_limit ` (数值): 视频的年龄限制（年） 
  * ` 直播状态 ` (字符串): 可选值为 "not_live"（未直播）, "is_live"（正在直播）, "is_upcoming"（即将直播）, "was_live"（曾经直播）, "post_live"（曾经直播，但VOD尚未处理） 
  * ` 是否直播 ` (布尔值): 视频是直播流还是固定长度视频 
  * ` 是否曾经直播 ` (布尔值): 视频是否曾经是直播流 
  * ` 是否允许在其他网站的嵌入播放器中播放 ` (字符串): 视频是否允许在其他网站的嵌入播放器中播放 
  * ` 可用性 ` (字符串): 视频的可用性，可选值为 "private"（私有）, "premium_only"（仅限高级用户）, "subscriber_only"（仅限订阅用户）, "needs_auth"（需要验证）, "unlisted"（未列出）或 "public"（公开） 
  * ` 开始时间 ` (数值): 视频在URL中指定的开始播放时间（以秒为单位） 
  * ` 结束时间 ` (数值): 视频在URL中指定的结束播放时间（以秒为单位） 
  * ` 提取器名称 ` (字符串): 提取器的名称 
  * ` 提取器键名 ` (字符串): 提取器的键名 
  * ` 提取信息完成的Unix时间戳 ` (数值): 提取信息完成的Unix时间戳 
  * ` 自动编号 ` (数值): 每次下载时将递增的编号，从 ` --autonumber-start ` 开始，填充前导零至5位数 
  * ` 视频自动编号 ` (数值): 每个视频将递增的编号 
  * ` 播放列表中提取的总项目数 ` (数值): 播放列表中提取的总项目数 
  * ` 包含视频的播放列表标识符 ` (字符串): 包含视频的播放列表的标识符 
  * ` 包含视频的播放列表名称 ` (字符串): 包含视频的播放列表的名称 
  * ` 播放列表 ` (字符串): ` playlist_id ` 或 ` playlist_title `
  * ` 播放列表中的总项目数 ` (数值): 播放列表中的总项目数。如果未提取整个播放列表，则可能未知 
  * ` 视频在播放列表中的索引 ` (数值): 视频在播放列表中的索引，根据最终索引填充前导零 
  * ` 视频在播放列表下载队列中的位置 ` (数值): 视频在播放列表下载队列中的位置，根据播放列表的总长度填充前导零 
  * ` 播放列表上传者的全名 ` (字符串): 播放列表上传者的全名 
  * ` 播放列表上传者的昵称或ID ` (字符串): 播放列表上传者的昵称或ID 
  * ` 视频网页的URL ` (字符串): 视频网页的URL，如果提供给yt-dlp，应该能够获得相同的结果 
  * ` 视频网页URL的基本名称 ` (字符串): 视频网页URL的基本名称 
  * ` 视频网页URL的域名 ` (字符串): 视频网页URL的域名 
  * ` 用户提供的URL（或与 ` webpage_url ` 相同的URL，用于播放列表条目） `



所有字段在  过滤格式  也可以使用 

适用于属于某个逻辑章节或部分的视频： 

  * ` chapter ` (字符串): 视频所属章节的名称或标题 
  * ` chapter_number ` (数字): 视频所属章节的编号 
  * ` chapter_id ` (字符串): 视频所属章节的ID 



适用于某个系列或节目的视频剧集： 

  * ` series ` (字符串): 视频剧集所属系列或节目的标题 
  * ` season ` (字符串): 视频剧集所属季的标题 
  * ` season_number ` (数字): 视频剧集所属季的编号 
  * ` season_id ` (字符串): 视频剧集所属季的ID 
  * ` episode ` (字符串): 视频剧集的标题 
  * ` episode_number ` (数字): 视频剧集在季内的编号 
  * ` episode_id ` (字符串): 视频剧集的ID 



适用于音乐专辑中的音轨或部分媒体： 

  * ` track ` (字符串): 音轨的标题 
  * ` track_number ` (数字): 音轨在专辑或光盘中的编号 
  * ` track_id ` (字符串): 音轨的ID 
  * ` artist ` (字符串): 音轨的艺术家 
  * ` genre ` (字符串): 音轨的流派 
  * ` album ` (字符串): 音轨所属专辑的标题 
  * ` album_type ` (字符串): 专辑的类型 
  * ` album_artist ` (字符串): 出现在专辑上的所有艺术家的列表 
  * ` disc_number ` (数字): 音轨所属的光盘或其他物理介质的编号 
  * ` release_year ` (数字): 专辑发行的年份（YYYY） 



仅在使用 ` --download-sections ` 且对于具有内部章节的视频使用 ` --split-chapters ` 时可用： 

  * ` section_title ` (字符串): 章节的标题 
  * ` section_number ` (数字): 文件中章节的编号 
  * ` section_start ` (数字): 章节的开始时间（以秒为单位） 
  * ` section_end ` (数字): 章节的结束时间（以秒为单位） 



仅在使用 ` --print ` 时可用： 

  * ` urls ` (字符串): 所有请求格式的URL，每行一个 
  * ` filename ` (字符串): 视频文件的名称。请注意，  实际文件名可能会有所不同 
  * ` formats_table ` (表格): 视频格式表，由 ` --list-formats ` 打印而来 
  * ` thumbnails_table ` (表格): 缩略图格式表，由 ` --list-thumbnails ` 打印而来 
  * ` subtitles_table ` (表格): 字幕格式表，由 ` --list-subs ` 打印而来 
  * ` automatic_captions_table ` (表格): 自动字幕格式表，由 ` --list-subs ` 打印而来 



仅在视频下载后可用 ( ` post_process ` / ` after_move ` )： 

  * ` filepath ` : 下载的视频文件的实际路径 



仅在 ` --sponsorblock-chapter-title ` 中可用： 

  * ` start_time ` (数值): 章节的开始时间（以秒为单位） 
  * ` end_time ` (数值): 章节的结束时间（以秒为单位） 
  * ` categories ` (列表): 章节所属的 [ SponsorBlock类别 ](https://wiki.sponsor.ajay.app/w/Types#Category)
  * ` category ` (字符串): 章节所属的最小SponsorBlock类别 
  * ` category_names ` (列表): 类别的友好名称 
  * ` name ` (字符串): 最小类别的友好名称 
  * ` type ` (字符串): 章节的 [ SponsorBlock操作类型 ](https://wiki.sponsor.ajay.app/w/Types#Action_Type)



当在输出模板中引用上述序列时，将被替换为对应的实际值。例如，对于 ` -o %(title)s-%(id)s.%(ext)s ` 和标题为 ` yt-dlp测试视频 ` ，ID为 ` BaW_jenozKc ` 的mp4视频，将在当前目录中创建一个名为 ` yt-dlp测试视频-BaW_jenozKc.mp4 ` 的文件。 

**注意** ：某些序列不能保证存在，因为它们取决于特定提取器获取的元数据。这些序列将被替换为提供的占位符值， ` --output-na-placeholder ` （默认为 ` NA ` ）。 

**提示** ：查看 ` -j ` 输出以确定特定URL可用的字段 

对于数值序列，您可以使用 [ 数值相关的格式化 ](https://docs.python.org/3/library/stdtypes.html#printf-style-string-formatting) ；例如， ` %(view_count)05d ` 将生成一个字符串，其中的观看次数用零填充，直到达到5个字符，例如 ` 00042 ` 。 

输出模板还可以包含任意的层次路径，例如 ` -o "%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s" ` 这将导致每个视频下载到与此路径模板对应的目录中。任何缺失的目录都将自动为您创建。 

要在输出模板中使用百分比文字，请使用 ` %% ` 。要输出到标准输出，请使用 ` -o - ` 。 

当前的默认模板是 ` %(title)s [%(id)s].%(ext)s ` 。 

在某些情况下，您不希望特殊字符，如中文、空格或&，例如在将下载的文件名传输到Windows系统或通过8位不安全通道传输文件名时。在这些情况下，添加 ` --restrict-filenames ` 标志以获得较短的标题。 

####  输出模板示例 
    
    
    $ yt-dlp --print filename -o "test video.%(ext)s" BaW_jenozKc
    test video.webm    # 带有正确扩展名的文字名称
    
    $ yt-dlp --print filename -o "%(title)s.%(ext)s" BaW_jenozKc
    youtube-dl test video ''_ä↭𝕐.webm    # 各种奇怪的字符
    
    $ yt-dlp --print filename -o "%(title)s.%(ext)s" BaW_jenozKc --restrict-filenames
    youtube-dl_test_video_.webm    # 限制的文件名
    
    # 在播放列表中的每个视频的目录中下载YouTube播放列表视频
    $ yt-dlp -o "%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s" "https://www.youtube.com/playlist?list=PLwiyx1dc3P2JR9N8gQaQN_BCvlSlap7re"
    
    # 根据上传年份将YouTube播放列表视频下载到不同的目录中
    $ yt-dlp -o "%(upload_date>%Y)s/%(title)s.%(ext)s" "https://www.youtube.com/playlist?list=PLwiyx1dc3P2JR9N8gQaQN_BCvlSlap7re"
    
    # 使用“ - ”分隔符为播放列表索引添加前缀，但仅在可用时添加
    $ yt-dlp -o "%(playlist_index&{} - |)s%(title)s.%(ext)s" BaW_jenozKc "https://www.youtube.com/user/TheLinuxFoundation/playlists"
    
    # 下载YouTube频道/用户的所有播放列表，将每个播放列表保存在单独的目录中：
    $ yt-dlp -o "%(uploader)s/%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s" "https://www.youtube.com/user/TheLinuxFoundation/playlists"
    
    # 下载Udemy课程，将每个章节保存在家目录下的单独目录中
    $ yt-dlp -u user -p password -P "~/MyVideos" -o "%(playlist)s/%(chapter_number)s - %(chapter)s/%(title)s.%(ext)s" "https://www.udemy.com/java-tutorial"
    
    # 下载整个系列的季节，将每个系列和每个季节保存在C:/MyVideos下的单独目录中
    $ yt-dlp -P "C:/MyVideos" -o "%(series)s/%(season_number)s - %(season)s/%(episode_number)s - %(episode)s.%(ext)s" "https://videomore.ru/kino_v_detalayah/5_sezon/367617"
    
    # 将视频下载为“C:\MyVideos\uploader\title.ext”，将字幕下载为“C:\MyVideos\subs\uploader\title.ext”
    # 并将所有临时文件放在“C:\MyVideos\tmp”中
    $ yt-dlp -P "C:/MyVideos" -P "temp:tmp" -P "subtitle:subs" -o "%(uploader)s/%(title)s.%(ext)s" BaW_jenoz --write-subs
    
    # 将视频下载为“C:\MyVideos\uploader\title.ext”，将字幕下载为“C:\MyVideos\uploader\subs\title.ext”
    $ yt-dlp -P "C:/MyVideos" -o "%(uploader)s/%(title)s.%(ext)s" -o "subtitle:%(uploader)s/subs/%(title)s.%(ext)s" BaW_jenozKc --write-subs
    
    # 将正在下载的视频流式传输到标准输出
    $ yt-dlp -o - BaW_jenozKc
    

#  格式选择 

默认情况下，yt-dlp会尝试下载最佳可用质量，如果您没有传递任何选项。 这通常相当于使用 ` -f bestvideo*+bestaudio/best ` 。然而，如果启用了多个音频流 ( ` --audio-multistreams ` )，默认格式将变为 ` -f bestvideo+bestaudio/best ` 。类似地，如果ffmpeg不可用，或者您使用yt-dlp流式传输到 ` stdout ` ( ` -o - ` )，默认值将变为 ` -f best/bestvideo+bestaudio ` 。 

**弃用警告** ：最新版本的yt-dlp可以使用ffmpeg同时将多个格式流式传输到stdout。因此，在将来的版本中，此默认值将设置为 ` -f bv*+ba/b ` ，类似于普通下载。如果您想保留 ` -f b/bv+ba ` 设置，建议在配置选项中明确指定。 

格式选择的一般语法是 ` -f FORMAT ` (或 ` --format FORMAT ` )，其中 ` FORMAT ` 是一个 _选择器表达式_ ，即描述您想要下载的格式或格式的表达式。 

MANPAGE: BEGIN EXCLUDED SECTION 

**简而言之：** 将我导航到示例  . 

MANPAGE: END EXCLUDED SECTION 

最简单的情况是请求特定的格式；例如，使用 ` -f 22 ` 可以下载格式代码为22的格式。您可以使用 ` --list-formats ` 或 ` -F ` 获取特定视频的可用格式代码列表。请注意，这些格式代码是特定于提取器的。 

您还可以使用文件扩展名（目前支持 ` 3gp ` 、 ` aac ` 、 ` flv ` 、 ` m4a ` 、 ` mp3 ` 、 ` mp4 ` 、 ` ogg ` 、 ` wav ` 、 ` webm ` ）来下载特定文件扩展名的最佳质量格式，作为单个文件提供，例如 ` -f webm ` 将下载以 ` webm ` 扩展名提供的最佳质量格式作为单个文件。 

您可以使用 ` -f - ` 交互式地为每个视频提供格式选择器 _。_

您还可以使用特殊名称选择特定的边缘情况格式： 

  * ` all ` ：选择 **所有格式** 分别 
  * ` mergeall ` ：选择并 **合并所有格式** （必须与 ` --audio-multistreams ` 、 ` --video-multistreams ` 或两者同时使用） 
  * ` b* ` 、 ` best* ` ：选择包含 **视频或音频或两者都包含** 的最佳质量格式（即； ` vcodec!=none or acodec!=none ` ） 
  * ` b ` 、 ` best ` ：选择包含 **视频和音频** 的最佳质量格式。等同于 ` best*[vcodec!=none][acodec!=none] `
  * ` bv ` 、 ` bestvideo ` ：选择最佳质量的 **仅视频** 格式。等同于 ` best*[acodec=none] `
  * ` bv* ` 、 ` bestvideo* ` ：选择包含 **视频** 的最佳质量格式。它也可能包含音频。等同于 ` best*[vcodec!=none] `
  * ` ba ` 、 ` bestaudio ` ：选择最佳质量的 **仅音频** 格式。等同于 ` best*[vcodec=none] `
  * ` ba* ` 、 ` bestaudio* ` ：选择包含 **音频** 的最佳质量格式。它也可能包含视频。等同于 ` best*[acodec!=none] ` （ [ 不要使用！ ](https://github.com/yt-dlp/yt-dlp/issues/979#issuecomment-919629354) ） 
  * ` w* ` 、 ` worst* ` ：选择包含 **视频或音频** 的最差质量格式 
  * ` w ` 、 ` worst ` ：选择包含 **视频和音频** 的最差质量格式。等同于 ` worst*[vcodec!=none][acodec!=none] `
  * ` wv ` 、 ` worstvideo ` ：选择最差质量的仅视频格式。等同于 ` worst*[acodec=none] `
  * ` wv* ` 、 ` worstvideo* ` ：选择包含视频的最差质量格式。它也可能包含音频。等同于 ` worst*[vcodec!=none] `
  * ` wa ` 、 ` worstaudio ` ：选择最差质量的仅音频格式。等同于 ` worst*[vcodec=none] `
  * ` wa* ` 、 ` worstaudio* ` ：选择包含音频的最差质量格式。它也可能包含视频。等同于 ` worst*[acodec!=none] `



例如，要下载最差的视频格式，您可以使用 ` -f worstvideo ` 。然而，不建议使用 ` worst ` 和相关选项。当您的格式选择器为 ` worst ` 时，将选择在所有方面都最差的格式。大多数情况下，您实际上想要的是文件大小最小的视频。因此，通常最好使用 ` -S +size ` 或更严格地使用 ` -S +size,+br,+res,+fps ` 而不是 ` -f worst ` 。有关更多详细信息，请参见  格式排序  。 

您可以使用 ` best<type>.<n> ` 来选择第n个最佳类型的格式。例如， ` best.2 ` 将选择第2个最佳的组合格式。类似地， ` bv*.3 ` 将选择包含视频流的第3个最佳格式。 

如果您想下载多个视频，并且它们没有相同的可用格式，您可以使用斜杠指定优先顺序。请注意，左侧的格式优先；例如， ` -f 22/17/18 ` 将下载格式22（如果可用），否则将下载格式17（如果可用），否则将下载格式18（如果可用），否则将报告没有适合下载的格式。 

如果您想下载同一视频的多个格式，请使用逗号作为分隔符，例如 ` -f 22,17,18 ` 将下载这三种格式，当然前提是它们可用。或者结合优先级功能的更复杂的示例： ` -f 136/137/mp4/bestvideo,140/m4a/bestaudio ` 。 

您可以使用 ` -f <format1>+<format2>+... ` 将多个格式的视频和音频合并为单个文件（需要安装ffmpeg）；例如， ` -f bestvideo+bestaudio ` 将下载最佳的仅视频格式、最佳的仅音频格式，并使用ffmpeg将它们混合在一起。 

**弃用警告** ：由于下面描述的行为复杂且反直观，将来将删除此功能，并默认启用多流。将添加一个新的运算符来限制格式为单个音频/视频。 

除非使用 ` --video-multistreams ` ，否则将忽略除第一个之外的所有具有视频流的格式。同样，除非使用 ` --audio-multistreams ` ，否则将忽略除第一个之外的所有具有音频流的格式。例如 ` -f bestvideo+best+bestaudio --video-multistreams --audio-multistreams ` 将下载并合并所有给定的3个格式。生成的文件将有2个视频流和2个音频流。但是 ` -f bestvideo+best+bestaudio --no-video-multistreams ` 将只下载并合并 ` bestvideo ` 和 ` bestaudio ` 。 ` best ` 被忽略，因为已经选择了另一个包含视频流的格式（ ` bestvideo ` ）。因此，格式的顺序很重要。 ` -f best+bestaudio --no-audio-multistreams ` 将只下载 ` best ` ，而 ` -f bestaudio+best --no-audio-multistreams ` 将忽略 ` best ` 并只下载 ` bestaudio ` 。 

##  过滤格式 

您还可以通过在括号中设置条件来过滤视频格式，例如 ` -f "best[height=720]" ` （或 ` -f "[filesize>10M]" ` ，因为没有选择器的过滤器被解释为 ` best ` ）。 

可以使用以下数字元字段进行比较 ` < ` 、 ` <= ` 、 ` > ` 、 ` >= ` 、 ` = ` （等于）， ` != ` （不等于）： 

  * ` filesize ` ：字节数，如果事先已知 
  * ` filesize_approx ` ：字节数的估计 
  * ` width ` ：视频的宽度，如果已知 
  * ` height ` ：视频的高度，如果已知 
  * ` aspect_ratio ` ：视频的宽高比，如果已知 
  * ` tbr ` ：音频和视频的平均比特率（以KBit/s为单位） 
  * ` abr ` ：音频的平均比特率（以KBit/s为单位） 
  * ` vbr ` ：视频的平均比特率（以KBit/s为单位） 
  * ` asr ` ：音频的采样率（以赫兹为单位） 
  * ` fps ` ：帧率 
  * ` audio_channels ` ：音频通道数 
  * ` stretched_ratio ` ： ` width:height ` ，如果不是正方形的视频像素 



过滤器还适用于以下字符串元字段的比较 ` = ` （等于）， ` ^= ` （以...开头）， ` $= ` （以...结尾）， ` *= ` （包含...）， ` ~= ` （与正则表达式匹配），以及以下字符串元字段： 

  * ` url ` : 视频URL 
  * ` ext ` : 文件扩展名 
  * ` acodec ` : 使用的音频编解码器名称 
  * ` vcodec ` : 使用的视频编解码器名称 
  * ` container ` : 容器格式名称 
  * ` protocol ` : 实际下载时将使用的协议，小写 ( ` http ` , ` https ` , ` rtsp ` , ` rtmp ` , ` rtmpe ` , ` mms ` , ` f4m ` , ` ism ` , ` http_dash_segments ` , ` m3u8 ` , 或 ` m3u8_native ` ) 
  * ` language ` : 语言代码 
  * ` dynamic_range ` : 视频的动态范围 
  * ` format_id ` : 格式的简短描述 
  * ` format ` : 格式的可读描述 
  * ` format_note ` : 关于格式的附加信息 
  * ` resolution ` : 宽度和高度的文本描述 



任何字符串比较都可以在操作符前加上否定符号 ` ! ` ，以产生相反的比较，例如 ` !*= ` （不包含）。如果字符串比较的比较对象包含空格或除 ` ._- ` 之外的特殊字符，则需要用双引号或单引号括起来。 

**注意** ：以上提到的元字段都不能保证存在，因为这完全取决于特定提取器获取的元数据，即网站提供的元数据。提取器提供的任何其他字段也可以用于过滤。 

未知值的格式将被排除，除非在操作符后加上问号 ( ` ? ` )。您可以组合格式过滤器，例如 ` -f "bv[height<=?720][tbr>500]" ` 选择最高为720p的视频（或高度未知的视频），且比特率至少为500 KBit/s。您还可以将过滤器与 ` all ` 一起使用，以下载满足过滤器的所有格式，例如 ` -f "all[vcodec=none]" ` 选择所有仅音频的格式。 

格式选择器也可以使用括号进行分组；例如 ` -f "(mp4,webm)[height<480]" ` 将下载高度低于480的最佳预合并的mp4和webm格式。 

##  格式排序 

您可以使用 ` -S ` ( ` --format-sort ` )来更改被视为 ` best ` 的标准。其一般格式为 ` --format-sort field1,field2... ` 。 

可用的字段有： 

  * ` hasvid ` ：优先选择具有视频流的格式 
  * ` hasaud ` ：优先选择具有音频流的格式 
  * ` ie_pref ` ：格式偏好 
  * ` lang ` ：语言偏好 
  * ` quality ` ：格式的质量 
  * ` source ` ：来源偏好 
  * ` proto ` ：下载使用的协议 ( ` https ` / ` ftps ` > ` http ` / ` ftp ` > ` m3u8_native ` / ` m3u8 ` > ` http_dash_segments ` > ` websocket_frag ` > ` mms ` / ` rtsp ` > ` f4f ` / ` f4m ` ) 
  * ` vcodec ` ：视频编解码器 ( ` av01 ` > ` vp9.2 ` > ` vp9 ` > ` h265 ` > ` h264 ` > ` vp8 ` > ` h263 ` > ` theora ` > 其他) 
  * ` acodec ` ：音频编解码器 ( ` flac ` / ` alac ` > ` wav ` / ` aiff ` > ` opus ` > ` vorbis ` > ` aac ` > ` mp4a ` > ` mp3 ` > ` ac4 ` > ` eac3 ` > ` ac3 ` > ` dts ` > 其他) 
  * ` codec ` ：等同于 ` vcodec,acodec `
  * ` vext ` ：视频扩展名 ( ` mp4 ` > ` mov ` > ` webm ` > ` flv ` > 其他)。如果使用了 ` --prefer-free-formats ` ，则优先选择 ` webm ` 。 
  * ` aext ` ：音频扩展名（ ` m4a ` > ` aac ` > ` mp3 ` > ` ogg ` > ` opus ` > ` webm ` > 其他）。如果使用 ` --prefer-free-formats ` ，顺序将变为 ` ogg ` > ` opus ` > ` webm ` > ` mp3 ` > ` m4a ` > ` aac `
  * ` ext ` ：等同于 ` vext,aext `
  * ` filesize ` ：确切的文件大小，如果事先已知 
  * ` fs_approx ` ：近似的文件大小 
  * ` size ` ：如果有的话，精确的文件大小，否则为近似文件大小 
  * ` height ` ：视频的高度 
  * ` width ` ：视频的宽度 
  * ` res ` ：视频分辨率，计算为最小维度。 
  * ` fps ` ：视频的帧率 
  * ` hdr ` ：视频的动态范围（ ` DV ` > ` HDR12 ` > ` HDR10+ ` > ` HDR10 ` > ` HLG ` > ` SDR ` ） 
  * ` channels ` ：音频通道数 
  * ` tbr ` ：总平均比特率（以KBit/s为单位） 
  * ` vbr ` ：视频的平均比特率（以KBit/s为单位） 
  * ` abr ` ：音频的平均比特率（以KBit/s为单位） 
  * ` br ` ：平均比特率（以KBit/s为单位）， ` tbr ` / ` vbr ` / ` abr `
  * ` asr ` ：音频采样率（以Hz为单位） 



**废弃警告** ：其中许多字段具有（目前未记录的）别名，可能在将来的版本中被删除。建议仅使用记录的字段名称。 

所有字段（除非另有说明）均按降序排序。要反转此顺序，请在字段前加上 ` + ` 。例如 ` +res ` 偏好具有最小分辨率的格式。此外，您可以在字段后面加上首选值，用 ` : ` 分隔。例如 ` res:720 ` 偏好较大的视频，但不超过720p，并且如果没有小于720p的视频，则选择最小的视频。对于 ` codec ` 和 ` ext ` ，您可以提供两个首选值，第一个用于视频，第二个用于音频。例如 ` +codec:avc:m4a ` （等同于 ` +vcodec:avc,+acodec:m4a ` ）将视频编解码器首选项设置为 ` h264 ` > ` h265 ` > ` vp9 ` > ` vp9.2 ` > ` av01 ` > ` vp8 ` > ` h263 ` > ` theora ` ，音频编解码器首选项设置为 ` mp4a ` > ` aac ` > ` vorbis ` > ` opus ` > ` mp3 ` > ` ac3 ` > ` dts ` 。您还可以使用 ` ~ ` 作为分隔符，使排序偏好提供的最接近值。例如 ` filesize~1G ` 偏好与最接近1 GiB的文件大小的格式。 

无论用户定义的顺序如何，字段 ` hasvid ` 和 ` ie_pref ` 始终具有最高的排序优先级。可以使用 ` --format-sort-force ` 更改此行为。除此之外，默认使用的顺序是： ` lang,quality,res,fps,hdr:12,vcodec:vp9.2,channels,acodec,size,br,asr,proto,ext,hasaud,source,id ` 。提取器可能会覆盖此默认顺序，但不能覆盖用户提供的顺序。 

请注意，默认值为 ` vcodec:vp9.2 ` ；即不偏好 ` av1 ` 。类似地，默认值为 ` hdr:12 ` ；即不偏好杜比视界。这些选择是因为DV和AV1格式尚未与大多数设备完全兼容。随着更多设备能够流畅播放这些格式，这可能会在将来发生变化。 

如果您的格式选择器是 ` worst ` ，则在排序后选择最后一项。这意味着它将选择在所有方面都最差的格式。大多数情况下，您实际上想要的是具有最小文件大小的视频。因此，通常最好使用 ` -f best -S +size,+br,+res,+fps ` 。 

**提示** ：您可以使用 ` -v -F ` 来查看格式的排序情况（从差到好）。 

##  格式选择示例 
    
    
    # Download and merge the best video-only format and the best audio-only format,
    # or download the best combined format if video-only format is not available
    $ yt-dlp -f "bv+ba/b"
    
    # Download best format that contains video,
    # and if it doesn't already have an audio stream, merge it with best audio-only format
    $ yt-dlp -f "bv*+ba/b"
    
    # Same as above
    $ yt-dlp
    
    # Download the best video-only format and the best audio-only format without merging them
    # For this case, an output template should be used since
    # by default, bestvideo and bestaudio will have the same file name.
    $ yt-dlp -f "bv,ba" -o "%(title)s.f%(format_id)s.%(ext)s"
    
    # Download and merge the best format that has a video stream,
    # and all audio-only formats into one file
    $ yt-dlp -f "bv*+mergeall[vcodec=none]" --audio-multistreams
    
    # Download and merge the best format that has a video stream,
    # and the best 2 audio-only formats into one file
    $ yt-dlp -f "bv*+ba+ba.2" --audio-multistreams
    
    
    # The following examples show the old method (without -S) of format selection
    # and how to use -S to achieve a similar but (generally) better result
    
    # Download the worst video available (old method)
    $ yt-dlp -f "wv*+wa/w"
    
    # Download the best video available but with the smallest resolution
    $ yt-dlp -S "+res"
    
    # Download the smallest video available
    $ yt-dlp -S "+size,+br"
    
    
    
    # Download the best mp4 video available, or the best video if no mp4 available
    $ yt-dlp -f "bv*[ext=mp4]+ba[ext=m4a]/b[ext=mp4] / bv*+ba/b"
    
    # Download the best video with the best extension
    # (For video, mp4 > mov > webm > flv. For audio, m4a > aac > mp3 ...)
    $ yt-dlp -S "ext"
    
    
    
    # Download the best video available but no better than 480p,
    # or the worst video if there is no video under 480p
    $ yt-dlp -f "bv*[height<=480]+ba/b[height<=480] / wv*+ba/w"
    
    # Download the best video available with the largest height but no better than 480p,
    # or the best video with the smallest resolution if there is no video under 480p
    $ yt-dlp -S "height:480"
    
    # Download the best video available with the largest resolution but no better than 480p,
    # or the best video with the smallest resolution if there is no video under 480p
    # Resolution is determined by using the smallest dimension.
    # So this works correctly for vertical videos as well
    $ yt-dlp -S "res:480"
    
    
    
    # Download the best video (that also has audio) but no bigger than 50 MB,
    # or the worst video (that also has audio) if there is no video under 50 MB
    $ yt-dlp -f "b[filesize<50M] / w"
    
    # Download largest video (that also has audio) but no bigger than 50 MB,
    # or the smallest video (that also has audio) if there is no video under 50 MB
    $ yt-dlp -f "b" -S "filesize:50M"
    
    # Download best video (that also has audio) that is closest in size to 50 MB
    $ yt-dlp -f "b" -S "filesize~50M"
    
    
    
    # Download best video available via direct link over HTTP/HTTPS protocol,
    # or the best video available via any protocol if there is no such video
    $ yt-dlp -f "(bv*+ba/b)[protocol^=http][protocol!*=dash] / (bv*+ba/b)"
    
    # Download best video available via the best protocol
    # (https/ftps > http/ftp > m3u8_native > m3u8 > http_dash_segments ...)
    $ yt-dlp -S "proto"
    
    
    
    # Download the best video with either h264 or h265 codec,
    # or the best video if there is no such video
    $ yt-dlp -f "(bv*[vcodec~='^((he|a)vc|h26[45])']+ba) / (bv*+ba/b)"
    
    # Download the best video with best codec no better than h264,
    # or the best video with worst codec if there is no such video
    $ yt-dlp -S "codec:h264"
    
    # Download the best video with worst codec no worse than h264,
    # or the best video with best codec if there is no such video
    $*+ba/b)[protocol^=http][protocol!*=dash] / (bv*+ba/b)"
    
    # Download best video available via the best protocol
    # (https/ftps > http/ftp > m3u8_native > m3u8 > http_dash_segments ...)
    $ yt-dlp -S "proto"
    
    
    
    # Download the best video with either h264 or h265 codec,
    # or the best video if there is no such video
    $ yt-dlp -f "(bv*[vcodec~='^((he|a)vc|h26[45])']+ba) / (bv*+ba/b)"
    
    # Download the best video with best codec no better than h264,
    # or the best video with worst codec if there is no such video
    $ yt-dlp -S "codec:h264"
    
    # Download the best video with worst codec no worse than h264,
    # or the best video with best codec if there is no such video
    $ yt-dlp -S "+codec:h264"
    
    
    
    # More complex examples
    
    # Download the best video no better than 720p preferring framerate greater than 30,
    # or the worst video (still preferring framerate greater than 30) if there is no such video
    $ yt-dlp -f "((bv*[fps>30]/bv*)[height<=720]/(wv*[fps>30]/wv*)) + ba / (b[fps>30]/b)[height<=720]/(w[fps>30]/w)"
    
    # Download the video with the largest resolution no better than 720p,
    # or the video with the smallest resolution available if there is no such video,
    # preferring larger framerate for formats with the same resolution
    $ yt-dlp -S "res:720,fps"
    
    
    
    # Download the video with smallest resolution no worse than 480p,
    # or the video with the largest resolution available if there is no such video,
    # preferring better codec and then larger total bitrate for the same resolution
    $ yt-dlp -S "+res:480,codec,br"
    

#  修改元数据 

通过使用 ` --parse-metadata ` 和 ` --replace-in-metadata ` 可以修改提取器获取的元数据 

` --replace-in-metadata FIELDS REGEX REPLACE ` 用于使用 [ Python正则表达式 ](https://docs.python.org/3/library/re.html#regular-expression-syntax) 替换任何元数据字段中的文本。 可以在替换字符串中使用 [ 反向引用 ](https://docs.python.org/3/library/re.html?highlight=backreferences#re.sub) 进行高级用法。 

` --parse-metadata FROM:TO ` 的一般语法是提供要从中提取数据的字段或  输出模板  的名称，以及用于解释它的格式，由冒号 ` : ` 分隔。可以使用带有命名捕获组的 [ Python正则表达式 ](https://docs.python.org/3/library/re.html#regular-expression-syntax) ，单个字段名称或类似于  输出模板  的语法（仅支持 ` %(field)s ` 格式化）用于 ` TO ` 。可以多次使用该选项来解析和修改各个字段。 

请注意，这些选项保留它们的相对顺序，允许在解析字段和反之亦然进行替换。此外，任何这样创建的字段都可以在  输出模板  中使用，并且还将影响在使用 ` --embed-metadata ` 时添加的媒体文件的元数据。 

此选项还有一些特殊用途： 

  * 您可以基于当前下载的视频的元数据下载其他URL。要执行此操作，请将字段 ` additional_urls ` 设置为要下载的URL。例如 ` --parse-metadata "description:(?P<additional_urls>https?://www\.vimeo\.com/\d+)" ` 将下载在描述中找到的第一个vimeo视频 

  * 您可以使用此功能更改嵌入在媒体文件中的元数据。要执行此操作，请使用 ` meta_ ` 前缀设置相应字段的值。例如，将任何值设置为 ` meta_description ` 字段将添加到文件中的 ` description ` 字段中-您可以使用此功能设置不同的“描述”和“简介”。要修改单个流的元数据，请使用 ` meta<n>_ ` 前缀（例如 ` meta1_language ` ）。设置为 ` meta_ ` 字段的任何值都将覆盖所有默认值。 




**注意** ：元数据修改发生在格式选择、提取后和其他后处理操作之前。在这些步骤中可能会添加或更改某些字段，覆盖您的更改。 

供参考，这些是yt-dlp默认添加到文件元数据中的字段： 

元数据字段  |  来源   
---|---  
` 标题 ` |  ` 轨道 ` 或 ` 标题 `  
` 日期 ` |  ` 上传日期 `  
` 描述 ` , ` 概要 ` |  ` 描述 `  
` 持久链接 ` , ` 评论 ` |  ` 网页链接 `  
` 轨道 ` |  ` 轨道编号 `  
` 艺术家 ` |  ` 艺术家 ` , ` 创作者 ` , ` 上传者 ` 或 ` 上传者ID `  
` 流派 ` |  ` 流派 `  
` 专辑 ` |  ` 专辑 `  
` 专辑艺术家 ` |  ` 专辑艺术家 `  
` 光盘 ` |  ` 光盘编号 `  
` 节目 ` |  ` 系列 `  
` 季数 ` |  ` 季数 `  
` 剧集ID ` |  ` 剧集 ` 或 ` 剧集ID `  
` 剧集排序 ` |  ` 剧集编号 `  
` 每个流的语言 ` |  该格式的 ` 语言 `  
  
**注意** ：文件格式可能不支持其中一些字段 

##  修改元数据示例 
    
    
    # 将标题解释为“艺术家 - 标题”
    $ yt-dlp --parse-metadata "title:%(artist)s - %(title)s"
    
    # 正则表达式示例
    $ yt-dlp --parse-metadata "description:Artist - (?P<artist>.+)"
    
    # 将标题设置为“系列名称 S01E05”
    $ yt-dlp --parse-metadata "%(series)s S%(season_number)02dE%(episode_number)02d:%(title)s"
    
    # 将视频元数据中的“artist”字段设置为上传者
    $ yt-dlp --parse-metadata "%(uploader|)s:%(meta_artist)s" --embed-metadata
    
    # 使用描述而不是网页链接正确处理多行，将视频元数据中的“comment”字段设置为描述
    $ yt-dlp --parse-metadata "description:(?s)(?P<meta_comment>.+)" --embed-metadata
    
    # 在视频元数据中不设置任何“synopsis”
    $ yt-dlp --parse-metadata ":(?P<meta_synopsis>)"
    
    # 通过将其设置为空字符串，从infojson中删除“formats”字段
    $ yt-dlp --parse-metadata "video::(?P<formats>)" --write-info-json
    
    # 将标题和上传者中的所有空格和“_”替换为“-”
    $ yt-dlp --replace-in-metadata "title,uploader" "[ _]" "-"
    
    

#  提取器参数 

一些提取器接受额外的参数，可以使用 ` --extractor-args KEY:ARGS ` 来传递这些参数。 ` ARGS ` 是一个以 ` ; ` （分号）分隔的字符串，格式为 ` ARG=VAL1,VAL2 ` 。例如： ` --extractor-args "youtube:player-client=android_embedded,web;include_live_dash" --extractor-args "funimation:version=uncut" `

注意：在命令行界面中， ` ARG ` 可以使用 ` - ` 替代 ` _ ` ，例如 ` youtube:player-client" ` 可以写成 ` youtube:player_client" `

以下提取器使用了这个特性： 

####  youtube 

  * ` lang ` ：首选此语言代码（区分大小写）的翻译元数据（ ` title ` 、 ` description ` 等）。默认情况下，首选视频的主要语言元数据，如果没有，则回退到 ` en ` 的翻译。请参阅 [ youtube.py ](https://github.com/yt-dlp/yt-dlp/blob/c26f9b991a0681fd3ea548d535919cec1fbbd430/yt_dlp/extractor/youtube.py#L381-L390) 以获取支持的内容语言代码列表 
  * ` skip ` ：跳过提取m3u8清单、dash清单和 [ 自动翻译的字幕 ](https://github.com/yt-dlp/yt-dlp/issues/4090#issuecomment-1158102032) 的操作，可以是 ` hls ` 、 ` dash ` 或 ` translated_subs ` 中的一个或多个 
  * ` player_client ` ：从中提取视频数据的客户端。主要客户端包括 ` web ` 、 ` android ` 和 ` ios ` ，还有变体 ` _music ` 、 ` _embedded ` 、 ` _embedscreen ` 、 ` _creator ` （例如 ` web_embedded ` ）；以及 ` mweb ` 和 ` tv_embedded ` （绕过年龄验证）没有变体。默认情况下，使用 ` ios,android,web ` ，但根据需要添加 ` tv_embedded ` 和 ` creator ` 变体以用于年龄限制的视频。类似地，对于 ` music.youtube.com ` 的URL，会添加音乐变体。您可以使用 ` all ` 使用所有客户端，使用 ` default ` 使用默认客户端。 
  * ` player_skip ` ：跳过一些通常需要的网络请求以实现稳定的提取。可以是 ` configs ` （跳过客户端配置）、 ` webpage ` （跳过初始网页）、 ` js ` （跳过js播放器）中的一个或多个选项。尽管这些选项可以帮助减少所需的请求数量或避免一些速率限制，但可能会导致一些问题。有关更多详细信息，请参阅 [ #860 ](https://github.com/yt-dlp/yt-dlp/pull/860)
  * ` player_params ` ：用于播放器请求的YouTube播放器参数。将覆盖yt-dlp设置的任何默认参数。 
  * ` comment_sort ` ： ` top ` 或 ` new ` （默认）-选择评论排序模式（在YouTube的一侧） 
  * ` max_comments ` ：限制要收集的评论数量。以逗号分隔的整数列表，表示 ` max-comments,max-parents,max-replies,max-replies-per-thread ` 。默认为 ` all,all,all,all `
    * 例如， ` all,all,1000,10 ` 将最多获取1000个回复，每个线程最多有10个回复。 ` 1000,all,100 ` 将最多获取1000个评论，最多有100个回复 
  * ` 格式 ` ：更改要返回的格式类型。 ` dashy ` （将HTTP转换为DASH）， ` duplicate ` （相同内容但不同的URL或协议；包括 ` dashy ` ）， ` incomplete ` （无法完全下载-直播dash和直播后m3u8） 
  * ` innertube_host ` ：用于所有API请求的Innertube API主机；例如 ` studio.youtube.com ` ， ` youtubei.googleapis.com ` 。请注意，从一个子域导出的cookie在其他子域上无效 
  * ` innertube_key ` ：用于所有API请求的Innertube API密钥 



####  youtubetab (YouTube播放列表、频道、订阅等) 

  * ` skip ` ：跳过一个或多个 ` webpage ` （跳过初始网页下载）， ` authcheck ` （允许下载需要身份验证的播放列表，当没有下载初始网页时。这可能会导致不希望的行为，请参阅 [ #1122 ](https://github.com/yt-dlp/yt-dlp/pull/1122) 了解更多详情） 
  * ` approximate_date ` ：在flat-playlist中提取近似的 ` upload_date ` 和 ` timestamp ` 。这可能会导致基于日期的过滤器稍微偏离 



####  generic 

  * ` fragment_query ` ：将mpd/m3u8清单URL中的任何查询传递给其片段，如果没有提供值，或者应用给定的查询字符串作为 ` fragment_query=VALUE ` 。不适用于ffmpeg 
  * ` variant_query ` ：将主m3u8 URL查询传递给其变体播放列表URL，如果没有提供值，或者应用给定的查询字符串作为 ` variant_query=VALUE `
  * ` hls_key ` ：HLS AES-128密钥URI _或_ 密钥（十六进制），以及可选的IV（十六进制），形式为 ` (URI|KEY)[,IV] ` ；例如 ` generic:hls_key=ABCDEF1234567980,0xFEDCBA0987654321 ` 。传递这些值中的任何一个将强制使用本机HLS下载器，并覆盖在m3u8播放列表中找到的相应值 
  * ` is_live ` ：绕过直播HLS检测并手动设置 ` live_status ` \- 值为 ` false ` 将设置为 ` not_live ` ，任何其他值（或无值）将设置为 ` is_live `



####  funimation 

  * ` language ` ：要提取的音频语言，例如 ` funimation:language=english,japanese `
  * ` version ` ：要提取的视频版本 - ` uncut ` 或 ` simulcast `



####  crunchyrollbeta (Crunchyroll) 

  * ` format ` ：要提取的流类型（默认为 ` adaptive_hls ` ）。可能有用的值包括 ` adaptive_hls ` 、 ` adaptive_dash ` 、 ` vo_adaptive_hls ` 、 ` vo_adaptive_dash ` 、 ` download_hls ` 、 ` download_dash ` 、 ` multitrack_adaptive_hls_v2 `
  * ` hardsub ` ：要提取的硬字幕版本的首选顺序，或者 ` all ` （默认为 ` None ` =无硬字幕），例如 ` crunchyrollbeta:hardsub=en-US,None `



####  vikichannel 

  * ` video_types ` ：要下载的视频类型-一个或多个 ` episodes ` 、 ` movies ` 、 ` clips ` 、 ` trailers `



####  niconico 

  * ` segment_duration ` ：HLS-DMC格式的片段持续时间（以毫秒为单位）。请自行承担风险，因为此功能 **可能导致您的账户被终止。**



####  youtubewebarchive 

  * ` check_all ` ：尝试更多检查，但会增加请求次数。一个或多个 ` thumbnails ` 、 ` captures `



####  gamejolt 

  * ` comment_sort ` ： ` hot ` （默认）， ` you ` （需要cookies）， ` top ` ， ` new ` \- 选择评论排序模式（在GameJolt的一侧） 



####  hotstar 

  * ` res ` ：要忽略的分辨率-一个或多个 ` sd ` 、 ` hd ` 、 ` fhd `
  * ` vcodec ` ：要忽略的vcodec-一个或多个 ` h264 ` 、 ` h265 ` 、 ` dvh265 `
  * ` dr ` ：要忽略的动态范围-一个或多个 ` sdr ` 、 ` hdr10 ` 、 ` dv `



####  tiktok 

  * ` api_hostname ` ：用于移动API请求的主机名，例如 ` api-h2.tiktokv.com `
  * ` app_version ` ：调用移动API的应用版本-应与 ` manifest_app_version ` 一起设置，例如 ` 20.2.1 `
  * ` manifest_app_version ` ：调用移动API的数字应用版本，例如 ` 221 `



####  rokfinchannel 

  * ` tab ` ：要下载的选项卡-其中之一 ` new ` 、 ` top ` 、 ` videos ` 、 ` podcasts ` 、 ` streams ` 、 ` stacks `



####  twitter 

  * ` legacy_api ` ：强制使用传统的Twitter API而不是GraphQL API进行推文提取。如果传递了登录cookies，则无效果 



####  stacommu, wrestleuniverse 

  * ` device_id ` ：由网站分配的UUID值，用于限制付费直播内容的设备数量。可以在浏览器本地存储中找到 



####  twitch 

  * ` client_id ` ：用于发送GraphQL请求的客户端ID值，例如 ` twitch:client_id=kimne78kx3ncx6brgo4mv6wki5h1ko `



####  nhkradirulive (NHK らじる★らじる LIVE) 

  * ` area ` ：要提取的地区变体。有效的地区有： ` sapporo ` 、 ` sendai ` 、 ` tokyo ` 、 ` nagoya ` 、 ` osaka ` 、 ` hiroshima ` 、 ` matsuyama ` 、 ` fukuoka ` 。默认为 ` tokyo `



**注意** ：这些选项可能会在未来更改/删除，不会考虑向后兼容性 

MANPAGE: MOVE "INSTALLATION" SECTION HERE 

#  插件 

请注意， **所有** 插件都会被导入，即使没有被调用，并且对插件代码不进行任何检查。 **使用插件需自担风险，并且只有在信任代码的情况下才能使用！**

插件可以是 ` <type> ` 类型的 ` extractor ` 或 ` postprocessor ` 。 \- 当输入的URL适合时，不需要从CLI启用提取器插件，它们会自动调用。 \- 提取器插件优先于内置提取器。 \- 可以使用 ` --use-postprocessor NAME ` 来调用后处理器插件。 

插件从命名空间包 ` yt_dlp_plugins.extractor ` 和 ` yt_dlp_plugins.postprocessor ` 中加载。 

换句话说，磁盘上的文件结构如下所示： 
    
    
        yt_dlp_plugins/
            extractor/
                myplugin.py
            postprocessor/
                myplugin.py
    

yt-dlp会在许多位置查找这些 ` yt_dlp_plugins ` 命名空间文件夹，并从 **所有** 文件夹中加载插件。 

请参阅 [ 维基页面以获取一些已知插件 ](https://github.com/yt-dlp/yt-dlp/wiki/Plugins)

##  安装插件 

插件可以使用各种方法和位置进行安装。 

  1. **配置目录** ： 插件包（包含一个 ` yt_dlp_plugins ` 命名空间文件夹）可以放置在以下标准  配置位置  中： 
    * **用户插件**
    * ` ${XDG_CONFIG_HOME}/yt-dlp/plugins/<package name>/yt_dlp_plugins/ ` （在Linux/macOS上推荐） 
    * ` ${XDG_CONFIG_HOME}/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
    * ` ${APPDATA}/yt-dlp/plugins/<package name>/yt_dlp_plugins/ ` （在Windows上推荐） 
    * ` ${APPDATA}/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
    * ` ~/.yt-dlp/plugins/<package name>/yt_dlp_plugins/ `
    * ` ~/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
    * **系统插件**
    * ` /etc/yt-dlp/plugins/<package name>/yt_dlp_plugins/ `
    * ` /etc/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
  2. **可执行文件位置** ：插件包同样可以安装在可执行文件位置下的 ` yt-dlp-plugins ` 目录中（推荐用于便携安装）： 

    * 二进制文件：位于 ` <root-dir>/yt-dlp.exe ` ， ` <root-dir>/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
    * 源代码：位于 ` <root-dir>/yt_dlp/__main__.py ` ， ` <root-dir>/yt-dlp-plugins/<package name>/yt_dlp_plugins/ `
  3. **pip和其他` PYTHONPATH ` 中的位置 **

    * 插件包可以使用 ` pip ` 进行安装和管理。参见 [ yt-dlp-sample-plugins ](https://github.com/yt-dlp/yt-dlp-sample-plugins) 的示例。 
    * 注意：使用pip安装的插件包之间的插件文件必须具有唯一的文件名。 
    * 在 ` PYTHONPATH ` 中的任何路径都会被搜索以寻找 ` yt_dlp_plugins ` 命名空间文件夹。 
    * 注意：这不适用于Pyinstaller/py2exe构建。 



` .zip ` 、 ` .egg ` 和 ` .whl ` 格式的存档文件，如果它们的根目录中包含一个 ` yt_dlp_plugins ` 命名空间文件夹，也可以作为插件包进行支持。 * 例如， ` ${XDG_CONFIG_HOME}/yt-dlp/plugins/mypluginpkg.zip ` ，其中 ` mypluginpkg.zip ` 包含 ` yt_dlp_plugins/<type>/myplugin.py `

运行yt-dlp并使用 ` --verbose ` 检查插件是否已加载。 

##  开发插件 

请参阅 [ yt-dlp-sample-plugins ](https://github.com/yt-dlp/yt-dlp-sample-plugins) 存储库以获取模板插件包和 [ 插件开发 ](https://github.com/yt-dlp/yt-dlp/wiki/Plugin-Development) 部分的插件开发指南。 

所有以 ` IE ` / ` PP ` 结尾的公共类都从每个文件中导入，用于提取器和后处理器。这尊重下划线前缀（例如 ` _MyBasePluginIE ` 是私有的）和 ` __all__ ` 。模块也可以通过在模块名前加下划线来排除（例如 ` _myplugin.py ` ）。 

要用子类替换现有的提取器，请设置 ` plugin_name ` 类关键字参数（例如 ` class MyPluginIE(ABuiltInIE, plugin_name='myplugin') ` 将用 ` MyPluginIE ` 替换 ` ABuiltInIE ` ）。由于提取器替换了父类，您应该通过使用上述方法之一将子类提取器排除在单独导入之外，使其成为私有的。 

如果您是插件作者，请将 [ yt-dlp-plugins ](https://github.com/topics/yt-dlp-plugins) 添加为您的存储库的主题，以提高可发现性。 

请参阅 [ 开发者说明 ](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#developer-instructions) 以了解如何编写和测试提取器。 

#  嵌入YT-DLP 

yt-dlp尽力成为一个良好的命令行程序，因此应该可以从任何编程语言调用。 

您的程序应避免解析正常的stdout，因为它们可能在将来的版本中更改。相反，它们应该使用诸如 ` -J ` 、 ` --print ` 、 ` --progress-template ` 、 ` --exec ` 等选项来创建可靠重现和解析的控制台输出。 

从Python程序中，您可以以更强大的方式嵌入yt-dlp，如下所示： 
    
    
    from yt_dlp import YoutubeDL
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    with YoutubeDL() as ydl:
        ydl.download(URLS)
    

最有可能的是，您会想使用各种选项。要查看可用选项的列表，请查看 [ ` yt_dlp/YoutubeDL.py ` ](yt_dlp/YoutubeDL.py#L183) 或在Python shell中使用 ` help(yt_dlp.YoutubeDL) ` 。如果您已经熟悉CLI，您可以使用 [ ` devscripts/cli_to_api.py ` ](https://github.com/yt-dlp/yt-dlp/blob/master/devscripts/cli_to_api.py) 将任何CLI开关转换为 ` YoutubeDL ` 参数。 

**提示** ：如果您正在将代码从youtube-dl移植到yt-dlp，请注意一个重要的问题，即我们不保证 ` YoutubeDL.extract_info ` 的返回值是可JSON序列化的，甚至是一个字典。它将类似于字典，但如果您想确保它是可序列化的字典，请将其通过 ` YoutubeDL.sanitize_info ` 传递，如下所示  示例 

##  嵌入示例 

####  提取信息 
    
    
    import json
    import yt_dlp
    
    URL = 'https://www.youtube.com/watch?v=BaW_jenozKc'
    
    # ℹ️ 查看 help(yt_dlp.YoutubeDL) 获取可用选项和公共函数列表
    ydl_opts = {}
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        info = ydl.extract_info(URL, download=False)
    
        # ℹ️ ydl.sanitize_info 使 info 可以被序列化为 json
        print(json.dumps(ydl.sanitize_info(info)))
    

####  使用 info-json 下载 
    
    
    import yt_dlp
    
    INFO_FILE = 'path/to/video.info.json'
    
    with yt_dlp.YoutubeDL() as ydl:
        error_code = ydl.download_with_info_file(INFO_FILE)
    
    print('一些视频下载失败' if error_code
          else '所有视频下载成功')
    

####  提取音频 
    
    
    import yt_dlp
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    
    ydl_opts = {
        'format': 'm4a/bestaudio/best',
        # ℹ️ 查看 help(yt_dlp.postprocessor) 获取可用的后处理器和参数列表
        'postprocessors': [{  # 使用 ffmpeg 提取音频
            'key': 'FFmpegExtractAudio',
            'preferredcodec': 'm4a',
        }]
    }
    
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        error_code = ydl.download(URLS)
    

####  过滤视频 
    
    
    import yt_dlp
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    
    def longer_than_a_minute(info, *, incomplete):
        """仅下载时长超过一分钟的视频（或未知时长的视频）"""
        duration = info.get('duration')
        if duration and duration < 60:
            return '视频太短'
    
    ydl_opts = {
        'match_filter': longer_than_a_minute,
    }
    
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        error_code = ydl.download(URLS)
    

####  添加日志记录器和进度钩子 
    
    
    import yt_dlp
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    
    class MyLogger:
        def debug(self, msg):
            # 为了与 youtube-dl 兼容，debug 和 info 都传递给 debug
            # 可以通过前缀 '[debug] ' 区分它们
            if msg.startswith('[debug] '):
                pass
            else:
                self.info(msg)
    
        def info(self, msg):
            pass
    
        def warning(self, msg):
            pass
    
        def error(self, msg):
            print(msg)
    
    
    # ℹ️ 查看 help(yt_dlp.YoutubeDL) 中的 "progress_hooks"
    def my_hook(d):
        if d['status'] == 'finished':
            print('下载完成，现在进行后处理...')
    
    
    ydl_opts = {
        'logger': MyLogger(),
        'progress_hooks': [my_hook],
    }
    
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download(URLS)
    

####  添加自定义后处理器 
    
    
    import yt_dlp
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    
    # ℹ️ 查看 help(yt_dlp.postprocessor.PostProcessor)
    class MyCustomPP(yt_dlp.postprocessor.PostProcessor):
        def run(self, info):
            self.to_screen('正在处理')
            return [], info
    
    
    with yt_dlp.YoutubeDL() as ydl:
        # ℹ️ "when" 可以取 yt_dlp.utils.POSTPROCESS_WHEN 中的任何值
        ydl.add_post_processor(MyCustomPP(), when='pre_process')
        ydl.download(URLS)
    

####  使用自定义格式选择器 
    
    
    import yt_dlp
    
    URLS = ['https://www.youtube.com/watch?v=BaW_jenozKc']
    
    def format_selector(ctx):
        """ 选择最佳的视频和最佳的音频，不会导致mkv格式。
        注意：这只是一个示例，不处理所有情况 """
    
        # 格式已经按照最差到最好的顺序排序
        formats = ctx.get('formats')[::-1]
    
        # acodec='none' 表示没有音频
        best_video = next(f for f in formats
                          if f['vcodec'] != 'none' and f['acodec'] == 'none')
    
        # 找到兼容的音频扩展名
        audio_ext = {'mp4': 'm4a', 'webm': 'webm'}[best_video['ext']]
        # vcodec='none' 表示没有视频
        best_audio = next(f for f in formats if (
            f['acodec'] != 'none' and f['vcodec'] == 'none' and f['ext'] == audio_ext))
    
        # 这些是合并格式所需的最小字段
        yield {
            'format_id': f'{best_video["format_id"]}+{best_audio["format_id"]}',
            'ext': best_video['ext'],
            'requested_formats': [best_video, best_audio],
            # 必须是以+分隔的协议列表
            'protocol': f'{best_video["protocol"]}+{best_audio["protocol"]}'
        }
    
    
    ydl_opts = {
        'format': format_selector,
    }
    
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download(URLS)
    

MANPAGE: MOVE "NEW FEATURES" SECTION HERE 

#  已弃用选项 

这些都是已弃用的选项，以及实现相同效果的当前替代方法 

####  几乎冗余的选项 

尽管这些选项与它们的新对应项几乎相同，但由于存在一些差异，它们并不冗余 
    
    
    -j, --dump-json                  --print "%()j"
    -F, --list-formats               --print formats_table
    --list-thumbnails                --print thumbnails_table --print playlist:thumbnails_table
    --list-subs                      --print automatic_captions_table --print subtitles_table
    

####  冗余的选项 

尽管这些选项是冗余的，但由于使用简便，仍然预计会被使用 
    
    
    --get-description                --print description
    --get-duration                   --print duration_string
    --get-filename                   --print filename
    --get-format                     --print format
    --get-id                         --print id
    --get-thumbnail                  --print thumbnail
    -e, --get-title                  --print title
    -g, --get-url                    --print urls
    --match-title REGEX              --match-filter "title ~= (?i)REGEX"
    --reject-title REGEX             --match-filter "title !~= (?i)REGEX"
    --min-views COUNT                --match-filter "view_count >=? COUNT"
    --max-views COUNT                --match-filter "view_count <=? COUNT"
    --break-on-reject                使用 --break-match-filter
    --user-agent UA                  --add-header "User-Agent:UA"
    --referer URL                    --add-header "Referer:URL"
    --playlist-start NUMBER          -I NUMBER:
    --playlist-end NUMBER            -I :NUMBER
    --playlist-reverse               -I ::-1
    --no-playlist-reverse            默认
    --no-colors                      --color no_color
    

####  不推荐使用 

尽管这些选项仍然有效，但不推荐使用，因为有其他替代方法可以实现相同的效果 
    
    
    --force-generic-extractor        --ies generic,default
    --exec-before-download CMD       --exec "before_dl:CMD"
    --no-exec-before-download        --no-exec
    --all-formats                    -f all
    --all-subs                       --sub-langs all --write-subs
    --print-json                     -j --no-simulate
    --autonumber-size NUMBER         使用字符串格式化，例如 %(autonumber)03d
    --autonumber-start NUMBER        使用内部字段格式化，如 %(autonumber+NUMBER)s
    --id                             -o "%(id)s.%(ext)s"
    --metadata-from-title FORMAT     --parse-metadata "%(title)s:FORMAT"
    --hls-prefer-native              --downloader "m3u8:native"
    --hls-prefer-ffmpeg              --downloader "m3u8:ffmpeg"
    --list-formats-old               --compat-options list-formats (别名: --no-list-formats-as-table)
    --list-formats-as-table          --compat-options -list-formats [默认] (别名: --no-list-formats-old)
    --youtube-skip-dash-manifest     --extractor-args "youtube:skip=dash" (别名: --no-youtube-include-dash-manifest)
    --youtube-skip-hls-manifest      --extractor-args "youtube:skip=hls" (别名: --no-youtube-include-hls-manifest)
    --youtube-include-dash-manifest  默认 (别名: --no-youtube-skip-dash-manifest)
    --youtube-include-hls-manifest   默认 (别名: --no-youtube-skip-hls-manifest)
    --geo-bypass                     --xff "default"
    --no-geo-bypass                  --xff "never"
    --geo-bypass-country CODE        --xff CODE
    --geo-bypass-ip-block IP_BLOCK   --xff IP_BLOCK
    

####  开发者选项 

这些选项不适用于最终用户使用 
    
    
    --test                           仅下载视频的一部分以测试提取器
    --load-pages                     加载由 --write-pages 转储的页面
    --youtube-print-sig-code         用于测试YouTube签名
    --allow-unplayable-formats       列出不可播放的格式
    --no-allow-unplayable-formats    默认
    

####  旧别名 

这些是不再为各种原因记录的别名 
    
    
    --avconv-location                --ffmpeg-location
    --clean-infojson                 --clean-info-json
    --cn-verification-proxy URL      --geo-verification-proxy URL
    --dump-headers                   --print-traffic
    --dump-intermediate-pages        --dump-pages
    --force-write-download-archive   --force-write-archive
    --load-info                      --load-info-json
    --no-clean-infojson              --no-clean-info-json
    --no-split-tracks                --no-split-chapters
    --no-write-srt                   --no-write-subs
    --prefer-unsecure                --prefer-insecure
    --rate-limit RATE                --limit-rate RATE
    --split-tracks                   --split-chapters
    --srt-lang LANGS                 --sub-langs LANGS
    --trim-file-names LENGTH         --trim-filenames LENGTH
    --write-srt                      --write-subs
    --yes-overwrites                 --force-overwrites
    

####  Sponskrub Options 

支持 [ SponSkrub ](https://github.com/faissaloo/SponSkrub) 已被弃用，推荐使用 ` --sponsorblock ` 选项 
    
    
    --sponskrub                      --sponsorblock-mark all
    --no-sponskrub                   --no-sponsorblock
    --sponskrub-cut                  --sponsorblock-remove all
    --no-sponskrub-cut               --sponsorblock-remove -all
    --sponskrub-force                不适用
    --no-sponskrub-force             不适用
    --sponskrub-location             不适用
    --sponskrub-args                 不适用
    

####  不再支持 

这些选项可能不再按预期工作 
    
    
    --prefer-avconv                  yt-dlp不再官方支持avconv（别名：--no-prefer-ffmpeg）
    --prefer-ffmpeg                  默认（别名：--no-prefer-avconv）
    -C, --call-home                  未实现
    --no-call-home                   默认
    --include-ads                    不再支持
    --no-include-ads                 默认
    --write-annotations              现在没有受支持的网站有注释
    --no-write-annotations           默认
    --compat-options seperate-video-versions  不再需要
    

####  已移除 

这些选项自2014年起已被弃用，现已完全移除 
    
    
    -A, --auto-number                -o "%(autonumber)s-%(id)s.%(ext)s"
    -t, -l, --title, --literal       -o "%(title)s-%(id)s.%(ext)s"
    

#  CONTRIBUTING 

请参阅 [ CONTRIBUTING.md ](CONTRIBUTING.md#contributing-to-yt-dlp) 了解有关 [ 提出问题 ](CONTRIBUTING.md#opening-an-issue) 和 [ 贡献代码给项目 ](CONTRIBUTING.md#developer-instructions) 的说明 

#  WIKI 

请参阅 [ Wiki ](https://github.com/yt-dlp/yt-dlp/wiki) 了解更多信息 
