<template>
  <v-row>
    <v-col class="text-center">
      <h2>{{ response }}</h2>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'axios',
  data() {
    return {
      response: '',
    }
  },
  async asyncData({ $axios, params }) {
    const sleep = (msec) => new Promise((resolve) => setTimeout(resolve, msec))
    // ipアドレスを取得
    const response = await $axios.$get(
      'https://zipcloud.ibsnet.co.jp/api/search?zipcode=' + params.postcode
    )
    // 5秒待つ
    await sleep(5000)
    return { response }
  },
}
</script>
