<template>
  <div>
      <div class="d-flex justify-content-around align-items-center p-1" >
      <button v-on:click="back" type="button" class="btn btn-lg btn-link">Вернуться назад</button>
      <button type="button" class="btn btn-secondary">Другой текст</button>
      <h3>00:00</h3>
      </div>
      <hr style="width:90%" class="m-auto">
      <p class="text p-3">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum eligendi facilis odio eum nemo esse assumenda id ipsa! Aspernatur, natus! Dicta doloribus ab corrupti ipsam consequuntur vitae ullam nulla libero!
      </p>
  </div>
  
</template>

<script>
export default {
    name:'TrainingStart',
    methods: {
        back() {
            this.$emit('back')
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