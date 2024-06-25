<script setup>
import { ref, provide, watch, computed } from 'vue'

import Header from './components/Header.vue'
import HomePage from './pages/Home.vue'
import Drawer from './components/Drawer.vue'

const drawerOpen = ref(false)

const closeDrawer = () => {
  drawerOpen.value = false
}

const openDrawer = () => {
  drawerOpen.value = true
}

provide('cartActions', {
  closeDrawer,
  openDrawer
})
</script>

<template>
  <Drawer v-if="drawerOpen" />

  <div class="bg-white w-3/5 m-auto rounded-xl shadow-xl shadow-grey-200 mt-20">
    <Header @open-drawer="openDrawer" />

    <HomePage />
  </div>
</template>
