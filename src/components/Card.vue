<template>
    <div class="card">
        <img :src="character.image" alt="" width="300" height="300">
        <h3>{{character.name}}</h3>
        <div>
            <p><span class="field_header">Статус:</span> {{character.status | statusToRussian}}</p>
            <p><span class="field_header">Род:</span> {{character.species | speciesToRussian}}</p>
            <p><span class="field_header">Пол:</span> {{character.gender | genderToRussian}}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['character'],
    filters: {
        statusToRussian(value) {
            switch (value) {
                case 'Alive':
                    return 'Живой'
                    break;
                case 'Dead':
                    return 'Мёртв'
                    break;
            
                default:
                    return 'Не известно'
                    break;
            }
        },
        speciesToRussian(value) {
            switch (value) {
                case 'Human':
                    return 'Человек'
                    break;
                case 'Alien':
                    return 'Пришелец'
                    break;
            
                default:
                    return 'Не известно'
                    break;
            }
        },
        genderToRussian(value) {
            switch (value) {
                case 'Male':
                    return 'Мужчина'
                    break;
                case 'Female':
                    return 'Женщина'
                    break;
            
                default:
                    return 'Не известно'
                    break;
            }
        }
    }
}
</script>

<style scoped>
    div.card {
        width: 400px;
        padding: 15px;
        border: 1px solid gray;
        border-radius: 15px;
        background-color: #3c3e44;
        color: white;
        margin: 35px;
    }
    div.card h3 {
        font-size: 2rem;
    }
    div.card img {
        border-radius: 15px;
    }
    span.field_header {
        font-weight: bold;
        color: white;
    }
    p {
        color: #b1b1b1;
    }
</style>