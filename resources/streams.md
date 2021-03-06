# Streams

***

Streams are video broadcasts that are currently live. They have a [broadcaster][users] and are part of a [channel][channels].

| Endpoint | Description |
| ---- | --------------- |
| [GET /streams/:channel/](/resources/streams.md#get-streamschannel) | Get stream object |
| [GET /streams](/resources/streams.md#get-streams) | Get stream object |
| [GET /streams/featured](/resources/streams.md#get-streamsfeatured) | Get a list of featured streams |
| [GET /streams/summary](/resources/streams.md#get-streamssummary) | Get a summary of streams |
| [GET /streams/followed](/resources/streams.md#get-streamsfollowed) | Get a list of streams user is following |

[users]: /resources/users.md
[channels]: /resources/channels.md

## `GET /streams/:channel/`

Returns a stream object if live.

### Example Request

```bash
curl -i https://api.twitch.tv/kraken/streams/test_channel
```

### Example Response

#### If offline

```json
{
  "stream": null,
  "_links": {
    "self": "https://api.twitch.tv/kraken/streams/test_channel",
    "channel": "https://api.twitch.tv/kraken/channels/test_channel"
  }
}
```

#### If online

```json
{
  "_links": {
    "channel": "https://api.twitch.tv/kraken/channels/test_channel",
    "self": "https://api.twitch.tv/kraken/streams/test_channel"
  },
  "stream": {
    "_links": {
      "self": "https://api.twitch.tv/kraken/streams/test_channel"
    },
    "broadcaster": "test_user1",
    "preview": "http://static-cdn.jtvnw.net/previews-ttv/live_user_test_channel-320x200.jpg",
    "_id": 4869165040,
    "viewers": 11754,
    "channel": {
      "display_name": "test_channel",
      "_links": {
        "stream_key": "https://api.twitch.tv/kraken/channels/test_channel/stream_key",
        "editors": "https://api.twitch.tv/kraken/channels/test_channel/editors",
        "subscriptions": "https://api.twitch.tv/kraken/channels/test_channel/subscriptions",
        "commercial": "https://api.twitch.tv/kraken/channels/test_channel/commercial",
        "videos": "https://api.twitch.tv/kraken/channels/test_channel/videos",
        "follows": "https://api.twitch.tv/kraken/channels/test_channel/follows",
        "self": "https://api.twitch.tv/kraken/channels/test_channel",
        "chat": "https://api.twitch.tv/kraken/chat/test_channel",
        "features": "https://api.twitch.tv/kraken/channels/test_channel/features"
      },
      "teams": [ ],
      "status": "Testing 1 2 3",
      "created_at": "2011-12-23T18:03:44Z",
      "logo": "http://static-cdn.jtvnw.net/jtv_user_pictures/test_channel-profile_image-1806cdccb1108442-300x300.jpeg",
      "updated_at": "2013-02-15T15:22:24Z",
      "mature": null,
      "video_banner": null,
      "_id": 26991613,
      "background": "http://static-cdn.jtvnw.net/jtv_user_pictures/test_channel-channel_background_image-21fffe7f0c309a23.jpeg",
      "banner": "http://static-cdn.jtvnw.net/jtv_user_pictures/test_channel-channel_header_image-4eb6147d464d9053-640x125.jpeg",
      "name": "test_channel",
      "url": "http://www.twitch.tv/test_channel",
      "game": "Magic: The Gathering"
    },
    "name": "test_channel",
    "game": "Magic: The Gathering"
  }
}
```

## `GET /streams`

Returns a list of stream objects that are queried by a number of parameters.

### Parameters

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Required?</th>
            <th width="50">Type</th>
            <th width=100%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>game</code></td>
            <td>optional</td>
            <td>string</td>
            <td>Streams categorized under <code>game</code>.</td>
        </tr>
        <tr>
            <td><code>channel</code></td>
            <td>optional</td>
            <td>string</td>
            <td>Streams from a comma separated list of channels.</td>
        </tr>
        <tr>
            <td><code>limit</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Maximum number of objects in array. Default is 25. Maximum is 100.</td>
        </tr>
        <tr>
            <td><code>offset</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Object offset for pagination. Default is 0.</td>
        </tr>
        <tr>
            <td><code>embeddable</code></td>
            <td>optional</td>
            <td>bool</td>
            <td>If set to true, only returns streams that can be embedded</td>
        </tr>
        <tr>
            <td><code>hls</code></td>
            <td>optional</td>
            <td>bool</td>
            <td>If set to true, only returns streams using HLS</td>
        </tr>
    </tbody>
</table>

### Example Request

### Example Response

#### Get list of Diablo III streams

`GET /streams?game=Diablo+III`

#### Get multiple channels

`GET /streams?channel=incredibleorb,incontroltv`

## `GET /streams/featured`

Returns a list of featured (promoted) stream objects.

### Parameters

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Required?</th>
            <th width="50">Type</th>
            <th width=100%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>limit</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Maximum number of objects in array. Default is 25. Maximum is 100.</td>
        </tr>
        <tr>
            <td><code>offset</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Object offset for pagination. Default is 0.</td>
        </tr>
        <tr>
            <td><code>hls</code></td>
            <td>optional</td>
            <td>bool</td>
            <td>If set to true, only returns streams using HLS</td>
        </tr>
    </tbody>
</table>

Note that the number of promoted streams varies from day to day, and there is no guarantee on how many streams will be promoted at a given time.

### Example Request

```bash
curl -i https://api.twitch.tv/kraken/streams/featured
```

### Example Response

```json
{
  "_links": {
     "self": "https://api.twitch.tv/kraken/streams/featured?limit=25&offset=0",
     "next": "https://api.twitch.tv/kraken/streams/featured?limit=25&offset=25"
  },
  "featured": [
    {
      "image": "http://s.jtvnw.net/jtv_user_pictures/hosted_images/therun.jpg",
      "text": "This is the run! Watch as multi-time world record Super Mario 64 gamer, Siglemic, pushes the N64 classic to its absolute limits.",
      "stream": {
        ...
      }
    },
    [...]
  ]
}
```
    
## `GET /streams/summary`

Returns a summary of current streams.

### Parameters

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Required?</th>
            <th width="50">Type</th>
            <th width=100%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>limit</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Maximum number of objects in array. Default is 25. Maximum is 100.</td>
        </tr>
        <tr>
            <td><code>offset</code></td>
            <td>optional</td>
            <td>integer</td>
            <td>Object offset for pagination. Default is 0.</td>
        </tr>
        <tr>
            <td><code>hls</code></td>
            <td>optional</td>
            <td>bool</td>
            <td>If set to true, only returns streams using HLS</td>
        </tr>
    </tbody>
</table>

### Example Request

```bash
curl -i https://api.twitch.tv/kraken/streams/summary
```

### Example Response

```json
{
  "viewers": 194774,
  "_links": {
    "self": "https://api.twitch.tv/kraken/streams/summary"
  },
  "channels": 4144
}
```

## `GET /streams/followed`

[See the Users resource][users]

[users]: /resources/users.md

## Embedding

[See here for embedding.][embedding]

[embedding]: /embedding.md#embedding-streams-vods-and-chat
