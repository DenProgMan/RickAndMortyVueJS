<template>
    <div class="wrapper">
        <Card
            v-for="(character, i) in data"
            :character="character"
            :index="i"
            :key="i"
        />
    </div>
</template>

<script>
import Card from '@/components/Card';

export default {
    props: ['data'],
    components: {
        Card,
    }
}
</script>

<style scoped>
    div.wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        flex-wrap: wrap;
        margin: auto;
    }
</style>