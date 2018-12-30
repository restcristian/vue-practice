<template>
  <div class="skills page">
    <div class="holder">
      <form v-on:submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">
            {{errors.first('skill')}}
          </p>
        </transition>

      </form>
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" v-bind:key="data.id">
            {{data.skill}}
            <i class = "fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>

      </ul>
      <p>These are the skills that you have.</p>
    </div>
  </div>
</template>

<script>


  export default {
    name: 'Skills',
    data() {
      return {
        skills: [
          { id:0,skill: "Vue.js" },
          { id:1,skill: "Frontend Developer" },
        ],
        skill: '',
      }
    },
    methods: {
      addSkill() {
        this.$validator.validateAll().then((result) => {
          if (result && this.skill.trim().length !== 0) {
            const newSkill = {id:this.skills.length,skill: this.skill};
            this.skills.push(newSkill);
            this.skill = '';
          } else {
            console.log('Not valid');
          }
        });

      },
      remove(index){
        this.skills.splice(index, 1);
      }
    }

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  @import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css';

  .holder {
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
    background-color: #E0EDF4;
    border-left: 5px solid #3B3F65;
    margin-bottom: 2px;
    color: #3B3522;

  }

  p {
    padding: 30px 0;
    text-align: center;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  input {
    width: calc(100% - 40px);
    border: none;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7f;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }

  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }

  @keyframes bounce-in {
    0% {
      transform: scale(0)
    }

    50% {
      transform: scale(1.5)
    }

    100% {
      transform: scale(1)
    }
  }

  i{
    float:right;
    cursor: pointer;
  }
</style>