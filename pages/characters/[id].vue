<template>
    <div>
        <div class="navbar bg-base-100">
            <NuxtLink to="/" class="btn btn-ghost normal-case text-xl">Rick and Morty</NuxtLink>
        </div>
        <CharacterCard 
            :id="data.character.id"
            :name="data.character.name"
            :image="data.character.image"
            :status="data.character.status"
            :species="data.character.species"
            :location="data.character.location.name" 
    />
    </div>
</template>

<script setup lang="ts">
    const route = useRoute()

    type Character = {
        character: {
            name: string
            image: string
            status: string
            id: string
            species: string
            loncation: {
                name: string
            }
        }
    }
    const query = gql`
        query getCharacter {
        character(id: ${route.params.id}) {
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
`

const { data } = await useAsyncQuery<Character>(query)
</script>

