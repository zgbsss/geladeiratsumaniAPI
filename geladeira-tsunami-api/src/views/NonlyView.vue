<script>
import axios from 'axios'
export default {
  data() {
    return {
      token: "dddd",
      dados: {},
      albums: [],
      artista2: {}
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
    this.token = this.$route.query["access_token"];

    response = await axios.get('https://api.spotify.com/v1/artists/3ZHU5AKrUmIPnCFfr82QER', { headers: {
      Authorization: `Bearer ${this.token}`} 
    })
    this.artista2 = response.data
    // console.log(this.getHashParams());
  },
};