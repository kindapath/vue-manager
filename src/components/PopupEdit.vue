<template>
  <popup @edit-item="editItem" :edit="true">
    <template v-slot:btn-icon>
      <v-icon icon="mdi-pencil"></v-icon>
    </template>
  </popup>
</template>

<script>
import Popup from "./Popup.vue";

export default {
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
