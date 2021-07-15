<template>
  <div class="center grid">
    <FiltersResult></FiltersResult>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import FiltersResult from "@/components/FiltersResult.vue";
@Component({
  components: {
    FiltersResult,
  },
})
export default class Home extends Vue {}
</script>
