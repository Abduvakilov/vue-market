<template>
  <div class="card cart-total" v-if="cart!==null">
    <table>
      <tr>
        <td>
          Subtotal
        </td>
        <td>
          {{round(toBePaid)}} soʻm
        </td>
      </tr>
      <tr>
        <td>
          Discount
        </td>
        <td>
          0 soʻm
        </td>
      </tr>
      <tr>
        <td>
          To be Paid
        </td>
        <td class="larger">
          {{round(toBePaid)}} soʻm
        </td>
      </tr>
    </table>
    <div class="flex">
      <a href='#' class='button'><UserIcon /></a>
      <a href='#' class='button'><SaveIcon /></a>
      <a href='#' class='button'><PrinterIcon /></a>
      <a href='#' class='button'><PercentIcon /></a>
      <button class='button success mla'>Pay</button>
    </div>
  </div>
</template>

<script>
import { UserIcon, SaveIcon, PrinterIcon, PercentIcon } from '@zhuowenli/vue-feather-icons'
import mixins from '../mixins.js'
export default {
  name: 'CartTotal',
  props: [
    'toBePaid'
  ],
  components: {
    UserIcon,
    SaveIcon,
    PrinterIcon,
    PercentIcon,
  },
  mixins: [mixins]

}
</script>

<style scoped>
.cart-total.card {
  background-color: var(--accent-strong);
  color: var(--complement-weak);
  padding: 25px;
}
table {
  width: 100%;
  margin-bottom: 30px;
}
td {
  padding-top: 10px;
}
td:last-child {
  color: white;
  text-align: right;
}

.button {
  margin-right: 5px;
}
.success {
  padding: 12px 15px;
  color: var(--complement-strong);
}
</style>