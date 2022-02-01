<template>
 <div  class="bg-light  pt-3 px-3 pt-md-5 px-md-5 mb-4 text-center" >
     
        <h2 class="display-5">Тренировка скорописи.</h2>
        <p class="lead">Улучши свои показатели, и не забывай о технике!</p>
     
      <div class="bg-body shadow-lg mx-auto " style="width: 80%; min-height: 200px; border-radius: 21px 21px 21px 21px;">
        <TrainingLobby  v-if="!isStart && !isFinish" @start="onStart"/>
        <TrainingStart @fetchText="fetchText" v-bind:text="text" v-if="isStart" @finish="finish" @back="onBack"/> 
        <TrainingFinish v-if="isFinish" v-bind:result="result" @back="onBackFromFinish"/>
      </div>
    </div>
</template>

<script>
import TrainingLobby from '@/components/TrainingLobby.vue'
import TrainingStart from '@/components/TrainingStart.vue'
import TrainingFinish from '@/components/TrainingFinish.vue'
import axios from 'axios'

export default {
    components: {
      TrainingLobby,
      TrainingStart,
      TrainingFinish,
    },
    data () {
      return {
        isStart:false,
        text:{},
        n:null,
        isFinish:false,
        result:[]
        
      }
    },
    methods: {
      onStart(data) {
        this.isStart=true
        this.fetchText(data)
      },
      finish(arr) {
        this.isStart=false
        this.isFinish=true
        this.result=arr
        
      },
      onBack() {
        this.isStart=false
        console.log('lol')
      },
      onBackFromFinish() {
        this.isStart=false
        this.isFinish=false
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
