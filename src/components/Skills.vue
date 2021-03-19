<template>
  <div class="hello">
    <div class="abc">
      <form @submit.prevent="addSkill">
        <input
          type="text"
          placeholder="Enter your Skills..."
          v-validate="'min:2'"
          v-model="skill"
          name="skill"
        />
        <transition name="alert-in">
          <p class="alert" v-if="errors.has('skill')">
            {{ errors.first("skill") }}
          </p>
          
        </transition>
        <!--{{ skill }} -->
        <!--<input type="checkbox" id="checkbox" v-model="check"> -->
      </form>

      <ul>
        <transition-group
          name="list"
          enter-active-class="animated bounceInUp"
          leave-active-class="animated bounceOutDown">

          <li v-for="(data, index) in yourskill" :key="index">
            {{ data.skill }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
          
        </transition-group>

        <p><strong>These are the skills you possess !</strong></p>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      /*check: false,*/
      skill: "",
      yourskill: [{ skill: "vue.js" }, { skill: "frontend developer" }],
    };
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.yourskill.push({ skill: this.skill });
          this.skill = "";
          /*console.log("The checkbox value is: " + this.check)*/
        } else {
          alert("Invalid Data");
          console.log("Invalid Data");
        }
      });
    },
    remove(id){
      this.yourskill.splice(id,1);
    }
  },
};
</script>

<style scoped>
/* SCOPPED IS USED TO APPLY STYLES ONLY TO A PARTICULAR FILE'S HTML */
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1"; /*Animate css*/
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.abc {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

ul p {
  text-align: center;
  padding: 30px 0;
  color: rgb(78, 180, 18);
}

.container {
  box-shadow: 0px 0px 40px rgb(211, 211, 211);
}

input {
  width: calc(100% - 40px);
  background-color: #323333;
  padding: 20px;
  margin-bottom: 0px;
  font-size: 1.3em;
  color: white;
  border: none;
  border-block-color: black;
}

.alert {
  color: red;
  display: inline-block;
  font-weight: bolder;
}

.alert-in-enter-active {
  animation: bounce-in 0.5s;
}
.alert-in-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i{
  float: right;
  cursor: pointer;
}
</style>
