<template>
  <v-container fluid class="fill-height">
    <v-responsive
      class="align-centerfill-height mx-auto"
      
    >
      <v-img
        class="mb-4"
        height="150"
        src="@/assets/logo.png"
      />

      <div class="text-center">
        <div class="text-body-2 font-weight-light mb-n1">Welcome to</div>

        <h1 class="text-h2 font-weight-bold">Exercise Enhancer</h1>
      </div>

      <div class="py-4" />

      <v-row>
        <v-col cols="8" offset="2">
          <v-card
            class="py-4"
            color="surface-variant"
            prepend-icon="mdi-arrow-up-bold-box-outline"
            variant="outlined"
          >
            

            <template #title>
              <h2 class="text-h5 font-weight-bold">Upload Your PDF</h2>
            </template>

            <v-row>
              <v-col cols="7" class="ml-5">
                <input type="file" @change="handleFileUpload">
              </v-col>
            
              <v-col>
              <v-btn elevation="8" size="x-large" class="mb-10" @click="apiRequest">Generate alternative</v-btn>
            </v-col>

          </v-row>
                

          </v-card>
        </v-col>

     <!--  <v-col cols="6">
          <v-card
            append-icon="mdi-open-in-new"
            class="py-4"
            color="surface-variant"
            href="https://vuetifyjs.com/"
            prepend-icon="mdi-text-box-outline"
            rel="noopener noreferrer"
            rounded="lg"
            subtitle="Learn about all things Vuetify in our documentation."
            target="_blank"
            title="Documentation"
            variant="text"
          >
            <v-overlay
              opacity=".06"
              scrim="primary"
              contained
              model-value
              persistent
            />
          </v-card>
        </v-col>

        <v-col cols="6">
          <v-card
            append-icon="mdi-open-in-new"
            class="py-4"
            color="surface-variant"
            href="https://vuetifyjs.com/introduction/why-vuetify/#feature-guides"
            prepend-icon="mdi-star-circle-outline"
            rel="noopener noreferrer"
            rounded="lg"
            subtitle="Explore available framework Features."
            target="_blank"
            title="Features"
            variant="text"
          >
            <v-overlay
              opacity=".06"
              scrim="primary"
              contained
              model-value
              persistent
            />
          </v-card>
        </v-col>

        <v-col cols="6">
          <v-card
            append-icon="mdi-open-in-new"
            class="py-4"
            color="surface-variant"
            href="https://vuetifyjs.com/components/all"
            prepend-icon="mdi-widgets-outline"
            rel="noopener noreferrer"
            rounded="lg"
            subtitle="Discover components in the API Explorer."
            target="_blank"
            title="Components"
            variant="text"
          >
            <v-overlay
              opacity=".06"
              scrim="primary"
              contained
              model-value
              persistent
            />
          </v-card>
        </v-col>

        <v-col cols="6">
          <v-card
            append-icon="mdi-open-in-new"
            class="py-4"
            color="surface-variant"
            href="https://discord.vuetifyjs.com"
            prepend-icon="mdi-account-group-outline"
            rel="noopener noreferrer"
            rounded="lg"
            subtitle="Connect with Vuetify developers."
            target="_blank"
            title="Community"
            variant="text"
          >
            <v-overlay
              opacity=".06"
              scrim="primary"
              contained
              model-value
              persistent
            />
          </v-card>
        </v-col> --> 
      </v-row>
      <v-row>
        <v-col cols="6">
          <iframe
            v-if="pdfData"
            :src="pdfData"
            width="100%"
            height="600px"
            frameborder="0"
            scrolling="auto"
          ></iframe>
        </v-col>
        <v-col cols="6">
          <iframe
            v-if="pdfData"
            :src="pdfData"
            width="100%"
            height="600px"
            frameborder="0"
            scrolling="auto"
          ></iframe>
        </v-col>
      </v-row>
    </v-responsive>
    </v-container>

 </template>

<script>
  import axios from 'axios';
  export default{
    // Properties returned from data() become reactive state
    // and will be exposed on `this`.
    data: () => ({
        show: false,
        pdfData: null,
        pdfData2: null,
      
    }),
    // Methods are functions that mutate state and trigger updates.
    // They can be bound as event handlers in templates.
    methods: {
      handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        this.readPdfFile(file);
      }
    },
    readPdfFile(file) {
      const reader = new FileReader();
      reader.onload = (e) => {
        this.pdfData = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    apiRequest(){
      axios
      //.post('', {PDF: this.pdfData})
      .get('https://arxiv.org/pdf/2404.01381.pdf')
      .then(response => console.log(response))
      .then(response => (this.pdfData2 = response.data))
    }
  
    
  },
 }

</script>
