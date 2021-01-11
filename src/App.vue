<template>
  <div>
    <input type="text" placeholder="todo" v-model="newItem" />
    <button @click="addItem">dsa</button>
    <div v-for="item in items" v-bind:key="item.id">
      <h2>{{ item.title }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      itemCounter: 0,
      items: [],
    };
  },
  methods: {
    addItem() {
      this.newItem &&
        this.items.push({
          title: this.newItem,
          completed: false,
          id: this.itemCounter,
        });
      this.newItem && this.itemCounter++;
    },
  },
};
</script>

<style>
</style>
