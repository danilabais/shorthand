<template>
  <div>
      <div class="d-flex justify-content-around align-items-center p-1" >
      <button v-on:click="fetchText" type="button" onclick="blur()" class="btn btn-outline-secondary">Начать заново</button>
      <h3>324</h3>
      <h3>24</h3>
      </div>
      <hr style="width:90%" class="m-auto">
      <p  v-html="text"  class="text p-2">
      </p>
  </div>
</template>

<script>
export default {
    name:'ExamStart',
    props: {
      text: {
        type: String,
        required:true,
      }
    },
    methods: {
      fetchText(){
        this.$emit('fetchText')
      }
    }
}
</script>

<style>

</style>