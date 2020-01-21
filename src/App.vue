<template>
  <div id="app">
    <nav>
      <ul>
        <a href="#inline" @click="setComponent('InlineStyle')">Estilo inline</a>
        <a href="#css1" @click="setComponent('CSSVars1')">Variáveis CSS I</a>
        <a href="#css2" @click="setComponent('CSSVars2')">Variáveis CSS II</a>
      </ul>
    </nav>
    <component :is='componentName'/>
  </div>
</template>

<script>
import CSSVars1 from './components/CSSVars1.vue'
import CSSVars2 from './components/CSSVars2.vue'
import InlineStyle from './components/InlineStyle.vue'

export default {
  name: 'app',
  data() {
    return {
      componentName: 'InlineStyle'
    }
  },
  components: {
    CSSVars1,
    CSSVars2,
    InlineStyle
  },
  methods: {
    setComponent(name) {
      this.componentName = name
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  list-style: none;
  display: flex;
  justify-content: space-around;
}

code {
  display: block;
  margin: 1rem 0;
}
.rect {
  width: 30rem;
  height: 20rem;
  margin: 3rem auto;
  transition: background-color .2s ease;
}
</style>
