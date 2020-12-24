<template>
  <div class="container">
    <div style="text-align: center">

      <h4>あなたの寿命は？</h4>
      <b-form-group label="あなたの心拍数(分)" >
        <b-form-input
            style="width: 250px; text-align: center; margin: 10px auto;"
            placeholder="あなたの心拍数(分)"
            size="lg"
            v-model="input_sinpaku"
        >

        </b-form-input>
      </b-form-group>

      <h5>あなたの予想寿命</h5>
      <H1>{{ Math.round((jumyo_max_sinpaku / input_sinpaku) / 525600)}}歳</H1>


    </div>
  </div>
</template>

<script>
export default {
  name: 'index.vue',
  data () {
    return {
      jumyo_max_sinpaku: 2300000000,
      input_sinpaku: 50
    }
  },
}
</script>

<style scoped>

</style>
