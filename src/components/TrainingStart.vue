<template>
  <div>
      <div class="d-flex justify-content-around align-items-center p-1" >
      <button v-on:click="back" type="button" class="btn btn-lg btn-link">Вернуться назад</button>
      <button v-on:click="fetchText" type="button" class="btn btn-secondary">Другой текст</button>
      <h3>00:00</h3>
      </div>
      <hr style="width:90%" class="m-auto">
      <p class="text p-3" v-html="text.newArr">
          
      </p>
  </div>
  
</template>

<script>
export default {
    name:'TrainingStart',
    props: {
        text: {
            type: Object,
            required:true,
        }
    },
    methods: {
        back() {
            this.$emit('back')
        },
        fetchText() {
            this.$emit('fetchText', this.text.n)
            
        }
    }
}
</script>

<style>
.text {
    font-size: 2rem;
    font-weight: bold;
}
</style>