<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item" v-for="item in items" :key="item.id">
        {{item.title}} -${{item.price}}
        <button
          @click="$emit('remove-from-cart', item)"
          class="btn badge badge-danger float-right"
        >Remove from cart</button>
      </li>
    </ul>
    <div class="p-3 my-5">
      <h4 class="text-center text-info">Total ${{total}}</h4>
    </div>
    <button
      :disabled="items.length === 0"
      class="btn btn-dark form-control"
      @click="$emit('pay')"
    >Pay Now</button>
  </div>
</template>

<script>
export default {
  props: ["items"],
  computed: {
    total() {
      return this.items.reduce((acc, item) => acc + Number(item.price), 0);
    }
  }
};
</script>

<style>
</style>