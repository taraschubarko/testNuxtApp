<template>
  <v-list-item-content>
    <v-list-item-title>{{item.full_name}}</v-list-item-title>
    <v-list-item-subtitle>{{item.address.street}}, {{item.address.city}}</v-list-item-subtitle>
  </v-list-item-content>
</template>

<script>
export default {
  name: "SeatchesItem",

  props: {
    item: {
      type: Object,
      default: () => {
      },
    },
  },
}
</script>

<style scoped>

</style>
