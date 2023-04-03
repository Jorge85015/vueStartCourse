<template>
  <div class="mainPage">
      <h1>Hello {{ students.name }}</h1> <!--Interpolation-->
      <a :href="github" target="blank" rel="nooperner noreferrer"><h2>Github</h2></a>
      <a v-bind:href="twitter" target="blank"><h2>Twitter</h2></a>
      <br>
      <h4>Student List</h4>
      <ul class="list-of-students">
        <li v-for="student in students" :key="student.id">
          <a @click="selectedStudent = student" :class="{ 'is-active': selectedStudent === student }"> <!--Event binding-->
            <span>{{ student.name }} {{ student.surname }}</span>
          </a>
        </li>  <!-- Property binding shortcut : -->
      </ul>
      <p>student information:</p>
      <div v-if="selectedStudent">  <!-- Conditional rendering -->
        <div>
          <label class="label" for="id">id: </label>
          <label class="input" id="id">{{ selectedStudent.id }}</label><br>
        </div>
        <div>
          <label class="label" for="name">name: </label>
          <input type="input" v-model="selectedStudent.name"><br/>
        </div>
        <div>
          <label for="show" class="checkbox">
            show more
            <input type="checkbox" id="show" v-model="showMore"/>
          </label>
        </div>
        <div  v-show="showMore">
          <label class="label" for="id">surname: </label>
          <input type="input" v-model="selectedStudent.surname"/><br>
        </div>
        <div v-show="showMore">
          <label class="label" for="age" >age: </label>
          <input type="input" v-model="selectedStudent.age"/><br>
        </div>

      </div>
  </div>
</template>

<script>

export default {
  name: "HelloWorld",
  data() {
    return {
      selectedStudent: undefined,
      showMore: false,
      students: [
        {
          id: 1,
          name: "Jorge",
          surname: "Quinonez",
          age: 19,
          carreer: "Software Engineer",
          nationality: "Guatemala",
          eyesColor: "",
          grade: "",
          active: true,
          description: "",
        },
        {
          id: 2,
          name: "Qory",
          surname: "Centeno",
          age: 21,
          carreer: "Psicology",
          nationality: "Peru",
          eyesColor: "",
          grade: "",
          active: true,
          description: "",
        },
        {
          id: 3,
          name: "Tomi",
          surname: "Marcelo",
          age: 19,
          carreer: "Arquitecture",
          nationality: "Spain",
          eyesColor: "",
          grade: "",
          active: false,
          description: "",
        }
      ],
      message: 'Student information:',
    }
  },
}
</script>

<style>
p {
  font-weight: bold;
}

.colored-line {
  width: 160px;
  height: 8px;
  border: 1px #dbdbdb solid;
  margin: 8px 0;
}

span:hover {
  cursor: pointer;
  color: rgb(15, 21, 182);
}

.is-active {
  background-color: blue;
  color: white;
}
</style>




