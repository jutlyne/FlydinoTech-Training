<template>
  <div class="container" v-show="isShow">
    <transition name="trans">
    <div :class="{ blue : isChange }" v-show = "transf">
      <form action="" method="post">
        <div class="imgcontainer">
          <img src="https://www.w3schools.com/howto/img_avatar2.png" alt="Avatar" class="avatar">
        </div>

        <div class="container">
          <label for="uname"><b>Username</b></label>
          <input type="text" placeholder="Enter Username" name="uname" required>

          <label for="psw"><b>Password</b></label>
          <input type="password" placeholder="Enter Password" v-model="pass" name="psw" required>

          <label for="psw"><b>Re-Password</b></label>
          <input type="password" placeholder="Enter Password" v-model="pass"  name="psw" required>

          <button type="submit" @click = "isChange = ! isChange" v-bind:style = "styleobj" v-on:mouseover = "changebgcolor" v-on:mouseout = "originalcolor">Regis</button>
          <label>
            <input type="checkbox" checked="checked" name="remember"> Remember me
          </label>
        </div>

        <div class="container" style="background-color:#f1f1f1">
          <button type="button" v-on:click = "showdata"  class="cancelbtn">Cancel</button>
          <span class="psw">Forgot <a href="#">password?</a></span>
        </div>
      </form>
      
    </div>
    </transition>
    <transition name="show">
      <button v-if="show" @click="showdata">Click Me</button>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show : false,
      isChange : true,
      pass : "",
      total : '',
      styleobj : {
        backgroundColor:"green"
        },
      isShow : true,
      transf : true
    }
  },
  methods : {
      changebgcolor : function() {
        this.styleobj.backgroundColor = "blue";
      },
      originalcolor : function() {
        this.styleobj.backgroundColor = "red";
      },
      showdata : function() {
        this.show = !this.show;
        this.transf = !this.transf;
      }

  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.trans-enter-active, .trans-leave-active {
  transition: opacity 2s
}
.trans-enter, .trans-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0
}
.show-enter-active, .show-leave-active {
  transition: opacity 3s;
}
.show-enter, .show-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0
}
/* Bordered form */
form {
  border: 3px solid #f1f1f1;
}

/* Full-width inputs */
input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

/* Add a hover effect for buttons */
button:hover {
  opacity: 0.8;
}

.blue {
  background: rgb(167, 167, 182);
}

/* Extra style for the cancel button (red) */
.cancelbtn {
  width: auto;
  padding: 10px 18px;
  background-color: #f44336;
}

/* Center the avatar image inside this container */
.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}

/* Avatar image */
img.avatar {
  width: 40%;
  border-radius: 50%;
}

/* Add padding to containers */
.container {
  padding: 16px;
}

/* The "Forgot password" text */
span.psw {
  float: right;
  padding-top: 16px;
}

/* Change styles for span and cancel button on extra small screens */
@media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }
  .cancelbtn {
    width: 100%;
  }
}

</style>
