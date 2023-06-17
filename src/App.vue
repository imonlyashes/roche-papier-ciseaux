<script>
import PageHeader from './components/PageHeader.vue'
import Game from './components/Game.vue'

export default {
    components: { PageHeader, Game },
    data(){
      return{
        purpleWord: "Roche",
        cyanWord: "Papier",
        orangeWord: "Ciseaux"
      }
    }
  }
</script>

<template>
  <header>
    <PageHeader :purpleWord="purpleWord" :cyanWord="cyanWord" :orangeWord="orangeWord" />
  </header>

  <main>
    <Game />
  </main>
</template>
