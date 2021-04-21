<template>
<div class="wrapper">
  <div class="accordion-wrapper left-column ">
     <div v-for="(product, index) in products" :key="index">
          <div v-on:click="toggleAccordion(product)" class="product"><h4>{{ product.product }}</h4></div>
          <div v-show="isOpen.includes(product)" v-for="country in product.country" :key="country.name">
             <div class="product__country" v-on:click="toggleAccordion(product.product + country.name)"><h6>{{ country.name }}</h6></div>
             <div v-show="isOpen.includes(product.product + country.name)">
               <div v-for="sort in country.sort" :key="sort">
                 <p class="product__sort" v-on:click="chooseProduct( product.product, country.name, sort)">{{ sort }}</p>
               </div>
             </div>
          </div>
     </div>
  </div>
  <div class="right-column">
      <p id="activeProduct">{{activeProduct}}</p>
  </div>
</div>
</template>

<script>
export default {
  name: 'Accordion',
  props: {
    products: Array
  },
   data: function () {
    return {
      activeProduct: "Ви ще не обрали товар",
      isOpen: []
    }
  },
  methods: {
      chooseProduct: function(product, country, sort) {
          this.activeProduct = `Обраний продукт: ${product}. Країна походження: ${country}. Сорт продукту: ${sort}`;
          let sorts = document.querySelectorAll('.isActive');
          sorts.forEach(sort => sort.classList.remove('isActive'));
           event.target.classList.add('isActive');
      },
      toggleAccordion(index) {
      if (this.isOpen.includes(index)) {
        this.isOpen = this.isOpen.filter(i => i !== index);
        return;
      }

      this.isOpen.push(index);
    }
  }
}
</script>

<style scoped>

  p {
      margin: 0;
      padding: 10px;
  }

  ul {
      margin: 0;
      padding: 0;
  }

  .wrapper {
      max-width: 900px; 
      margin:  100px auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: 
      'left-column right-column'
    ;
  }

  .accordion-wrapper {
    background-color: #eee;
    border-radius: 5px;
    text-align: center;

    -webkit-box-shadow: 8px 4px 8px 0px rgba(34, 60, 80, 0.2);
    -moz-box-shadow: 8px 4px 8px 0px rgba(34, 60, 80, 0.2);
    box-shadow: 8px 4px 8px 0px rgba(34, 60, 80, 0.2);
  }

  .product {
      color: black;
      text-align: center;
      border-bottom:1px solid black;
      font-size: 24px;
      cursor: pointer;
      margin: 0;
      padding: 10px;
  }

  .product:hover {
      background-color: #ccc;
  }

  .product__country {
    cursor: pointer;
    margin: 0;
    padding: 10px;
  }

   .product__country:hover {
      background-color: #ccc;
  }

  .product__sort {
      cursor: pointer;
  }

  .product__sort:hover {
      background-color: #ccc;
  }

  .right-column {
    text-align: center;  
    margin: auto;
  }

  .isActive {
      background: yellow;
  }

  .isActive:hover {
      background: rgb(255, 208, 0) !important;
  }
</style>