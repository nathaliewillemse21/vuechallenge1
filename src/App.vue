<template>
<h3>{{ msg }}</h3>
<!-- <input type="text" v-model="msg"> -->
  <div  class="wrapper"> 
  <div class="row" v-if="products.length">
    <div class="prodCard" v-for="product in products" :key="product.id" >
      <div class="card-header">
        <h3>{{ product.prodName }}</h3>
      </div>
      <div class="card-body">
        <img @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" :src="product.image" :alt="product.prodName" loading="lazy">
        <p :class="product.amount > 420 ? 'expensive' : 'cheap'">R{{ product.amount.toFixed(2) }}</p>
      </div>
    </div>
  </div>
  <div v-else>
<h2>Sorry, our products are out of stock.</h2>
  </div>
</div>
     
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      products:[
        {
          id: 1,
          prodName: 'Ichigo Daifuku',
          category: 'It is filled with a sweet red bean paste and a strawberry',
          amount: 60,
          image: 'https://i.postimg.cc/W1mV8yrp/ichigo-daifuku.jpg',
          
          
        },
        {
          id: 2,
          prodName: 'Sakura Mochi',
          category: 'This classic mochi is wrapped in a pickled sakura leaf',
          amount: 60,
          image: 'https://i.postimg.cc/05HyKhGL/sakura-mochi.jpg',
        },
        {
          id: 3,
          prodName: 'Kusa Mochi',
          category: 'This mochi is filled with the  sweet red bean paste and give of a hint of green tea.',
          amount: 75,
          image: 'https://i.postimg.cc/W4rk5T8F/Kusa-mochi.jpg',
          
        },
      ]
    }
  },
  computed: {
    categories() {
      return {
        msg: 'Sakura Mochi'
        //   ["Sakura Mochi", "Ichigo Daifuku", "Kusa Mochi"]
      }
    }

  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.prodCard {
  width: 18rem;
}
.prodCard :is(>*, img){
  width: 100%;
  aspect-ratio: 1/1;
}
.expensive {
  font-weight: bolder;
  color: darkkhaki;
}
.cheap {
  color: black;
}
</style>
