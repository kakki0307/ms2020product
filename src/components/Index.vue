<template>
  <div id="app">
    <h1>商品詳細画面</h1>
    <div id="products">
      <h2>{{ state.productName }}</h2>
      <img :src="imageUrl" />
      <p>{{ state.productPrice }}円</p>
      <p>{{ state.productDescription }}</p>
      <p>{{ state.productBrand }}</p>
    </div>
  </div>
</template>
<script>
const ProductInfo = [
  {
    productName: '四季彩の丘',
    productImageUrl: 'product_image/product000.png',
    productDescription:
      '夏のグリーンシーズンは、色鮮やかな花畑や雄大な景色を。 冬のウィンターシーズンは、雪化粧した丘で迫力満点のアクティビティをお楽しみください。',
    productPrice: 25000,
    productBrand: '北海道・美瑛の「四季彩の丘」'
  },
  {
    productName: '天に続く道',
    productImageUrl: 'product_image/product001.png',
    productDescription:
      '天に続く道は、北海道斜里町にある全長約28.1キロメートルの直線道路です。真っ直ぐな道がはるか遠くまで続き、あたかも天まで続いているように見えることから名付けられました。おすすめの時期は、春分の日と秋分の日辺りの年に2回で、道の延長上に夕日が沈んでいく様子を見ることができます。また、付近には名もなき展望台があり、オホーツク海や田畑を見渡すことができます。',
    productPrice: 19000,
    productBrand: '北海道の国道334・244号線'
  }
]

export default{
  data () {
    let id = this.$route.query.id
    if (!id) {
      id = 0
    }
    const state = ProductInfo[id]
    const image = state.productImageUrl
    return {
      state,
      imageUrl: require(`../assets/${image}`),
      id
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
  width: 200px;
  height: 200px;
  border: 1px black solid;
}
</style>
