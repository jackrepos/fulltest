<script lang="ts">
import { Configuration, OpenAIApi } from "openai"

export default {
    data() {
        return {
            apiKey: '',
            prompt: '',
            response: '',
        };
    },

    methods: {
        async handleOpenAi() {

            const configuration = new Configuration({
                // apiKey: process.env.OPENAI_API_KEY,
                // apiKey: document.querySelector('#apikey').value,
                apiKey: this.apiKey,
            });

            const openai = new OpenAIApi(configuration);



            try {
                const result = await openai.createCompletion({
                    model: "text-davinci-003",
                    prompt: this.prompt !== '' ? this.prompt : "This is an api test. Are you up?",
                    temperature: 0.7,
                    max_tokens: 256,
                    top_p: 1,
                    frequency_penalty: 0,
                    presence_penalty: 0,
                });

                this.response = result.data.choices[0].text ?? 'No response';
            } catch (error) {
                this.response = 'Error: ' + error;
            }

            console.log(this.response)
        },
    },
};
</script>

<template>
    <div class="about container">
        <div class="row">
            <h1>This is an about page</h1>
        </div>

        <div class="row mt-4 mb-4 justify-content-center">
            <div class="col-12">
                <form @submit.prevent="handleOpenAi">
                    <div class="input-group mb-4">
                        <input type="text" class="form-control" id="apikey" v-model="apiKey" placeholder="Api Key" aria-label="Search"
                            aria-describedby="basic-addon1">
                        <span class="input-group-text" id="basic-addon1"><i class="bi bi-search"></i></span>
                    </div>

                    <div class="input-group mb-4">
                        <input type="text" class="form-control" id="prompt" v-model="prompt" placeholder="Prompt" aria-label="Search"
                            aria-describedby="basic-addon2">
                        <span class="input-group-text" id="basic-addon2"><i class="bi bi-search"></i></span>
                    </div>

                    <div class="d-grid gap-2 mb-3">
                        <button class="btn btn-primary" type="submit">Submit</button>
                    </div>
                </form>

                <div class="card">
                    <div v-if="response" class="card-body">{{ response }}</div>
                </div>
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
