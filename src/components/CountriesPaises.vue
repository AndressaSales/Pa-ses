<template>
    <div>
        <div class="container">
            <div class="text">
                <input type="text" v-model="name" placeholder="Digite um nome de um país.....">
                <button @click="bus">Buscar</button>
            </div>
         
            <div class="res">
                <img :src="country.flags && country.flags.svg ? country.flags.svg : 'fallback.svg'" alt="">
                <img :src="country.coatOfArms && country.coatOfArms.svg ? country.coatOfArms.svg : 'fallback.svg'" alt="">
                <div class="t">
                    <div class="tt">
                        <h4>Capital: </h4>
                        <span v-if="country.capital && country.capital.length > 0">{{ country.capital[0] }}</span>
                    </div>
                    <div class="tt">
                        <h4>Continente: </h4>
                        <span v-if="country.continents && country.continents.length > 0">{{ country.continents[0] }}</span>
                    </div>
                     <div class="tt">  
                        <h4>População: </h4>
                        <span>{{ country.population }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: "CountriesPaises",
    data(){
        return{
            country : {},
            name: ""
        }
    },
    methods:{
        async bus(){
            try{
                const res = await fetch(`https://restcountries.com/v3.1/name/${this.name}`)
                const data = await res.json()
                this.country = data[0]
            }catch(error){
                console.error('Error ao buscar dados do país!', error)
            }
        }
    }
}
</script>

<style scoped>
    .container{
        background: rgba(30, 23, 227, 0.6);
        width: 80vw;
        max-width: 37.5em;
        padding: 3em 2.5em;
        position: absolute;
        transform: translate(-50%, -50%);
        top: 50%;
        left: 50%;
        border-radius: 20px;
    }
    .text{
        display: grid;
        grid-template-columns: 9fr 3fr;
        grid: 1.25em;
    }
    .text button{
        font-size: 1rem;
        background: #cfcfcf;
        color: #f00;
        padding: 0.8em 0;
        border: none;
        cursor: pointer;
        font-weight: bold;
        margin-left: 10px;
        border-radius: 20px;
    }
    .text input{
        background: transparent;
        border-bottom:4px solid #cfcfcf;
        border-left: none;
        border-right: none;
        border-top: none;
        color: #fff;
        font-size: 1rem;
        outline: none;
    }
    .text input::placeholder{
        color: #fff;
    }
    .res{
        margin-top: 1.25em;
    }
    .container img{
        display: block;
        width: 40%;
        min-width: 7.5em;
        margin: 1.8em auto 1.2em auto;
    }
    .tt{
        margin-bottom: 1em;
        letter-spacing: 0.3px;
    }
    .container h4{
        display: inline;
        font-weight: 500;
        color: #fff;
    }
    .container span{
        color: #cfcfcf;
    }
</style>