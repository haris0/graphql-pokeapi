# graphql-pokeapi - GraphQL implementation of pokeapi.co

<p align="center">
	<img height="200" src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi.svg?sanitize=true" alt="PokeAPI">
</p>
<p align="center">
	<img src="https://github.com/mazipan/graphql-pokeapi/workflows/Main%20workflow/badge.svg" alt="Actions">
</p>

## Graphql Playground

[https://graphql-pokeapi.vercel.app/api/graphql](https://graphql-pokeapi.vercel.app/api/graphql)

## Queries

| Query        | Desc                       | Variables         |
| ------------ | -------------------------- | ----------------- |
| `pokemons`   | Get list of pokemons       | `limit`, `offset` |
| `pokemon`    | Get detail info of pokemon | `name`            |
| `ability`    | Get detail of ability      | `ability`         |
| `eggGroup`   | Get detail of egg group    | `eggGroup`        |
| `gender`     | Get detail of gender       | `gender`          |
| `growthRate` | Get detail of growth rate  | `growthRate`      |
| `move`       | Get detail of move         | `move`            |
| `nature`     | Get detail of nature       | `nature`          |

## Examples

### pokemon

Desc: Get detail info of pokemon

<details>
  <summary>Sample Query</summary>
  <p><pre>query pokemon($name: String!) {
  pokemon(name: $name) {
    id
    name
    abilities {
      ability {
        name
      }
    }
    moves {
      move {
        name
      }
    }
    types {
      type {
        name
      }
    }
    message
    status
  }
}</pre></p>
</details>

<details>
  <summary>Sample Variables</summary>
  <p><pre>{
  "name": "ditto"
}</pre></p>
</details>

<details>
  <summary>Sample Result</summary>
  <p><pre>{
  "data": {
    "pokemon": {
      "id": 132,
      "name": "ditto",
      "abilities": [
        {
          "ability": {
            "name": "imposter"
          }
        },
        {
          "ability": {
            "name": "limber"
          }
        }
      ],
      "moves": [
        {
          "move": {
            "name": "transform"
          }
        }
      ],
      "types": [
        {
          "type": {
            "name": "normal"
          }
        }
      ],
      "message": "",
      "status": true
    }
  }
}</pre></p>
</details>

### pokemons

Desc: Get list of pokemons

<details>
  <summary>Sample Query</summary>
  <p><pre>query pokemons($limit: Int, $offset: Int) {
  pokemons(limit: $limit, offset: $offset) {
    count
    next
    previous
    status
    message
    results {
      url
      name
      image
    }
  }
}</pre></p>
</details>


<details>
  <summary>Sample Variables</summary>
  <p><pre>{
  "limit": 2,
  "offset": 1
}</pre></p>
</details>

<details>
  <summary>Sample Result</summary>
  <p><pre>{
  "data": {
    "pokemons": {
      "count": 964,
      "next": "https://pokeapi.co/api/v2/pokemon/?offset=3&limit=3",
      "previous": null,
      "results": [
        {
          "url": "https://pokeapi.co/api/v2/pokemon/1/",
          "name": "bulbasaur",
          "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png"
        },
        {
          "url": "https://pokeapi.co/api/v2/pokemon/2/",
          "name": "ivysaur",
          "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/2.png"
        },
        {
          "url": "https://pokeapi.co/api/v2/pokemon/3/",
          "name": "venusaur",
          "image": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/3.png"
        }
      ],
      "status": true,
      "message": ""
    }
  }
}</pre></p>
</details>

## Credits

- [PokeAPI](https://github.com/PokeAPI/pokeapi)
- [Pokedex Promise V2](https://github.com/PokeAPI/pokedex-promise-v2#pokemon)
- [Vercel](https://vercel.com/)

---

Copyright © By Irfan Maulana
