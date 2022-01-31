<template>
  <div>
      <div  class="bg-light  pt-3 px-3 pt-md-5 px-md-5 text-center">
        <h2 class="display-5">Экзамен</h2>
            <ul class="lead">
                <li>
                Нельзя выбрать количество предложений
                </li>
                <hr style="width:20%" class="m-auto">
                <li>
                Убраны лишнии визуальные элементы
                </li>
                <hr style="width:20%" class="m-auto">
                <li>
                Рекорды сохраняются
                </li>
                <hr style="width:20%" class="m-auto">
                <li>
                Максимальная концентрация
                </li>
                </ul>
            <button v-on:click="start" type="button" class="btn btn-lg btn-outline-success mt-5 mb-5">Начать экзамен</button>
        </div>
        
  </div>
</template>

<script>
import TrainingStart from '@/components/TrainingStart.vue'
export default {
    name:'Exam',
    components: {
        TrainingStart

    } 
}
</script>

<style scoped>
li {
    font-size: 1.3em;
    list-style: none;
}
</style>