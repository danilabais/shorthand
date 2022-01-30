<template>
 <div  class="bg-light  pt-3 px-3 pt-md-5 px-md-5 text-center" >
     
        <h2 class="display-5">Тренировка скорописи.</h2>
        <p class="lead">Улучши свои показатели, и не забывай о технике!</p>
     
      <div class="bg-body shadow-sx mx-auto" style="width: 80%; min-height: 300px; border-radius: 21px 21px 21px 21px;">
        <TrainingLobby v-if="!isStart" @start="onStart"/>
        <TrainingStart @fetchText="fetchText" v-bind:text="text" v-if="isStart" @back="onBack"/>
      </div>
    </div>
</template>

<script>
import TrainingLobby from '@/components/TrainingLobby.vue'
import TrainingStart from '@/components/TrainingStart.vue'
import axios from 'axios'

export default {
    components: {
      TrainingLobby,
      TrainingStart,
    },
    data () {
      return {
        isStart:false,
        text:{},
        n:null,
        
      }
    },
    methods: {
      onStart(data) {
        this.isStart=true
        this.fetchText(data)
      },
      onBack() {
        this.isStart=false
      },
       async fetchText(n) {
        try {
          const response = await axios.get(`https://fish-text.ru/get?format=text&number=${n}`)
          this.text = this.wrap(response.data.text,n)
        } catch (error) {
          alert('ошибка ', error)
        }
      },
      wrap(text,n) {
        const arr=text.split('')
        let newArr=[]
        for (let i=0; i<arr.length;i++) {
          newArr.push(`<span>${arr[i]}</span>`)
        }
        newArr=newArr.join('')
        console.log(newArr)
        return {
          newArr,
          n,
        }
      },
      
    }
    
}
</script>

<style>

</style>
