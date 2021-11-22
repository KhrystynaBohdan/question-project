<template>
  <div>
    <div class="p-10 flex justify-center focus:outline-none focus:ring focus:border-blue-300">
      <form class="border-solid border-gray-200 border-2">
        <input type="text" v-model="question" placeholder="Type question..." class="h-full"/>
        <button class="bg-green-100 p-4" @click="onSubmit">Submit</button>
      </form>
    </div>
    <div class="p-10 flex justify-center">
      <form>
        <div class="p-4 border-solid border-gray-200 border-2">
          <label for="position">Position:</label>
          <select v-model="position" @change="fetchData" id="position">
            <option>Junior</option>
            <option>Middle</option>
            <option>Senior</option>
          </select>
        </div>
        <div class="p-4 border-solid border-gray-200 border-2">
          <label for="framework">Framework:</label>
          <select v-model="framework" @change="fetchData" id="framework">
            <option>HTML</option>
            <option>CSS</option>
            <option>JavaScript</option>
            <option>React</option>
            <option>Vue</option>
          </select>
        </div>
      </form>
    </div>
    <QuestionsList/>
  </div>
</template>

<script>

import QuestionsList from "./QuestionsList";
import {mapActions} from 'vuex';

export default {
  name: 'Home',
  components: {QuestionsList},
  data() {
    return {
      question: "",
      position: 'Junior',
      framework: 'CSS',
    };
  },
  methods: {
    ...mapActions(['addQuestion', 'fetchQuestion']),
    onSubmit(event) {
      event.preventDefault();
      this.addQuestion(this.question);
      this.question = ''
    },
    fetchData() {
      this.fetchQuestion({
        position: this.position,
        framework: this.framework
      });
    }
  }
}
</script>

