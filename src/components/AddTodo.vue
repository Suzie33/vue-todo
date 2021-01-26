<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button class="create" type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: '',
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    },
  },
};
</script>

<style scoped>
  form {
    display: flex;
    justify-content: center;
    margin-bottom: 15px;
  }

  input {
    width: 40%;
    margin-right: 20px;
  }
</style>
