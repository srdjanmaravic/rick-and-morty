<template>
    <div>
      <div class="navbar bg-base-100 mb-6">
        <NuxtLink to="/" class="btn btn-ghost normal-case text-xl">Rick and Morty</NuxtLink>
      </div>
      <div class="flex flex-wrap artboard artboard-horizontal ">
        <CharacterCard 
        v-for=" { id , name, image, status, species, location } in data.characters.results"
        :key="id"
        :id="id"
        :name="name"
        :image="image"
        :status="status"
        :species="species"
        :location="location.name" 
        />
      </div>
      <footer class="footer footer-center p-4 bg-base-300 text-base-content">
        <div>
          <p>Copyleft © 2022 -  Srdjan Maravic</p>
        </div>
      </footer>
    </div>
</template>
<script lang="ts" setup>
  type CharactersResults = {
    characters : { 
      results: {
        id: string,
        name: string,
        image: string,
        status: string,
        species: string,
        location: {
          name: string
        }
      }[]
    }
  }

const query = gql`
  query getCharacters {
  characters {
    results {
      name
      image
      status
      id
      species
      location {
        name
      }
    }
  }
}
`

const { data } = await useAsyncQuery<CharactersResults>(query)
</script>
