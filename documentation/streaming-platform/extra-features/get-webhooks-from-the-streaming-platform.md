---
title: get-webhooks-from-the-streaming-platform
displayName: Webhooks
published: true
order: 40
toc:
   --1--What is it used for?: "what-are-the-video-streaming-webhooks-used-for"
   --1--Configure the webhook integration: "configure-the-webhook-integration"
   --1--Examples of available webhooks: "webhook-examples-of-all-video-streaming-events"
pageTitle: Understanding Webhooks With Examples | Gcore
pageDescription: What automatic notifications of the Video Streaming events you may receive.
---
# Get webhooks from the Video Streaming 

A webhook is a free automated notification about an event in our service. You can receive notifications about the following events of our Video Streaming:

- A live stream has started or finished.
- Recording of a live stream has started or paused.
- Updates on processing of a live stream recording: a recording has started processing, partially processed, or completely processed.
- Updates on broadcast statuses: pending, live, paused, or finished.
- A video is uploaded to the Gcore Customer Portal.
- Updates on video processing: a video has started processing, partially processed, or completely processed.
- Updates to a restream: it was created, is live, or was stopped.

Whenever any of these events happens, our server will create an HTTP POST request and notify you about it. You will receive the information in JSON format. Below is an example of a webhook triggered when a live stream starts.

<code-block>
{   
    "type": "stream",   
     "message": {   
           "stream": {   
             "id": <span style="color:#FF5913">12345</span>,   
             "live": <span style="color:#FF5913">true</span>,  
             "recording": <span style="color:#FF5913">false</span>    
           }   
      }   
}
</code-block>

Customize the following values:

- <span style="color:#FF5913">12345</span> is the stream ID in the Gcore Customer Portal,
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your stream,
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being recorded.

## What are the Video Streaming webhooks used for?

Webhooks are used by apps integrated with the Video Streaming. You can configure your app so that it will activate automatic workflows whenever it receives a webhook.

For example, users share videos in your app. When a user adds a new video, it is uploaded and processed through our Video Streaming. Then you need to embed the video in your application. You set up the auto-posting: as soon as the video is processed, the Video Streaming will send a webhook, and your app will post the video.

## Configure the webhook integration

1\. Prepare your HTTP server to receive webhooks.

2\. Contact us via chat or email [support@gcore.com](mailto:support@gcore.com) and ask to enable the webhook integration. Specify your ID (personal client ID) and the URL of the server that will receive webhooks. You can find your ID in the <a href="https://accounts.gcore.com/reports/dashboard" target="_blank">Gcore Customer Portal</a>.

<img src="https://assets.gcore.pro/docs/streaming-platform/extra-features/get-webhooks-from-the-streaming-platform/image.png" alt="your ID in the Gcore Customer Portal">

The message template: *"Good afternoon! Please configure the Video Streaming webhook integration for my account with ID..... The URL of my server to send webhooks to is ...."*.

3\. We will notify you when we configure the webhook integration.

We deliver webhooks for free from the IP range *92.223.123.0/24*.

We can send webhooks of one account only to one server. If your server is unavailable, undelivered webhooks won't be sent again. You will only receive a webhook of the next event.

## Webhook examples of all Video Streaming events 

Below are examples of all the webhooks that you can get from our service. Parameters are explained in round brackets.

**A live stream has started**

<code-block>
{   
  "type": "stream",   
  "message": {   
    "stream": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "live": <span style="color:#FF5913">true</span>,   
      "recording": <span style="color:#FF5913">false</span>   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the stream ID in Gcore Customer Portal,
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your stream,
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being recorded.

**A live stream is paused**

<code-block>
{   
  "type": "stream",   
  "message": {   
    "stream": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "live": <span style="color:#FF5913">false</span>,   
      "recording": <span style="color:#FF5913">false</span>   
    }   
  }   
} 
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the stream ID in the Gcore Customer Portal,
- <span style="color:#FF5913">false</span> is the indicator the Video Streaming is not receiving your stream,
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being recorded.


**Recording has started**

<code-block>
{  
  "type": "stream",   
  "message": {   
    "stream": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "live": <span style="color:#FF5913">true</span>,   
      "recording": <span style="color:#FF5913">true</span>  
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the stream ID in the Gcore Customer Portal,
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your stream,
- <span style="color:#FF5913">true</span> is the indicator that your stream is being recorded.

**Recording has finished**

<code-block>
{   
  "type": "stream",   
  "message": {   
    "stream": {   
       "id": <span style="color:#FF5913">12345</span>,   
       "live": <span style="color:#FF5913">true</span>,   
       "recording": <span style="color:#FF5913">false</span>  
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the stream ID in the Gcore Customer Portal,
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your stream,
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being recorded.

**A recording has started processing**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "slug": "<span style="color:#FF5913">ZeC44gtQQ4E97N9S</span>",   
      "name": "Stream Record: <span style="color:#FF5913">test</span>, 2022-05-27 09:08:40 +0000",   
      "duration": <span style="color:#FF5913">19580</span>,   
      "status": "pending",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"  
        },   
        {            
           "name": "<span style="color:#FF5913">vod480n</span>",   
           "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
           "name": "<span style="color:#FF5913">vod240n</span>",   
           "status": "<span style="color:#FF5913">processing</span>"   
        }   
      ]    
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the recording ID in the Gcore Customer Portal,
- <span style="color:#FF5913">ZeC44gtQQ4E97N9S</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">test</span> is your stream name,
- <span style="color:#FF5913">19580</span> is the recording duration in seconds,
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the record.  
- <span style="color:#FF5913">processing</span> is indicator that the recording is being processed.

**A recording is partially processed**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "slug": "<span style="color:#FF5913">ZeC44gtQQ4E97N9S</span>",   
      "name": "Stream Record: <span style="color:#FF5913">test</span>, 2022-05-27 09:08:40 +0000",   
      "duration": <span style="color:#FF5913">19580</span>,   
      "status": "viewable",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod480n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod240n</span>",    
          "status": "<span style="color:#FF5913">processing</span>"   
        }   
      ]   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the recording ID in the Gcore Customer Portal,
- <span style="color:#FF5913">ZeC44gtQQ4E97N9S</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">test</span> is your stream name,
- <span style="color:#FF5913">19580</span> is the recording duration in seconds,
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the record.  
- <span style="color:#FF5913">processing</span> is indicator that the recording is being processed.
- <span style="color:#FF5913">complete</span> is the indicator that the processing is completed.

**A recording is completely processed**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "slug": "<span style="color:#FF5913">ZeC44gtQQ4E97N9S</span>",   
      "name": "Stream Record: <span style="color:#FF5913">test</span>, 2022-05-27 09:08:40 +0000",   
      "duration": <span style="color:#FF5913">19580</span>,   
      "status": "ready",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
           "name": "<span style="color:#FF5913">vod480n</span>",   
           "status": "<span style="color:#FF5913">complete</span>"   
        },  
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"  
        },   
        {   
          "name": "<span style="color:#FF5913">vod240n</span>",    
          "status": "<span style="color:#FF5913">complete</span>"    
        }   
      ]   
    }   
  }   
} 
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the recording ID in the Gcore Customer Portal,
- <span style="color:#FF5913">ZeC44gtQQ4E97N9S</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">test</span> is your stream name,
- <span style="color:#FF5913">19580</span> is the recording duration in seconds,
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the record.  
- <span style="color:#FF5913">complete</span> is the indicator that the processing is completed.


**A broadcast status is updated to "Waiting to start"**

<code-block>
{   
  "type": "broadcast",   
  "message": {   
    "broadcast": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "status": "<span style="color:#FF5913">pending</span>"   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the broadcast ID in your personal account,
- <span style="color:#FF5913">pending</span> is the status which means "Waiting to start".

**A broadcast status is updated to "Live"**

<code-block>
{   
  "type": "broadcast",   
  "message": {   
    "broadcast": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "status": "<span style="color:#FF5913">live</span>"   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the broadcast ID in your personal account,
- <span style="color:#FF5913">live</span> is the status which means "Live".

**A broadcast status is updated to "Finished"**

<code-block>
{   
  "type": "broadcast",   
  "message": {   
    "broadcast": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "status": "<span style="color:#FF5913">finished</span>"   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the broadcast ID in your personal account,
- <span style="color:#FF5913">finished</span> is the status which means "Finished".

**A broadcast status is updated to "Paused"**

<code-block>
{   
  "type": "broadcast",   
  "message": {   
    "broadcast": {   
      "id": <span style="color:#FF5913">12345</span>,   
      "status": "<span style="color:#FF5913">paused</span>"  
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">12345</span> is the broadcast ID in your personal account,
- <span style="color:#FF5913">paused</span> is the status which means "Paused".

**A video is uploaded to the Video Streaming**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">54321</span>,   
      "slug": "<span style="color:#FF5913">Lfsq14hKvLkNsExx</span>",   
      "name": "<span style="color:#FF5913">SampleVideo</span>",   
      "duration": <span style="color:#FF5913">170859</span>,   
      "status": "<span style="color:#FF5913">empty</span>",   
      "converted_videos": []   
    }   
  }   
} 
</code-block>

Where:

- <span style="color:#FF5913">54321</span> is the video ID in the Gcore Customer Portal,
- <span style="color:#FF5913">Lfsq14hKvLkNsExx</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">SampleVideo</span> is the video name,
- <span style="color:#FF5913">170859</span> is the duration of the video in seconds,
- <span style="color:#FF5913">empty</span> is the status which means that the video has not been processed yet


**A video has started processing**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">784280</span>,   
      "slug": "<span style="color:#FF5913">Lfsq14hKvLkNsExx</span>",   
      "name": "<span style="color:#FF5913">SampleVideo</span>",   
      "duration": <span style="color:#FF5913">170859</span>,   
      "status": "<span style="color:#FF5913">pending</span>",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod480n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod240n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"  
        }   
      ]   
    }   
  }   
}
</code-block>

Where:

- <span style="color:#FF5913">784280</span> is the video ID in the Gcore Customer Portal,
- <span style="color:#FF5913">Lfsq14hKvLkNsExx</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">SampleVideo</span> is the video name,
- <span style="color:#FF5913">170859</span> is the duration of the video in seconds,
- <span style="color:#FF5913">processing, pending</span> are the different statuses of the video processing.
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the video.  

**A video is partially processed**

<code-block>
{   
  "type": "video",   
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">784280</span>,   
      "slug": "<span style="color:#FF5913">Lfsq14hKvLkNsExx</span>",   
      "name": "<span style="color:#FF5913">SampleVideo</span>",   
      "duration": <span style="color:#FF5913">170859</span>,   
      "status": "<span style="color:#FF5913">viewable</span>",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod480n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"  
        },   
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod240n</span>",   
          "status": "<span style="color:#FF5913">processing</span>"  
        }   
      ]   
    }   
  }  
}
</code-block>

Where:

- <span style="color:#FF5913">784280</span> is the video ID in the Gcore Customer Portal,
- <span style="color:#FF5913">Lfsq14hKvLkNsExx</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">SampleVideo</span> is the video name,
- <span style="color:#FF5913">170859</span> is the duration of the video in seconds,
- <span style="color:#FF5913">processing, complete, viewable</span> are the different statuses of the video processing.
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the video.  


**A video is completely processed**

<code-block>
{   
  "type": "video",  
  "message": {   
    "video": {   
      "id": <span style="color:#FF5913">784280</span>,   
      "slug": "<span style="color:#FF5913">Lfsq14hKvLkNsExx</span>",   
      "name": "<span style="color:#FF5913">SampleVideo</span>",   
      "duration": <span style="color:#FF5913">170859</span>,   
      "status": "<span style="color:#FF5913">ready</span>",   
      "converted_videos": [   
        {   
          "name": "<span style="color:#FF5913">vod720n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod480n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod360n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        },   
        {   
          "name": "<span style="color:#FF5913">vod240n</span>",   
          "status": "<span style="color:#FF5913">complete</span>"   
        }   
      ]   
    }   
  }  
}
</code-block>

Where:

- <span style="color:#FF5913">784280</span> is the video ID in the Gcore Customer Portal,
- <span style="color:#FF5913">Lfsq14hKvLkNsExx</span> is the video ID presented as a random set of characters, which prevents a video URL from stealing if the webhook is intercepted,
- <span style="color:#FF5913">SampleVideo</span> is the video name,
- <span style="color:#FF5913">170859</span> is the duration of the video in seconds,
- <span style="color:#FF5913">complete, ready</span> is the status which means that the video was processed.
- <span style="color:#FF5913">vod720n, vod480n, vod360n, vod240n</span> are the different qualities of the video. 

**A restream was created**

<code-block>
{ 
  "type": "restream", 
  "message": { 
    "restream": { 
      "id": <span style="color:#FF5913">228237<span>, 
      "name": "<span style="color:#FF5913">restream 1</span>", 
      "stream_id": <span style="color:#FF5913">1665243</span>, 
      "live": <span style="color:#FF5913">true</span> 
      "active": <span style="color:#FF5913">false</span> 
    } 
  }
}
</code-block>  

Where:

- <span style="color:#FF5913">228237</span> is the restream ID in Gcore Customer Portal
- <span style="color:#FF5913"> restream 1</span> is the name of your restream
- <span style="color:#FF5913">1665243</span> is the stream ID in Gcore Customer Portal
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your restream
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being broadcasted

**A restream is live**

<code-block>
{ 
  "type": "restream", 
  "message": { 
    "restream": { 
      "id": 228237, 
      "name": "restream 1", 
      "stream_id": 1665243, 
      "live": true 
    } 
  } 
} 
</code-block>  

Where:

- <span style="color:#FF5913">228237</span> is the restream ID in Gcore Customer Portal
- <span style="color:#FF5913"> restream 1</span> is the name of your restream
- <span style="color:#FF5913">1665243</span> is the stream ID in Gcore Customer Portal
- <span style="color:#FF5913">true</span> is the indicator that the Video Streaming is receiving your restream

**A restream was stopped**

<code-block>
{ 
  "type": "restream", 
  "message": { 
    "restream": { 
      "id": 228237, 
      "name": "restream 1", 
      "stream_id": 1665243, 
      "active": false 
    } 
  } 
} 
</code-block>

Where:

- <span style="color:#FF5913">228237</span> is the restream ID in Gcore Customer Portal
- <span style="color:#FF5913"> restream 1</span> is the name of your restream
- <span style="color:#FF5913">1665243</span> is the stream ID in Gcore Customer Portal
- <span style="color:#FF5913">false</span> is the indicator that your stream is not being broadcasted