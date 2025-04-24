

# 📖 Animekai Provider 

This document provides a comprehensive guide to the Animekai Provider endpoint, detailing the available routes, their usage, and response schemas. The API offers various endpoints to fetch anime-related data from animekai.

---

## 📌 Table of Contents

1. [Search](#1-search)
2. [Anime Info](#2-anime-info)
3.  [Anime Servers](#3-anime-servers)
4.  [Anime Provider Sources](#4-anime-provider-sources)

---

## 1. Search <a id="1-search"></a>

### Endpoint  
```plaintext
GET /api/animekai/search
```

### Description
This endpoint allows you to search for anime based on a query.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `q`       | string | The search query of the anime. | Yes | `''` |
| `page`    | number | The page number of results to return. | No | `1` |


### Example
```plaintext
/api/animekai/search?q=bleach&page=1
```

<details>
<summary>📄 Response Schema</summary>

```json

{
  "data": {
    "success": "boolean",
    "status": "number",
    "hasNextPage": "boolean",
    "currentPage": "number",
    "totalPages": "number",
    "data": [
      {
        "id": "string",
        "title": "string",
        "image": "string",
        "romaji": "string",
        "type": "string",
        "sub": "number",
        "dub": "number",
        "episodes": "number"
      }
    ]
  }
}



```
</details>

---

## 2. Anime Info <a id="2-anime-info"></a>

### Endpoint
```plaintext
GET /api/animekai/info/:animeId
```

### Description
Retrieves  information including episodes about a specific anime..

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `animeId` | string | The unique identifier of the anime from search results.. | Yes | `''` |

### Example
```plaintext
/api/animekai/info/bleach-thousand-year-blood-war-the-conflict-zev9
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "number",
    "data": {
      "animeId": "string",
      "title": "string",
      "romaji": "string",
      "posterImage": "string",
      "type": "string",
      "synopsis": "string",
      "episodes": {
        "sub": "number",
        "dub": "number"
      },
      "totalEpisodes": "number"
    },
    "providerEpisodes": [
      {
        "episodeId": "string",
        "number": "number",
        "title": "string"
      }
    ]
  }
}

```
</details>

---


## 3. Anime Servers <a id="3-anime-servers"></a>

### Endpoint
```plaintext
GET /api/animekai/servers/:episodeId
```

### Description
Retrieves available streaming servers for a specific episode.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `episodeId` | string | The unique identifier of the anime episode from the episodes endpoint. | Yes | `''` |

### Query Parameters  

| Parameter  | Type   | Description                                      | Required? | Default |  
|------------|--------|--------------------------------------------------|-----------|---------|  
| `category` | string | Specifies the anime language: `sub` (subtitled) or `dub` (dubbed). | No | `sub` | 

### Example
```plaintext
/api/animekai/servers/bleach-thousand-year-blood-war-the-conflict-zev9$ep=12$token=ON65rODlu0ik1HRMhM2X?category=sub
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "number",
    "data": [
      {
        "name": "string",
        "url": "string",
        "intro": {
          "start": "number",
          "end": "number"
        },
        "outro": {
          "start": "number",
          "end": "number"
        }
      }
    ]
  }
}



```
</details>

---

## 4. Anime Provider Sources <a id="4-anime-provider-sources"></a>

### Endpoint
```plaintext
GET /api/animekai/watch/:episodeId
```

### Description
Retrieves  streaming sources for a specific anime episode..

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `episodeId` | string | The unique identifier of the anime episode from the episodes endpoint . | Yes | `''` |

### Query Parameters  

| Parameter  | Type   | Description                                      | Required? | Default |  
|------------|--------|--------------------------------------------------|-----------|---------|  
| `category` | string | Specifies the anime language: `sub` (subtitled) or `dub` (dubbed). | No | `sub` |  


### Example
```plaintext
/api/animekai/watch/bleach-thousand-year-blood-war-the-conflict-zev9$ep=12$token=ON65rODlu0ik1HRMhM2X?category=sub
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "headers": {
      "Referer": "string"
    },
    "data": {
      "intro": {
        "start": "number",
        "end": "number"
      },
      "outro": {
        "start": "number",
        "end": "number"
      },
      "subtitles": [
        {
          "file": "string",
          "label": "string",
          "kind": "string",
          "default": "boolean"
        },
        {
          "file": "string",
          "kind": "string"
        }
      ],
      "sources": [
        {
          "url": "string",
          "type": "string"
        }
      ]
    }
  }
}


```
</details>

## Handling CORS 403 Forbidden Errors for M3U8 Streams
 (CORS) `403 Forbidden` errors when trying to access M3U8 (HTTP Live Streaming) playlists and their associated media segments from a web application. This often occurs when the server hosting the M3U8 content is on a different domain than your web application and doesn't have the necessary CORS headers configured.

**The Solution: Using an M3U8 Proxy**

The most common and effective way to overcome this limitation is to use a **proxy server** that sits between your web application and the M3U8 content server. This proxy server fetches the M3U8 playlist and its segments on behalf of your application and adds the necessary CORS headers to its responses, effectively making the content accessible to your browser.
Pass the referer header to the proxy

---

<p align="center">
  <strong><a href="./hianime.md">Previous (HiAnime docs)</a></strong> &emsp;&emsp; 
</p>