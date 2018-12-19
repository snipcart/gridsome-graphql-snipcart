<template>
  <Layout>
    <section class="products">
      <g-link
        v-for="edge in $page.allProduct.edges" :key="edge.node.id"
       :to="edge.node.path" class="product">
        <ProductPreview :product="edge.node" />
      </g-link>
    </section>
    <Pager :info="$page.allProduct.pageInfo" class="product-navigation" />
  </Layout>
</template>

<style>
.product-navigation {
  display: flex;
  justify-content: center;
}

.product-navigation a {
  box-sizing: border-box;
  width: 2em;
  background-color: #E3E3E3;
  color: black;
  font-weight: bold;
  margin: .5em;
  text-align: center;
  text-decoration: none;
  border-radius: .2em;
}

.product-navigation a.active {
  font-weight: normal;
  background-color: hsla(152, 65%, 80%, 1);;
}

.products {
  display: flex;
  flex-wrap: wrap;
}

.products figure, .products img {
  width: 100%;
  margin: 0;
}

.products a {
  color: inherit;
}

.products .product {
  display: block;
  width: 10em;
  margin: 1em;
}

</style>


<script>
import { Pager } from 'gridsome'
import ProductPreview from '../components/ProductPreview'

export default {
  components: {
    Pager,
    ProductPreview,
  },
};
</script>

<page-query>
query Products($page: Int) {
  allProduct (perPage: 3, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node{
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
  }
}
</page-query>