<template>
  {{ this.getEmps() }}
  <h1>Информация о сотруднике</h1>
  <h2>{{ employee.name }} {{ employee.surname }} {{ employee.middleName }}</h2>
  <h3>Должность: {{ employee.job }}</h3>
  <p>Трудовая книжка: {{ employee.book ? "есть" : "нет" }}</p>
  <p>Оклад: {{ employee.salary }}</p>
  <p>Дата выхода на работу: {{ employee.enterDate }}</p>
  <p>Ставка: {{ employee.pay }}</p>
</template>

<script>
import { toRaw } from "vue";

export default {
  // mounted() {
  //   this.getEmps();
  // },
  methods: {
    getEmps() {
      const data = localStorage.getItem("employees");
      data ? (this.employees = toRaw(JSON.parse(data))) : null;
    },
  },
  data() {
    return {
      data: null,
      employees: [],
    };
  },
  computed: {
    employeeId() {
      return parseInt(this.$route.params.id);
    },
    employee() {
      return toRaw(this.employees).find(
        (el, index) => index === this.employeeId
      );
    },
  },
};
</script>
