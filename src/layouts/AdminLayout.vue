<template>
  <div class="app-layout">
    <Sidebar v-if="!$route.meta.hideLayout"/>
    <div class="content">
      <Topbar v-if="!$route.meta.hideLayout"/>
      <main class="page">
        <slot />
      </main>
    </div>
  </div>
</template>

<script>
import Sidebar from '../components/Sidebar.vue'
import Topbar from '../components/Topbar.vue'

export default { components: { Sidebar, Topbar } }
</script>
