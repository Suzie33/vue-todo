<template>
  <li>
    <span :class="{done: todo.completed}">
      <input
       type="checkbox"
       v-model="todo.completed">
      <strong>{{ index + 1 }}.</strong>
      {{ todo.title | uppercase }}
    </span>
    <button
     class="btn-remove"
      @click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    },
  },
};
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  .btn-remove {
    background: red;
    color: #fff;
    border-radius: 50%;
    font-weight: 700;
  }

  .btn-remove:hover {
    cursor: pointer;
    opacity: .8;
  }

  input {
    margin-right: 1rem;
  }

  .done {
    text-decoration: line-through;
  }
</style>
