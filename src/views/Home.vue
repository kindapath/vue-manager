<template>
  <div class="home bg-pink-darken-4 h-100">
    <h1 class="text-h4 font-weight-light ml-9 mb-3">
      Поиск информации о сотрудниках
    </h1>
    <Table />
    <v-container class="mt-6">
      <Popup />
    </v-container>
  </div>
</template>

<script setup>
import Popup from "@/components/Popup.vue";
import Table from "@/components/Table.vue";
</script>
