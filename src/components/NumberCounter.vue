<template>
    <div class="wrapper">
        <h1>
            Contador
        </h1>

        <p>{{ count }}</p>

        <div class="botones">
            <button class="botones-increment" @click="increment">Incrementar</button>
            <button 
                @click="decrement"
                class="botones-decrement"
                :class="{
                    deshabilitado: count === 0
                }"
                :disabled="count === 0 ? true: false"
            >Decrementar</button>
        </div>
    </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
    name: "NumberCounter",
    computed: {
        
        ...mapGetters({
            count: 'getCount'
        })
    },
    
    methods: {
        ...mapActions({
            increment: 'increment',
            decrement: 'decrement'
        })
    }
}

</script>


<style scoped>
    .botones {
        display: flex;
        gap: 2rem;
        justify-content: center;
    }
    p {
        font-size: 5rem;
    }
    .botones-increment {
        background-color: rgb(135, 160, 216);
        border-radius: 1rem;
        padding: 1rem 2rem;
        font-weight: 900;
        color: #FFF;
        cursor: pointer;
    }

    .botones-decrement {
        background-color: rgb(189, 39, 72);
        border-radius: 1rem;
        padding: 1rem 2rem;
        font-weight: 900;
        color: #FFF;
        cursor: pointer;
    }
    .deshabilitado {
        opacity: .5;
        cursor: not-allowed;
    }
</style>