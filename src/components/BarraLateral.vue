<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="logo-vue">
        </h1>
        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'BarraLateral',
        data () {
            return {
                modoEscuroAtivo: false
            }
        },
        emits: ['aoTemaAlterado'],
        computed: {
            textoBotao () {
                if(this.modoEscuroAtivo) {
                    return 'Desativar Modo Escuro'
                }
                return 'Ativar Modo Escuro'
            }
        },
        methods: {
            alterarTema () {
                this.modoEscuroAtivo = !this.modoEscuroAtivo
                this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
            }
        }
    })
</script>

<style scoped>
    header {
        padding: 1rem;
        background: #0d3b66;
        width: 100%;
        height: 100vh;
        text-align: center;
    }

    @media only screen and (max-width: 768px) {
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
    header h1 {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 1rem;
    }

    img {
        height: 5rem;
    }
</style>