<template>
  <div>
    <TestCourse/>
  </div>
</template>

<script lang="ts">
import {Options, Vue} from 'vue-class-component';
import TestCourse from "@/components/TestCourse.vue";

@Options({
  components: {TestCourse},
})
export default class App extends Vue {

}

</script>

<style lang="scss">

</style>
