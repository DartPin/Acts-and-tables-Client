<template>
  <div id="app">
    <Header :componentName="componentName" @newName="componentName = $event"></Header>
    <component :xlsx="xlsx" :OurTk="OurTk" v-bind:is="currentNameComponent"> </component>
    
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Tk from "./components/Tk.vue";
import CostImg from "./components/CostImg.vue";
import TablesImg from "./components/TablesImg.vue";

export default {
  name: "app",
  data() {
    return {
      OurTk: [],
      componentName: "Tk",
      xlsx: null
    };
  },
  components: {
    Header,
    Tk,
    TablesImg,
    CostImg
  },
  mounted() {
    axios
      .get("http://localhost:8081/")
      .then(
        response => (
          (this.OurTk = response.data.tk), (this.xlsx = response.data.xlsx)
        )
      );
  },
  computed:{ 
    currentNameComponent: function () {
      return this.componentName
    }
  },
};
</script>


