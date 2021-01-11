<template>
  <div>
    <div class="item">
      <p>Nowe todo: {{ JSON.stringify(items) }}</p>
      <input type="text" placeholder="todo" v-model="newItem" />
      <button @click="addItem">dsa</button>
    </div>
    <div class="item" v-bind:class="{
      completed: item.completed
    }" v-for="item in items" v-bind:key="item.id">
      <h2>{{ item.title }}</h2>
      <button v-if="!item.completed" @click="removeItem(item.id)">remove</button>
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
      this.newItem = '';
    },
    removeItem(id) {
      console.log(this.items[id].id, id)
      const index = this.items.findIndex(item => item.id === id)
      this.items[index].completed = true;
    }
  },
};
</script>

<style>
.item {
  border: 1px solid #cdcdcd;
  margin: 8px;
  padding: 10px;
}

.completed {
  opacity: 0.5;
}

.completed h2 {
  text-decoration: line-through;
}
</style>
