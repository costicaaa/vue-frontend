<template>
  <div class="hello">
    <template v-for="item of names">
      <p :key="item.id">{{item.id}} - {{item.name}}</p>
    </template>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return {
      names: []
    }
  },
  props: {
    msg: String
  },
  methods: {
      getData(){
        console.log(process.env);
        console.log(process.env.VUE_APP_API_URL);
        let baseUrl = process.env.VUE_APP_API_URL + '/api';
        console.log(baseUrl);
        this.$axios.get(baseUrl + '/' + 'example-get')
        .then((response) => {
          this.names = response.data;
        }).catch((error) => {
          console.log(error);
          this.names = [{
            id: 1,
            name: 'error'
          }];
        })
      }
  },
  mounted(){
    this.getData();
  }
}
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
</style>
