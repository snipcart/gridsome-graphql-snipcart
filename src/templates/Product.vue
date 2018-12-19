<template>
  <Layout>
      <section class="main">
        <aside>
            <figure>
                <img :src="$page.product.picture[selected].thumbnails.large.url.src"
                    alt="Product Image" class="img-main" />
            </figure>
            <p>
                <img v-for="(img, index) in $page.product.picture"
                    :key="img.thumbnails.large.url.src"
                    @click="select(index)"
                    :src="img.thumbnails.large.url.src"
                    class="img-preview"
                    :class="{active: index == selected}" />
            </p>
        </aside>
        <h1>{{$page.product.title}}</h1>
        <buy-button :product="$page.product" />
        <p>{{$page.product.content}}</p>
      </section>
  </Layout>
</template>

<style scoped>

aside {
    width: 20em;
    float: left;
    margin-right: 1em;
}

figure, .img-main {
    display: block;
    width: 100%;
    margin: 0;
}

figure {
    height: 20em;
    display: flex;
    align-items: center;
    justify-content: center;
}

.img-preview {
    width: 4em;
    box-sizing: border-box;
    border: 2px solid black;
    margin: .5em;
}

.img-preview.active {
    border: 2px solid hsla(152, 65%, 80%, 1);
}

</style>



<script>
import BuyButton from '../components/BuyButton';
import { debug } from 'util';

export default {
    components: {
        BuyButton,
    },
    data() {
        return {
            selected: 0,
        };
    },
    metaInfo () {
        return {
            title: this.$page.product.title,
        };
    },
    methods: {
        select(index) {
            this.selected = index;
        } 
    }
}
</script>

<page-query>
query Product ($path: String!) {
  product(path: $path) {
    id,
    title,
    path,
    price,
    content,
    picture {
      thumbnails {
         large{
          url
        }
      }
    }
  }
}
</page-query>