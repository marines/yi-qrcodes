<template>
  <div
    id="app"
    class="container"
  >
    <h1 class="text-center my-5">YI live streaming QR Code generator</h1>

    <div class="row">
      <div class="col-md-6 order-md-2">
        <QRCode :options="streamingOptions" />
      </div>
      <div class="col-md-6 order-md-1 mt-sm-4 mt-md-auto">
        <StreamingOptions @change="updateStreamingOptions" />
        <p>If you're ready just scan the QR code with your camera (it's updated automatically). <a href="#">You don't know how?</a></p>
      </div>
    </div>
  </div>
</template>

<script>
import StreamingOptions from "./components/StreamingOptions";
import QRCode from "./components/QRCode.vue";

export default {
  name: "app",
  components: {
    StreamingOptions,
    QRCode
  },
  data: () => ({
    streamingOptions: {}
  }),
  methods: {
    updateStreamingOptions(newOptions) {
      this.streamingOptions = newOptions;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
