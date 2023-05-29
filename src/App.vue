<script setup>
import TopUsers from './components/TopUsers.vue'
</script>

<template>
  <main>
    <h1>HERO</h1>
    <Suspense>
      <template #default>
        <TopUsers />
      </template>
      <template #fallback>
        <div>
          <p>Loading...</p>
        </div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped></style>
