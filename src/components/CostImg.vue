<template>
  <div>
    {{sizes}}
    {{alert()}}
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">ТК</th>
          <th scope="col">Сумма</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item of Tks" :key="item.id">
          <th scope="row">{{item.number}}</th>
          <td>винил</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'CostImg',
  props: ["xlsx","OurTk"],
  data () {
    return {
        headers: this.xlsx[2],
        datas: [],
        Tks:[],
        sizes: this.xlsx[3],
        sqr: []
    }
  },
  methods: {
    alert: function(){
        
        var Tk = []
        var info = []
        var Sizes = this.sizes
        var Sq = []

        this.OurTk.forEach(element => {
            this.xlsx.forEach(function (item, i) {
                if(item[0] === Number(element.number)){
                    Tk.push(item)
                    info.push(element)
                }
            });   
        });

        this.datas = Tk
        this.Tks = info
        

        this.sqr = Sq

      }
  },
  computed:{
      
  },
  mounted() {
  }
}
</script>

