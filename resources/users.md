# Users

These are members of the Twitch community who have a Twitch account. If broadcasting, they can own a [stream][streams] that they can broadcast on their [channel][channels]. If mainly viewing, they might [follow][follows] or [subscribe][subscriptions] to channels.

[streams]: /resources/streams.md
[channels]: /resources/channels.md
[follows]: /resources/follows.md
[subscriptions]: /resources/subscriptions.md

## Get user

`GET /users/:user`

Returns a user object.

### Response

```json
{
  "name": "hebo",
  "created_at": "2011-03-19T15:42:22Z",
  "updated_at": "2012-06-14T00:14:27Z",
  "_links": {
    "self": "https://api.twitch.tv/kraken/users/hebo"
  },
  "logo": "http://static-cdn.jtvnw.net/jtv_user_pictures/hebo-profile_image-6947308654ad603f-300x300.jpeg",
  "_id": 21229404,
  "display_name": "Hebo"
}
```

## Get authenticated user <a id="user"/>

`GET /user`

_Authenticated_, required scope: `user_read`

Returns an authenticated user object.

### Response

```json
{
  "name": "cevtest12",
  "created_at": "2011-06-03T17:49:19Z",
  "updated_at": "2012-06-18T17:19:57Z",
  "_links": {
    "self": "https://api.twitch.tv/kraken/users/cevtest12"
  },
  "logo": "http://static-cdn.jtvnw.net/jtv_user_pictures/cevtest12-profile_image-62e8318af864d6d7-300x300.jpeg",
  "_id": 22761313,
  "display_name": "Cevtest12",
  "email": "asdf@asdf.com",
  "partnered": true
}
```

## Get a list of followed streams

`GET /streams/followed`

_Authenticated_, required scope: `user_read`

List the live streams that the authenticated user is following.

### Response

```json
{
  "_links": {
    "self": "https://api.twitch.tv/kraken/streams/followed?limit=25&offset=0",
    "next": "https://api.twitch.tv/kraken/streams/followed?limit=25&offset=25"
  },
  "streams": [...]
}
```
