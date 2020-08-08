<template>
  <div>
    <input class="input-link" v-model="message" placeholder="edit me">
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">外窓リンク</label>
    <br>
    <input type="radio" id="usually" value="usually" v-model="picked">
    <label for="usually">usually</label>
    <input type="radio" id="mail" value="mail" v-model="picked">
    <label for="mail">mail</label>
    <input type="radio" id="tel" value="tel" v-model="picked">
    <label for="tel">tel</label>
    <br>
    <span>Picked: {{ picked }}</span>
    <p id="target">&lt;a href="<span v-if="picked === 'mail'">mailto:</span><span v-else-if="picked === 'tel'">tel:</span>{{ message }}" <span v-if="checked">target="_blank"</span> &gt;{{ message }}&lt;/a&gt;</p>
    <button class="btn-copy" @click="witeToClipboard()">copy</button>
    <p>{{ result }}</p>
  </div>
</template>

<script>
export default {
  name: 'ConversionLink',
  data: function () {
    return {
      message: "",
      result: "",
      checked: false,
      picked: ""
    }
  },
  methods: {
    witeToClipboard() {
      const copyText = this.$el.querySelector('#target').textContent
      navigator.clipboard
        .writeText(copyText)
        .then(() => {
          console.log('テキストコピー完了');
          this.result = "テキストコピー完了";
        })
        .catch(e => {
          console.error(e);
          this.result = e;
        })
    }
  }
}
</script>

<style scoped>
.input-link {
  display: block;
  margin: 0 auto 10px;
}

.btn-copy {
  padding: 6px 12px;
  color: #fff;
  background-color: #3B5998;
  border: none;
  border-radius: 8px;
  font-size: 18px;
  outline: none;
  appearance: none;
  transition: all .4s;
}

.btn-copy:hover {
  cursor: pointer;
  opacity: 0.8;
}
</style>