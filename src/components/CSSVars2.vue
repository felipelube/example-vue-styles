<template>
  <div>
    <div :style="cssVars" class="rect variable-color"></div>
    <button @click="setColor('#aa0000')">Vermelho</button>
    <button @click="setColor('#00aa00')">Verde</button>
    <button @click="setColor('#0000dd')">Azul</button>
    <pre>
    1. O estilo do elemento utiliza o valor da variável css para definir a
    cor de fundo:

    .variable-color {
      background-color: var(<b>--the-color</b>, #aa0011)
    }

    Uma valor <i>failback</i> é definido para a cor: #aa0011. Ele é usado no
    estado inicial.

    2. A variável css é definida diretamente através do atributo <i>style</i>
    do elemento:

    &lt;div
      :style=&quot;<b>{--the-color: {{color}}}</b>&quot;
      class=&quot;rect variable-color&quot;&gt;
    &lt;/div&gt;

    3. Efetivamente o código é renderizado como:

    &lt;div
      style=&quot;<b>--the-color: {{color}}</b>&quot;
      class=&quot;rect variable-color&quot;&gt;
    &lt;/div&gt;
    </pre>
  </div>
</template>

<script>
export default {
  name: 'CSSVars2',
  props: {
    msg: String
  },
  data() {
    return  {
      color: '#aa0000'
    }
  },
  computed: {
    cssVars() {
      return {
        '--the-color': this.color
      }
    }
  },
  methods: {
    setColor(hexValue) {
      this.color=hexValue
    }
  }
}
</script>
<style scoped>
/** Definição da cor de fundo com um valor failback */
.variable-color {
  background-color: var(--the-color, #aa0011)
}
</style>
