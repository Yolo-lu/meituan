<template>
  <div>
 
      <div class="wrap">
        <navHead></navHead>
        <navsearch></navsearch>
      </div>
    <nuxt />
    <div class="wrap">
      <navbottom></navbottom>
    </div>
  </div>
</template>

<script>
import navHead from "../components/head/index";
import navsearch from "../components/search/index";
import navbottom from "../components/bottom/index"
export default {
  data() {
    return {};
  },
  components: {
    navHead,
    navsearch,
    navbottom
  },
  methods: {},

  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
@media screen and (max-width: 1200px){
  .wrap{
    width: 940px !important;
    margin: auto !important;
  }
}
</style>