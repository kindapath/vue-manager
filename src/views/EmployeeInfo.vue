<template>
  <div class="d-flex flex-column pa-10 h-100">
    {{ this.getEmps() }}
    <h1 class="mb-3">Информация о сотруднике</h1>
    <h2 class="mb-3">
      {{ employee.name }} {{ employee.surname }} {{ employee.middleName }}
    </h2>
    <p class="mb-3"><strong>Должность:</strong> {{ employee.job }}</p>
    <p class="mb-3">
      <strong>Трудовая книжка:</strong> {{ employee.book ? "есть" : "нет" }}
    </p>
    <p class="mb-3"><strong>Оклад:</strong> {{ employee.salary }}</p>
    <p class="mb-3">
      <strong>Дата выхода на работу:</strong> {{ employee.enterDate }}
    </p>
    <p class="mb-3"><strong>Ставка:</strong> {{ employee.pay }}</p>
  </div>
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
