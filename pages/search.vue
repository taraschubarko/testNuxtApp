<template>
  <v-row justify="center" align="center">
    <searches-form v-model="search"/>
  </v-row>
</template>

<script>
import SearchesForm from "~/components/searches/SearchesForm";
export default {
  name: "PageSearch",
  components: {SearchesForm},

  data() {
    return {
      search: null,
      items: [],
      loading: false
    }
  },
}
</script>

<style scoped>

</style>
