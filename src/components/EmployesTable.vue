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

    <!-- list -->
    <employees-list
      @edit-item="editItem"
      @removeItem="removeItem"
      :search="search"
      :employees="employees"
    />
  </v-card>
</template>

<script>
import EmployeesList from "./EmployeesList.vue";

export default {
  props: {
    employees: {
      type: [Object, Array],
      required: true,
    },
  },
  components: {
    EmployeesList,
  },
  data() {
    return {
      search: "",
    };
  },
  methods: {
    removeItem(index) {
      this.$emit("removeItem", index);
    },
    editItem(employee, index) {
      this.$emit("editItem", employee, index);
    },
  },
};
</script>
