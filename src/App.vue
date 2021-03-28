<template>
  <div>
    <div v-show="completed" class="popup">
      <div class="popupBody">
        <div class="window">
        <div class="text">
          <div class="title">Готово</div>
          <div class="description">Регистрация завершена</div>
        </div>
      </div>
      <button @click="completed = false">OK</button>
      </div>
    </div>
    <div class="container">
      <div class="block">
        <div>
          <h3>Общая информация</h3>
          <hr>
        </div>
        <div class="table">
          <Form :label="'Фамилия*'" :placeholder="'Пушкин'" @value="fields.sname = $event" :error="$v.fields.sname.$error"/>
          <Form :label="'Имя*'" :placeholder="'Александр'"  @value="fields.fname = $event" :error="$v.fields.fname.$error" />
          <Form :label="'Отчество'" :placeholder="'Сергеевич'" />
          <Form :label="'Дата рождения*'" :placeholder="'26/05/1799'"  @value="fields.birth = $event" :error="$v.fields.birth.$error" />
          <Form :label="'Номер телефона*'" :placeholder="'78009000000'"  @value="fields.number = $event" :error="$v.fields.number.$error" />
          <Form :label="'Пол'" :placeholder="'Мужской'" />
          <Form :label="'Группа клиентов*'" :options="['', 'VIP', 'Проблемные', 'ОМС']"  @value="fields.group = $event" :error="$v.fields.group.$error" />
          <Form :label="'Лечащий врач'" :options="['', 'Иванов', 'Захаров', 'Чернышева']" />
        </div>

        <div>
          <h3>Адрес</h3>
          <hr>
        </div>
        <div class="table">
          <Form :label="'Индекс'" :placeholder="'101000'" />
          <Form :label="'Страна'" :placeholder="'Россия'" />
          <Form :label="'Область'" :placeholder="'Московская область'" />
          <Form :label="'Город*'" :placeholder="'Москва'" @value="fields.city = $event" :error="$v.fields.city.$error" />
          <Form :label="'Улица'" :placeholder="'Свободы'" />
          <Form :label="'Дом'" :placeholder="'21'" />
        </div>

        <div>
          <h3>Паспорт</h3>
          <hr>
        </div>
        <div class="table">
          <Form :label="'Тип документа*'" :options="['', 'Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение']" @value="fields.doc = $event" :error="$v.fields.doc.$error"/>
          <Form :label="'Серия'" :placeholder="'4515'" />
          <Form :label="'Номер'" :placeholder="'020105'" />
          <Form :label="'Кем выдан'" :placeholder="'ОТДЕЛОМ УФМС РОССИИ ПО ГОР. МОСКВЕ'" :length="2" />
          <Form :label="'Дата выдачи*'" :placeholder="'26/05/1813'" @value="fields.docDate = $event" :error="$v.fields.docDate.$error" />
        </div>

        <div class="end">
          <label><input type="checkbox" checked>Отправить СМС</label>
          <button type="buton" @click="chechFields">Создать учётную запись</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { validationMixin } from 'vuelidate'
import { required, helpers } from 'vuelidate/lib/validators'
import Vue from 'vue'
import Form from '@/components/form.vue'

export default Vue.extend({
  name: 'App',
  mixins: [validationMixin],
  components: { Form },
  data() {
    return {
      fields: {
        fname: '',
        sname: '',
        birth: '',
        number: '',
        group: '',
        city: '',
        doc: '',
        docDate: ''
      },
      completed: false
    }
  },
  methods: {
    chechFields() { 
      this.$v.fields.$touch()
      if (!this.$v.fields.$error) this.completed = true
    }
  },
  validations: {
    fields: {
      fname: {
        required
      },
      sname: {
        required
      },
      birth: {
        required
      },
      number: {
        validate(value) {
          return value ? /^7\d{10}$/gm.test(value) : false
        }
      },
      group: {
        required
      },
      city: {
        required
      },
      doc: {
        required
      },
      docDate: {
        required
      }
    }
  }
})
</script>

<style lang="sass">
@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Regular'), local('SFProDisplay-Regular'), url('assets/fonts/SFProDisplay-Regular.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Regular.woff') format('woff'), url('assets/fonts/SFProDisplay-Regular.ttf') format('truetype')
  font-weight: normal
  font-style: normal

@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Bold'), local('SFProDisplay-Bold'), url('assets/fonts/SFProDisplay-Bold.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Bold.woff') format('woff'), url('assets/fonts/SFProDisplay-Bold.ttf') format('truetype')
  font-weight: bold
  font-style: normal

@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Light'), local('SFProDisplay-Light'), url('assets/fonts/SFProDisplay-Light.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Light.woff') format('woff'), url('assets/fonts/SFProDisplay-Light.ttf') format('truetype')
  font-weight: 200
  font-style: normal

@media screen and (max-width: 990px)
  .table
    grid-template-columns: repeat(2, 1fr) !important

  .table>.group[style]
    grid-column-end: span 1 !important

@media screen and (max-width: 510px)
  .table
    grid-template-columns: repeat(1, 1fr) !important
    grid-row-gap: unset !important

  .table>.group[style]
    grid-column-end: span 1 !important

body
  font-family: SF Pro Display, Regular !important
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  margin: 0

.container
  display: flex
  justify-content: center
  align-items: center

.block
  justify-content: center
  display: flex
  flex-direction: column

h3
  margin-top: 40px
  margin-block-end: 0

.table
  display: grid
  grid-template-columns: repeat(3, 1fr)
  grid-template-rows: auto
  grid-gap: 10px

.end
  margin-block: 20px
  display: flex
  flex-direction: column
  align-items: center
  height: 70px
  justify-content: space-around

  >label
    font-size: 12px

    >input
      vertical-align: sub

  >button
    display: flex;
    padding: 10px 20px
    background-color: black
    color: white
    border: none
    border-radius: 36px
    cursor: pointer

    &:hover
      opacity: .8
      transition: opacity 200ms linear

    &:focus
      outline: none

.popup
  position: fixed
  z-index: 1
  width: 100%
  height: 100%
  display: flex
  justify-content: center
  align-items: center
  background-color: rgba(0, 0, 0, .4)

.popupBody
  display: flex
  flex-direction: column

  >button
    border: 0
    padding: 0
    cursor: pointer
    font-size: inherit
    background-color: white
    border-radius: 0 0 14px 14px
    height: 30px
    margin-top: 1px
    font-size: 14px

    &:focus
      outline: none

.window
  display: flex
  flex-direction: column
  background-color: white
  border-radius: 14px 14px 0 0
  min-width: 200px

  >.text
    text-align: center
    padding: 20px;
    max-width: 200px

    >.title
      font-weight: bold

    >.description
      font-size: 14px
      overflow: hidden
      text-overflow: ellipsis
</style>
