<template>
    <div id="app">
        <h1>The Rick and Morty Vue.js</h1>
        <Loader v-if="loading" />
        <CardsBoard
            v-else
            v-bind:data="characters"
        />

        <hr>

    </div>
</template>

<script>

import CardsBoard from '@/components/CardsBoard';
import Loader from '@/components/Loader';

export default {
    name: 'App',
    data() {
        return {
            characters: [],
            loading: true,
        }
    },
    async mounted() {
        const response = await fetch('https://rickandmortyapi.com/api/character');
        const result = await response.json();

        setTimeout(() => {
            this.characters = result?.results ?? [];
            this.loading = false;
        }, 1000); // Сервер слишком быстро отвечает, не видно Loader
    },
    components: {
        CardsBoard, Loader
    }
}
</script>

<style>
    body {
        background-color: #24282f;
        padding: 45px;
    }
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
    h1 {
        color: white;
        font-size: 6rem;
        margin-bottom: 45px;
    }
    hr {
        margin: 45px 0;
    }
</style>
