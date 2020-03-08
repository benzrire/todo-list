<template>
  <section class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-6">
        <h1 class="display-4">Todo</h1>

        <Form @submit="onSubmit" />

        <Item
        v-for="item in items"
        :key="item.id"
        :id="item.id"
        :checked="item.checked"
        :text="item.text"
        @delete="onDelete"
        />
      </div>
    </div>
  </section>
</template>

<script>
  import Form from './Form.vue'
  import Item from './Item.vue'

  export default {
    components: {
      Form,
      Item,
    },
    data() {
      const items = [
        {
          id: Date.now().toString(),
          checked: false,
          text: "First item"
        }
      ]

      return {
        items,
      }
    },
    methods: {
      onSubmit(value) {
        this.items.push({
          id: Date.now().toString(),
          checked: false,
          text: value
        })
      },
      onDelete(value) {
        this.items.splice(this.itemsIndex(value), 1)
      },
      itemsIndex(id) {
        return this.items.findIndex((item) => {
          return item.id == id
        })
      }
    }
  }
</script>