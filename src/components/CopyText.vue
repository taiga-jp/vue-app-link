<template>
  <div style="display: none;">
    <button class="btn-copy"
      @click="witeToClipboard()"
    >
      copy
    </button>

    <div id="target">
      <p>コピーテキスト</p>
    </div>

    <p>{{ result }}</p>
  </div>
</template>

<script>
export default {
  name: 'CopyText',
  data: function () {
    return {
      result: ""
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
.btn-copy {
  padding: 6px 12px;
  color: #fff;
  background-color: #3B5998;
  border: none;
  border-radius: 8px;
  font-size: 18px;
  outline: none;
  appearance: none;
}

.btn-copy:hover {
  cursor: pointer;
}
</style>