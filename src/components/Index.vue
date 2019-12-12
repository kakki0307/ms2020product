<template>
  <div id="app">
    <div class="product">
      <div>
        <img :src="state.productImageUrl" width="100%" />
      </div>
      <div class="product-text">
        <h2 class="product-title">{{ state.productName }}</h2>
        <p class="product-price">{{ commaProductPrice }}<s>円(税込)</s></p>
        <p class="product-desc">{{ state.productDescription }}</p>
      </div>
      <div class="buy-button">
        <i class="material-icons"> redeem </i>購入する
      </div>
    </div>
  </div>
</template>
<script>
const commaNumber = require('comma-number')
const ProductInfo = [
  {
    productName: '四季彩の丘',
    productImageUrl:
      'data:image/gif;base64,R0lGODdhEAAJAIABAP8AAP///ywAAAAAEAAJAAACCoSPqcvtD6OclBUAOw==',
    productDescription:
      '夏のグリーンシーズンは、色鮮やかな花畑や雄大な景色を。 冬のウィンターシーズンは、雪化粧した丘で迫力満点のアクティビティをお楽しみください。',
    productPrice: 25000
  },
  {
    productName: '天に続く道',
    productImageUrl:
      'data:image/gif;base64,R0lGODdhEAAJAIABAP8AAP///ywAAAAAEAAJAAACCoSPqcvtD6OclBUAOw==',
    productDescription:
      '天に続く道は、北海道斜里町にある全長約28.1キロメートルの直線道路です。真っ直ぐな道がはるか遠くまで続き、あたかも天まで続いているように見えることから名付けられました。おすすめの時期は、春分の日と秋分の日辺りの年に2回で、道の延長上に夕日が沈んでいく様子を見ることができます。また、付近には名もなき展望台があり、オホーツク海や田畑を見渡すことができます。',
    productPrice: 19000
  }
]

export default {
  data () {
    const id = this.$route.params.id
    const state = ProductInfo[id]
    return {
      state
    }
  },
  computed: {
    commaProductPrice () {
      return commaNumber(this.state.productPrice)
    }
  }
}
</script>
<style scoped>
#app {
  font-family: "Open Sans", "Noto Sans JP", "Avenir", Helvetica, Arial,
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #431;
  max-width: 500px;
  margin: 0 auto;
  line-height: 1.5;
  font-weight: 400;
}
.product-text {
  padding: 0 1rem;
}
.product-title {
  padding-top: 1rem;
  padding-bottom: 1rem;
  font-size: 2rem;
  line-height: 1;
  font-weight: inherit;
  font-weight: 300;
}
.product-price {
  font-size: 1.7rem;
  line-height: 1;
  padding-bottom: 1rem;
  font-weight: 300;
}
.product-price s {
  font-style: normal;
  text-decoration: none;
  font-size: 0.6em;
  padding-left: 0.3em;
}
.product-desc {
}
.buy-button {
  margin: 1rem 2rem;
  border: 1px solid #999;
  border-radius: 1rem;
  padding: 0.8rem;
  font-size: 1.5rem;
  text-align: center;
  vertical-align: middle;
}
.buy-button i {
  font-size: 1.5rem;
  vertical-align: middle;
  padding-right: 0.3rem;
}
</style>
