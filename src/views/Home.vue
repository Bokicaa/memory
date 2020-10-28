<template>
  <div class="home">
    <Memory :images="images"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Memory from '@/components/Memory.vue'

export default {
  name: 'home',
  data() {
    return {
      images: [
      [
        {id: '0', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300082/96755210-single-sweet-yellow-pepper-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '1', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300071/96755133-single-brown-onion-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '2', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300085/96755219-single-green-cabbage-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '3', img: 'https://previews.123rf.com/images/kulyk/kulyk1703/kulyk170300007/73432765-single-pear-fruit-close-up-raw-pear-with-leaf-isolated-on-white-background-qualitative-vector-illust.jpg'},
        {id: '4', img: 'https://thumbs.dreamstime.com/b/broccoli-2021380.jpg'},
        {id: '5', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170501873/77536046-tigre-joven-solo-icono-de-los-animales-en-el-calificador-del-estilo-de-la-historieta-web-com%C3%BAn-del-ejemp.jpg'},
        {id: '6', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170500292/77140005-cachorro-labrador-animales-%C3%ADcono-%C3%BAnico-en-estilo-de-dibujos-animados-ilustraci%C3%B3n-vectorial-s%C3%ADmbolo-stock-web-.jpg'},
        {id: '7', img: 'https://www.colourbox.com/preview/34215816-red-fox-animals-single-icon-in-cartoon-style-vector-symbol-stock-illustration-web.jpg'},
        {id: '8', img: 'https://www.pngkit.com/png/detail/36-363828_clip-art-download-lamp-png-oil-diwali-decoration.png'},
        {id: '9', img: 'https://previews.123rf.com/images/ylivdesign/ylivdesign1609/ylivdesign160905554/62985388-wooden-chair-icon-in-cartoon-style-isolated-on-white-background-vector-illustration.jpg'},
        {id: '10', img: 'https://png.pngtree.com/png-clipart/20190905/original/pngtree-a-laptop-illustration-png-image_4519740.jpg'},
        {id: '11', img: 'https://cdn.shopify.com/s/files/1/1758/4341/products/S-01.jpg?v=1546184258'}
      ],
      [
        {id: '0', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300082/96755210-single-sweet-yellow-pepper-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '1', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300071/96755133-single-brown-onion-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '2', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300085/96755219-single-green-cabbage-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '3', img: 'https://previews.123rf.com/images/kulyk/kulyk1703/kulyk170300007/73432765-single-pear-fruit-close-up-raw-pear-with-leaf-isolated-on-white-background-qualitative-vector-illust.jpg'},
        {id: '4', img: 'https://thumbs.dreamstime.com/b/broccoli-2021380.jpg'},
        {id: '5', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170501873/77536046-tigre-joven-solo-icono-de-los-animales-en-el-calificador-del-estilo-de-la-historieta-web-com%C3%BAn-del-ejemp.jpg'},
        {id: '6', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170500292/77140005-cachorro-labrador-animales-%C3%ADcono-%C3%BAnico-en-estilo-de-dibujos-animados-ilustraci%C3%B3n-vectorial-s%C3%ADmbolo-stock-web-.jpg'},
        {id: '7', img: 'https://www.colourbox.com/preview/34215816-red-fox-animals-single-icon-in-cartoon-style-vector-symbol-stock-illustration-web.jpg'},
        {id: '8', img: 'https://www.pngkit.com/png/detail/36-363828_clip-art-download-lamp-png-oil-diwali-decoration.png'},
        {id: '9', img: 'https://previews.123rf.com/images/ylivdesign/ylivdesign1609/ylivdesign160905554/62985388-wooden-chair-icon-in-cartoon-style-isolated-on-white-background-vector-illustration.jpg'},
        {id: '10', img: 'https://png.pngtree.com/png-clipart/20190905/original/pngtree-a-laptop-illustration-png-image_4519740.jpg'},
        {id: '11', img: 'https://cdn.shopify.com/s/files/1/1758/4341/products/S-01.jpg?v=1546184258'},
        {id: '12', img: 'https://mir-s3-cdn-cf.behance.net/project_modules/1400/9a968718325641.5a96e2cfc6f5c.jpg'},
        {id: '13', img: 'https://i.etsystatic.com/15458805/r/il/78b25c/1711086161/il_570xN.1711086161_meig.jpg'}
      ],
      [
        {id: '0', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300082/96755210-single-sweet-yellow-pepper-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '1', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300071/96755133-single-brown-onion-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '2', img: 'https://previews.123rf.com/images/arnygfx/arnygfx1803/arnygfx180300085/96755219-single-green-cabbage-on-white-background-vegetables-vector-illustration-.jpg'},
        {id: '3', img: 'https://previews.123rf.com/images/kulyk/kulyk1703/kulyk170300007/73432765-single-pear-fruit-close-up-raw-pear-with-leaf-isolated-on-white-background-qualitative-vector-illust.jpg'},
        {id: '4', img: 'https://thumbs.dreamstime.com/b/broccoli-2021380.jpg'},
        {id: '5', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170501873/77536046-tigre-joven-solo-icono-de-los-animales-en-el-calificador-del-estilo-de-la-historieta-web-com%C3%BAn-del-ejemp.jpg'},
        {id: '6', img: 'https://previews.123rf.com/images/pandavector/pandavector1705/pandavector170500292/77140005-cachorro-labrador-animales-%C3%ADcono-%C3%BAnico-en-estilo-de-dibujos-animados-ilustraci%C3%B3n-vectorial-s%C3%ADmbolo-stock-web-.jpg'},
        {id: '7', img: 'https://www.colourbox.com/preview/34215816-red-fox-animals-single-icon-in-cartoon-style-vector-symbol-stock-illustration-web.jpg'},
        {id: '8', img: 'https://www.pngkit.com/png/detail/36-363828_clip-art-download-lamp-png-oil-diwali-decoration.png'},
        {id: '9', img: 'https://previews.123rf.com/images/ylivdesign/ylivdesign1609/ylivdesign160905554/62985388-wooden-chair-icon-in-cartoon-style-isolated-on-white-background-vector-illustration.jpg'},
        {id: '10', img: 'https://png.pngtree.com/png-clipart/20190905/original/pngtree-a-laptop-illustration-png-image_4519740.jpg'},
        {id: '11', img: 'https://cdn.shopify.com/s/files/1/1758/4341/products/S-01.jpg?v=1546184258'},
        {id: '12', img: 'https://mir-s3-cdn-cf.behance.net/project_modules/1400/9a968718325641.5a96e2cfc6f5c.jpg'},
        {id: '13', img: 'https://i.etsystatic.com/15458805/r/il/78b25c/1711086161/il_570xN.1711086161_meig.jpg'},
        {id: '14', img: 'https://images.squarespace-cdn.com/content/v1/5281873ae4b05f093cd13878/1530809193791-Y7SJWW7HTKGP8ZN24GWY/ke17ZwdGBToddI8pDm48kF_9s3zVrf2BM7LLPrSvgmAUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKcln5zjEp46fW8FFGIxcn3qxhYaYnabf6bXP6VCJ_YcfimPSvxK2iZ7hWlcCxjDp4e/Fig+3.jpg?format=1500w'},
        {id: '15', img: 'https://png.pngtree.com/png-vector/20191113/ourlarge/pngtree-illustration-of-mangosteen-fruit-on-a-white-background-png-image_1987356.jpg'}
      ]
    ]
    }
  },
  components: {
    Memory
  }
}
</script>
