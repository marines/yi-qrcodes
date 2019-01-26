<template>
  <form>
    <div class="form-group row">
      <label class="col-sm-6 col-form-label text-sm-right">RTMP URL
        <small
          id="urlHelp"
          class="form-text text-muted"
        ><a href="#">Confused?</a></small>
      </label>
      <div class="col-sm-6">
        <input
          type="text"
          class="form-control"
          aria-describedby="urlHelp"
          placeholder="Enter RTMP URL"
          v-model="model.url"
          @keyup="emitOptions"
        >
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-6 col-form-label text-sm-right">WiFi SSID
        <small
          id="ssidHelp"
          class="form-text text-muted"
        >Your WiFi network name.</small>
      </label>
      <div class="col-sm-6">
        <input
          type="text"
          class="form-control"
          aria-describedby="ssidHelp"
          placeholder="Enter SSID"
          v-model="model.ssid"
          @keyup="emitOptions"
        >
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-6 col-form-label text-sm-right">WiFi Password
        <small
          id="passwordHelp"
          class="form-text text-muted"
        >The password isn't being sent anywhere.</small>
      </label>
      <div class="col-sm-6">
        <input
          type="password"
          class="form-control"
          aria-describedby="passwordHelp"
          placeholder="Enter password"
          v-model="model.pwd"
          @keyup="emitOptions"
        >
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-6 col-form-label text-sm-right">Resolution
        <small
          id="resHelp"
          class="form-text text-muted"
        >Resolution of your stream.</small>
      </label>
      <div class="col-sm-6">
        <select
          class="form-control"
          aria-describedby="resHelp"
          v-model="model.res"
          @change="emitOptions"
        >
          <option value="1080p">1080p</option>
          <option value="720p">720p</option>
          <option value="480p">480p</option>
          <option value="360p">360p</option>
        </select>
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-6 col-form-label text-sm-right">Bitrate
        <small
          id="rateHelp"
          class="form-text text-muted"
        >Quality of your stream.</small>
      </label>
      <div class="col-sm-6">
        <select
          class="form-control"
          aria-describedby="rateHelp"
          v-model="model.rate"
          @change="emitOptions"
        >
          <option value="0">Auto</option>
          <option value="3">High</option>
          <option value="2">Medium</option>
          <option value="1">Low</option>
        </select>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data: () => ({
    model: {
      ssid: "",
      pwd: "",
      res: "1080p",
      rate: "0",
      dur: "0",
      url: '',
        // "rtmp://live-api-s.facebook.com:80/rtmp/2284082301603026?s_sw=0&s_vt=api-s&a=AbxhaJLkusWI5LYd"
    }
  }),

  created() {
    this.emitOptions();
  },

  methods: {
    emitOptions() {
      this.$emit("change", { ...this.model });
    }
  }
};
</script>
