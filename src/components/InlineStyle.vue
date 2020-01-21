<template>
  <div>
    <div :style="{backgroundColor: this.color}" class="rect variable-color"></div>
    <button @click="setColor('#aa0000')">Vermelho</button>
    <button @click="setColor('#00aa00')">Verde</button>
    <button @click="setColor('#0000dd')">Azul</button>
    <pre>
    1. A propriedade css tem seu valor setado diretamente através do atributo
    <i>style</i> (o vue converte de <i>camelCase</i> para <i>kebab-case</i>):

    &lt;div
      :style=&quot;<b>{backgroundColor: {{color}}}</b>&quot;
      class=&quot;rect variable-color&quot;&gt;
    &lt;/div&gt;

    2. Efetivamente o código é renderizado como:

    &lt;div
      style=&quot;<b>background-color: {{color}};</b>&quot;
      class=&quot;rect variable-color&quot;&gt;
    &lt;/div&gt;
    </pre>
  </div>
</template>

<script>
export default {
  name: 'InlineStyle',
  props: {
    msg: String
  },
  data() {
    return {
      color: '#aa0000'
    }
  },
  methods: {
    setColor(hexValue) {
      this.color=hexValue
    }
  }
}
</script>

<style>
pre {
  text-align: left;
}
</style>
