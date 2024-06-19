<script setup>
import Card from './Card.vue'

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Добавить')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :isFavorite="false"
      :onClickAdd="onClickAdd"
      :isAdded="true"
    />
  </div>
</template>
