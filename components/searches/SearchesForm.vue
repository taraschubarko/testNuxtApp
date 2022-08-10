<template>
<v-form class="search-form">
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-text-field label="Введіть імя" v-model="full_name" @input="$emit('input', $event)" :loading="loading"/>
      </v-col>
    </v-row>
  </v-container>
</v-form>
</template>

<script>
export default {
  name: "SearchesForm",
  props: {
    loading: {
      type: Boolean,
      default: false
    },
  },
  data() {
    return {
      full_name: null,
    }
  },
}
</script>

<style lang="scss" scoped>
.search-form{
  min-width: 400px;
}
</style>
