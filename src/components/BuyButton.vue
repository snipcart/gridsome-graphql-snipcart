<template>
    <button class="snipcart-add-item"
        :data-item-id="product.id"
        :data-item-name="product.title"
        :data-item-description="excerpt"
        :data-item-image="image.url"
        :data-item-price="product.price"
        :data-item-url="'https://snipcart-gridsome-airtable.netlify.com' + product.path">
        <slot>
            Buy for {{ product.price }}$
        </slot>
    </button>
</template>

<script>

function makeExcerpt(str, len) {
    var words = str.substr(0, len).split(' ');
    return words.slice(0, words.length - 1).join(' ') + '…';
}

export default {
    name: 'ProductPreview',
    props: ['product'],
    data() {
        return {
            excerpt: makeExcerpt(this.product.content, 125),
            image: this.product.picture.length ? {
                name: this.product.picture[0].filename,
                url: this.product.picture[0].thumbnails.large.url.src,
            } : null,
        };
    }
};
</script>

<style scoped>
button {
    background-color: #E3E3E3;
    border: 0;
    font-family: inherit;
    font-size: inherit;
    border-radius: .2em;
    padding: .4em;
}

button:hover {
    background-color: hsla(152, 65%, 80%, 1);
    cursor: pointer;
}
</style>

