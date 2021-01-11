<template>
  <div>
    <div class="item">
      <p>Nowe todo: <strong> {{ newItem }} </strong></p>
      <input type="text" placeholder="todo" v-model="newItem" />
      <button @click="addItem">dsa</button>
    </div>
    <TodoItem 
        v-for="item in items" 
        :key="item.id"
        :item="item"
        @removeClicked="removeItem"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  components: {
    TodoItem,
  },
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
      this.newItem = "";
    },
    removeItem(id) {
      const index = this.items.findIndex((item) => item.id === id);
      this.items[index].completed = true;
    },
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
