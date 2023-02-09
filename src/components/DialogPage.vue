<template>
  <va-card outlined v-for="response in responses" :key="response.id">
    <va-card-content @click="responseClick(response)">
      <div class="d-flex" style="width: 100%; justify-content: space-between;">
        {{response.response}}
      </div>
    </va-card-content>
  </va-card>



  <div style="width:100%">
    <va-input v-model="userInput" label="User Input"></va-input>
    <va-button @click="sendInput()">Send</va-button>
  </div>

</template>

<script>
/* eslint-disable */
export default {
  name: 'HelloWorld',
  data() {
    return {
      userInput: "",
      responses: [],
    }
  },
  methods:{
    sendInput(){
      this.generateResponse(this.userInput);
      this.userInput = "";
    },
    generateResponse(input){
      var dto = {
        id: (this.responses.length),
        response: input
      }

      this.responses.push(dto);
    }
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
