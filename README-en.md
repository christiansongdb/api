# Christian Song Database API
**EN** | [PT](README.md)

API for accessing information and content available in the Christian Song Database.<br/>
By using the API you agree to the [Terms of Service](https://api.csdb.app/terms).<br/>
<br/>

Christian Song Database (CSDB) is a database of evangelical songs that was created with the aim of storing and concentrating reliable information in one place.<br>
Stores the id/link of a song across different streaming services, maintaining the correct version compatible with each recording, reducing the risk of the song version in one streaming link being different from the song version in another streaming.<br>
It also stores information about the songwriters, as well as relationships that may be interesting, such as the list of compositions by a particular person, the list of songs that use the same composition, what the original composition is when a song is translated from another language, etc.

---

## Request
All API responses return a standard object:
| Name | Type  | Description |
| ---- | :---: | ------------|
| `status` | _String_ | It might be *'ok'* or *'error'* |
| `error` | _String (optional)_ | Error message if status equals *error* |
| `result` | _Object (optional)_ | Response content if *status* equals *ok* |

default URL
```
https://api.csdb.app/v1/
```

# Available endpoints 
  - [profile/{id}](#profileid)
  - [work/{id}](#workid)
  - [track/{id}](#trackid)
  - [profile/{id}/tracks](#profileidtracks)
  - [profile/{id}/works](#profileidworks)
  - [work/{id}/recordings](#workidrecordings)
  - [work/{id}/versions](#workidversions)
  - [work/{id}/recordings_and_versions](#workidrecordingsandversions)
  - [{external_link_type}/profile/{id}](#externallinktypeprofileid)
  - [{external_link_type}/track/{id}](#externallinktypetrackid)
  - [popular/profile](#popularprofile)
  - [popular/track](#populartrack)
  - [popular/work](#popularwork)
  - [search/profile](#searchprofile)
  - [search/track](#searchtrack)


---

### profile/{id}
Returns a profile

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Profile ID |


**Response:**

| Type  |
| :---: |
| _[Profile](#profile)_ | 


**Example:** [` api.csdb.app/v1/profile/5450607 `](https://api.csdb.app/v1/profile/5450607)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "id": 5450607,
    "name": "Aline Kistenmacker Barros dos Santos",
    "alias": "Aline Barros",
    "alias_author": "",
    "country": "BR",
    "copyright": "",
    "about": "",
    "gospel": true,
    "site": null,
    "work_count": 61,
    "track_count": 820,
    "external_links": [
      {
        "type": "spotify",
        "id": "2aKyKSggb31Kw9s9i3iXoo",
        "url": "https://open.spotify.com/artist/2aKyKSggb31Kw9s9i3iXoo",
        "uri": "spotify:artist:2aKyKSggb31Kw9s9i3iXoo"
      },
      {
        "type": "youtube",
        "id": "UCK_FvuzJN7rP4k2Ppwnvj5g",
        "url": "https://www.youtube.com/channel/UCK_FvuzJN7rP4k2Ppwnvj5g"
      },
      {
        "type": "youtube_music",
        "id": "UCLht-MP7US76eAlqD1xuDng",
        "url": "https://music.youtube.com/channel/UCLht-MP7US76eAlqD1xuDng"
      },
      {
        "type": "deezer",
        "id": "14000",
        "url": "https://www.deezer.com/artist/14000",
        "uri": "deezer://www.deezer.com/artist/14000"
      },
      {
        "type": "multitracks",
        "id": "Aline-Barros",
        "url": "https://www.multitracks.com/artists/Aline-Barros/"
      },
      {
        "type": "letras_mus",
        "id": "aline-barros",
        "url": "https://www.letras.mus.br/aline-barros"
      }
    ],
    "_links": {
      "_self": "https://api.csdb.app/v1/profile/5450607"
    }
  }
}
```
</details>


---

### work/{id}
Returns a work

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Work ID |


**Response:**

| Type  |
| :---: |
| _[Work](#work)_ | 


**Example:** [` api.csdb.app/v1/work/8063427 `](https://api.csdb.app/v1/work/8063427)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "id": 8063427,
    "title": "Jeová Jireh",
    "year": 2021,
    "language": "por",
    "derived_from": null,
    "references": [
      {
        "type": "author",
        "profile": {
          "id": 6199575,
          "name": "Samuel Messias Cabral",
          "alias": "Samuel Messias",
          "alias_author": "",
          "type": "person",
          "country": "BR",
          "copyright": "",
          "gospel": true,
          "_links": {
            "_self": "https://api.csdb.app/v1/profile/6199575"
          }
        }
      }
    ],
    "recording_count": 12,
    "_links": {
      "_self": "https://api.csdb.app/v1/work/8063427"
    }
  }
}
```
</details>


---

### track/{id}
Returns a song (recording)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |


**Response:**

| Type  |
| :---: |
| _[Track](#track)_ | 


**Example:** [` api.csdb.app/v1/track/3165776 `](https://api.csdb.app/v1/track/3165776)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "id": 3165776,
    "title": "Jeová Jireh",
    "year": 2021,
    "language": "por",
    "isrc": "BXBKK2100090",
    "bpm": "67",
    "key": "G",
    "time_sig": "4/4",
    "references": [
      {
        "type": "artist",
        "profile": {
          "id": 5450607,
          "name": "Aline Kistenmacker Barros dos Santos",
          "alias": "Aline Barros",
          "alias_author": "",
          "type": "person",
          "country": "BR",
          "copyright": "",
          "gospel": true,
          "_links": {
            "_self": "https://api.csdb.app/v1/profile/5450607"
          }
        }
      }
    ],
    "works": [
      {
        "id": 8063427,
        "title": "Jeová Jireh",
        "year": 2021,
        "language": "por",
        "derived_from": null,
        "references": [
          {
            "type": "author",
            "profile": {
              "id": 6199575,
              "name": "Samuel Messias Cabral",
              "alias": "Samuel Messias",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6199575"
              }
            }
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/work/8063427"
        }
      }
    ],
    "external_links": [
      {
        "type": "spotify",
        "id": "1uoA57FMhP9QjZxIJZVEWo",
        "url": "https://open.spotify.com/track/1uoA57FMhP9QjZxIJZVEWo",
        "uri": "spotify:track:1uoA57FMhP9QjZxIJZVEWo"
      },
      {
        "type": "spotify_bt",
        "id": "1HUdrBWYNNB1FdEjHZ4s53",
        "url": "https://open.spotify.com/track/1HUdrBWYNNB1FdEjHZ4s53",
        "uri": "spotify:track:1HUdrBWYNNB1FdEjHZ4s53"
      },
      {
        "type": "youtube",
        "id": "PxHCmlyNvhk",
        "url": "https://music.youtube.com/watch?v=PxHCmlyNvhk"
      },
      {
        "type": "youtube_bt",
        "id": "FMacI8fHefw",
        "url": "https://music.youtube.com/watch?v=FMacI8fHefw"
      },
      {
        "type": "deezer",
        "id": "1617019152",
        "url": "https://www.deezer.com/track/1617019152",
        "uri": "deezer://www.deezer.com/track/1617019152"
      },
      {
        "type": "deezer_bt",
        "id": "1617027062",
        "url": "https://www.deezer.com/track/1617027062",
        "uri": "deezer://www.deezer.com/track/1617027062"
      },
      {
        "type": "letras_mus",
        "id": "aline-barros/jeova-jireh",
        "url": "https://www.letras.mus.br/aline-barros/jeova-jireh"
      }
    ],
    "_links": {
      "_self": "https://api.csdb.app/v1/track/3165776"
    }
  }
}
```
</details>


---

### profile/{id}/tracks
Returns the list of songs from a profile

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |
| `limit` | _Number (optional)_ | `1 ~ 100` `Default: 10` |
| `page` | _Number (optional)_ |  `Default: 1` |
| `order` | _String (optional)_ | Sorting mode of the items.<br>It can be: `title` `popularity` `date` `date_descending` `Default: title` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tracks` | _Array&lt;[Track](#track)&gt;_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `order` | _String_ |  |
| `total` | _Number_ | Total number of available items |


**Example:** [` api.csdb.app/v1/profile/5450607/tracks?limit=10&page=1&order=popularity `](https://api.csdb.app/v1/profile/5450607/tracks?limit=10&page=1&order=popularity)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "tracks": [
      {
        "id": 3165776,
        "title": "Jeová Jireh",
        "year": 2021,
        "language": "por",
        "isrc": "BXBKK2100090",
        "bpm": "67",
        "key": "G",
        "time_sig": "4/4",
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 5450607,
              "name": "Aline Kistenmacker Barros dos Santos",
              "alias": "Aline Barros",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/5450607"
              }
            }
          }
        ],
        "works": [
          {
            "id": 8063427,
            "title": "Jeová Jireh",
            "year": 2021,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 6199575,
                  "name": "Samuel Messias Cabral",
                  "alias": "Samuel Messias",
                  "alias_author": "",
                  "type": "person",
                  "country": "BR",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/6199575"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/8063427"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/3165776"
        }
      }
    ],
    "limit": 10,
    "page": 1,
    "order": "popularity",
    "total": 515
  }
}
```
</details>


---

### profile/{id}/works
Returns the list of compositions of a profile

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Work ID |
| `limit` | _Number (optional)_ | `1 ~ 100` `Default: 10` |
| `page` | _Number (optional)_ |  `Default: 1` |
| `order` | _String (optional)_ | Sorting mode of the items.<br>It can be: `title` `popularity` `date` `date_descending` `Default: title` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `works` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `order` | _String_ |  |
| `total` | _Number_ | Total number of available items |


**Example:** [` api.csdb.app/v1/profile/5450607/works?limit=10&page=1&order=popularity `](https://api.csdb.app/v1/profile/5450607/works?limit=10&page=1&order=popularity)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "works": [
      {
        "id": 7905303,
        "title": "Sonda-me, Usa-me",
        "year": 2004,
        "language": "por",
        "derived_from": null,
        "references": [
          {
            "type": "author",
            "profile": {
              "id": 5450607,
              "name": "Aline Kistenmacker Barros dos Santos",
              "alias": "Aline Barros",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "about": "",
              "gospel": true,
              "site": null,
              "external_links": [],
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/5450607"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 6866327,
              "name": "Edson Feitosa dos Santos",
              "alias": "Edson Feitosa",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "about": "",
              "gospel": true,
              "site": null,
              "external_links": [],
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6866327"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 9875393,
              "name": "Ana Cláudia D'Araújo I. Feitosa dos Santos",
              "alias": "Ana Feitosa",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "about": "",
              "gospel": true,
              "site": null,
              "external_links": [],
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/9875393"
              }
            }
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/work/7905303"
        }
      }
    ],
    "limit": 10,
    "page": 1,
    "order": "popularity",
    "total": 61
  }
}
```
</details>


---

### work/{id}/recordings
Returns the list of recordings of the respective work

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Work ID |
| `limit` | _Number (optional)_ | `1 ~ 100` `Default: 10` |
| `page` | _Number (optional)_ |  `Default: 1` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `recordings` | _[Track](#track)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total` | _Number_ | Total number of available items |


**Example:** [` api.csdb.app/v1/work/8063427/recordings?limit=10&page=1 `](https://api.csdb.app/v1/work/8063427/recordings?limit=10&page=1)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "recordings": [
      {
        "id": 3165776,
        "title": "Jeová Jireh",
        "year": 2021,
        "language": "por",
        "isrc": "BXBKK2100090",
        "bpm": "67",
        "key": "G",
        "time_sig": "4/4",
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 5450607,
              "name": "Aline Kistenmacker Barros dos Santos",
              "alias": "Aline Barros",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/5450607"
              }
            }
          }
        ],
        "works": [
          {
            "id": 8063427,
            "title": "Jeová Jireh",
            "year": 2021,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 6199575,
                  "name": "Samuel Messias Cabral",
                  "alias": "Samuel Messias",
                  "alias_author": "",
                  "type": "person",
                  "country": "BR",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/6199575"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/8063427"
            }
          }
        ],
        "external_links": [
          {
            "type": "spotify",
            "id": "1uoA57FMhP9QjZxIJZVEWo",
            "url": "https://open.spotify.com/track/1uoA57FMhP9QjZxIJZVEWo",
            "uri": "spotify:track:1uoA57FMhP9QjZxIJZVEWo"
          },
          {
            "type": "spotify_bt",
            "id": "1HUdrBWYNNB1FdEjHZ4s53",
            "url": "https://open.spotify.com/track/1HUdrBWYNNB1FdEjHZ4s53",
            "uri": "spotify:track:1HUdrBWYNNB1FdEjHZ4s53"
          },
          {
            "type": "youtube",
            "id": "PxHCmlyNvhk",
            "url": "https://music.youtube.com/watch?v=PxHCmlyNvhk"
          },
          {
            "type": "youtube_bt",
            "id": "FMacI8fHefw",
            "url": "https://music.youtube.com/watch?v=FMacI8fHefw"
          },
          {
            "type": "deezer",
            "id": "1617019152",
            "url": "https://www.deezer.com/track/1617019152",
            "uri": "deezer://www.deezer.com/track/1617019152"
          },
          {
            "type": "deezer_bt",
            "id": "1617027062",
            "url": "https://www.deezer.com/track/1617027062",
            "uri": "deezer://www.deezer.com/track/1617027062"
          },
          {
            "type": "letras_mus",
            "id": "aline-barros/jeova-jireh",
            "url": "https://www.letras.mus.br/aline-barros/jeova-jireh"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/3165776"
        }
      }
    ],
    "limit": 10,
    "page": 1,
    "total": 10
  }
}
```
</details>


---

### work/{id}/versions
Returns the list of derivative works (versions) of the respective work

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Work ID |
| `limit` | _Number (optional)_ | `1 ~ 100` `Default: 10` |
| `page` | _Number (optional)_ |  `Default: 1` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `versions` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total` | _Number_ | Total number of available items |


**Example:** [` api.csdb.app/v1/work/7269270/versions?limit=10&page=1 `](https://api.csdb.app/v1/work/7269270/versions?limit=10&page=1)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "versions": [
      {
        "id": 8947355,
        "title": "Bondade de Deus",
        "year": 2022,
        "language": "por",
        "references": [
          {
            "type": "author",
            "profile": {
              "id": 2073892,
              "name": "Brian Mark Johnson",
              "alias": "Brian Johnson",
              "alias_author": "",
              "type": "person",
              "country": "US",
              "copyright": "",
              "gospel": false,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/2073892"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 2365747,
              "name": "Jason David Ingram",
              "alias": "Jason Ingram",
              "alias_author": "",
              "type": "person",
              "country": "US",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/2365747"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 3475062,
              "name": "Edmond Martin Cash",
              "alias": "Ed Cash",
              "alias_author": "",
              "type": "person",
              "country": "US",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/3475062"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 5081677,
              "name": "Benjamin David Fielding",
              "alias": "Ben Fielding",
              "alias_author": "",
              "type": "person",
              "country": "AU",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/5081677"
              }
            }
          },
          {
            "type": "author",
            "profile": {
              "id": 7545720,
              "name": "Jennifer Louise Johnson",
              "alias": "Jenn Johnson",
              "alias_author": "",
              "type": "person",
              "country": "US",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/7545720"
              }
            }
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/work/8947355"
        }
      }
    ],
    "limit": 10,
    "page": 1,
    "total": 1
  }
}
```
</details>


---

### work/{id}/recordings_and_versions
Returns the list of recordings and the list of derivative works (versions) of the respective work

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Work ID |
| `limit` | _Number (optional)_ | `1 ~ 100` `Default: 10` |
| `page` | _Number (optional)_ |  `Default: 1` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `recordings` | _[Track](#track)_ |  |
| `versions` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total_recordings` | _Number_ | Total number of recordings available |
| `total_versions` | _Number_ | Total number of available versions |


**Example:** [` api.csdb.app/v1/work/7269270/recordings_and_versions?limit=10&page=1 `](https://api.csdb.app/v1/work/7269270/recordings_and_versions?limit=10&page=1)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "recordings_response": {
      "recordings": [
        {
          "id": 2451905,
          "title": "Goodness Of God",
          "year": null,
          "language": "eng",
          "isrc": null,
          "bpm": null,
          "key": null,
          "time_sig": null,
          "references": [
            {
              "type": "artist",
              "profile": {
                "id": 3505099,
                "name": null,
                "alias": "Bethel Music",
                "alias_author": "",
                "type": "group",
                "country": "US",
                "copyright": "",
                "gospel": true,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/3505099"
                }
              }
            }
          ],
          "works": [
            {
              "id": 7269270,
              "title": "Goodness Of God",
              "year": null,
              "language": "eng",
              "derived_from": null,
              "references": [],
              "_links": {
                "_self": "https://api.csdb.app/v1/work/7269270"
              }
            }
          ],
          "external_links": [
            {
              "type": "letras_mus",
              "id": "bethel-music/goodness-of-god",
              "url": "https://www.letras.mus.br/bethel-music/goodness-of-god"
            }
          ],
          "_links": {
            "_self": "https://api.csdb.app/v1/track/2451905"
          }
        }
      ],
      "limit": 10,
      "page": 1,
      "total": 4
    },
    "versions_response": {
      "versions": [
        {
          "id": 8947355,
          "title": "Bondade de Deus",
          "year": 2022,
          "language": "por",
          "references": [
            {
              "type": "author",
              "profile": {
                "id": 2073892,
                "name": "Brian Mark Johnson",
                "alias": "Brian Johnson",
                "alias_author": "",
                "type": "person",
                "country": "US",
                "copyright": "",
                "gospel": false,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/2073892"
                }
              }
            },
            {
              "type": "author",
              "profile": {
                "id": 2365747,
                "name": "Jason David Ingram",
                "alias": "Jason Ingram",
                "alias_author": "",
                "type": "person",
                "country": "US",
                "copyright": "",
                "gospel": true,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/2365747"
                }
              }
            },
            {
              "type": "author",
              "profile": {
                "id": 3475062,
                "name": "Edmond Martin Cash",
                "alias": "Ed Cash",
                "alias_author": "",
                "type": "person",
                "country": "US",
                "copyright": "",
                "gospel": true,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/3475062"
                }
              }
            },
            {
              "type": "author",
              "profile": {
                "id": 5081677,
                "name": "Benjamin David Fielding",
                "alias": "Ben Fielding",
                "alias_author": "",
                "type": "person",
                "country": "AU",
                "copyright": "",
                "gospel": true,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/5081677"
                }
              }
            },
            {
              "type": "author",
              "profile": {
                "id": 7545720,
                "name": "Jennifer Louise Johnson",
                "alias": "Jenn Johnson",
                "alias_author": "",
                "type": "person",
                "country": "US",
                "copyright": "",
                "gospel": true,
                "_links": {
                  "_self": "https://api.csdb.app/v1/profile/7545720"
                }
              }
            }
          ],
          "_links": {
            "_self": "https://api.csdb.app/v1/work/8947355"
          }
        }
      ],
      "limit": 10,
      "page": 1,
      "total": 1
    }
  }
}
```
</details>


---

### {external_link_type}/profile/{id}
Returns the profile based on the ID of the respective external service

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `external_link_type` | _String_ | It can be: `spotify` `youtube` `apple_music` `amazon_music` `deezer` |
| `id` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _[Profile](#profile)_ | 


**Example:** [` api.csdb.app/v1/spotify/profile/2aKyKSggb31Kw9s9i3iXoo `](https://api.csdb.app/v1/spotify/profile/2aKyKSggb31Kw9s9i3iXoo)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "id": 5450607,
    "name": "Aline Kistenmacker Barros dos Santos",
    "alias": "Aline Barros",
    "alias_author": "",
    "type": "person",
    "country": "BR",
    "copyright": "",
    "about": "",
    "gospel": true,
    "site": null,
    "external_links": [
      {
        "type": "spotify",
        "id": "2aKyKSggb31Kw9s9i3iXoo",
        "url": "https://open.spotify.com/artist/2aKyKSggb31Kw9s9i3iXoo",
        "uri": "spotify:artist:2aKyKSggb31Kw9s9i3iXoo"
      },
      {
        "type": "youtube",
        "id": "UCK_FvuzJN7rP4k2Ppwnvj5g",
        "url": "https://www.youtube.com/channel/UCK_FvuzJN7rP4k2Ppwnvj5g"
      },
      {
        "type": "youtube_music",
        "id": "UCLht-MP7US76eAlqD1xuDng",
        "url": "https://music.youtube.com/channel/UCLht-MP7US76eAlqD1xuDng"
      },
      {
        "type": "deezer",
        "id": "14000",
        "url": "https://www.deezer.com/artist/14000",
        "uri": "deezer://www.deezer.com/artist/14000"
      },
      {
        "type": "multitracks",
        "id": "Aline-Barros",
        "url": "https://www.multitracks.com/artists/Aline-Barros/"
      },
      {
        "type": "letras_mus",
        "id": "aline-barros",
        "url": "https://www.letras.mus.br/aline-barros"
      }
    ],
    "_links": {
      "_self": "https://api.csdb.app/v1/profile/5450607"
    }
  }
}
```
</details>


---

### {external_link_type}/track/{id}
Returns the song based on the ID of the respective external service

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `external_link_type` | _String_ | It can be: `isrc` `spotify` `youtube` `apple_music` `amazon_music` `deezer` |
| `id` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _[Track](#track)_ | 


**Example:** [` api.csdb.app/v1/spotify/track/1uoA57FMhP9QjZxIJZVEWo `](https://api.csdb.app/v1/spotify/track/1uoA57FMhP9QjZxIJZVEWo)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "id": 3165776,
    "title": "Jeová Jireh",
    "year": 2021,
    "language": "por",
    "isrc": "BXBKK2100090",
    "bpm": "67",
    "key": "G",
    "time_sig": "4/4",
    "references": [
      {
        "type": "artist",
        "profile": {
          "id": 5450607,
          "name": "Aline Kistenmacker Barros dos Santos",
          "alias": "Aline Barros",
          "alias_author": "",
          "type": "person",
          "country": "BR",
          "copyright": "",
          "gospel": true,
          "_links": {
            "_self": "https://api.csdb.app/v1/profile/5450607"
          }
        }
      }
    ],
    "works": [
      {
        "id": 8063427,
        "title": "Jeová Jireh",
        "year": 2021,
        "language": "por",
        "derived_from": null,
        "references": [
          {
            "type": "author",
            "profile": {
              "id": 6199575,
              "name": "Samuel Messias Cabral",
              "alias": "Samuel Messias",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6199575"
              }
            }
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/work/8063427"
        }
      }
    ],
    "external_links": [
      {
        "type": "spotify",
        "id": "1uoA57FMhP9QjZxIJZVEWo",
        "url": "https://open.spotify.com/track/1uoA57FMhP9QjZxIJZVEWo",
        "uri": "spotify:track:1uoA57FMhP9QjZxIJZVEWo"
      },
      {
        "type": "spotify_bt",
        "id": "1HUdrBWYNNB1FdEjHZ4s53",
        "url": "https://open.spotify.com/track/1HUdrBWYNNB1FdEjHZ4s53",
        "uri": "spotify:track:1HUdrBWYNNB1FdEjHZ4s53"
      },
      {
        "type": "youtube",
        "id": "PxHCmlyNvhk",
        "url": "https://music.youtube.com/watch?v=PxHCmlyNvhk"
      },
      {
        "type": "youtube_bt",
        "id": "FMacI8fHefw",
        "url": "https://music.youtube.com/watch?v=FMacI8fHefw"
      },
      {
        "type": "deezer",
        "id": "1617019152",
        "url": "https://www.deezer.com/track/1617019152",
        "uri": "deezer://www.deezer.com/track/1617019152"
      },
      {
        "type": "deezer_bt",
        "id": "1617027062",
        "url": "https://www.deezer.com/track/1617027062",
        "uri": "deezer://www.deezer.com/track/1617027062"
      },
      {
        "type": "letras_mus",
        "id": "aline-barros/jeova-jireh",
        "url": "https://www.letras.mus.br/aline-barros/jeova-jireh"
      }
    ],
    "_links": {
      "_self": "https://api.csdb.app/v1/track/3165776"
    }
  }
}
```
</details>


---

### popular/profile
Returns the list of popular profiles

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `limit` | _Number (optional)_ | Maximum number of items returned. `1 ~ 100` `Default: 10` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `profiles` | _Array&lt;[Profile](#profile)&gt;_ |  |
| `limit` | _Number_ |  |


**Example:** [` api.csdb.app/v1/popular/profile?limit=5 `](https://api.csdb.app/v1/popular/profile?limit=5)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "profiles": [
      {
        "id": 5450607,
        "name": "Aline Kistenmacker Barros dos Santos",
        "alias": "Aline Barros",
        "alias_author": "",
        "type": "person",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "2aKyKSggb31Kw9s9i3iXoo",
            "url": "https://open.spotify.com/artist/2aKyKSggb31Kw9s9i3iXoo",
            "uri": "spotify:artist:2aKyKSggb31Kw9s9i3iXoo"
          },
          {
            "type": "youtube",
            "id": "UCK_FvuzJN7rP4k2Ppwnvj5g",
            "url": "https://www.youtube.com/channel/UCK_FvuzJN7rP4k2Ppwnvj5g"
          },
          {
            "type": "youtube_music",
            "id": "UCLht-MP7US76eAlqD1xuDng",
            "url": "https://music.youtube.com/channel/UCLht-MP7US76eAlqD1xuDng"
          },
          {
            "type": "deezer",
            "id": "14000",
            "url": "https://www.deezer.com/artist/14000",
            "uri": "deezer://www.deezer.com/artist/14000"
          },
          {
            "type": "multitracks",
            "id": "Aline-Barros",
            "url": "https://www.multitracks.com/artists/Aline-Barros/"
          },
          {
            "type": "letras_mus",
            "id": "aline-barros",
            "url": "https://www.letras.mus.br/aline-barros"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/5450607"
        }
      },
      {
        "id": 6401907,
        "name": "Gabriela Rocha Correa Moreira",
        "alias": "Gabriela Rocha",
        "alias_author": "",
        "type": "person",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "4fdCGYM7dtJLa3LvR1ccto",
            "url": "https://open.spotify.com/artist/4fdCGYM7dtJLa3LvR1ccto",
            "uri": "spotify:artist:4fdCGYM7dtJLa3LvR1ccto"
          },
          {
            "type": "youtube",
            "id": "UC4t2mdI8uAiJDJSRjiWJT1Q",
            "url": "https://www.youtube.com/channel/UC4t2mdI8uAiJDJSRjiWJT1Q"
          },
          {
            "type": "youtube_music",
            "id": "UCtilVkO8eHizeFSs5s5vvCA",
            "url": "https://music.youtube.com/channel/UCtilVkO8eHizeFSs5s5vvCA"
          },
          {
            "type": "deezer",
            "id": "4023522",
            "url": "https://www.deezer.com/artist/4023522",
            "uri": "deezer://www.deezer.com/artist/4023522"
          },
          {
            "type": "multitracks",
            "id": "Gabriela-Rocha",
            "url": "https://www.multitracks.com/artists/Gabriela-Rocha/"
          },
          {
            "type": "letras_mus",
            "id": "gabriela-rocha",
            "url": "https://www.letras.mus.br/gabriela-rocha"
          },
          {
            "type": "wikipedia",
            "id": "Gabriela_Rocha",
            "language": "pt",
            "url": "https://pt.wikipedia.org/wiki/Gabriela_Rocha"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/6401907"
        }
      },
      {
        "id": 6686102,
        "name": null,
        "alias": "Diante do Trono",
        "alias_author": "",
        "type": "group",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "4AeWCU2yUgVFbqKmOezL75",
            "url": "https://open.spotify.com/artist/4AeWCU2yUgVFbqKmOezL75",
            "uri": "spotify:artist:4AeWCU2yUgVFbqKmOezL75"
          },
          {
            "type": "youtube",
            "id": "UCmofVw_WgKPDy3pEiXLskug",
            "url": "https://www.youtube.com/channel/UCmofVw_WgKPDy3pEiXLskug"
          },
          {
            "type": "youtube_music",
            "id": "UCOajFLbHBSI0U0oNs3lB-ng",
            "url": "https://music.youtube.com/channel/UCOajFLbHBSI0U0oNs3lB-ng"
          },
          {
            "type": "deezer",
            "id": "1264091",
            "url": "https://www.deezer.com/artist/1264091",
            "uri": "deezer://www.deezer.com/artist/1264091"
          },
          {
            "type": "multitracks",
            "id": "Diante-do-Trono",
            "url": "https://www.multitracks.com/artists/Diante-do-Trono/"
          },
          {
            "type": "letras_mus",
            "id": "diante-do-trono",
            "url": "https://www.letras.mus.br/diante-do-trono"
          },
          {
            "type": "wikipedia",
            "id": "Diante_do_Trono",
            "language": "pt",
            "url": "https://pt.wikipedia.org/wiki/Diante_do_Trono"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/6686102"
        }
      },
      {
        "id": 5580760,
        "name": "Fernando Jerônimo dos Santos Júnior",
        "alias": "Fernandinho",
        "alias_author": "",
        "type": "person",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "6iAY2AyUZLSX3PWLIAfFZY",
            "url": "https://open.spotify.com/artist/6iAY2AyUZLSX3PWLIAfFZY",
            "uri": "spotify:artist:6iAY2AyUZLSX3PWLIAfFZY"
          },
          {
            "type": "youtube",
            "id": "UCH1U29foC-5RyAa4ZgkuQYA",
            "url": "https://www.youtube.com/channel/UCH1U29foC-5RyAa4ZgkuQYA"
          },
          {
            "type": "youtube_music",
            "id": "UCwQLQJL8Cpyk5tVPOJdXJgw",
            "url": "https://music.youtube.com/channel/UCwQLQJL8Cpyk5tVPOJdXJgw"
          },
          {
            "type": "deezer",
            "id": "1352049",
            "url": "https://www.deezer.com/artist/1352049",
            "uri": "deezer://www.deezer.com/artist/1352049"
          },
          {
            "type": "multitracks",
            "id": "Fernandinho",
            "url": "https://www.multitracks.com/artists/Fernandinho/"
          },
          {
            "type": "letras_mus",
            "id": "fernandinho",
            "url": "https://www.letras.mus.br/fernandinho"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/5580760"
        }
      },
      {
        "id": 8963068,
        "name": "Nívea da Costa Pinto Soares",
        "alias": "Nívea Soares",
        "alias_author": "",
        "type": "person",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "7FJXPSSrHgr0YDfeiQ63uk",
            "url": "https://open.spotify.com/artist/7FJXPSSrHgr0YDfeiQ63uk",
            "uri": "spotify:artist:7FJXPSSrHgr0YDfeiQ63uk"
          },
          {
            "type": "youtube",
            "id": "UCZfSPADOfrGs4ub5XLfywFQ",
            "url": "https://www.youtube.com/channel/UCZfSPADOfrGs4ub5XLfywFQ"
          },
          {
            "type": "youtube_music",
            "id": "UCSAm-SyAHDUFMYUew6Iuw-w",
            "url": "https://music.youtube.com/channel/UCSAm-SyAHDUFMYUew6Iuw-w"
          },
          {
            "type": "deezer",
            "id": "1511656",
            "url": "https://www.deezer.com/artist/1511656",
            "uri": "deezer://www.deezer.com/artist/1511656"
          },
          {
            "type": "multitracks",
            "id": "Nivea-Soares",
            "url": "https://www.multitracks.com/artists/Nivea-Soares/"
          },
          {
            "type": "letras_mus",
            "id": "nivea-soares",
            "url": "https://www.letras.mus.br/nivea-soares"
          },
          {
            "type": "wikipedia",
            "id": "Nívea_Soares",
            "language": "pt",
            "url": "https://pt.wikipedia.org/wiki/Nívea_Soares"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/8963068"
        }
      }
    ],
    "limit": 5
  }
}
```
</details>


---

### popular/track
Returns the list of popular songs

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `profile` | _String (optional)_ | Profile ID to return only the songs from a specific profile |
| `limit` | _Number (optional)_ | Maximum number of items returned. `1 ~ 100` `Default: 10` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tracks` | _Array&lt;[Track](#track)&gt;_ |  |
| `limit` | _Number_ |  |


**Example:** [` api.csdb.app/v1/popular/track?profile=&limit=5 `](https://api.csdb.app/v1/popular/track?profile=&limit=5)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "tracks": [
      {
        "id": 9103469,
        "title": "Porque Ele Vive",
        "year": 1971,
        "language": "por",
        "isrc": null,
        "bpm": null,
        "key": null,
        "time_sig": null,
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 2803360,
              "name": null,
              "alias": "Harpa Cristã",
              "alias_author": "",
              "type": "hymnal",
              "country": null,
              "copyright": "",
              "about": "",
              "gospel": true,
              "site": null,
              "external_links": [
                {
                  "type": "letras_mus",
                  "id": "harpa-crista",
                  "url": "https://www.letras.mus.br/harpa-crista"
                }
              ],
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/2803360"
              }
            }
          }
        ],
        "works": [
          {
            "id": 2156246,
            "title": "Porque Ele Vive",
            "year": 1971,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 5368196,
                  "name": "Gloria Lee Sickal",
                  "alias": "Gloria Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "about": "",
                  "gospel": true,
                  "site": null,
                  "external_links": [
                    {
                      "type": "spotify",
                      "id": "1NUEskG7Eh72xoCMvtvn5C",
                      "url": "https://open.spotify.com/artist/1NUEskG7Eh72xoCMvtvn5C",
                      "uri": "spotify:artist:1NUEskG7Eh72xoCMvtvn5C"
                    },
                    {
                      "type": "wikipedia",
                      "id": "Gloria_Gaither",
                      "language": "en",
                      "url": "https://en.wikipedia.org/wiki/Gloria_Gaither"
                    }
                  ],
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/5368196"
                  }
                }
              },
              {
                "type": "author",
                "profile": {
                  "id": 9132429,
                  "name": "William James Gaither",
                  "alias": "William Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "about": "",
                  "gospel": true,
                  "site": null,
                  "external_links": [
                    {
                      "type": "spotify",
                      "id": "1rKNroS04wbR4kgHIGBghY",
                      "url": "https://open.spotify.com/artist/1rKNroS04wbR4kgHIGBghY",
                      "uri": "spotify:artist:1rKNroS04wbR4kgHIGBghY"
                    },
                    {
                      "type": "wikipedia",
                      "id": "Bill_Gaither",
                      "language": "en",
                      "url": "https://en.wikipedia.org/wiki/Bill_Gaither"
                    }
                  ],
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9132429"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/2156246"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/9103469"
        }
      }
    ],
    "limit": 5
  }
}
```
</details>


---

### popular/work
Returns the list of popular works

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `profile` | _String (optional)_ | Profile ID to return only the works of a specific profile |
| `limit` | _Number (optional)_ | Maximum number of items returned. `1 ~ 100` `Default: 10` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `works` | _Array&lt;[Work](#work)&gt;_ |  |
| `limit` | _Number_ |  |


**Example:** [` api.csdb.app/v1/popular/work?profile=&limit=5 `](https://api.csdb.app/v1/popular/work?profile=&limit=5)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "tracks": [
      {
        "id": 9103469,
        "title": "Porque Ele Vive",
        "year": 1971,
        "language": "por",
        "isrc": null,
        "bpm": null,
        "key": null,
        "time_sig": null,
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 2803360,
              "name": null,
              "alias": "Harpa Cristã",
              "alias_author": "",
              "type": "hymnal",
              "country": null,
              "copyright": "",
              "about": "",
              "gospel": true,
              "site": null,
              "external_links": [
                {
                  "type": "letras_mus",
                  "id": "harpa-crista",
                  "url": "https://www.letras.mus.br/harpa-crista"
                }
              ],
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/2803360"
              }
            }
          }
        ],
        "works": [
          {
            "id": 2156246,
            "title": "Porque Ele Vive",
            "year": 1971,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 5368196,
                  "name": "Gloria Lee Sickal",
                  "alias": "Gloria Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "about": "",
                  "gospel": true,
                  "site": null,
                  "external_links": [
                    {
                      "type": "spotify",
                      "id": "1NUEskG7Eh72xoCMvtvn5C",
                      "url": "https://open.spotify.com/artist/1NUEskG7Eh72xoCMvtvn5C",
                      "uri": "spotify:artist:1NUEskG7Eh72xoCMvtvn5C"
                    },
                    {
                      "type": "wikipedia",
                      "id": "Gloria_Gaither",
                      "language": "en",
                      "url": "https://en.wikipedia.org/wiki/Gloria_Gaither"
                    }
                  ],
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/5368196"
                  }
                }
              },
              {
                "type": "author",
                "profile": {
                  "id": 9132429,
                  "name": "William James Gaither",
                  "alias": "William Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "about": "",
                  "gospel": true,
                  "site": null,
                  "external_links": [
                    {
                      "type": "spotify",
                      "id": "1rKNroS04wbR4kgHIGBghY",
                      "url": "https://open.spotify.com/artist/1rKNroS04wbR4kgHIGBghY",
                      "uri": "spotify:artist:1rKNroS04wbR4kgHIGBghY"
                    },
                    {
                      "type": "wikipedia",
                      "id": "Bill_Gaither",
                      "language": "en",
                      "url": "https://en.wikipedia.org/wiki/Bill_Gaither"
                    }
                  ],
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9132429"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/2156246"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/9103469"
        }
      }
    ],
    "limit": 5
  }
}
```
</details>


---

### search/profile
Search for a profile by name

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `q` | _String_ | Text to be searched |


**Response:**

| Name | Type  |
| ---- | :---: |
| `profiles` | _Array&lt;[Profile](#profile)&gt;_| 


**Example:** [` api.csdb.app/v1/search/profile?q=fernandinho `](https://api.csdb.app/v1/search/profile?q=fernandinho)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "profiles": [
      {
        "id": 5580760,
        "name": "Fernando Jerônimo dos Santos Júnior",
        "alias": "Fernandinho",
        "alias_author": "",
        "type": "person",
        "country": "BR",
        "copyright": "",
        "about": "",
        "gospel": true,
        "site": null,
        "external_links": [
          {
            "type": "spotify",
            "id": "6iAY2AyUZLSX3PWLIAfFZY",
            "url": "https://open.spotify.com/artist/6iAY2AyUZLSX3PWLIAfFZY",
            "uri": "spotify:artist:6iAY2AyUZLSX3PWLIAfFZY"
          },
          {
            "type": "youtube",
            "id": "UCH1U29foC-5RyAa4ZgkuQYA",
            "url": "https://www.youtube.com/channel/UCH1U29foC-5RyAa4ZgkuQYA"
          },
          {
            "type": "youtube_music",
            "id": "UCwQLQJL8Cpyk5tVPOJdXJgw",
            "url": "https://music.youtube.com/channel/UCwQLQJL8Cpyk5tVPOJdXJgw"
          },
          {
            "type": "deezer",
            "id": "1352049",
            "url": "https://www.deezer.com/artist/1352049",
            "uri": "deezer://www.deezer.com/artist/1352049"
          },
          {
            "type": "multitracks",
            "id": "Fernandinho",
            "url": "https://www.multitracks.com/artists/Fernandinho/"
          },
          {
            "type": "letras_mus",
            "id": "fernandinho",
            "url": "https://www.letras.mus.br/fernandinho"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/profile/5580760"
        }
      }
    ]
  }
}
```
</details>


---

### search/track
Search for a song by name

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `q` | _String_ | Text to be searched |


**Response:**

| Name | Type  |
| ---- | :---: |
| `tracks` | _Array&lt;[Track](#track)&gt;_| 


**Example:** [` api.csdb.app/v1/search/track?q=a%20ele%20a%20gloria `](https://api.csdb.app/v1/search/track?q=a%20ele%20a%20gloria)<br>

<details>
  <summary>Response</summary>

```json
{
  "status": "ok",
  "result": {
    "tracks": [
      {
        "id": 4055834,
        "title": "A Ele a Glória",
        "year": 1999,
        "language": "por",
        "isrc": "BRMLH0400046",
        "bpm": "76",
        "key": "Em",
        "time_sig": "4/4",
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 6686102,
              "name": null,
              "alias": "Diante do Trono",
              "alias_author": "",
              "type": "group",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6686102"
              }
            }
          }
        ],
        "works": [
          {
            "id": 3651970,
            "title": "A Ele a Glória",
            "year": 1999,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 9265151,
                  "name": "Paul Kevin Jonas Sr.",
                  "alias": "Kevin Jonas",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9265151"
                  }
                }
              },
              {
                "type": "versionist",
                "profile": {
                  "id": 6179930,
                  "name": "Ana Paula Machado Valadão Bessa",
                  "alias": "Ana Paula Valadão",
                  "alias_author": "",
                  "type": "person",
                  "country": "BR",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/6179930"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/3651970"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/4055834"
        }
      },
      {
        "id": 8566982,
        "title": "A Ele a Glória",
        "year": 2019,
        "language": "por",
        "isrc": "BR4WM1900007",
        "bpm": "68",
        "key": "F#",
        "time_sig": "4/4",
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 6401907,
              "name": "Gabriela Rocha Correa Moreira",
              "alias": "Gabriela Rocha",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6401907"
              }
            }
          }
        ],
        "works": [
          {
            "id": 3651970,
            "title": "A Ele a Glória",
            "year": 1999,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 9265151,
                  "name": "Paul Kevin Jonas Sr.",
                  "alias": "Kevin Jonas",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9265151"
                  }
                }
              },
              {
                "type": "versionist",
                "profile": {
                  "id": 6179930,
                  "name": "Ana Paula Machado Valadão Bessa",
                  "alias": "Ana Paula Valadão",
                  "alias_author": "",
                  "type": "person",
                  "country": "BR",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/6179930"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/3651970"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/8566982"
        }
      },
      {
        "id": 5245461,
        "title": "A Ele a Glória, Porque Ele Vive",
        "year": 2020,
        "language": "por",
        "isrc": "BR4WM2000005",
        "bpm": null,
        "key": null,
        "time_sig": null,
        "references": [
          {
            "type": "artist",
            "profile": {
              "id": 6401907,
              "name": "Gabriela Rocha Correa Moreira",
              "alias": "Gabriela Rocha",
              "alias_author": "",
              "type": "person",
              "country": "BR",
              "copyright": "",
              "gospel": true,
              "_links": {
                "_self": "https://api.csdb.app/v1/profile/6401907"
              }
            }
          }
        ],
        "works": [
          {
            "id": 2156246,
            "title": "Porque Ele Vive",
            "year": 1971,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 5368196,
                  "name": "Gloria Lee Sickal",
                  "alias": "Gloria Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/5368196"
                  }
                }
              },
              {
                "type": "author",
                "profile": {
                  "id": 9132429,
                  "name": "William James Gaither",
                  "alias": "William Gaither",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9132429"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/2156246"
            }
          },
          {
            "id": 3651970,
            "title": "A Ele a Glória",
            "year": 1999,
            "language": "por",
            "derived_from": null,
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 9265151,
                  "name": "Paul Kevin Jonas Sr.",
                  "alias": "Kevin Jonas",
                  "alias_author": "",
                  "type": "person",
                  "country": "US",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/9265151"
                  }
                }
              },
              {
                "type": "versionist",
                "profile": {
                  "id": 6179930,
                  "name": "Ana Paula Machado Valadão Bessa",
                  "alias": "Ana Paula Valadão",
                  "alias_author": "",
                  "type": "person",
                  "country": "BR",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/6179930"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/3651970"
            }
          }
        ],
        "external_links": [],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/5245461"
        }
      }
    ]
  }
}
```
</details>


---



# Classes

## Profile
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String (optional)_ | Full name |
| `alias` | _String_ | Stage name |
| `alias_author` | _String_ | Alternative name (optional) used in places that inform author/composer |
| `type` | _String_ | Profile type.<br>It can be: `person` `group` `label` `publisher` `hymnal` |
| `country` | _String_ | ISO 639 two-letter language code |
| `copyright` | _String_ |  |
| `about` | _String_ |  |
| `gospel` | _Boolean_ | **true** if the profile is associated with a person/group/evangelical band |
| `site` | _String_ | https://example.com |
| `work_count` | _Number_ | Number of compositions associated with the profile |
| `track_count` | _Number_ | Number of recordings associated with the profile |
| `external_links` | _Array&lt;[ExternalLink](#externallink)&gt;_ | External profile links (for example, social media) |

## Work
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `title` | _String_ | Title of the work |
| `year` | _Number_ |  |
| `language` | _String_ | ISO 639 three-letter language code |
| `derived_from` | _[WorkDerivedFrom](#workderivedfrom)_ | Returns the information of the original work if the item is a derivative work (a translated version, for example) |
| `bpm` | _Number_ | BPM |
| `references` | _Array&lt;[WorkReference](#workreference)&gt;_ | References of the work (composers, for example) |
| `recording_count` | _Number_ | Number of recordings that use this work |

## Track
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `title` | _String_ | Song title |
| `year` | _Number_ | Release year |
| `language` | _String_ | ISO 639 three-letter language code |
| `isrc` | _String_ | ISRC Code |
| `bpm` | _Number_ | BPM |
| `key` | _Number_ | Tone.<br>It can be: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `time_sig` | _Number_ | Music time.<br>It can be: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `references` | _Array&lt;[TrackReference](#trackreference)&gt;_ | Music references (artists, for example) |
| `works` | _Array&lt;[Work](#work)&gt;_ | Work(s) used in the recording |
| `external_links` | _Array&lt;[ExternalLink](#externallink)&gt;_ | External links of the song |

## WorkReference
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | It can be: `author` `composer` `versionist` `editor` `publisher` `administrator` |
| `profile` | _[Profile](#profile)_ |  |

## TrackReference
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | It can be: `artist` `label` `publisher` `administrator` |
| `profile` | _[Profile](#profile)_ |  |

## ExternalLink
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | For objects of type `Profile`, it can be: `spotify` `youtube` `youtube_music` `apple_music` `amazon_music` `deezer` `multitracks` `letras_mus` `facebook` `instagram` `tiktok` `twitter` `wikipedia`<br><br>For objects of type `Track`, it can be: `youtube_video` `spotify` `youtube` `apple_music` `amazon_music` `deezer` `youtube_video_lyrics` `multitracks` `letras_mus` `cifra_club` `spotify_bt` `youtube_bt` `apple_music_bt` `amazon_music_bt` `deezer_bt` `youtube_video_lyrics_bt`<br><br>Items ending in `_bt` means `Backing Track`, that is, it is the "Playback" of the respective song |
| `id` | _String_ | Resource ID in the respective service |
| `url` | _String_ | URL to access the resource |
| `uri` | _String (optional)_ | Resource URI (available only for certain types, such as Spotify, for example) |
| `language` | _String (optional)_ | Available only for `type=wikipedia`<br>ISO 639 two-letter language code<br> |

## WorkDerivedFrom
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | ID of the respective `Work` object |
| `title` | _String_ |  |
| `year` | _Number_ |  |
| `language` | _String_ | ISO 639 three-letter language code |
