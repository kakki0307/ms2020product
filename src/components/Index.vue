<template>
  <div id="app">
    <h1>商品詳細画面</h1>
    <div id="products">
      <h2>{{ state.productName }}</h2>
      <p>{{ state.productPrice }}円</p>
      <p>{{ state.productDescription }}</p>
    </div>
  </div>
</template>
<script>
const ProductInfo = [
  {
    productName: '四季彩の丘',
    productImageUrl: 'test.png',
    productDescription:
      '夏のグリーンシーズンは、色鮮やかな花畑や雄大な景色を。 冬のウィンターシーズンは、雪化粧した丘で迫力満点のアクティビティをお楽しみください。',
    productPrice: 25000
  },
  {
    productName: '天に続く道',
    productImageUrl: 'test.png',
    productDescription:
      '天に続く道は、北海道斜里町にある全長約28.1キロメートルの直線道路です。真っ直ぐな道がはるか遠くまで続き、あたかも天まで続いているように見えることから名付けられました。おすすめの時期は、春分の日と秋分の日辺りの年に2回で、道の延長上に夕日が沈んでいく様子を見ることができます。また、付近には名もなき展望台があり、オホーツク海や田畑を見渡すことができます。',
    productPrice: 19000
  }
]

export default{
  data () {
    const id = this.$route.query.id
    const state = ProductInfo[id]
    return {
      state
    }
  }
}
</script>
<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #706d71;
  margin-top: 60px;
}
img {
  border: 1px black solid;
}
</style>
