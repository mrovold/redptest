<template>
  <div class="about__wrapper">
    <!-- <div>
      <b-table striped hover :items="items"></b-table>
    </div> -->

    <div>
      <b-form inline>
        <label class="sr-only" for="inline-form-input-name">Имя</label>
        <b-form-input
          id="inline-form-input-name"
          class="mb-2 mr-sm-2 mb-sm-0"
          placeholder="Jane Doe"
        ></b-form-input>

        <label class="sr-only" for="inline-form-input-username">Фамилия</label>
        <b-input-group class="mb-2 mr-sm-2 mb-sm-0">
          <b-form-input id="inline-form-input-username" placeholder="Пользователь"></b-form-input>
        </b-input-group>

        <div>
          <label for="example-datepicker">Дата рождения</label>
          <b-form-datepicker id="example-datepicker" v-model="birth" class="mb-2"></b-form-datepicker>
        </div>
        
        <div>
          <b-form-select v-model="selected" :options="options" size="lg" class="mb-3"></b-form-select>
        </div>


        <b-button variant="primary">Сохранить</b-button>
      </b-form>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        selected: null,
        options: [
          { value: null, text: 'Выберите город' },
          { value: 'a', text: 'Оренбург' },
          { value: 'b', text: 'Москва' },
          { value: 'c', text: 'Санкт-Петербург' },
          { value: 'd', text: 'Екатеринбург' },
          { value: 'e', text: 'Нижний Новгород' },
          { value: 'f', text: 'Самара' }
        ],
        birth: '',
        items: [
          { age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
          { age: 21, first_name: 'Larsen', last_name: 'Shaw' },
          { age: 89, first_name: 'Geneva', last_name: 'Wilson' },
          { age: 38, first_name: 'Jami', last_name: 'Carney' }
        ]
      }
    }
  }
</script>