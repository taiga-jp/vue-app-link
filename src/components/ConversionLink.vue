<template>
  <div class="container-app">
    <div class="area-input">
      <div class="area-input-content">
        <input class="input-link" v-model="message" placeholder="input link">
        <div class="check-external-link">
          <input type="checkbox" id="checkbox" v-model="checked">
          <label for="checkbox">外窓リンク</label>
        </div>
        <div class="radio-link-type">
          <span class="radio-btn">
            <input type="radio" id="usually" value="usually" v-model="picked">
            <label for="usually">テキスト</label>
          </span>
          <span class="radio-btn">
            <input type="radio" id="mail" value="mail" v-model="picked">
            <label for="mail">メール</label>
          </span>
          <span class="radio-btn">
            <input type="radio" id="tel" value="tel" v-model="picked">
            <label for="tel">電話</label>
          </span>
        </div>
      </div>
    </div>
    <div class="area-result">
      <p class="result-head">テキストリンク変換後↓↓</p>
      <p id="target" class="result-text">&lt;a href="<span v-if="picked === 'mail'">mailto:</span><span v-else-if="picked === 'tel'">tel:</span>{{ message }}" <span v-if="checked">target="_blank"</span> &gt;{{ message }}&lt;/a&gt;</p>
      <button class="btn-copy" @click="witeToClipboard()">コピー</button>
      <p class="result-cpry-btn">{{ result }}</p>
    </div>
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
.container-app {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 40px 0;
  padding: 0 32px;
}

.area-input {
  width: 50%;
  text-align: center;
}

.area-input-content {
  display: inline-block
}

.input-link {
  display: block;
  width: 250px;
}

.check-external-link {
  margin-top: 10px;
  text-align: left;
}

.radio-link-type {
  margin-top: 10px;
  text-align: left;
}

.radio-btn {
  margin-left: 5px;
}

.radio-btn:first-of-type {
  margin-left: 0;
}

.area-result {
  width: 50%;
  text-align: center;
}

.result-head {
  margin: 0;
  font-size: 20px;
}

.result-text {
  margin-top: 14px;
  margin-bottom: 0;
  color: #000;
  font-size: 14px;
}

.btn-copy {
  margin-top: 20px;
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