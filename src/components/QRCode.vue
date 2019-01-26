<template>
  <div>
    <img
      v-if="codeImageData"
      :src="codeImageData"
    />
  </div>
</template>

<script>
const qrcode = require("qrcode");

export default {
  props: {
    options: {
      type: Object,
      default: {},
    }
  },
  data: () => ({
    isGenerating: false,
    codeImageData: '',
    codeOptions: {
      margin: 1,
      width: 350
    }
  }),

  watch: {
    options() {
      this.regenerateCode();
    }
  },

  created() {
    this.regenerateCode();
  },

  methods: {
    regenerateCode() {
      this.isGenerating = true;
      qrcode.toDataURL(JSON.stringify(this.options), this.codeOptions).then(url => {
        this.codeImageData = url;
        this.isGenerating = false;
      });
    }
  }
};
</script>

<style scoped>
div {
  text-align: center;
}
img {
  max-width: 100%;
}
</style>
