<script>
import axios from "axios";
export default {
    data() {
      return{
        albums: {},
      };
    },
  methods: {
    getHashParams() {
      var hashParams = {};
      var e,
        r = /([^&;=]+)=?([^&;]*)/g,
        q = this.token;
      e = r.exec(q);
      while (e) {
        hashParams[e[1]] = decodeURIComponent(e[2]);
        e = r.exec(q);
      }
      return hashParams;
    },
  },
  async created() {
    let response = await axios.get("https://api.spotify.com/v1/albums/2hPHncbZRuWiCBauEUJxyA?market=BR", {
      headers: {
        Authorization: `Bearer BQBRTR1DlM_10jxnyTISb9HxKe2HUE9Rj_jLoCCgg4rlExqrOtDjDX_VA4FUkXPmFw9ycSnpAEeQCHHshMcwguPQdLds129mn73TDM7_rT6YH5Hm7rQtbogbeass2NkuqLTgCLdI3qS_l8r5Db9V3hYsIPSvQkWvzLdhTy0Dbzok13t4_czOdk7PkSl1slGhzhERTYtvKwa14QEtj2ejbg`,
      },
    });
    this.albums = response.data;
  }
}

</script>
<template>
    <h2>{{ albums }}</h2>
</template>