<template>
  <div class="about__wrapper">
    <div>
      <b-table striped hover :items="items"></b-table>
    </div>
    
    <div>
        <b-button v-b-modal.modal-1 variant="outline-primary">Добавить обращение</b-button>

        <b-modal id="modal-1" title="Новое обращение" :footer-bg-variant="footerBgVariant">
            <div>
                <b-form @submit="onSubmit" @reset="onReset">
                    <b-form-group
                        id="input-group-1"
                        label="Заголовок"
                        label-for="input-1"
                    >
                        <b-form-input
                        id="input-1"
                        v-model="form.email"
                        required
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-2" label="Описание" label-for="input-2">
                        <b-form-input
                        id="input-2"
                        v-model="form.name"
                        required
                        ></b-form-input>
                    </b-form-group>

                    <b-button type="submit" variant="primary">Отправить</b-button>
                    <b-button type="reset" variant="danger">Сбросить</b-button>
                    
                </b-form>
            </div>
            <template #modal-footer>
                <div class="w-100">
                </div>
            </template>
        </b-modal>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
          form: {
          email: '',
          name: '',},
        items: [
          { 'Заголовок': 'Обращение 1', 'Описание': 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', 'id': '001' },
          { 'Заголовок': 'Обращение 2', 'Описание': 'Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', 'id': '002' },
          { 'Заголовок': 'Обращение 3', 'Описание': 'Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.', 'id': '003' },
          { 'Заголовок': 'Обращение 4', 'Описание': 'Placerat orci nulla pellentesque dignissim.', 'id': '004' }
        ]
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        this.items.push({ 'Заголовок': `${this.form.email}`, 'Описание': `${this.form.name}`, 'id': `${Math.floor(Math.random() * (1000 - 100) + 100)}` })
      },
      onReset(event) {
        event.preventDefault()
        // Сбросить значения нашей формы
        this.form.email = ''
        this.form.name = ''
        // Уловка для сброса/очистки состояния проверки формы в собственном браузере
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>