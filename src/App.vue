
<template>
  <div id="app">
    <Accordion :products='products'  />
  </div>
</template>

<script>
import products from './data'
console.log(products);
import Accordion from './components/Accordion'

export default {
  name: 'App',
  components: {
    Accordion
  },
 data: function () {
    return {
      products
    }
  }
}
</script> 

<style>
:root{
    --mainText:black;
    --secondaryText:#4b5156;
}

h1, h2, h3, h4, h5, h6, strong {
    color: var(--mainText);
    font-family: 'Russo One', sans-serif;
    font-weight: 500;
    margin: 0;
    padding: 5px;
}

h1 { font-size: 56px;}
h2 { font-size: 36px;}
h3 { font-size: 28px;}
h4 { font-size: 24px;}
h5 { font-size: 20px;}
h6 { font-size: 16px;}

a, p, li, span, label, input, textarea {
    color: var(--secondaryText);
    font-family: 'Roboto Mono', monospace;
}

html, body {
    padding: 0;
    margin: 0;
}

body *{
    transition: 0.3s;
}

#app {
  text-align: center;
  min-height: 600px;
}

h1, h2, h3, h4, h5, h6, strong {
    color: var(--mainText);
    font-family: 'Russo One', sans-serif;
    font-weight: 500;
}

a, p, li, span, label, input, textarea {
    color: var(--secondaryText);
    font-family: 'Roboto Mono', monospace;
}


ul{
    list-style: none;
}

</style>
