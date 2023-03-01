<script>
import { Configuration, OpenAIApi } from "openai"

export default {
    data() {


        return {
            output: "response"
        }
    },

    methods: {
        handleOpenAi() {

            const configuration = new Configuration({
                // apiKey: process.env.OPENAI_API_KEY,
                apiKey: document.querySelector('#apikey').value,
            });

            const openai = new OpenAIApi(configuration);

            const response =  openai.createCompletion({
                model: "text-davinci-003",
                prompt: "This is an api test. Are you up?",
                temperature: 0.7,
                max_tokens: 256,
                top_p: 1,
                frequency_penalty: 0,
                presence_penalty: 0,
            });

            console.log(response)
        }
    }
}
</script>

<template>
  <div class="about container">
    <div class="row">
        <h1>This is an about page</h1>
    </div>

    <div class="row mt-4 mb-4 justify-content-center">
        <div class="col-12">
            <form>
                <div class="input-group mb-4">
                    <input type="text" class="form-control" id="apikey" placeholder="Text" aria-label="Search" aria-describedby="basic-addon1">
                    <span class="input-group-text" id="basic-addon1"><i class="bi bi-search"></i></span>
                </div>

                <div class="d-grid gap-2">
                    <button @click="handleOpenAi" class="btn btn-primary" type="button">Submit</button>
                </div>

                <div class="card">
                    <div class="card-body">{{ output }}</div>
                </div>
            </form>
        </div>
    </div>

  </div>
</template>

<style>
@media (min-width: 1024px) {
  /* .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  } */
}
</style>
