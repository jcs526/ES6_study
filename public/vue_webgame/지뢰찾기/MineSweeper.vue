<template>
  <div>
    <mine-form></mine-form>
    <div>{{ timer }}</div>
    <table-component></table-component>
    <div>{{ result }}</div>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import store, { INCREMENT_TIMER } from './store';
import TableComponent from './TableComponent'
import MineForm from './MIneForm'

let interval;
export default {
  store,
  components: {
    TableComponent,
    MineForm,
  },

  data() {
    return {

    };
  },
  computed: {
    ...mapState(['timer', 'result','halted']),
  },
  methods: {


  },
  watch: {
    halted(value, oldValue) {
      if (value === false) {
        interval = setInterval(() => {
          this.$store.commit(INCREMENT_TIMER);
        },1000);
      } else {
        clearInterval(interval);
      }
    }
  }

}
</script>

<style>
</style>