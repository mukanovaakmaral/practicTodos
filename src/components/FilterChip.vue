<template>
  <div
      @click="$emit('onClick',chip.id)"
      :class="{active:chip.selected}"
      class="chip"><span v-if="prefix">x</span>{{ chip.value }} <span v-if="suffix">y</span></div>
</template>

<script>
export default {
  name: "FilterChip",
  props: {
    chip: {
      type: Object,
      required: true
    },
    prefix: {
      type: Boolean,
      required: false,
      default: false
    },
    suffix: {
      type: Boolean,
      required: false,
      default: false
    }
  }
}
</script>

<style scoped>
.chip {
  width: fit-content;
  padding: .5rem 1rem;
  background: #dcdcdc;
  color: #000;
  font-weight: 600;
  font-size: 14px;
  border-radius: 8px;
  cursor: pointer;
}

.active {
  background: #51a551;
}
</style>
