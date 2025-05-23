---
title: obs
displayName: OBS
published: true
order: 30
pageTitle: Live Stream Setup with OBS | Gcore
pageDescription: A step-by-step guide to pushing live streams via Open Broadcaster Software (OBS).
---

# Open Broadcaster Software

Open Broadcaster Software (OBS) is a free and open-source encoder for video recording, screencasting, and live streaming. It’s suitable for video game streaming, blogging, educational content, and more.

OBS links your device (a laptop or a PC) and different streaming platforms (Gcore Video Streaming, YouTube, Twitch, etc.). It takes an image captured by a camera, converts it into a video stream, and then sends it to the streaming platform.

## Setup

1\. Download Open Broadcaster Software (OBS) from the <a href="https://obsproject.com" target="_blank">official website</a> and install it.

2\. Open the **Settings** section and go to the **Stream** tab. Complete the remaining steps in it.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807190142097.png" alt="Stream tab.">

3\. Select **Custom** from the dropdown list.

4\. Enter the Server URL into the Server field and the unique key into the Stream Key field. To get the Server URL and key, go to the <a href="https://streaming.gcore.com/streaming/list" target="_blank">Streaming list</a>, open the Live stream settings you need, and copy the relevant value from the URLs for the encoder section.

For example, if you see these values on the Live stream settings page:

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/11774973436177.png" alt="Live stream settings" width="50%">

paste them to the OBS Settings as follows:

-   _rtmp://vp-push-ix1.gvideo.co/in/_ is the Server;
-   _400448?cdf2a7ccf990e464c2b…_ is the Stream Key.

5\. Click the **Apply** button to save the new configuration.

6\. Go to the main OBS menu, select the source of the stream (video capture device, display capture, etc.), and click **Start Streaming**.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807465490193.png" alt="Start Streaming">

7\. Once the streaming has started, go to the <a href="https://streaming.gcore.com/streaming/list" target="_blank">Streaming list</a>, open the Live Stream settings, and copy the link to embed the broadcast to your website.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/11775007043985.png" alt="Streaming list" width="80%">

That’s it. The stream from OBS will be broadcast to your website.

## Configure the stream parameters for optimal performance

To ensure optimal streaming performance, we recommend configuring the stream parameters you will send to our server. You can adjust these settings in the Output, Audio, and Video tabs within OBS.

### Output parameters

1\. Open OBS Settings and go to the **Output** tab. Select **Simple** mode.

2\. Set the parameters as follows:

-   **Video Bitrate:** The resolution of your stream determines the required bitrate: The higher the resolution, the higher the bitrate. To stream at 720p resolution, set the bitrate to 2000Kbps. If you’re broadcasting at 1080p, set the bitrate to 4000Kbps.
-   **Audio Bitrate:** 128.
-   **Encoder:** Software (x264), or any other H264 codec.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807571524241.png" alt="Manage the stream parameters" width="80%">

3\. Click **Advanced** mode.

4\. Set the parameters as follows:

-   **Rate control:** CRF (the default value is 23)
-   **Keyframe Interval (0=auto):** 2s
-   **CPU Usage Preset:** veryfast
-   **Profile:** baseline

5\. Click **Apply** to save the configuration.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807656645393.png" alt="configuration" width="80%">

### Audio parameters

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807660371473.png" alt="Audio parameters" width="80%">

1\. Open OBS Settings and go to the Audio tab.

2\. Set the Sample Rate to 44.1 kHz (default) or 48 kHz. Select **Stereo** for the best sound quality.

3\. Click **Apply**.

### Video parameters

If you need to reduce the original resolution (downscale), follow the instructions in this section. If no resolution change is required, you can skip this step.

1\. Open OBS Settings and go to the **Video** tab.

2\. Set the following parameters:

-   **Output (Scaled) Resolution:** 1280×720
-   **Downscale Filter:** Bicubic
-   **Common FPS Values:** 30

3\. Click **Apply**.

<img src="https://assets.gcore.pro/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs/10807613445521.png" alt="Video parameters Apply" width="80%">

**Hints.** You can see the stream's [output parameters here](https://gcore.com/docs/streaming-platform/live-streaming/push-live-streams-software/push-live-streams-via-obs#output-parameters). If you need to increase the FPS to 60, make sure to also increase the bitrate accordingly for optimal stream quality.
