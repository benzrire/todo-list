<template>
  <section class="pt-4 pb-3 pr-3 border-bottom d-flex flex-row justify-content-between">
    <div class="custom-control custom-checkbox">
      <input
      v-model="check"
      :id="id"
      type="checkbox"
      class="custom-control-input"
      />
      <label :for="id" class="custom-control-label">
        <s v-if="check" class="text-muted">{{ text }}</s>
        <span v-else>{{ text }}</span>
      </label>
    </div>
    <span @click="deleteItem"><i class="fas fa-times"></i></span>
  </section>
</template>

<script>
  export default {
    props: {
      checked: {
        type: Boolean,
        detault() {
          return false
        }
      },
      id: {
        type: String,
        default() {
          return Date.now().toString()
        }
      },
      text: {
        type: String,
        default() {
          return ""
        }
      }
    },
    data() {
      const check = this.checked

      return {
        check
      }
    },
    methods: {
      deleteItem() {
        this.$emit("delete", this.id)
      }
    }
  }
</script>