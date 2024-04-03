<template>
  <div id="app" class="container">
    <h1>VueJS</h1>
    
    <button @click="componentSelecionado = 'HomeComponent'">Home</button>
    <button @click="componentSelecionado = 'PostsLista'">Lista</button>
    <button @click="componentSelecionado = 'SobreComponent'">Sobre</button>

    <component 
      :is="componentSelecionado"
      v-bind="propsAtuais">
    </component>
  </div>
</template>

<script>

import HomeComponent from './components/HomeComponent.vue'
import PostsLista from './components/PostsLista.vue'
import SobreComponent from './components/SobreComponent.vue'

export default {
  components: {
    HomeComponent,
    PostsLista,
    SobreComponent
  },
  data () {
    return {
        componentSelecionado: 'HomeComponent',
        posts: [
            { id: 1, titulo: 'Components no VueJS', conteudo: 'Components são uma das peças mais importantes no VueJS', autor: 'Hesnan Ávila'},
            { id: 2, titulo: 'Components no VueJS 2', conteudo: 'Components são uma das peças mais importantes no VueJS 2', autor: 'Hesnan Ávila 2'}
        ]
    }
  },
  computed: {
    propsAtuais () {
      return this.componentSelecionado === 'PostsLista'
        ? { posts: this.posts }
        : {}
    }
  }
}
</script>

<style scoped>
  .container {
    width: 960px;
    margin: auto;
  }
</style>
