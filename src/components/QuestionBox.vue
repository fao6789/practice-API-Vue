<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>{{currentQuestion.question}}</template>

      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item v-for="(a, index) in answer" :key="index" @click="seclect(index)">{{a}}</b-list-group-item>
      </b-list-group>
      <b-button variant="primary" href="#">Submit</b-button>
      <b-button @click="next" variant="success" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  data() {
    select: null;
  },
  computed: {
    answer() {
      // đẩy cái đúng vào cái đúng để được 1 list câu trả lời
      let answer = [...this.currentQuestion.incorrect_answers];
      answer.push(this.currentQuestion.correct_answer);
      return answer;
    }
  },
  mounted() {
    console.log(this.currentQuestion);
  },
  methods: {
    seclect(index) {
      this.select = index;
    }
  }
};
</script>