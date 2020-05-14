<template>
  <div class="user" v-if="user">
    <Home :name="user" :imgSrc="imgSrc"  />
  </div>
  <div v-else class="login">
    <div class="user_pic" @click="handleClick">
      <input type="file" id="imgChange" class="upload" @change="addImg" ref="inputer" style="display: none;" />
      <img id="img" src="../assets/test.jpeg" class="img" />
    </div>
    <input type="text" class="name" placeholder="userName" v-model="username" />
    <button class="btn" @click="btnClick">
      Enter
    </button>    
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
import Home from './Home.vue'
export default {
  components: {
    Home
  },
  data () {
    return {
      username: '',
      imgSrc: ''
    }
  },
  computed: {
    ...mapState(['user'])
  },
  methods: {
    ...mapMutations(['setUser']),
    addImg () {
      var that = this
      let inputDOM = this.$refs.inputer
      const fileInfo = {
        file: inputDOM.files[0],
        id: new Date().getTime()
      }
      const reader = new FileReader()
      reader.readAsDataURL(fileInfo.file)
      reader.onload = function () {
        document.getElementById('img').setAttribute('src', this.result)
        that.imgSrc = this.result
      }
    },
    handleClick () {
      document.getElementById('imgChange').click()
    },
    btnClick () {
      this.setUser(this.username)
    }
  }
}
</script>

<style lang="scss">
  body {
    height: 100%;
    // font-family: system, -apple-system, '.SFNSText-Regular', 'SF UI Text', 'Lucida Grande', 'Segoe UI', Ubuntu, Cantarell, sans-serif;
    background-color: #8aba87;    
  }
  .login {
    text-align: center;
    // font-size: 34px;
  }
  .name {
    width: 80%;
    height: 40px;
    margin: 10px;
    margin: 30px auto;
    border: none;
    outline: none;
    background-color: #8aba87;
    border-bottom: 1px solid #000;
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
  }
  .btn {
    background-color: green;
    color: white;
    height: 40px;
    width: 100px;
    border-radius: 20px;
    border: none;
    outline: none;
  }
  .btn:hover {
    opacity: 0.8;
  }
  .btn:active {
    border-color: red;
  }
  .user_pic {
    margin: 100px auto;
    width: 80px;
    height: 80px;
    border-radius: 100%;
    overflow: hidden;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);

    img {
      display: block;
      width: 100%;
      height: 100%;
    }
  }
</style>
