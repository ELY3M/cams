## Cams

![Cams](https://raw.githubusercontent.com/vladpen/cams/main/fastlane/metadata/android/ru-RU/images/phoneScreenshots/5_cover.jpg)

A simple mobile application for Android for playing RTSP streams from IP cameras.

Features:

- Viewing RTSP streams from any IP cameras, including H.265+.
- Simultaneous viewing of multiple streams.
- Twenty-fold image zoom.
- Support for dual-channel cameras.
- Viewing video recordings or images via SFTP.
- Ability to configure notifications about camera motion detection.
- High connection speed.
- Extremely easy navigation and control.
- Maximum security and data privacy.
- TCP/UDP protocol switching.
This option is important when viewing cameras via the Internet, where UDP may not be supported or work poorly.

<img src="https://raw.githubusercontent.com/vladpen/cams/main/fastlane/metadata/android/ru-RU/images/phoneScreenshots/1_main_ru.jpg"
alt="Main screen"
width="200">&nbsp;
<img src="https://raw.githubusercontent.com/vladpen/cams/main/fastlane/metadata/android/ru-RU/images/phoneScreenshots/2_edit_ru.jpg"
alt="Edit screen"
width="200">&nbsp;
<img src="https://raw.githubusercontent.com/vladpen/cams/main/fastlane/metadata/android/ru-RU/images/phoneScreenshots/3_files_ru.jpg"
alt="Files screen"
width="200">&nbsp;
<img src="https://raw.githubusercontent.com/vladpen/cams/main/fastlane/metadata/android/ru-RU/images/phoneScreenshots/4_video_ru.jpg"
alt="Video screen"
width="200">

The application is written for use with the [python-rtsp-server](https://github.com/vladpen/python-rtsp-server) server,
but works great autonomously thanks to the ability to connect to any IP cameras, as well as video recorders that support SFTP.

Plays most types of video streams (not only RTSP).
The screenshot above shows an image from a real video camera and three test videos in the "Group" mode.

*IMPORTANT. The application is focused on security and privacy of data, so it does not collect or process any information about the user.
Data is not sent to any servers, including Google's technical infrastructure and "cloud" storage of camera manufacturers.*

## Installation

You can build the APK file yourself, [download from Github](https://github.com/vladpen/cams/raw/main/app/release/app-armeabi-v7a-release.apk),
install using [F-Droid](https://f-droid.org/ru/packages/com.vladpen.cams/)
or [RuStore](https://www.rustore.ru/catalog/app/com.vladpen.cams).
The supported architecture is armeabi-v7a (used in most modern mobile phones), arm64-v8a, x86-64 and x86.

## Configuration

To connect to a video camera, enter its URL specified by the manufacturer in the "Address" field. It usually looks like this:
```
[rtsp://][<user>:<password>@]<IP>[:<port>][/<path>]
```
Parameters in square brackets are optional (depending on the camera settings).

For dual-channel cameras, you can additionally specify the address of the second channel.
For example, for Hikvision cameras and their derivatives, the path will look like this:
```
ISAPI/Streaming/Channels/<channel number>
```
Then the first channel (high resolution) will have the number 101, and the second (low resolution) - 102.

Low resolution channels can be used to speed up image loading,
to save traffic and to reduce the load on the device processor.
This is especially convenient for viewing a group of cameras at a low connection speed.
During playback, channels can be switched using the K1/K2 button in the lower right corner of the screen.
On camera group screens, K2 is used by default.

Also, to reduce the load, playback of cameras that go beyond the screen boundaries when the image is enlarged is paused.

The address of the SFTP server or video recorder looks like this:
```
[sftp://]<user>:<password>@<IP>[:<port>][/<path>]
```
ATTENTION! It is strongly recommended not to use administrator access data.
For the SFTP server, it is better to create a chroot, for example, as described [here](https://wiki.archlinux.org/title/SFTP_chroot).

**Tip:** you can use emoji as an icon in the camera name.
For example, the screenshots above use icons from the standard mobile phone set.

## Motion alert

Optionally, the application can notify about the triggering of the camera motion detector.
The notification is triggered when a new image from the camera appears in the specified SFTP server folder.
For this function to work, you need to configure the cameras and the server for storing the received images.
These settings are described in detail in the parallel project [Cams-PWA](https://github.com/vladpen/cams-pwa).

A detailed discussion of the application: [habr.com/ru/post/654915](https://habr.com/ru/post/654915/)
and the server: [habr.com/ru/post/597363](https://habr.com/ru/post/597363/).

[<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png"
alt="Get it on Github"
height="80">](https://github.com/vladpen/cams/tree/main/app/release)
[<img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
alt="Get it on F-Droid"
height="80">](https://f-droid.org/packages/com.vladpen.cams/)

&nbsp; [<img src="https://user-images.githubusercontent.com/3853013/194689050-e6da2f21-9aa3-4662-9b7d-7293b140f22f.svg"
alt="Available in RuStore"
height="57">](https://apps.rustore.ru/app/com.vladpen.cams)

*Copyright (c) 2022-2024 vladpen under MIT license. Use it with absolutely no warranty.*
