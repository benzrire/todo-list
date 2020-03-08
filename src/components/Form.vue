<template>
  <section>
    <form @submit.prevent="submit" class="d-flex flex-row">
      <input
      v-model="text"
      type="text"
      class="form-control"
      placeholder="what needs to be done?"
      />
      <button type="submit" class="btn btn-primary ml-1 px-4">Add</button>
    </form>
  </section>
</template>

<script>
  export default {
    data() {
      const text = ""

      return {
        text
      }
    },
    methods: {
      submit() {
        this.$emit("submit", this.text)
        this.text = ""
      }
    }
  }
</script>