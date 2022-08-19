 <template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="name">
    Hello {{name}}
   <input type="number" v-model="num">
    {{num}}
    
   <input type="number" v-model="num">
     {{num}}
    
    

  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  data(){
    return{
      name: ''
    }
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
