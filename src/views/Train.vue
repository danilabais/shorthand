<template>
 <div  class="bg-light  pt-3 px-3 pt-md-5 px-md-5 text-center" >
     
        <h2 class="display-5">Тренировка скорописи.</h2>
        <p class="lead">Улучши свои показатели, и не забывай о технике!</p>
     
      <div class="bg-body shadow-sx mx-auto" style="width: 80%; min-height: 300px; border-radius: 21px 21px 21px 21px;">
        <TrainingLobby v-if="!isStart" @start="onStart"/>
        <TrainingStart v-if="isStart" @back="onBack"/>
      </div>
    </div>
</template>

<script>
import TrainingLobby from '@/components/TrainingLobby.vue'
import TrainingStart from '@/components/TrainingStart.vue'

export default {
    components: {
      TrainingLobby,
      TrainingStart,
    },
    data () {
      return {
        isStart:false,
      }
    },
    methods: {
      onStart(data) {
        this.isStart=true
      },
      onBack() {
        this.isStart=false
      }
    }
    
}
</script>

<style>

</style>
