<template>
  <v-container justify="center" align="center">
    <searches-form v-model="search" :loading="loading"/>
    <v-card
      class="mx-auto"
      max-width="400"
      tile>
      <v-list-item v-if="searched.length" v-for="(item,k) in searched" :key="k">
        <seatches-item :item="item"/>
      </v-list-item>
    </v-card>
  </v-container>
</template>

<script>
import SearchesForm from "~/components/searches/SearchesForm";
import SeatchesItem from "~/components/searches/SeatchesItem";
//Імпортуємо данні для пошуку
import jsonItems from '../store/data.json'

export default {
  name: "PageSearch",
  components: {SeatchesItem, SearchesForm},

  data() {
    return {
      search: null,
      searched: [],
      loading: false
    }
  },

  computed: {
    items() {
      return jsonItems ? jsonItems : [];
    }
  },

  methods: {
    getSearch(val) {
      if (this.items.length) {
        this.loading = true;
        //Робимо паузу debounce
        setTimeout(() => {
          //Якко пошук не пстий то виводимо результат
          if (val !== '') {
            const needle = val.toLowerCase();
            this.searched = this.items.filter(v => v.full_name.toLowerCase().indexOf(needle) > -1)
          } else {
            this.searched = [];
          }
          this.loading = false;
        }, 2000);
      }
    }
  },

  watch: {
    //Слухаємо модель на зміни та починаємо пошук
    search(newValue, oldValue) {
      this.getSearch(newValue);
    }
  },

}
</script>

<style scoped>

</style>
