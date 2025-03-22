

# 📖 Anilist Metadata Provider 

This document provides a comprehensive guide to the Anilist Metadata Provider API, detailing the available routes, their usage, and response schemas. The API is built using Fastify and offers various endpoints to fetch anime-related data from Anilist.

---

## 📌 Table of Contents

1. [Search](#1-search)
2. [Anime Info](#2-anime-info)
3. [Top Airing](#3-top-airing)
4. [Most Popular](#4-most-popular)
5. [Top Anime](#5-top-anime)
6. [Upcoming Anime](#6-upcoming-anime)
7. [Characters](#7-characters)
8. [Trending](#8-trending)
9. [Related](#9-related)
10. [Season](#10-season)
11. [Anime Provider ID](#11-anime-provider-id)
12. [Anime Provider Episodes](#12-anime-provider-episodes)

---

## 1. Search <a id="1-search"></a>

### Endpoint  
```plaintext
GET /api/anilist/search
```

### Description
This endpoint allows you to search for anime based on a query.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `q`       | string | The search query of the anime. | Yes | `''` |
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/search?q=bleach&page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
    "success": "boolean",
    "status": "string",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
        {
            "malId": "integer",
            "anilistId": "integer",
            "image": "string",
            "color": "string",
            "bannerImage": "string",
            "title": {
                "romaji": "string",
                "english": "string",
                "native": "string"
            },
            "trailer": {
                "id": "string",
                "site": "string",
                "thumbnail": "string"
            },
            "format": "string",
            "status": "string",
            "duration": "integer",
            "score": "integer",
            "genres": [
                "string"
            ],
            "episodes": "integer",
            "synopsis": "string",
            "season": "string",
            "startDate": "string",
            "endDate": "string",
            "studio": "string",
            "producers": [
                "string"
            ]
        }
    ]
}
```
</details>

---

## 2. Anime Info <a id="2-anime-info"></a>

### Endpoint
```plaintext
GET /api/anilist/info/:anilistId
```

### Description
Retrieves detailed information about a specific anime.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `anilistId` | number | The Anilist ID of the anime. | Yes | `''` |

### Example
```plaintext
/api/anilist/info/269
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "data": {
      "malId": "integer",
      "anilistId": "integer",
      "image": "string",
      "color": "string",
      "bannerImage": "string",
      "title": {
        "romaji": "string",
        "english": "string",
        "native": "string"
      },
      "trailer": {
        "id": "string",
        "site": "string",
        "thumbnail": "string"
      },
      "format": "string",
      "status": "string",
      "duration": "integer",
      "score": "integer",
      "genres": [
        "string"
      ],
      "episodes": "integer",
      "synopsis": "string",
      "season": "string",
      "startDate": "string",
      "endDate": "string",
      "studio": "string",
      "producers": [
        "string"
      ]
    }
  }
}
```
</details>

---

## 3. Top Airing <a id="3-top-airing"></a>

### Endpoint
```plaintext
GET /api/anilist/top-airing
```

### Description
Retrieves the top airing anime.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/top-airing?page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "bannerImage": "string",
        "title": {
          "romaji": "string",
          "english": "string",
          "native": "string"
        },
        "trailer": "null",
        "format": "string",
        "status": "string",
        "duration": "integer",
        "score": "integer",
        "genres": [
          "string"
        ],
        "episodes": "null",
        "synopsis": "string",
        "season": "string",
        "startDate": "string",
        "endDate": "string",
        "studio": "string",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 4. Most Popular <a id="4-most-popular"></a>

### Endpoint
```plaintext
GET /api/anilist/most-popular
```

### Description
Retrieves the most popular anime.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `format`  | string | Format of anime (TV, MOVIE, SPECIAL, OVA, ONA, MUSIC). | No | `TV` |
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/most-popular?format=TV&page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "bannerImage": "string",
        "title": {
          "romaji": "string",
          "english": "string",
          "native": "string"
        },
        "trailer": {
          "id": "string",
          "site": "string",
          "thumbnail": "string"
        },
        "format": "string",
        "status": "string",
        "duration": "integer",
        "score": "integer",
        "genres": [
          "string"
        ],
        "episodes": "integer",
        "synopsis": "string",
        "season": "string",
        "startDate": "string",
        "endDate": "string",
        "studio": "string",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 5. Top Anime <a id="5-top-anime"></a>

### Endpoint
```plaintext
GET /api/anilist/top-anime
```

### Description
Retrieves the top-rated anime.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `format`  | string | Format of anime (TV, MOVIE, SPECIAL, OVA, ONA, MUSIC). | No | `TV` |
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/top-anime?format=TV&page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "bannerImage": "string",
        "title": {
          "romaji": "string",
          "english": "string",
          "native": "string"
        },
        "trailer": {
          "id": "string",
          "site": "string",
          "thumbnail": "string"
        },
        "format": "string",
        "status": "string",
        "duration": "integer",
        "score": "integer",
        "genres": [
          "string"
        ],
        "episodes": "integer",
        "synopsis": "string",
        "season": "string",
        "startDate": "string",
        "endDate": "string",
        "studio": "string",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 6. Upcoming Anime <a id="6-upcoming-anime"></a>

### Endpoint
```plaintext
GET /api/anilist/upcoming
```

### Description
Retrieves the upcoming anime.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/upcoming?page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "bannerImage": "string",
        "title": {
          "romaji": "string",
          "english": "string | null",
          "native": "string"
        },
        "trailer": {
          "id": "string",
          "site": "string",
          "thumbnail": "string"
        },
        "format": "string",
        "status": "string",
        "genres": [
          "string"
        ],
        "synopsis": "string",
        "startDate": "string",
        "studio": "string",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 7. Characters <a id="7-characters"></a>

### Endpoint
```plaintext
GET /api/anilist/characters/:anilistId
```

### Description
Retrieves the characters of a specific anime.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `anilistId` | number | The Anilist ID of the anime. | Yes | `''` |

### Example
```plaintext
/api/anilist/characters/269
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "data": {
      "malId": "integer",
      "anilistId": "integer",
      "title": {
        "romaji": "string",
        "english": "string",
        "native": "string"
      },
      "characters": [
        {
          "role": "string",
          "id": "integer",
          "name": "string",
          "image": "string",
          "voiceActors": [
            {
              "name": "string",
              "language": "string",
              "image": "string"
            }
          ]
        }
      ]
    }
  }
}
```
</details>

---

## 8. Trending <a id="8-trending"></a>

### Endpoint
```plaintext
GET /api/anilist/trending
```

### Description
Retrieves the trending anime.

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/trending?page=1&perPage=20
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "title": {
          "romaji": "string",
          "english": "string | null",
          "native": "string"
        },
        "format": "string",
        "status": "string",
        "popularity": "integer",
        "score": "integer",
        "genres": [
          "string"
        ],
        "episodes": "integer | null",
        "synopsis": "string",
        "season": "string | null",
        "startDate": "string | null",
        "endDate": "string | null",
        "studio": "string | null",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 9. Related <a id="9-related"></a>

### Endpoint
```plaintext
GET /api/anilist/related/:anilistId
```

### Description
Retrieves the related anime for a specific anime.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `anilistId` | number | The Anilist ID of the anime. | Yes | `''` |

### Example
```plaintext
/api/anilist/related/269
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "data": [
      {
        "anilistId": "integer",
        "malId": "integer",
        "title": {
          "romaji": "string",
          "english": "string | null",
          "native": "string"
        },
        "type": "string",
        "score": "integer",
        "image": "string",
        "bannerImage": "string",
        "color": "string"
      }
    ]
  }
}
```
</details>

---

## 10. Season <a id="10-season"></a>

### Endpoint
```plaintext
GET /api/anilist/seasons/:season/:year
```

### Description
Retrieves the anime for a specific season and year.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `season`  | string | The season (e.g., `spring`, `summer`, `fall`, `winter`). | Yes | `''` |
| `year`    | number | The year. | Yes | `''` |

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `format`  | string | Format of anime (TV, MOVIE, SPECIAL, OVA, ONA, MUSIC). | No | `TV` |
| `page`    | number | The page number of results to return. | No | `1` |
| `perPage` | number | The number of items per page. | No | `20` |

### Example
```plaintext
/api/anilist/seasons/spring/2024?format=TV&page=1&perPage=20
```
<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "hasNextPage": "boolean",
    "currentPage": "integer",
    "total": "integer",
    "lastPage": "integer",
    "perPage": "integer",
    "data": [
      {
        "malId": "integer",
        "anilistId": "integer",
        "image": "string",
        "bannerImage": "string",
        "title": {
          "romaji": "string",
          "english": "string | null",
          "native": "string"
        },
        "trailer": {
          "id": "string | null",
          "site": "string | null",
          "thumbnail": "string | null"
        },
        "format": "string",
        "status": "string",
        "duration": "integer | null",
        "score": "integer",
        "genres": [
          "string"
        ],
        "episodes": "integer | null",
        "synopsis": "string",
        "season": "string | null",
        "startDate": "string | null",
        "endDate": "string | null",
        "studio": "string | null",
        "producers": [
          "string"
        ]
      }
    ]
  }
}
```
</details>

---

## 11. Anime Provider ID <a id="11-anime-provider-id"></a>

### Endpoint
```plaintext
GET /api/anilist/get-provider/:anilistId
```

### Description
Retrieves anime provider information using the Anilist ID.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `anilistId` | number | The Anilist ID of the anime. | Yes | `''` |

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `provider` | string | The provider (e.g., `hianime`or`animekai`). | No | `hianime` |

### Example
```plaintext
/api/anilist/get-provider/269?provider=hianime
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "data": {
      "malId": "integer",
      "anilistId": "integer",
      "image": "string",
      "color": "string",
      "bannerImage": "string",
      "title": {
        "romaji": "string",
        "english": "string | null",
        "native": "string"
      },
      "trailer": {
        "id": "string | null",
        "site": "string | null",
        "thumbnail": "string | null"
      },
      "format": "string",
      "status": "string",
      "duration": "integer | null",
      "score": "integer",
      "genres": [
        "string"
      ],
      "episodes": "integer | null",
      "synopsis": "string",
      "season": "string | null",
      "startDate": "string | null",
      "endDate": "string | null",
      "studio": "string | null",
      "producers": [
        "string"
      ],
      "animeProvider": {
        "animeId": "string",
        "name": "string",
        "romaji": "string",
        "score": "integer | null"
      }
    }
  }
}
```
</details>

---

## 12. Anime Provider Episodes <a id="12-anime-provider-episodes"></a>

### Endpoint
```plaintext
GET /api/anilist/provider-episodes/:anilistId
```

### Description
Retrieves episodes for an anime using the Anilist ID and provider.

### Path Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `anilistId` | number | The Anilist ID of the anime. | Yes | `''` |

### Query Parameters
| Parameter | Type   | Description | Required?  | Default |
|-----------|--------|-------------|-----------|----------| 
| `provider` | string | The provider (e.g., `hianime`or`animekai`). | No | `hianime` |

### Example
```plaintext
/api/anilist/provider-episodes/269?provider=hianime
```

<details>
<summary>📄 Response Schema</summary>

```json
{
  "data": {
    "success": "boolean",
    "status": "integer",
    "data": {
      "malId": "integer",
      "anilistId": "integer",
      "image": "string",
      "color": "string",
      "bannerImage": "string",
      "title": {
        "romaji": "string",
        "english": "string | null",
        "native": "string"
      },
      "trailer": {
        "id": "string | null",
        "site": "string | null",
        "thumbnail": "string | null"
      },
      "format": "string",
      "status": "string",
      "duration": "integer | null",
      "score": "integer",
      "genres": [
        "string"
      ],
      "episodes": "integer | null",
      "synopsis": "string",
      "season": "string | null",
      "startDate": "string | null",
      "endDate": "string | null",
      "studio": "string | null",
      "producers": [
        "string"
      ]
    },
    "providerEpisodes": [
      {
        "episodeId": "string",
        "episodeNumber": "integer",
        "title": "string"
      },
      // ... more episode objects with the same structure
    ]
  }
}
```
</details>

<p align="center">
  <strong><a href="../README.md">Previous (Readme.md)</a></strong> &emsp;&emsp; | &emsp;&emsp;
  <strong><a href="./jikan.md">Next (Jikan docs)</a></strong>
</p>


