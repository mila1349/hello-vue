<script>
export default {
  data(){
        return{
            firstName:'Mila',
            count:0,
            red:false,
            selectedBook:"",
            books: [{ book: 'The crown prince' }, { book: 'Six crimson cranes' }, { book: 'The wrath and the down' }, { book: 'The school for bad and evil' }],
            message:""
        }
    },
    //normal methods like in javascript
    methods: {
        increment() {
          this.count++
          this.$refs.btn.focus()
        },
      },
    //do task only when component mounted (useEffect in react)
    mounted() {
        this.increment()
    },
    //method to update data to be dynamic (cannot add parameters)(like setState in react)
    computed:{
        countMany(){
            return this.count>1?'Yes':'No'
        },
        redButton(){
            return this.count>1?true:false
        }
    },
    //do this function whenever spesific data changes (dynamic data/ useEffect with [state] in react)
    //param (newState, oldState)
    watch:{
        count(newValue){    
            if (newValue<=5) {
                this.message="bad!"
            }else if(newValue>5){
                this.message="good!"
            }
        }
    },
}

</script>

<template>
  <div class="container">
    <h1>Hello {{firstName}}!</h1>
    <h2>{{message}}</h2>
    <button @click="increment" :id="dynamicId" :class="[button,{ red: redButton }]" ref="btn">{{ count }}</button>
    <p>Has published books:</p>
    <span :style="{'color':redButton?'red':''}">{{ countMany }}</span>
    <ul>
      <li  v-if="redButton" v-for="(item, index) in books">
        Book-{{index+1}} {{item.book}}
      </li>
    </ul>
    <p>Message is: {{selectedBook!==""?selectedBook:"No selected book"}}</p>
    <select v-model="selectedBook" v-if="redButton">
      <option v-for="item in books" :value="item.book">
        {{item.book}}
      </option>
    </select>
  </div>
</template>

<style scoped>
.red{
    background: red;
    color: white;
}
.button{
    padding: 0.5;
    border: none;
    border-radius: 12px;
}
</style>
