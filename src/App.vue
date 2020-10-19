<template>
  <div class="appContainer">
    <article-picker @submit-article="addArticle"></article-picker>
    <p class="arrayDisplay">Chosen Article: {{ selectedArticle }}</p>
    <project-basics @set-basic-data="setBasicData"></project-basics>
    <p class="arrayDisplay">Project Basic Data: {{ projectBasics }}</p>
    <project-details
      :article="selectedArticle"
      @submit-project-details="setAdvancedData"
    ></project-details>
    <p class="arrayDisplay">Project Advanced Data: {{ projectAdvanced }}</p>
    <checklist
      :projectBasics="projectBasics"
      :projectAdvanced="projectAdvanced"
      :selectedArticle="selectedArticle"
      :projectImage="projectImage"
    ></checklist>
  </div>
</template>

<script>
import articlePicker from "./components/articlePicker.vue";
import checklist from "./components/checklist.vue";
import projectDetails from "./components/projectDetails.vue";
import projectBasics from "./components/projectBasics";

export default {
  name: "App",
  components: {
    articlePicker: articlePicker,
    checklist: checklist,
    projectDetails: projectDetails,
    projectBasics: projectBasics,
  },
  data: function () {
    return {
      selectedArticle: "",
      projectBasics: null,
      projectAdvanced: null,
      projectImage:null,
    };
  },
  methods: {
    addArticle: function (article) {
      this.selectedArticle = article;
    },
    setBasicData: function (entity, date, pname, image) {
      this.projectBasics = {
        entity,
        "Project Date": date,
        "Project Name": pname,
        
      };
      this.projectImage= image
    },
    setAdvancedData: function (test) {
      this.projectAdvanced = test;
    },
  },
};
</script>

<style >
body {
  background: whitesmoke;
  font-family: "Sora", sans-serif;
}
.appContainer {
  border: 2px hsl(200, 35%, 45%) solid;
  border-radius: 5px;
  width: 80%;
  -webkit-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  -moz-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  margin: auto;
}
.contentContainer {
  -webkit-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  -moz-box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  box-shadow: 0px 15px 20px 5px rgba(0, 0, 0, 0.77);
  background: hsl(200, 30%, 30%);

  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  vertical-align: bottom;
  align-items: center;
  margin: auto;
  width: 70%;
  border-radius: 5px;
  margin-top: 10px;
}

h2 {
  background: hsl(200, 35%, 45%);
  color: whitesmoke;
  font-size: 20px;
  margin: auto;
  padding: 5px 5px 5px 5px;
  margin-top: 20px;
  margin-bottom: 20px;
  width: 70%;
  font-size: 30px;
  text-align: center;
}
label {
  color: white;
  align-self: center;
  margin-right: 2vmin;
  justify-self: center;
}

@import url(https://fonts.googleapis.com/css2?family=Sora&display=swap);
</style>

<style scoped>
button {
  color: purple;
  background: white;
  border: 3px purple solid;
  font-size: 20px;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  margin: auto;
}

button:hover {
  color: limegreen;
  border: limegreen 2px solid;
  background: rgb(37, 48, 51);
}

.arrayDisplay {
  background: hsl(0, 0%, 74%);
  text-align: center;
  font-family: monospace;
  color: white;
  width: 70%;
  margin: auto;
  margin-top: 20px;
}
</style>