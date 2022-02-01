<template>
  <div>
      <div class="bg-body shadow-lg mx-auto mt-3 " style="width: 80%; min-height: 200px; border-radius: 21px 21px 21px 21px;">
        <ExamLobby v-if="!isStart" v-on:startCounter="startCounter"/>
        <Counter v-if="isStart && !isStartExam" v-on:exam="exam"/>
        <ExamStart v-on:fetchText="repeat" v-bind:text="text" v-if="isStartExam"/>


        </div>
        
  </div>
</template>

<script>


    import axios from 'axios'
    import ExamLobby from '@/components/ExamLobby.vue'
    import Counter from '@/components/Counter.vue'
    import ExamStart from '@/components/ExamStart.vue'

export default {

    name:'Exam',
    data() {
        return {
            isStart:false,
            isStartExam:false,
            text:'',

        }
    },
    components: {
        ExamLobby,
        Counter,
        ExamStart,

    },
    methods: {
        repeat(){
             this.isStart=true
             this.isStartExam=false
            this.fetchText()
        },
        startCounter() {
            this.isStart=true
             this.fetchText()
        },
        exam() {
            this.isStartExam = true
            
            
        },
        async fetchText() {
        try {
          const response = await axios.get(`https://fish-text.ru/get?format=text&number=8`)
          this.text = this.wrap(response.data.text)
        } catch (error) {
          alert('ошибка ', error)
        }
        },
        wrap(text) {
        const arr=text.split('')
        let newArr=[]
        for (let i=0; i<arr.length;i++) {
          newArr.push(`<span>${arr[i]}</span>`)
        }
        newArr=newArr.join('')
        return newArr
      }
    },
    
   
}
</script>

<style>

</style>