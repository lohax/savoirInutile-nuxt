<template>
  <div class="container">
    <div>
      <h1 class="title">
        {{ phrase }}
      </h1>
      <h2 class="subtitle" @click="getPhrase()">
        Un nouveau savoir inutile ?
        <br>
        Clique ici !
      </h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "SavoirInutile",
  data() {
    return {
      phrase : "SavoirInutile"
    };
  },
  methods: {
    getPhrase(){
      axios
        .get('https://uselessfacts.jsph.pl/random.json?language=en')
        .then(res => this.phrase = res.data.text)

    }
  },
  mounted(){
    axios
        .get('https://uselessfacts.jsph.pl/random.json?language=en')
        .then(res => this.phrase = res.data.text)
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 30px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
  cursor: pointer;
}

.links {
  padding-top: 15px;
}
</style>
