
<template>
  <form>
      <label>Email:</label>
      <input type="email" required v-model="email">
      <label>Password:</label>
      <input type="password" required v-model="password">
      
      <label>Role:</label>
      <select v-model="role"> 
          <option value="developer">Web Developer</option>
          <option value="designer">Web Designer</option>
      </select>

      <label>Skills:</label>  
      <input type="text" v-model="tempSkill" @keyup.enter="addSkill">
      <div v-for="skill in skills" :key="skill" class="pill" >
        <span @click="deleteSkill(skill)">{{skill}}</span>
      </div>

      <div class="terms">
          <input type="checkbox" required v-model="terms">
          <label>Accept terms and conditions</label>
      </div>

  </form>
</template>

<script>

export default {
    data(){
        return{
            email:'',
            password:'',
            role:'designer',
            terms:'false',
            tempSkill:'',
            skills:[]
        }
    },
    methods:{
        addSkill(e){
            if(/*e.key ===',' &&*/ this.tempSkill){
                if(!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = ''
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter((item) =>{
                return item !== skill 
            })
        }
    }
}
</script>

<style>
form{
    max-width: 420px;
    margin:30px auto;
    background:white;
    text-align:left;
    padding: 40px;
    border-radius:10px;
}

label{
    color: #555;
    display:inline-block;
    margin:25px 0 15;
    font-size: 0.6em;
    letter-spacing:1px;
    text-transform: uppercase;
    font-weight: bold;
}

input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing:border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position:relative;
    top: 2px;
}

.terms {
    padding:15px 0;
}

.pill{
    display: inline-block;
    margin:20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size:12px;
    letter-spacing:1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

</style>