 <template>
  <div class="hello">
    <h1>{{ arithmetic }}</h1>
    
   <input type="number" v-model="num1">
    {{num1}}<br><br>
    
   <input type="number" v-model="num2">
     {{num2}}<br><br>
    
      <button @click="add">Add</button>
      <button @click="sub">Subtract</button>
      <button @click="mul">Multiply</button>
      <button @click="div">Divide</button>
      <p v-if="result>0" class="positive">{{ resultString }} {{ result }}</p>
      <p v-else-if="result<0" class="negative">{{ resultString }} {{ result }}</p>
      <p v-else>{{ resultString }}{{result}}</p>

  </div>
</template>

<script>
export default {
  props: {
   arithmetic : Number
  },
  data(){
    return{
      num1: '',
      num2: '',
      result: '',
      resultString: '',
      sum: '',
      diff: '',
      prod: '',
      quot: ''
    }
  },
    methods:{
    calculate(){
      this.sum = (Number(this.num1)+Number(this.num2))
      this.diff = (this.num1-this.num2)
      this.prod = (this.num1*this.num2)
      this.quot = (this.num1/this.num2)
    },
    add(){
      this.result = (Number(this.num1)+Number(this.num2))
      console.log(this.result);
      this.resultString = "Sum :"
    },
    sub(){
      this.result = (this.num1-this.num2)
      this.resultString = "Difference :"
    },
    mul(){
      this.result = (this.num1*this.num2)
      this.resultString = "Product :"
    },
    div(){
      this.resultString = ''
      if(this.num2 != 0){
        this.result = (this.num1/this.num2)
        this.resultString = "Quotient :"
      }
      else
        this.result = 'Divisor cannot be 0'
    },
  
}
}

</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


p{
  font-weight: bold;
  font-size: larger;
  font-style: normal;
  
}
button{
  margin-left: 7px;
}
div{
  margin-top: 5%;
}
.positive{
  color: red; 
}
.negative{
  color: orange;
}
</style>