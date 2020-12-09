<template>
  <div>
    <h1 class="h1 text-center">Добавить новый товар</h1>
    
    <form @submit.prevent="onSave()">
      <div class="form-group">
        <label class="mr-sm-2" for="product">Тип товара</label>
        <select class="custom-select mr-sm-2" id="product" v-model="choose" required>
          <option value="null">Choose...</option>
          <option value="MB">Материнская плата</option>
          <option value="CPU">Процессор</option>
        </select>
      </div>
      <div class="form-group">
        <label for="name">Имя</label>
        <input type="text" class="form-control border border-info" id="name" v-model="name" placeholder="Name..." required>
      </div>
      <div class="form-group">
        <label for="textarea">Описание</label>
        <textarea class="form-control text-warning" name="textarea" id="textarea" rows="10" placeholder="Text..." v-model="note" required>


        </textarea>
      </div>
      <div class="form-group">
        <label for="article">Артикл</label>
        <input type="number" class="form-control font-weight-bold" id="article" v-model="article" placeholder="12345..." required>
      </div>
      <button type="submit" class="btn btn-success">Добавить</button>
    </form>

    <div class="row">
      <div class="col-sm-6"><a href="http://localhost:3456/CPU" class="h2 d-block" target="_blank">Исходный список товаров процессоров</a></div>
      <div class="col-sm-6"><a href="http://localhost:3456/MB" class="h2 d-block" target="_blank">Исходный список товаров Мат. плат</a></div>
    </div>

    <footer class="mt-4 border-top border-left border-right rounded-lg p-2">
      Макаров Леонид Сергеевич, 181-362, 9 декабря 2020 <br>
      <div class="d-flex bd-highlight text-center">
        <a class="p-2 flex-fill bd-highlight" href="https://bootstrap-4.ru/docs/4.5/components/forms/  ">бутстрап</a>
        <a class="p-2 flex-fill bd-highlight" href="https://fcenter.ru/product/type/2">Товары</a>
        <a class="p-2 flex-fill bd-highlight" href="https://www.npmjs.com/package/axios">аксиос</a>
      </div>
    </footer>
  </div>
</template>

<script>
import axios from "axios";
  export default {
    data() {
      return {
        name: '',
        note: '',
        article: '',
        choose: null
      }
    },
    methods: {
      onSave() {
        let newNote = {
          name: this.name,
          attr: this.note,
          article: this.article
        }
        axios.post('http://localhost:3456/' + this.choose, newNote)
        .then(() => {
          alert('Товар добавлен')
        })
      }
    },
  }
</script>

<style scoped>


@media screen and (max-width: 400px) {
  footer {
    display: none;
  }
}

@media screen and (max-width: 200px) {
  h1, h2, h3, h4, h5, h6 {
    font-size: 12px !important;
  }
  .h1, .h2, .h3, .h4, .h5, .h6 {
    font-size: 12px !important;
  }
}
</style>