<template>
  <main>
    <h3>Kanye Weast Quotes</h3>
    <h4 v-if="loading">loading</h4>
    <h4 v-if="quote">{{quote}}</h4>

    <button v-on:click="getThings">Get another quote</button>
  </main>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      quote: "",
      loading: false
    };
  },
  methods: {
    getThings: async function() {
      this.loading = true;
      const data = await fetch("https://api.kanye.rest").then(rsp =>
        rsp.json()
      );

      this.quote = data.quote;
      this.loading = false;
    }
  },
  async mounted() {
    this.getThings();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

button {
  height: 44px;
  width: 100%;
  border: none;
  background: #007daa;
  color: white;
}
</style>
