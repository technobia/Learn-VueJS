<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ anotherMsg }}</h1>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.name }}, Quantity: {{ product.qty }}
        <button @click="addItem(product)">+</button>
        <button @click="removeItem(product)">-</button>
      </li>
    </ul>
    <div>Total Products: {{ totalProduct }}</div>
    <div>
      <input type="text" v-model="message" placeholder="Type some thing">
      Message is: {{ message }}
    </div>
    <div>
      <textarea v-model="initialTextarea"></textarea>
    </div>
    <div>
      <select v-model="selected">
        <option :key="index" v-for="(option, index) in options" v-bind:value="option.value">
          {{ option.text }}
        </option>
      </select>
      <span>Selected: {{ selected }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
    addItem: (product) => {
      product.qty += 1
    },
    removeItem: product => {
      product.qty -= 1
    }
  },
  data: () => ({
    msg: 'Hello world',
    anotherMsg: 'Another hello world',
    products: [
      { id: 1, qty: 0, name: 'Car' },
      { id: 2, qty: 2, name: 'Ship' },
      { id: 3, qty: 5, name: 'Boat' }
    ],
    message: '',
    initialTextarea: 'Initial text',
    selected: 'A',
    options: [
      { text: 'One', value: 'A' },
      { text: 'Two', value: 'B' },
      { text: 'Three', value: 'C' }
    ]
  }),
  computed: {
    totalProduct () {
      return this.products.reduce((sum, item) => {
        return sum + item.qty
      }, 0)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.hello {
  padding-bottom: 30px;
}
div {
  margin: 15px 0;
}
</style>
