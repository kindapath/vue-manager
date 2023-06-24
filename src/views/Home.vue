<template>
  <div class="home bg-pink-darken-4 h-100">
    <h1 class="text-h4 font-weight-light ml-9 mb-3">
      Поиск информации о сотрудниках
    </h1>

    <employes-table @removeItem="removeItem" :employees="employees" />

    <v-container class="mt-6">
      <popup @addItem="addItem" :employees="employees" />
    </v-container>
  </div>
</template>

<script>
export default {
  components: {
    Popup,
    EmployesTable,
  },
  async mounted() {
    const data = await localStorage.getItem("employees");
    data ? (this.employees = JSON.parse(data)) : null;
  },
  methods: {
    addItem(employee) {
      if (employee != "") {
        this.employees.push(employee);

        localStorage.setItem("employees", JSON.stringify(this.employees));
      }
      employee = "";
    },
    removeItem(index) {
      this.employees.splice(index, 1);
      localStorage.setItem("employees", JSON.stringify(this.employees));
    },
  },
  data() {
    return {
      employees: [],
    };
  },
};

import Popup from "@/components/Popup.vue";
import EmployesTable from "@/components/EmployesTable.vue";
</script>
