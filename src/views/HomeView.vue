

<template>
  <div class="home">
  <h3>{{counterData.title}} {{appTitle}}</h3>
 <button class="btn" @click="decreaseCounter(1)">-</button>
 <button class="btn" @click="decreaseCounter(2)">--</button>
 <span class="counter">{{counterData.count}}</span>
 <button class="btn" @click="increaseCounter(1,$event)">+</button>
 <button class="btn" @click="increaseCounter(2)">++</button>
 <p> This counter is {{oddOrEven}}</p>
 <div class="edit">
 <h4>Edit Counter Title: </h4>
<input
   type='text'
   v-model="counterData.title"
 />
 </div>
  </div>
</template>


<script setup>
import {ref, reactive,computed,
watch, onBeforeMount, onMounted, onUnmounted, onBeforeUnmount, onActivated, onDeactivated, onUpdated, onBeforeUpdate} from 'vue'

const appTitle = 'My Amazing Counter App'                                                                                                                                                                                                                                        
//using ref
  // const counter = ref(10),
  //       counterTitle = ref('My Counter')

  const counterData = reactive({
    count : 0,
    title: 'My Counter'
  })
  
  const oddOrEven = computed(() => {
    if(counterData.count % 2 === 0) return 'even'
    return 'odd'
  })

 watch(() => counterData.count, (newCount) => {
  if(newCount === 20){
    alert("way to go you made it to 20")
  }
 })


    const increaseCounter = (amount,e) =>{
      // counter.value++ ref
      counterData.count += amount //reactive
    }
    const decreaseCounter = (amount) => {
      // counter.value-- ref
      counterData.count -= amount
    }

  onBeforeMount(() => {
    console.log("onBeforeMount")
  })

  onMounted(() => {
    console.log("onMounted")
  })



  onUpdated(() => {
    console.log('updated')
  })

  onBeforeUpdate(() => {
    console.log("before update ")
  })

  onUnmounted(() => {
    console.log("on unmounted")
  })

  onBeforeUnmount(() => {
    console.log("on before unmount")
  })
  
  onActivated(() => {
    console.log("Activated")
  })

  onDeactivated(() => {
    console.log("Deactived")
  })





</script>

<!--
<script>
import {ref} from 'vue'
export default{
  setup(){
    const counter = ref(10)
    const increaseCounter = () =>{
      counter.value++
    }
    const decreaseCounter = () => {
      counter.value--
    }
    return{
      counter,
      increaseCounter,
      decreaseCounter
    }
  }
}
</script>

<!--
<script>
export default {
  data(){
    return{
      counter:0
    }
  },
  methods : {
    increaseCounter(){
      this.counter++
    },
    decreaseCounter(){
      this.counter--
    }
  }
}
</script>
-->

<style>
.home{
  text-align:center;
  padding:20px;
}
.btn,.counter{
  font-size:40px;
  margin:10px;
}
.edit{
  margin-top: 60px;
}
</style>
