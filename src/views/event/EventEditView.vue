<template>
  <p>Edit the event here</p>
  <button @click="edit">Save Edit</button>
</template>

<script>
export default {
  props: ['id', 'event'],
  inject: ['GStore'],
  methods: {
    edit() {
      //Assuming successful API call to register them

      //Set a flash message to appear on the next page loaded which says
      //'You are successfully registered for' + this.event.title

      this.GStore.flashMessage = this.event.title + 'has been edited.'
      setTimeout(() => {
        //After 3 seconds remove it
        this.GStore.flashMessage = ''
      }, 3000)

      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id }
      })
    }
  }
}
</script>
