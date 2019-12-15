<template>
  <div id="app">
    <div class="product">
      <div>
        <img :src="imageUrl" width="100%" />
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
    productName: "四季彩の丘",
    productDescription:
      "夏のグリーンシーズンは、色鮮やかな花畑や雄大な景色を。 冬のウィンターシーズンは、雪化粧した丘で迫力満点のアクティビティをお楽しみください。",
    productImageUrl: "product_image/product000.png",
    productBrand: "北海道・美瑛の「四季彩の丘」",
    productPrice: 25000
  },
  {
    productName: "天に続く道",
    productDescription:
      "天に続く道は、北海道斜里町にある全長約28.1キロメートルの直線道路です。真っ直ぐな道がはるか遠くまで続き、あたかも天まで続いているように見えることから名付けられました。 おすすめの時期は、春分の日と秋分の日辺りの年に2回で、道の延長上に夕日が沈んでいく様子を見ることができます。また、付近には名もなき展望台があり、オホーツク海や田畑を見渡すことができます",
    productImageUrl: "product_image/product001.png",
    productBrand: "北海道の国道334・244号線",
    productPrice: 19000
  },
  {
    productName: "幣舞橋",
    productDescription:
      "釧路一の有名観光スポットといえば、幣舞橋（ぬさまいばし）。とにかく絵になるこの橋は、釧路の観光パンフレットなどでは表紙を飾るほど美しく、街のランドマークともなっています。",
    productImageUrl: "product_image/product002.png",
    productBrand: "幣舞橋（釧路市）",
    productPrice: 14000
  },
  {
    productName: "千本鳥居",
    productDescription:
      "秋の京都・４大名所巡り♪伏見稲荷大社・清水寺・金閣寺・嵐山《日帰り》食事付【Ｓ：京料理御膳】１名様より出発保証！NO.1",
    productImageUrl: "product_image/product003.png",
    productBrand: "伏見稲荷大社",
    productPrice: 12000
  },
  {
    productName: "冬の下呂温泉花火物語",
    productDescription:
      "飛騨路の冬を彩る、日本特有の四季の行事や風習を和の風情ある花火で表現。日本トップクラスの花火師たちにより、毎回違う演出で花火が打ち上がるので、毎週見逃せない。何度見ても新しい感動を与えてくれる下呂温泉の花火大会に、足を運んでみよう。",
    productImageUrl: "product_image/product004.png",
    productBrand: "下呂大橋下流飛騨川河畔",
    productPrice: 15000
  },
  {
    productName: "ダナン",
    productDescription:
      "1名催行！うれしい燃油込価格♪羽田深夜発なのでお仕事帰りにもラクラクご出発！現地の空港～ホテル間は、日本語係員同行の往復送迎付き！ご出発40日前までのお受付コースとなります♪",
    productImageUrl: "product_image/product005.png",
    productBrand: "ベトナム",
    productPrice: 33800
  },
  {
    productName: "台北",
    productDescription:
      "うれしい台北3連泊！毎日の荷物の整理は必要ございません！",
    productImageUrl: "product_image/product006.png",
    productBrand: "台湾",
    productPrice: 49900
  },
  {
    productName: "ホノルル",
    productDescription:
      "とびっきり価格でハワイへ！空港からホテルまでの往路タクシー送迎付！追加代金で復路タクシー送迎もお申し込みいただけます。",
    productImageUrl: "product_image/product007.png",
    productBrand: "ハワイ",
    productPrice: 69700
  },
  {
    productName: "ラスベガス",
    productDescription:
      "改装でおしゃれなデザインに変身！ハネムーンにも女子旅にもおすすめホテル”約2年の月日をかけた大規模工事を行い、より一層スタイリッシュなホテルへと生まれ変わりました！煌びやかなラスベガスとはまた一味違う、おしゃれなデザインがホテル各所に♪無料のトラムを使えば、噴水ショーで有名なベラッジオまで約5分で移動可能です。（徒歩では約20分）",
    productImageUrl: "product_image/product008.png",
    productBrand: "アメリカ",
    productPrice: 59700
  },
  {
    productName: "ガーデンズ バイ ザ ベイ",
    productDescription:
      "昼間はマリーナ地区をたっぷり観光、夜は夜景を楽しみながらリバークルーズ、光のショーなどお楽しみください。夕食はシンガポール名物チリクラブです。",
    productImageUrl: "product_image/product009.png",
    productBrand: "シンガポール",
    productPrice: 22600
  },
  {
    productName: "ビッグマック",
    productDescription:
      "おいしさも食べごたえもビッグなマクドナルドの人気メニュー。こだわりの100%ビーフと、特製ビッグマックソースが決め手。",
    productImageUrl: "product_image/product010.png",
    productBrand: "マクドナルド",
    productPrice: 390
  },
  {
    productName: "絶品チーズバーガー",
    productDescription:
      "ややスパイスのきいたパンチがある味のパティと、ふわふわもちもちして糸を引くナチュラルチーズがまさに絶品。",
    productImageUrl: "product_image/product011.png",
    productBrand: "ロッテリア",
    productPrice: 360
  },
  {
    productName: "モスバーガー",
    productDescription: "ジューシーなパティに、特製ミートソース。モスの代表作です",
    productImageUrl: "product_image/product012.png",
    productBrand: "モスバーガー",
    productPrice: 374
  },
  {
    productName: "ハンバーグステーキ",
    productDescription:
      "お手頃価格なジューシーハンバーグ。濃厚デミグラスソースでご賞味ください。",
    productImageUrl: "product_image/product013.png",
    productBrand: "ガスト",
    productPrice: 494
  },
  {
    productName: "グラコロ",
    productDescription:
      "冬の風物詩「グラコロ」がもっと濃厚リッチな味わいになってリニューアル。今年も期間限定で登場します。クリーミーなホワイトソースに相性抜群のえびとマカロニを加え、外はサクサク、中はトロトロのグラタンコロッケに、卵黄を増やし濃厚になったコクのあるたまごソースと、スパイス感をアップさせた芳醇な味わいのコロッケソースを合わせ、バターを増やしてリッチになったふわふわ蒸しバンズではさみました。",
    productImageUrl: "product_image/product014.png",
    productBrand: "マクドナルド",
    productPrice: 340
  },
  {
    productName: "まぐろ",
    productDescription:
      "すしやの評価は赤身で決まるからこそ。仕入れも、選別も加工もスシロー専用基準。赤身は貴重な「天身」部位を使用。",
    productImageUrl: "product_image/product015.png",
    productBrand: "スシロー",
    productPrice: 100
  },
  {
    productName: "ちく玉ぶっかけ",
    productDescription:
      "もっちりとコシの強いうどんに、濃い目の出汁が絡まり、揚げたてのちくわ天と半熟卵の天ぷらは抜群の組み合わせ。レモン汁と大根おろしのトッピングがあることで、ボリュームあるうどんをあっさりと食べることができます。さらに濃い目がお好みの方は、醤油や七味を足していただくのもおススメ。",
    productImageUrl: "product_image/product016.png",
    productBrand: "釜たけうどん",
    productPrice: 780
  },
  {
    productName: "豆狸いなり",
    productDescription:
      "甘く素朴な味わいで変わらぬ人気の豆狸いなりと、本わさび花芽の辛味と揚げの甘みが絶妙な味わいの、わさびいなりを中心に月替りいなり等を販売いたします。すし飯、揚げ、具材の３つの絶妙なバランスを大切にしたいなりです。",
    productImageUrl: "product_image/product017.png",
    productBrand: "豆狸",
    productPrice: 99
  },
  {
    productName: "あごだしラーメン",
    productDescription: "「焼きあご」の風味と和風だしが効いた「あごだしラーメン」",
    productImageUrl: "product_image/product018.png",
    productBrand: "和食さと",
    productPrice: 861
  },
  {
    productName: "なべやの鍋",
    productDescription:
      "なべやオリジナルのオススメ鍋。ドーナツ状の盛り付けがインパクト大です。少し甘めですが、さっぱりとした味わいの特製つけダレでお召し上がりください。 ",
    productImageUrl: "product_image/product019.png",
    productBrand: "MA~なべや　大阪店",
    productPrice: 5780
  },
  {
    productName: "天然とんこつラーメン",
    productDescription:
      "余分なクセを完璧に取り除きとんこつの美味しさを最大限に引き出した天然とんこつスープ。一蘭特製生麺はスープとの相性を第一に考え、特別な小麦を独自にブレンド。更に唐辛子をベースに30数種類の材料を調合・熟成させた元祖「赤い秘伝のたれ」が、味に更なる深みを加えます。",
    productImageUrl: "product_image/product020.png",
    productBrand: "一蘭",
    productPrice: 790
  },
  {
    productName: "餃子",
    productDescription:
      "もちもちの皮の中からは豚肉とにんにく、野菜の旨味が溢れます。にんにくは青森県産、皮の小麦粉は北海道産、その他の主要食材も全て国産です。",
    productImageUrl: "product_image/product021.png",
    productBrand: "餃子の王将",
    productPrice: 220
  },
  {
    productName: "花椒と自家製ラー油の赤麻婆豆腐",
    productDescription:
      "花椒と自家製ラー油によって引き出された辛さと旨味を閉じ込めた逸品。",
    productImageUrl: "product_image/product022.png",
    productBrand: "バーミヤン",
    productPrice: 599
  },
  {
    productName: "中華そばプレミアム",
    productDescription:
      "豚のバラ肉を低温で熟成調理したチャーシューは舌の上でとろけるようにやわらかく、脂の甘味がしっかりと味わえる逸品だ。スープや麺と絡めることで絶妙なバランスとなり、さらにコショウなどの調味料と合わせることで違う味わいも楽しめる。",
    productImageUrl: "product_image/product023.png",
    productBrand: "幸楽苑",
    productPrice: 740
  },
  {
    productName: "チゲ味噌ラーメン",
    productDescription:
      "ニラ、白菜キムチ、玉ねぎとオリジナルの味噌、辛さを効かせた味噌を使用。炒めた具材とスープと合わせることでコクのあるスープに甘さと辛さが加わり、更に溶き卵を入れたことで味がまろやかに！",
    productImageUrl: "product_image/product024.png",
    productBrand: "日高屋",
    productPrice: 630
  },
  {
    productName: "赤福ぜんざい",
    productDescription:
      "冬の甘味「赤福ぜんざい」。ぜんざいに入る大粒の大納言小豆は、雑味を残さず、また小豆の粒と風味を損なわないように丁寧に炊き上げています。",
    productImageUrl: "product_image/product025.png",
    productBrand: "伊勢名物 赤福",
    productPrice: 530
  },
  {
    productName: "京菓抹茶パフェ",
    productDescription:
      "京都四条店限定のメニューが「京菓抹茶パフェ」。ゼリーやガナッシュなどの抹茶フレーバーを中心に、ラズベリーのコンポート、栗の甘露煮、求肥などが織り込まれ、味覚と食感の多様さ、層の美しさまで計算し尽されています。",
    productImageUrl: "product_image/product026.png",
    productBrand: "京都四条店限定",
    productPrice: 1404
  },
  {
    productName: "黒糖バブルミルク",
    productDescription:
      '台湾タピオカドリンク専門 "辰杏珠"のタピオカドリンク。厳選された黒糖を使用した燃え上がるようなサンゴ模様が特徴的な究極の黒糖バブルミルク。',
    productImageUrl: "product_image/product027.png",
    productBrand: "台湾タピオカドリンク専門 辰杏珠",
    productPrice: 540
  },
  {
    productName: "Strawberry Stardust",
    productDescription: "今流行のロールアイス！定番のストロベリー味です。",
    productImageUrl: "product_image/product028.png",
    productBrand: "ROLLICECREAMFACTORY",
    productPrice: 865
  },
  {
    productName: "ユニコーン",
    productDescription:
      "ピンクはストロベリー、水色はブルーハワイのアイス。トッピングは２色の綿菓子・マシュマロ・ホイップ・パールシュガー・とんがり菓子と可愛いだけでなく、少しずつ色々味わえて楽しくなります。",
    productImageUrl: "product_image/product029.png",
    productBrand: "FUWA ROLLICE CREAM FACTORY",
    productPrice: 800
  },
  {
    productName: "おやつカルパス",
    productDescription: "鶏肉と豚肉を使用しソフトな食感に仕上げました。",
    productImageUrl: "product_image/product030.png",
    productBrand: "ヤガイ",
    productPrice: 10
  },
  {
    productName: "ブタメン とんこつ",
    productDescription:
      "ブタメン定番の味。とんこつの旨みを効かせて風味豊かに仕上げてあります。",
    productImageUrl: "product_image/product031.png",
    productBrand: "おやつカンパニー",
    productPrice: 76
  },
  {
    productName: "うまい棒 コーンポタージュ味",
    productDescription:
      "生地のコーンに良く合う、まろやかなコーンポタージュスープをそのままうまい棒で再現しました。",
    productImageUrl: "product_image/product032.png",
    productBrand: "やおきん",
    productPrice: 10
  },
  {
    productName: "ブラックサンダー",
    productDescription:
      "ココアクッキーとプレーンビスケットをチョコレートでコーティングしました。ココアクッキーのほろ苦さとチョコレートの甘さがマッチした味わい、ザクザクとした特徴的な食感、小腹を満たすボリューム感の3拍子が揃った、有楽製菓を代表するお菓子です。",
    productImageUrl: "product_image/product033.png",
    productBrand: "有楽製菓",
    productPrice: 30
  },
  {
    productName: "蒲焼さん太郎",
    productDescription: "タレがしっかりついていて、一度食べると癖になります。",
    productImageUrl: "product_image/product034.png",
    productBrand: "菓道",
    productPrice: 10
  },
  {
    productName: "アクエリアス",
    productDescription:
      "アクエリアスは、水分だけでは足りないミネラルを配合。動くカラダをサポートします。",
    productImageUrl: "product_image/product035.png",
    productBrand: "日本コカ・コーラ社",
    productPrice: 150
  },
  {
    productName: "綾鷹",
    productDescription:
      "綾鷹ならではのにごりの製法による旨みで、厚みのある飲みごたえを実現しました。火入れの強めの茶葉を使用し、かき回さずじっくり抽出して、緑茶本来の旨み・渋み・苦みをていねいに引き出しました。",
    productImageUrl: "product_image/product036.png",
    productBrand: "日本コカ・コーラ社",
    productPrice: 150
  },
  {
    productName: "コカ・コーラ",
    productDescription:
      "今も昔も変わらず、炭酸の刺激と独特の味わいで、のどの渇きを癒すだけでなく、ココロとカラダの両方をリフレッシュし、前向きな楽しい気分へとスイッチしてくれます。",
    productImageUrl: "product_image/product037.png",
    productBrand: "ザ コカ・コーラ カンパニー",
    productPrice: 150
  },
  {
    productName: "STRONGZERO ダブルレモン",
    productDescription:
      "－196℃製法による果実の浸漬酒と果汁をダブルで使用しました。アルコール度数高めの飲みごたえとしっかりとしたレモンの果実感が特長です。",
    productImageUrl: "product_image/product038.png",
    productBrand: "サントリースピリッツ",
    productPrice: 250
  },
  {
    productName: "モンスターエナジー",
    productDescription:
      "アメリカで生まれ、世界中で一大ブームを巻き起こしているエナジードリンク、Monster! 誰もがハマる爽快感とパンチのあるテイスト。日本のMonsterファンのために、独自のエナジーブレンドを実現、Monsterならではのゾクゾク感を体感せよ。",
    productImageUrl: "product_image/product039.png",
    productBrand: "モンスタービバレッジコーポレーション",
    productPrice: 180
  },
  {
    productName: "いろはす",
    productDescription:
      "おいしい日本の天然水い･ろ･は･すは、厳選された全国7ヵ所で採水し、厳しい品質管理を経てお届けしています。また、赤ちゃんのミルクにも安心してお使いいただける軟水です。",
    productImageUrl: "product_image/product040.png",
    productBrand: "日本コカ・コーラ社",
    productPrice: 110
  },
  {
    productName: "CITIZEN AT8125-05E",
    productDescription:
      "１０万年に１秒の誤差しか生じないとされている「原子時計」。この原子時計をもとに送信される標準電波を受信し、自動的に時刻や日付を修正する時計、それが「電波時計」です。シチズンは、この電波時計の動力源にエコ・ドライブを組み合わせることで、正確な時間を常に刻み続ける時計を完成させました。面倒な時刻修正、電池交換の必要がありません。使用される二次電池に有害な金属を含んでおらず、さらに、製造過程で有害物質を使用しません。環境にやさしい、地球にやさしい世界に誇るシチズンテクノロジーです",
    productImageUrl: "product_image/product046.png",
    productBrand: "CITIZEN",
    productPrice: 44000
  },
  {
    productName: "エア-マックス-720-ウェーブス-メンズシューズ",
    productDescription:
      "ナイキ エア マックス 720 ウェーブスは、コート外の文化に新たな視点をもたらすシューズ。Nike史上最も高さのあるAirユニットを搭載したローカットスタイル。カルチャーとスポーツを融合したD/MX/Xデザインで、抜群に快適な新次元のバスケットボールスタイルを体感できます",
    productImageUrl: "product_image/product047.png",
    productBrand: "NIKE",
    productPrice: 19000
  },
  {
    productName: "＜THE NORTH FACE＞フロンティア キャップ",
    productDescription:
      "北の国で生まれたフロンティアキャップ。HARVENT製の表面は冬場でその性能を発揮します。",
    productImageUrl: "product_image/product048.png",
    productBrand: "THE NORTH FACE",
    productPrice: 8800
  },
  {
    productName: "腕時計 レディース 革ベルト メッシュ ウォッチ",
    productDescription:
      "MEIKAの薄型スリムケースは、オン・オフ問わず、あらゆるシーンに溶け込みます。時計を身につけたときの見た目だけでなく、手首にフィットする感覚も男児にしております。流行の大き目フェイスにキルティング柄の彫りを施しており、シンプルかつ他にはないトレンド館のあるデザインが人気を呼んでいます",
    productImageUrl: "product_image/product049.png",
    productBrand: "MEIKA",
    productPrice: 8820
  },
  {
    productName: "Verano Stone Bucket D5531910",
    productDescription:
      "パンクスピリッツを融合させたカリスマブランドのVOLCOMがプロデュースする人気のキャップシリーズの登場です。カジュアルなスケートスタイル&ストリートスタイルで人気商品！",
    productImageUrl: "product_image/product050.png",
    productBrand: "VOLCOM",
    productPrice: 5280
  },
  {
    productName: "ミラクルユー シャンプー",
    productDescription:
      "オーガニックギーオイル配合。傷んだ髪の奥、毛先、パサつきを整えます。ヘアカラーした髪や、紫外線などの乾燥によるダメージから髪を守ります。ノンシリコン、サルフェートフリー。フレッシュな果実のアクセントが輝くフローラルブーケの香り「シャイニーフローラルの香り」",
    productImageUrl: "product_image/product051.png",
    productBrand: "モイスト・ダイアン",
    productPrice: 960
  },
  {
    productName: "ミラクルユー トリートメント",
    productDescription:
      "オーガニックギーオイル配合。傷んだ髪の奥、毛先、パサつきを整えます。ヘアカラーした髪や、紫外線などの乾燥によるダメージから髪を守ります。フレッシュな果実のアクセントが輝くフローラルブーケの香り「シャイニーフローラルの香り」",
    productImageUrl: "product_image/product052.png",
    productBrand: "モイスト・ダイアン",
    productPrice: 968
  },
  {
    productName: "薬用シャンプー ボリュームアップ プレミアムスカルプケア",
    productDescription: "乾燥・かゆみ・フケを防ぎ、ボリュームのある髪へ。",
    productImageUrl: "product_image/product053.png",
    productBrand: "h＆s",
    productPrice: 556
  },
  {
    productName: "薬用コンディショナー ボリュームアップ プレミアムスカルプケア",
    productDescription: "乾燥・かゆみ・フケを防ぎ、ボリュームのある髪へ。",
    productImageUrl: "product_image/product054.png",
    productBrand: "h＆s",
    productPrice: 556
  },
  {
    productName: " スキンケア洗顔料 モイスチャ",
    productDescription:
      "洗うときの肌はとてもデリケートだから、負担をおさえるために洗浄成分にこだわりました。肌のうるおいを守りながら、刺激の一因となる汚れはきちんと落とします",
    productImageUrl: "product_image/product055.png",
    productBrand: "Biore",
    productPrice: 354
  },
  {
    productName: "シグニチャー ココット・ロンド 14cm",
    productDescription:
      "ムラのない熱まわりで、煮込み料理はもちろん炊飯にもおすすめです",
    productImageUrl: "product_image/product056.png",
    productBrand: "LE CREUSET",
    productPrice: 16600
  },
  {
    productName: "コンパクトホットプレート",
    productDescription:
      "毎日の食卓を彩るテーブルウエアの新定番。2~3人のご家庭でも気軽に使える魅力的なサイズ感",
    productImageUrl: "product_image/product057.png",
    productBrand: "BRUNO",
    productPrice: 9100
  },
  {
    productName: "マルチフードカッター",
    productDescription:
      "ハンドルを引くだけで、簡単にみじん切りができあがり。5枚刃なので、パワフル＆スピーディ。包丁、ピーラー要らずで、楽しく調理",
    productImageUrl: "product_image/product058.png",
    productBrand: "D&S",
    productPrice: 1940
  },
  {
    productName: "アボカドカッター",
    productDescription:
      "包丁を使うと滑りやすくて切りにくいアボカドをワンストロークで皮をむいてスライスした状態にできます。",
    productImageUrl: "product_image/product059.png",
    productBrand: "Chef`n",
    productPrice: 1000
  },
  {
    productName: "ガーリックズーム",
    productDescription:
      "本体をミニカーのように前後させて車輪と連動した内部の４枚の刃を回転させると、あっという間ににんにくのみじん切りが出来上がります",
    productImageUrl: "product_image/product060.png",
    productBrand: "Chef`n",
    productPrice: 1620
  },
  {
    productName: "電気シェーバーメンズ 髭剃り",
    productDescription:
      "洗顔ブラシ四つ機能を持つ電動シェーバー。ヘッドチェンジは上に引き抜くだけで用途に合わせたヘッド部分を変えることができます",
    productImageUrl: "product_image/product061.png",
    productBrand: "BOSHENGDA",
    productPrice: 3500
  },
  {
    productName: "ヘアードライヤー",
    productDescription: "過度な熱に頼らず最も速く髪を乾かすヘアードライヤー",
    productImageUrl: "product_image/product062.png",
    productBrand: "Dyson Supersonic Ionic",
    productPrice: 45000
  }
]

export default {
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
