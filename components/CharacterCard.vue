<template>
    <div class="card w-96 bg-base-100 shadow-xl m-4">
        <NuxtLink :to="`/characters/${id}`">
            <figure><NuxtImg 
                :src="image" 
                :modifiers="grayScaleWhenDead"
                width="200"
                height="200"
                class="rounded-xl"
            /></figure>
             <div class="card-body">
            <h2 class="card-title">
            {{ name }}
            </h2>
            <p>Location: {{ location }}</p>
            <div class="card-actions justify-end">
            <div class="badge badge-outline">{{ status }}</div> 
            <div class="badge badge-outline">{{ species }}</div>
            </div>
        </div>
        </NuxtLink>
        
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    name : {
        type: String,
        required: true
    },
    image: {
        type: String,
        required: true
    },
    status: {
        type: String,
        required: true
    },
    id: {
        type: String,
        required: true
    },
    species: {
        type: String,
        required: true
    },
    location : {
        type: String,
        required: true
    }
})

const grayScaleWhenDead = computed(()=> props.status === 'Dead' ? { grayscale: true } : {} )
</script>


