<template>
  <div class="table">
    <div class="group">
      <label class="control-label" for="nome">Имя*</label>
      <input name="nome" class="form" placeholder="Константин" type="text">
    </div>
    <div class="group">
      <label class="control-label" for="nome">Фамилия*</label>
      <input name="nome" class="form" placeholder="Циолковский" type="text">
    </div>
    <div class="group">
      <label class="control-label" for="nome">Отчество</label>
      <input name="nome" class="form" placeholder="Эдуардович" type="text">
    </div>
    <div class="group">
      <label class="control-label" for="nome">Дата рождения*</label>
      <input name="nome" class="form" placeholder="17/09/1857" type="text">
    </div>
    <div class="group">
      <label class="control-label" for="nome">Номер телефона*</label>
      <input name="nome" class="form" placeholder="78009003541" type="text">
    </div>
    <div class="group">
      <label class="control-label" for="nome">Пол</label>
      <input name="nome" class="form" placeholder="Мужской" type="text">
    </div>
    <div class="group" style="grid-area: 3 / 1 / 4 / 4">
      <label class="control-label" for="nome">Поле</label>
      <input name="nome" class="form" placeholder="Поле" type="text">
    </div>
  </div>
</template>

<style scoped lang="sass">
@media screen and (max-width: 990px)
  .table
    grid-template-columns: repeat(2, 1fr) !important

@media screen and (max-width: 510px)
  .table
    grid-template-columns: repeat(1, 1fr) !important
    grid-row-gap: unset !important

.group
  display: flex
  flex-direction: column

label
  font-weight: 200
  font-size: 14px
  margin: 14px 0 3px 0
  display: inline-block

.form
  display: block
  height: 14px
  padding: 6px 12px
  font-size: 14px
  line-height: 1.42857143
  color: #555
  border: 1px solid #D3D3D3
  border-radius: 6px

.table
  display: grid
  grid-template-columns: repeat(3, 1fr)
  grid-template-rows: repeat(5, 1fr)
  grid-gap: 10px
</style>