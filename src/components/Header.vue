<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <img src="../assets/logo.gif" class="logo">
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link"  @click="newComponentName('TablesImg')">Акты имидж
            <span class="sr-only">(current)</span>
          </a>
        </li>
        <li class="nav-item active">
          <a class="nav-link"  @click="newComponentName('Tk')">ТК
            <span class="sr-only">(current)</span>
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Header",
  props: ["componentName"],
  data() {
    return {};
  },
  methods: {
    newComponentName: function(value){
      this.$emit('newName', value)
    }
  }
};
</script>