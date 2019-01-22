<template>
  <div>
    <div v-for="(el, n) of datas" :key="el.id">
      <h2>Акт сдачи-приемки печатной продукции</h2>
      <h5>Заказчик: Лента</h5>
      <h5>Город: {{Tks[n].city}}</h5>
      <h5>Наименование обмотки : Дом</h5>
      <h5>Отправитель: РПК Ситиграфика</h5>
      <h5>Получатель: Лента-{{el[0]}}</h5>
      <h5>Адрес: {{Tks[n].adress}}</h5>

      <table class="table table-bordered">
        <thead>
          <tr>
            <th scope="col">Сюжет</th>
            <th scope="col">Материал</th>
            <th scope="col">Размеры</th>
            <th scope="col">Количество</th>
          </tr>
        </thead>
        <tbody>
          <tr v-if="item != null" v-for="(item, i) of headers" :key="item.id">
            <th scope="row" v-if="el[i] != null">{{item}}</th>
            <td v-if="el[i] != null">винил</td>
            <td v-if="el[i] != null">{{sizes[i]}}</td>
            <td v-if="el[i] != null">{{el[i]}}</td>
          </tr>
        </tbody>
      </table>
      <div class="container">
        <div class="row">
          <div class="col-2">Продукцию отправил</div>
          <div class="col-4"></div>
          <div class="col-2">Продукцию получил</div>
          <div class="col-4"></div>
        </div>
        <div class="row">
          <div class="col-2">Должность</div>
          <div class="col-4">___________________________</div>
          <div class="col-2">Должность</div>
          <div class="col-4">___________________________</div>
        </div>
        <div class="row">
          <div class="col-2">ФИО</div>
          <div class="col-4">___________________________</div>
          <div class="col-2">ФИО</div>
          <div class="col-4">___________________________</div>
        </div>
        <div class="row">
          <div class="col-2">Подпись</div>
          <div class="col-4">___________________________</div>
          <div class="col-2">Подпись</div>
          <div class="col-4">___________________________</div>
        </div>
        <div class="row">
          <div class="col-2">Дата</div>
          <div class="col-4">___________________________</div>
          <div class="col-2">Дата</div>
          <div class="col-4">___________________________</div>
        </div>
      </div>
      <p class="more"></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "TablesImg",
  props: ["xlsx", "OurTk"],
  data() {
    return {
      headers: this.xlsx[2],
      datas: [],
      Tks: [],
      sizes: this.xlsx[3]
    };
  },
  methods: {},
  mounted() {
    var Tk = this.datas;
    var info = this.Tks;

    this.OurTk.forEach(element => {
      this.xlsx.forEach(function(item, i) {
        if (item[0] === Number(element.number)) {
          Tk.push(item);
          info.push(element);
        }
      });
    });
    this.Tks = info;
    this.datas = Tk;
  }
};
</script>
