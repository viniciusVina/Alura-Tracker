<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
      <Cronometro :tempoEmSegundos="tempoemsegundos" />
      <button class="button" @click="iniciar" :disabled="cronometroRodando">
        <span class="icon">
          <i class="fas fa-play"></i>
        </span>
        <span>play</span>
      </button>
      <button class="button" @click="finalizar" :disabled="!cronometroRodando">
        <span class="icon">
          <i class="fas fa-stop"></i>
        </span>
        <span>stop</span>
      </button>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from "vue";
  import Cronometro from './Cronometro.vue'
  export default defineComponent({
    name: "Temporizador-APP",
    emits: ['aoTemporizadorFinalizado'],
    components: {
      Cronometro
    },
    data () {
      return {
        tempoemsegundos: 0,
        cronometro: 0,
        cronometroRodando: false
      }
    },
    methods: {
      iniciar () {
        // começar a contagem
        // 1 seg = 1000 ms
        this.cronometroRodando = true
        this.cronometro = setInterval(() => {
          this.tempoemsegundos +=1      
        }, 1000)
      },
      finalizar () {
        this.cronometroRodando = false
        clearInterval(this.cronometro)
        this.$emit('aoTemporizadorFinalizado', this.tempoemsegundos)
        this.tempoemsegundos = 0
      }
    }
  });
  </script>