---
title: general-issues
displayName: General issues
published: true
order: 10
pageTitle: Solving General Video Streaming Issues | Gcore
pageDescription: An explanation of common basic checks to address general issues that may arise when working with Video Streaming.
---

# General Video Streaming Issues

Common issues you may encounter when working with both Live and VOD streams, as well as steps you can take to troubleshoot them.

<alert-element type="tip" title="Live Streaming and VOD Uploads">

If you encounter problems that are specific to live streaming or VOD uploads, please refer to the [Live streaming issues](https://gcore.com/docs/streaming-platform/live-streaming/troubleshooting/live-streaming-issues) or [VOD issues](https://gcore.com/docs/streaming-platform/live-streaming/troubleshooting/vod-issues) pages.

</alert-element>

## General troubleshooting steps

For the most common issues, such as video not playing, taking a long time to start streaming, or looking blurry, these basic checks should help:

-   **Status page**. Check if the issue you are experiencing is related to any known issue or is an isolated one by visiting the <a href="https://status.gcore.com" target="_blank">status page</a>.
-   **Source video**. Ensure that the source content is uploaded for streaming. If the same issue occurs in the source, re-upload the video or restart the stream.
-   **Stream URL and code**. Make sure to use the exact URL and embed code that appear in the Streaming settings.
-   **Streaming settings**. Make sure the stream is enabled. If configured to pull a stream, make sure the source URL is correct.
-   **Encoder settings**. Make sure you are using the <a href="https://gcore.com/docs/streaming-platform/live-streams-and-videos-protocols-and-codecs/what-initial-parameters-of-your-live-streams-and-videos-we-can-accept" target="_blank">recommended settings</a>. If configured to push a stream, make sure the server URL and stream key are accurate.

Other things to try:

-   Clear the browsing data.
-   Disable any interfering browser extensions.
-   Ensure that the network connection is stable. Try connecting with or without a VPN.
-   Verify that the streaming ports are open on the firewall.
-   Update the browser or device OS.

## Common playback issues

Issues with playback can be caused by a variety of factors, including network issues, device compatibility, and encoding settings. Here are some common issues and their solutions.

### Stream does not appear on some devices

_Possible cause_: Device is too old.  
_Suggested solution_: Streaming should work on most devices, but some devices may not be compatible. Try using a modern device with enough processing power and memory to successfully stream video.

### Stream returns an HTTP 404 error

_Possible cause_: Transcoding is in progress.  
_Suggested solution_: Each video chunk may take several seconds to transcode. Allow 10 to 15 seconds for this to happen. Once the chunks have been transcoded, the stream should be ready to play.

_Possible cause_: Low Latency is not enabled in the Customer Portal.  
_Suggested solution_: Contact our [support team](mailto:support@gcore.com) to activate this option.

<alert-element type="tip" title="HTTP Status Codes">

For more details on HTTP status codes, see the <a href="https://gcore.com/docs/streaming-platform/troubleshooting/http-status-codes" target="_blank">HTTP status codes</a> page.

</alert-element>

### Stream returns an HTTP 502 error

_Possible cause_: CDN resource settings have been changed from the preset settings.  
_Suggested solution_: Contact our [support team](mailto:support@gcore.com) to assist you in restoring the settings.

_Possible cause_: Token configuration is not synchronized.  
_Suggested solution_: Contact our [support team](mailto:support@gcore.com) to help you restore the settings.

## Open a support ticket

If none of the above work or apply to your issue, contact our [support team](mailto:support@gcore.com) with the following information:

1.  Link to the stream.
2.  Description of the issue and steps to reproduce.
3.  List of steps taken to troubleshoot the issue.
4.  Screenshot of the information shown in http://iam.gcdn.co/info.
5.  Screenshot of the response to this command:

    ```
    curl http://iam.gcdn.co/info/json
    ```

6.  Screenshot of the speed test result using http://iam.gcdn.co/info.
7.  HAR file. This <a href="https://toolbox.googleapps.com/apps/har_analyzer/?lang=en" target="_blank">page</a> describes how to generate one in Chrome, Firefox, and Edge.
