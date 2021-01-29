<template>
  <table>
    <template  v-if='Object.keys(products).length > 0'>
      <tr v-for='(product, index) in products' :key='product.productId'>
        <td>
          {{index+1}}
        </td>
        <td>
          <div class='title'>
            {{product.title}}
          </div>
          <button class='border delete' @click="removeProductFromCart(index)">
            <TrashIcon />
          </button>
          <span >
            {{round(product.price || 0)}} soʻm <!-- Hard Coded currency -->
          </span>
        </td>
        <td>
          {{round((product.price || 0) * product.quantity)}} soʻm <!-- Hard Coded currency -->
        </td>
        <td class='quantity'>
          <button @click='product.quantity = Number(product.quantity) - 1'></button>
          <input type="number" v-model='product.quantity' min=0 max=10000>
          <button @click='product.quantity = Number(product.quantity) + 1' class='plus'></button>
        </td>
      </tr>
    </template>
  </table>
</template>

<script>
import { TrashIcon } from '@zhuowenli/vue-feather-icons'
import mixins from '../mixins.js'

export default {
  name: 'CartList',
  components: {
    TrashIcon
  },
  props: [
    'products'
  ],
  data() {
    return {
      productDetails: {},
    }
  },
  methods: {
    removeProductFromCart(key) {
      this.$emit('removeProductFromCart', key)
    }
  },
  mixins: [mixins]
}
</script>

<style scoped>
table {
  width:100%;
}
td {
  padding: 30px 10px 0;
}
.title {
  max-width: 300px;
  white-space: nowrap;  
  text-overflow: ellipsis;
  overflow: hidden;
}
button.delete {
  color: var(--faint-strong-down);
  margin: 5px 10px;
}
.quantity input {
  max-width: 2em;
}

.quantity {
  border: 0;
  display: inline-flex;
}

.quantity * {
  padding: 5px 10px;
  border-color: var(--complement-weak);
  border-style: solid;
}
.quantity button {
  border-width: 1px;
  border-style: solid;
  border-radius: var(--button-border-radius) 0 0 var(--button-border-radius);
}
.quantity button.plus {
  border-radius: 0 var(--button-border-radius) var(--button-border-radius) 0;
}
.quantity button:after {
  content: '-';
}
.quantity button.plus:after {
  content: '+';
}

.quantity input[type=number] {
  border-width: 1px 0;
  border-radius: 0;
}

</style>