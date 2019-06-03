<template>
  <div class='ui basic content center aligned segment'>
   
    <div class='ui centered card' >
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='ui button attached buttons'>
            <button class='ui primary positive button' v-on:click="sendForm()">
              Create
            </button>
           
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0) {
        const title = this.titleText;
        this.$emit('create-todo', {
          title,
          done: false,
        });
        this.titleText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>
<style>
.card {background-color: #66369D}
</style>
