<template>
  <div class="container">
      <div class="row">
          <div class="input-group mb-3 col-8">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Номер ТК</span>
            </div>
            <input type="text" class="form-control" v-model="numberTk">
          </div>
      </div>
      <div class="row">
          <div class="input-group mb-3 col-8">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Город</span>
            </div>
            <input type="text" class="form-control" v-model="cityTk">
          </div>
      </div>
      <div class="row">
          <div class="input-group mb-3 col-8">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Адрес</span>
            </div>
            <input type="text" class="form-control" v-model="adressTk">
          </div>
      </div>

      <div class="row" style="float: right; margin-right: 220px">
          <button type="button" class="btn btn-primary" @click="SaveTk()" >Сохранить</button>
      </div>

      <table class="table">
        <thead>
            <tr>
            <th scope="col">#</th>
            <th scope="col">Номер ТК</th>
            <th scope="col">Город</th>
            <th scope="col">Адрес</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, i) of OurTk" :key="item.numberTk">
            <th scope="row">{{i+1}}</th>
            <td>{{item.number}}</td>
            <td>{{item.city}}</td>
            <td>{{item.adress}}</td>
            </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'Tk',
  props: ["OurTk"],
  data () {
    return {
        numberTk: "",
        cityTk: "",
        adressTk: ""
    }
  },
  methods: {
      SaveTk: function(){
          var newTk = {}
          newTk.number = this.numberTk
          newTk.city = this.cityTk
          newTk.adress = this.adressTk
          this.OurTk.push(newTk)
          axios.post('http://localhost:8081/', newTk)
          .then(function (response) {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error);
          });
      }
  }
}
</script>

<style>

</style>
