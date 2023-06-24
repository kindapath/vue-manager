<template>
  <!-- list -->
  <v-data-table
    v-model:items-per-page="itemsPerPage"
    :headers="headers"
    :items="employees"
    :search="search"
    item-value="name"
    class="elevation-1"
  >
    <template v-slot:item="{ item }">
      <tr>
        <td class="w-25">{{ item.columns.name }}</td>
        <td class="w-25">{{ item.columns.surname }}</td>
        <td class="w-25">{{ item.columns.middleName }}</td>
        <td class="w-25">{{ item.columns.job }}</td>
        <td class="d-flex justify-end">
          <v-btn flat icon="mdi-pencil"></v-btn>
          <v-btn @click="removeItem(item.index)" flat icon="mdi-close"></v-btn>
          <v-btn
            router
            :to="'/employee/' + item.index"
            flat
            icon="mdi-page-next-outline"
          ></v-btn>
        </td>
      </tr>
    </template>
  </v-data-table>
</template>

<script>
import { VDataTable } from "vuetify/labs/VDataTable";

export default {
  props: {
    search: {},
    employees: {
      type: [Object, Array],
      required: true,
    },
  },
  methods: {
    removeItem(index) {
      this.$emit("removeItem", index);
    },
  },
  data() {
    return {
      sortBy: [{ key: "name", order: "asc" }],
      itemsPerPage: 5,
      headers: [
        { title: "Фамилия", align: "start", key: "surname" },
        { title: "Имя", align: "start", key: "name" },
        { title: "Отчество", align: "start", key: "middleName" },
        { title: "Должность", align: "start", key: "job" },
        { title: "Действия", align: "start", key: "action" },
      ],
    };
  },
};
</script>
