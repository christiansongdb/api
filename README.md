# Christian Song Database API
**PT** | [EN](README-en.md)

API de acesso às informações e conteúdos disponíveis no banco de dados Christian Song Database.<br/>
Ao utilizar a API você concorda com os [Termos de Serviço](https://api.csdb.app/terms).<br/>
<br/>

Christian Song Database (CSDB) é um banco de dados público e aberto de músicas evangélicas que foi criado com o objetivo de armazenar e concentrar informações confiáveis em um único local.<br>
Armazena o id/link de uma música em diferentes serviços de streamings, mantendo a versão correta compatível com cada gravação, diminuindo o risco da versão da música no link de um streaming ser diferente da versão da música em outro streaming.<br>
Armazena também informação dos compositores da música, além de relacionamentos que podem ser interessantes, como a lista de composições de uma determinada pessoa, a lista de músicas que usam a mesma composição, qual é a composição original quando é uma música traduzida de outro idioma, etc.

Download do banco de dados em formato csv disponível em [files/database.zip](files/database.zip)<br/>
Sempre que possível, recomendamos o acesso aos dados pela API, pois os dados são regularmente atualizados/corrigidos.

---

Para utilização da API é necessário um token de autorização<br/>
`Authorization: Bearer {token}`<br>

Para solicitar um token de acesso, entre em contato pelo email [csdb@csdb.app](mailto:csdb@csdb.app)

---

## Request
Todas as respostas da API retornam um objeto padrão:
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `status` | _String_ | Pode ser *'ok'* ou *'error'* |
| `error` | _String (opcional)_ | Mensagem de erro se *status* for igual a *error* |
| `result` | _Object (opcional)_ | Conteúdo da resposta se *status* for igual a *ok* |

URL padrão
```
https://api.csdb.app/v1/
```

# Endpoints disponíveis 
  - [profile/{id}](#profileid)
  - [work/{id}](#workid)
  - [track/{id}](#trackid)
  - [profile/{id}/tracks](#profileidtracks)
  - [profile/{id}/works](#profileidworks)
  - [work/{id}/recordings](#workidrecordings)
  - [work/{id}/versions](#workidversions)
  - [work/{id}/recordings_and_versions](#workidrecordingsandversions)
  - [track/{id}/alternative_versions](#trackidalternativeversions)
  - [{external_link_type}/profile/{id}](#externallinktypeprofileid)
  - [{external_link_type}/track/{id}](#externallinktypetrackid)
  - [popular/profile](#popularprofile)
  - [popular/track](#populartrack)
  - [popular/work](#popularwork)
  - [search/profile](#searchprofile)
  - [search/track](#searchtrack)


---

### profile/{id}
Retorna um perfil

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do perfil |


**Resposta:**

| Tipo  |
| :---: |
| _[Profile](#profile)_ | 


**Exemplo:** [` api.csdb.app/v1/profile/5450607 `](https://api.csdb.app/v1/profile/5450607)<br>

<details>
  <summary>Resposta</summary>

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
Retorna uma obra

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da obra |


**Resposta:**

| Tipo  |
| :---: |
| _[Work](#work)_ | 


**Exemplo:** [` api.csdb.app/v1/work/8063427 `](https://api.csdb.app/v1/work/8063427)<br>

<details>
  <summary>Resposta</summary>

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
Retorna uma música (gravação)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da música |


**Resposta:**

| Tipo  |
| :---: |
| _[Track](#track)_ | 


**Exemplo:** [` api.csdb.app/v1/track/3165776 `](https://api.csdb.app/v1/track/3165776)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista de músicas de um perfil

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da música |
| `limit` | _Number (opcional)_ | `1 ~ 100` `Padrão: 10` |
| `page` | _Number (opcional)_ |  `Padrão: 1` |
| `order` | _String (opcional)_ | Modo de ordenação dos items.<br>Pode ser: `title` `popularity` `date` `date_descending` `Padrão: title` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tracks` | _Array&lt;[Track](#track)&gt;_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `order` | _String_ |  |
| `total` | _Number_ | Total de itens disponíveis |


**Exemplo:** [` api.csdb.app/v1/profile/5450607/tracks?limit=10&page=1&order=popularity `](https://api.csdb.app/v1/profile/5450607/tracks?limit=10&page=1&order=popularity)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista de composições de um perfil

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da obra |
| `limit` | _Number (opcional)_ | `1 ~ 100` `Padrão: 10` |
| `page` | _Number (opcional)_ |  `Padrão: 1` |
| `order` | _String (opcional)_ | Modo de ordenação dos items.<br>Pode ser: `title` `popularity` `date` `date_descending` `Padrão: title` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `works` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `order` | _String_ |  |
| `total` | _Number_ | Total de itens disponíveis |


**Exemplo:** [` api.csdb.app/v1/profile/5450607/works?limit=10&page=1&order=popularity `](https://api.csdb.app/v1/profile/5450607/works?limit=10&page=1&order=popularity)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista de gravações da respectiva obra

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da obra |
| `limit` | _Number (opcional)_ | `1 ~ 100` `Padrão: 10` |
| `page` | _Number (opcional)_ |  `Padrão: 1` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `recordings` | _[Track](#track)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total` | _Number_ | Total de itens disponíveis |


**Exemplo:** [` api.csdb.app/v1/work/8063427/recordings?limit=10&page=1 `](https://api.csdb.app/v1/work/8063427/recordings?limit=10&page=1)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista de obras derivadas (versões) da respectiva obra

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da obra |
| `limit` | _Number (opcional)_ | `1 ~ 100` `Padrão: 10` |
| `page` | _Number (opcional)_ |  `Padrão: 1` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `versions` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total` | _Number_ | Total de itens disponíveis |


**Exemplo:** [` api.csdb.app/v1/work/7269270/versions?limit=10&page=1 `](https://api.csdb.app/v1/work/7269270/versions?limit=10&page=1)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista de gravações e a lista de obras derivadas (versões) da respectiva obra

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da obra |
| `limit` | _Number (opcional)_ | `1 ~ 100` `Padrão: 10` |
| `page` | _Number (opcional)_ |  `Padrão: 1` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `recordings` | _[Track](#track)_ |  |
| `versions` | _[Work](#work)_ |  |
| `limit` | _Number_ |  |
| `page` | _Number_ |  |
| `total_recordings` | _Number_ | Total de gravações disponíveis |
| `total_versions` | _Number_ | Total de versões disponíveis |


**Exemplo:** [` api.csdb.app/v1/work/7269270/recordings_and_versions?limit=10&page=1 `](https://api.csdb.app/v1/work/7269270/recordings_and_versions?limit=10&page=1)<br>

<details>
  <summary>Resposta</summary>

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

### track/{id}/alternative_versions
Retorna a lista de gravações do mesmo artista que utilizam a mesma composição

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da música |


**Resposta:**

| Nome | Tipo  |
| ---- | :---: |
| `alternative_versions` | _[Track](#track)_| 


**Exemplo:** [` api.csdb.app/v1/track/5099252/alternative_versions `](https://api.csdb.app/v1/track/5099252/alternative_versions)<br>

<details>
  <summary>Resposta</summary>

```json
{
  "status": "ok",
  "result": {
    "alternative_versions": [
      {
        "id": 5650723,
        "title": "Digno É o Senhor",
        "language": "por",
        "isrc": "BRDAR1200007",
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
                "_self": "https://api.csdb.app/v1/profile/5450607",
                "tracks": "https://api.csdb.app/v1/profile/5450607/tracks",
                "works": "https://api.csdb.app/v1/profile/5450607/works",
                "popular_tracks": "https://api.csdb.app/v1/popular/track?profile=5450607",
                "popular_works": "https://api.csdb.app/v1/popular/work?profile=5450607"
              }
            }
          }
        ],
        "works": [
          {
            "id": 8796326,
            "title": "Digno É o Senhor",
            "year": 2002,
            "language": "por",
            "derived_from": {
              "id": 2546419,
              "title": "Worthy Is The Lamb",
              "year": 2000,
              "language": "eng"
            },
            "references": [
              {
                "type": "author",
                "profile": {
                  "id": 7116363,
                  "name": "Darlene Joyce Steinhardt",
                  "alias": "Darlene Zschech",
                  "alias_author": "",
                  "type": "person",
                  "country": "AU",
                  "copyright": "",
                  "gospel": true,
                  "_links": {
                    "_self": "https://api.csdb.app/v1/profile/7116363",
                    "tracks": "https://api.csdb.app/v1/profile/7116363/tracks",
                    "works": "https://api.csdb.app/v1/profile/7116363/works",
                    "popular_tracks": "https://api.csdb.app/v1/popular/track?profile=7116363",
                    "popular_works": "https://api.csdb.app/v1/popular/work?profile=7116363"
                  }
                }
              }
            ],
            "_links": {
              "_self": "https://api.csdb.app/v1/work/8796326",
              "recordings": "https://api.csdb.app/v1/work/8796326/recordings",
              "versions": "https://api.csdb.app/v1/work/8796326/versions",
              "recordings_and_versions": "https://api.csdb.app/v1/work/8796326/recordings_and_versions",
              "popular": "https://api.csdb.app/v1/popular/work"
            }
          }
        ],
        "external_links": [
          {
            "type": "spotify",
            "id": "66WaKTCLP5nUwOrwn7Oet0",
            "url": "https://open.spotify.com/track/66WaKTCLP5nUwOrwn7Oet0",
            "uri": "spotify:track:66WaKTCLP5nUwOrwn7Oet0"
          },
          {
            "type": "youtube",
            "id": "71eB7qk9YVE",
            "url": "https://music.youtube.com/watch?v=71eB7qk9YVE"
          },
          {
            "type": "apple_music",
            "id": "547338659",
            "url": "https://music.apple.com/br/song/547338659"
          },
          {
            "type": "amazon_music",
            "id": "B009BIA066",
            "url": "https://music.amazon.com.br/tracks/B009BIA066"
          },
          {
            "type": "deezer",
            "id": "51546321",
            "url": "https://www.deezer.com/track/51546321",
            "uri": "deezer://www.deezer.com/track/51546321"
          },
          {
            "type": "letras_mus",
            "id": "aline-barros/127758",
            "url": "https://www.letras.mus.br/aline-barros/127758"
          }
        ],
        "_links": {
          "_self": "https://api.csdb.app/v1/track/5650723",
          "popular": "https://api.csdb.app/v1/popular/track"
        }
      }
    ]
  }
}
```
</details>


---

### {external_link_type}/profile/{id}
Retorna o perfil com base no ID do respectivo serviço externo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `external_link_type` | _String_ | Pode ser: `spotify` `youtube` `apple_music` `amazon_music` `deezer` |
| `id` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _[Profile](#profile)_ | 


**Exemplo:** [` api.csdb.app/v1/spotify/profile/2aKyKSggb31Kw9s9i3iXoo `](https://api.csdb.app/v1/spotify/profile/2aKyKSggb31Kw9s9i3iXoo)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a música com base no ID do respectivo serviço externo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `external_link_type` | _String_ | Pode ser: `isrc` `spotify` `youtube` `apple_music` `amazon_music` `deezer` |
| `id` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _[Track](#track)_ | 


**Exemplo:** [` api.csdb.app/v1/spotify/track/1uoA57FMhP9QjZxIJZVEWo `](https://api.csdb.app/v1/spotify/track/1uoA57FMhP9QjZxIJZVEWo)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista dos perfis populares

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `limit` | _Number (opcional)_ | Quantidade máxima de itens retornados. `1 ~ 100` `Padrão: 10` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `profiles` | _Array&lt;[Profile](#profile)&gt;_ |  |
| `limit` | _Number_ |  |


**Exemplo:** [` api.csdb.app/v1/popular/profile?limit=5 `](https://api.csdb.app/v1/popular/profile?limit=5)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista das músicas populares

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `profile` | _String (opcional)_ | ID do perfil para retornar apenas as músicas de um determinado perfil |
| `limit` | _Number (opcional)_ | Quantidade máxima de itens retornados. `1 ~ 100` `Padrão: 10` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tracks` | _Array&lt;[Track](#track)&gt;_ |  |
| `limit` | _Number_ |  |


**Exemplo:** [` api.csdb.app/v1/popular/track?profile=&limit=5 `](https://api.csdb.app/v1/popular/track?profile=&limit=5)<br>

<details>
  <summary>Resposta</summary>

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
Retorna a lista das obras populares

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `profile` | _String (opcional)_ | ID do perfil para retornar apenas as obras de um determinado perfil |
| `limit` | _Number (opcional)_ | Quantidade máxima de itens retornados. `1 ~ 100` `Padrão: 10` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `works` | _Array&lt;[Work](#work)&gt;_ |  |
| `limit` | _Number_ |  |


**Exemplo:** [` api.csdb.app/v1/popular/work?profile=&limit=5 `](https://api.csdb.app/v1/popular/work?profile=&limit=5)<br>

<details>
  <summary>Resposta</summary>

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
Pesquisa um perfil pelo nome

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `q` | _String_ | Texto a ser pesquisado |


**Resposta:**

| Nome | Tipo  |
| ---- | :---: |
| `profiles` | _Array&lt;[Profile](#profile)&gt;_| 


**Exemplo:** [` api.csdb.app/v1/search/profile?q=fernandinho `](https://api.csdb.app/v1/search/profile?q=fernandinho)<br>

<details>
  <summary>Resposta</summary>

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
Pesquisa uma música pelo nome

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `q` | _String_ | Texto a ser pesquisado |


**Resposta:**

| Nome | Tipo  |
| ---- | :---: |
| `tracks` | _Array&lt;[Track](#track)&gt;_| 


**Exemplo:** [` api.csdb.app/v1/search/track?q=a%20ele%20a%20gloria `](https://api.csdb.app/v1/search/track?q=a%20ele%20a%20gloria)<br>

<details>
  <summary>Resposta</summary>

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
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String (opcional)_ | Nome completo |
| `alias` | _String_ | Nome artístico |
| `alias_author` | _String_ | Nome alternativo (opcional) utilizado nos locais que informam autor/compositor |
| `type` | _String_ | Tipo do perfil.<br>Pode ser: `person` `group` `label` `publisher` `hymnal` |
| `country` | _String_ | ISO 639 two-letter language code |
| `copyright` | _String_ |  |
| `gospel` | _Boolean_ | **true** se o perfil for associado à uma pessoa/grupo/banda evangélica |
| `about` | _String_ |  |
| `site` | _String_ | https://example.com |
| `work_count` | _Number_ | Quantidade de composições associadas ao perfil |
| `track_count` | _Number_ | Quantidade de gravações associadas ao perfil |
| `external_links` | _Array&lt;[ExternalLink](#externallink)&gt;_ | Links externos do perfil (por exemplo, redes sociais) |

## Work
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `title` | _String_ | Título da obra |
| `year` | _Number_ |  |
| `language` | _String_ | ISO 639 three-letter language code |
| `derived_from` | _[WorkDerivedFrom](#workderivedfrom)_ | Retorna a informação da obra original se o item for uma obra derivada (uma versão traduzida, por exemplo) |
| `bpm` | _Number_ | BPM |
| `references` | _Array&lt;[WorkReference](#workreference)&gt;_ | Referências da obra (compositores, por exemplo) |
| `recording_count` | _Number_ | Quantidade de gravações que utilizam esta obra |

## Track
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `title` | _String_ | Título da música |
| `year` | _Number_ | Ano de lançamento |
| `language` | _String_ | ISO 639 three-letter language code |
| `isrc` | _String_ | Código ISRC |
| `bpm` | _Number_ | BPM |
| `key` | _Number_ | Tonalidade.<br>Pode ser: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `time_sig` | _Number_ | Tempo da música.<br>Pode ser: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `references` | _Array&lt;[TrackReference](#trackreference)&gt;_ | Referências da música (artistas, por exemplo) |
| `works` | _Array&lt;[Work](#work)&gt;_ | Obra(s) utilizada(s) na gravação |
| `external_links` | _Array&lt;[ExternalLink](#externallink)&gt;_ | Links externos da música |

## WorkReference
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Pode ser: `author` `composer` `versionist` `editor` `publisher` `administrator` |
| `profile` | _[Profile](#profile)_ |  |

## TrackReference
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Pode ser: `artist` `label` `publisher` `administrator` |
| `profile` | _[Profile](#profile)_ |  |

## ExternalLink
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Para objetos do tipo `Profile`, pode ser: `spotify` `youtube` `youtube_music` `apple_music` `amazon_music` `deezer` `multitracks` `letras_mus` `facebook` `instagram` `tiktok` `twitter` `wikipedia`<br><br>Para objetos do tipo `Track`, pode ser: `youtube_video` `spotify` `youtube` `apple_music` `amazon_music` `deezer` `youtube_video_lyrics` `multitracks` `letras_mus` `cifra_club` `spotify_bt` `youtube_bt` `apple_music_bt` `amazon_music_bt` `deezer_bt` `youtube_video_lyrics_bt`<br><br>Itens terminados em `_bt` significa `Backing Track`, ou seja, é o "Playback" da respectiva música |
| `id` | _String_ | ID do recurso no respectivo serviço |
| `url` | _String_ | URL para acesso ao recurso |
| `uri` | _String (opcional)_ | URI do recurso (disponível apenas para alguns tipos, como spotify, por exemplo) |
| `language` | _String (opcional)_ | Disponível apenas para `type=wikipedia`<br>ISO 639 two-letter language code<br> |

## WorkDerivedFrom
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do respectivo objeto `Work` |
| `title` | _String_ |  |
| `year` | _Number_ |  |
| `language` | _String_ | ISO 639 three-letter language code |
