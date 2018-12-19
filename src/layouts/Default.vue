<template>
  <div class="layout">
    <header class="header">
      <g-link :to="{ name: 'home' }" class="home-btn">Furniture Store</g-link>
    </header>
    <slot/>
    <footer>
      <p>Made with a few ☕️ at <a href="https://snipcart.com/">Snipcart</a></p>
      <p>
        Read our 
          <a href="">
            blog post on Gridsome and Airtable
          </a> or go see
          <a href="https://github.com/snipcart/snipcart-gridsome-airtable">
            the demo's repo
          </a>
      </p>
    </footer>
  </div>
</template>

<style>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 600px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.home-btn {
  text-decoration: none;
  color: #4cba86;
  font-size: 2.8em;
  line-height: 1em;
}

.home-btn:before {
  background-image: url('/logo.svg');
  content: "";
  width: 0.8em;
  height: 0.8em;
  display: inline-block;
  background-position: center;
  position: relative;
  top: 2px;
}

.nav__link {
  margin-left: 20px;
}

a {
  text-decoration: none;
  color: #4cba86;
}

</style>
