<template>
  <div class="group" :style="{gridColumnEnd: length ? 'span ' + length : ''}">
    <div class="title">
      <label>{{ label }}</label>
      <label v-if="error" class="error--text">Ошибка</label>
    </div>

    <select v-if="options" 
      @change="rt" 
      v-model="value"
      :class="error ? 'error' : ''"
    >
      <option v-for="option of options" :key="option">
        {{ option }}
      </option>
    </select>

    <input v-else
      @input="rt"
      v-model="value"
      :placeholder="placeholder"
      :class="error ? 'error' : ''"
      type="text"
    >
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
    },
    error: {
      type: Boolean
    }
  },
  data() { return { value: '' } },
  methods: {
    rt() {
      this.$emit('value', this.value)
    }
  }
})
</script>

<style scoped lang="sass">
.group
  display: flex
  flex-direction: column

.title
  font-weight: 200
  font-size: 14px
  margin: 14px 0 3px 0
  display: inline-flex
  justify-content: space-between

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

.error
  border: 1px solid red

.error--text
  color: red
</style>