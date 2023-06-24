<template>
  <v-card class="mx-9">
    <v-card-title class="mb-3">
      <h3 class="mb-3 font-weight-medium">Сотрудники</h3>
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>

    <!-- table -->
    <v-data-table
      v-model:items-per-page="itemsPerPage"
      :headers="headers"
      :items="employees"
      :search="search"
      item-value="name"
      class="elevation-1"
    >
      <template v-slot:item="{ item }">
        <!-- <v-btn @click="log(item.columns.name)"> -->
        <tr>
          <td>{{ item.columns.name }}</td>
          <td>{{ item.columns.surname }}</td>
          <td>{{ item.columns.middleName }}</td>
          <td>{{ item.columns.job }}</td>
        </tr>
        <!-- </v-btn> -->
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
import { VDataTable } from "vuetify/labs/VDataTable";

export default {
  methods: {
    log(name) {
      console.log(name);
    },
  },
  data() {
    return {
      search: "",
      sortBy: [{ key: "name", order: "asc" }],
      itemsPerPage: 5,
      headers: [
        { title: "Фамилия", align: "start", key: "surname" },
        { title: "Имя", align: "start", key: "name" },
        { title: "Отчество", align: "start", key: "middleName" },
        { title: "Должность", align: "start", key: "job" },
      ],
      employees: [
        {
          name: "Константин",
          surname: "Семенов",
          middleName: "Семеныч",
          job: "Разработчик",
          book: false,
          salary: 50000,
          enterDate: "11/22/33",
          pay: "Полная",
        },
        {
          name: "Пашок",
          surname: "Богданов",
          middleName: "Латибыч",
          job: "Доставщик",
          book: false,
          salary: 70000,
          enterDate: "11/22/33",
          pay: "Полная",
        },
        {
          name: "Денис",
          surname: "Генадьев",
          middleName: "Разивыч",
          job: "Пекарь",
          book: false,
          salary: 20000,
          enterDate: "11/22/33",
          pay: "Полная",
        },
      ],
    };
  },
};
</script>
