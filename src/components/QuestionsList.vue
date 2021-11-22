<template>
  <div>
    <h1 class="flex justify-center">Question</h1>
    <div class="p-10 flex justify-center">
    <ol class="flex flex-col gap-y-8">
      <li v-for="question in allList" :key="question.id" class="p-4 border-gray-200 border-2">{{ question }}<button class="p-10" @click="remove(question.id)">delete</button></li>
    </ol>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex';

export default {
  name: "QuestionsList",
  methods: {
    ...mapActions(['fetchQuestion', 'deleteQuestion']),
    remove(id) {this.deleteQuestion(id)}
  },
  computed: mapGetters(['allList']),
  created() {
    this.fetchQuestion();
  }
}
</script>

<style scoped>

</style>
