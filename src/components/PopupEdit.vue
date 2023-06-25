<template>
  <popup :employees="employees" @edit-item="editItem" :edit="true">
    <template v-slot:btn-icon>
      <v-icon icon="mdi-pencil"></v-icon>
    </template>
  </popup>
</template>

<script>
import Popup from "./Popup.vue";

export default {
  props: {
    employees: {
      type: [Object, Array],
      required: true,
    },
  },
  methods: {
    editItem(employee, index) {
      this.$emit("editItem", employee, index);
    },
  },
  components: {
    Popup,
  },
};
</script>
