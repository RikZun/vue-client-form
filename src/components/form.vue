<template>
  <div class="group" :style="{gridColumnEnd: length ? 'span ' + length : ''}">
    <label>{{ label }}</label>

    <select v-if="options">
      <option v-for="option of options" :key="option">
        {{ option }}
      </option>
    </select>

    <input v-else :placeholder="placeholder" type="text">
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    label: {
      required: true
    },
    placeholder: {},
    length: {
      type: Number
    },
    options: {
      type: Array
    }
  },
  data() { return { val: '' } },
})
</script>

<style scoped lang="sass">
.group
  display: flex
  flex-direction: column

label
  font-weight: 200
  font-size: 14px
  margin: 14px 0 3px 0
  display: inline-block

%input-block
  font-size: 14px
  border: 1px solid #D3D3D3
  border-radius: 6px

input
  display: block
  height: 14px
  padding: 6px 12px
  @extend %input-block

  &::placeholder
     color: #cecece

select
  @extend %input-block
  height: 28px
  padding-inline: 8px

</style>