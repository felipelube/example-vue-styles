<template>
  <div>
    <div ref="rect" class="rect variable-color"></div>
    <button @click="setColor('#aa0000')">Vermelho</button>
    <button @click="setColor('#00aa00')">Verde</button>
    <button @click="setColor('#0000dd')">Azul</button>
    <pre>


    1. O estilo do elemento utiliza o valor da variável css para definir a
    cor de fundo:

    .variable-color {
      background-color: var(<b>--the-color</b>, #aa0011)
    }

    Uma valor <i>failback</i> é definido para a cor: #aa0011. Ele é usado também
    no estado inicial.


    Variável CSS
      <b>--the-color: {{color}}</b>

    <template v-if="messages.length">
    2. Uma chamada à função <a
      taget="_blank"
      href="https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties#Values_in_JavaScript"
    >element.style.setProperty</a> define a variável
    css no elemento:

    {{messages.join("\n  ")}}
    </template>

    </pre>
  </div>

</template>

<script>
export default {
  name: 'CSSVars1',
  props: {
    msg: String
  },
  data() {
    return {
      color: '(não setada)',
      messages: []
    }
  },
  methods: {
    setColor(hexValue) {
      this.color = hexValue
      this.messages.push(`this.$refs.rect.style.setProperty('--the-color', ${hexValue})`)
    }
  },
  watch: {
    color(hexValue) {
      try {
        this.$refs.rect.style.setProperty('--the-color', hexValue)
      } catch {
        //ignore
      }
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
