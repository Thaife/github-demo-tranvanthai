<template>
  <div id="app">
    <TheNavbar />
    <TheContainer />
    <!-- <div class="div-test">
      <input class="test a-input" v-model="fullName" />
      <div>{{converUpperCaseFullName}}</div>
    </div> -->
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TheNavbar from "./components/layout/TheNavbar.vue";
import TheContainer from "./components/layout/TheContainer.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    TheNavbar,
    TheContainer,
  },
  // beforeCreate() {
  //   console.log("beforeCreate: " + this.sortNumber);
  // },
  // created() {
  //   console.log("created: " + this.sortNumber);
  // },
  // beforeMount() {
  //   let el = document.querySelector(".test");
  //   console.log("beforeMount: ");
  //   console.log(el);
  // },
  // mounted() {
  //   let el = document.querySelector(".test");
  //   console.log("mounted: ");
  //   console.log(el);
  // },
  // beforeUpdate() {
  //   console.log("beforeUpdate: ");
  //   let el = document.querySelector(".test")
  //   let value = el.value;
  //   if(value > 0) {
  //     el.classList.add('border-red')
  //   } else {
  //     el.classList.remove('border-red')
  //   }

  // },
  // updated() {
  //   console.log("Update: ");
  //   let el = document.querySelector(".test")
  //   let value = el.value;
  //   if(value > 0) {
  //     el.classList.add('border-violet')
  //   } else {
  //     el.classList.remove('border-violet')
  //   }
  // },
  
  //BeforeDestroy
  beforeDestroy() {
    
  },
  destroyed() {
    
  },
  props: [
    'formMode'
  ],
  computed: {
    converUpperCaseFullName(value) {
      console.log(value)
      return this.fullName.toUpperCase()
    }
  },
  watch: {
    fullName: function(value) {
      switch(value) {
        case 'Hồ Chí Minh':
          alert('Không được đặt tên giống tên Bác Hồ!')
          break;
        case 'Trần Văn Thái':
          alert('Tên này thì đặt thoải mái')
          break;
        default: 
          break;
      }
    }
  },
  data() {
    return {
      sortNumber: 1,
      fullName: '',
      customer: [
        {
          Code: "NV01",
          Name: "Tran Van Thai",
        },
      ],
    };
  },
};
</script>

<style>
@import url(./style/common/common.css);
@import url(./style/base/btn.css);
@import url(./style/base/icon.css);
@import url(./style/base/comboBox.css);
@import url(./style/base/input.css);
@import url(./style/base/table.css);
@import url(./style/base/chipStatus.css);
@import url(./style/base/toastMessenger.css);
@import url(./style/base/dialog.css);
@import url(./style/base/EditEmploy.css);
/* @import url(./style/layout/nav.css);
@import url(./style/layout/header.css);
@import url(./style/layout/content.css); */

#app {
  color: #2c3e50;
  display: flex;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: GoogleSans;
  font-size: 13px;
}

@font-face {
  font-family: GoogleSans;
  src: url(./assets/font/GoogleSans-Regular.otf);
}

@font-face {
  font-family: googleSans-Bold;
  src: url(./assets/font/GoogleSans-Bold.otf);
}

@font-face {
  font-family: GoogleSans-Italic;
  src: url(./assets/font/GoogleSans-Italic.otf);
}
</style>
