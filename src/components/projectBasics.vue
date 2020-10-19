<template>
  <div>
    <h2>Project Basics</h2>
    <div class="contentContainer" style="justify-content: flex-start">
      <div class="inputContainer">
        <label>Entity:</label>
        <Dropdown
          v-model="selectedEntity"
          :options="entities"
          optionLabel="entity"
        />
      </div>
      <div class="inputContainer">
        <label>Est. Completion Date:</label>

        <Calendar
          v-model="date"
          dateFormat="dd.mm.yy"
          :showIcon="true"
          :editable="true"
        />
      </div>
      <div class="inputContainer">
        <label>Project Name:</label>

        <InputText type="text" v-model="projectName" @keyup="setBasicData" />
      </div>
      <div class="inputContainer">
        <label>Upload Image:</label>
        <label style="border: 2px white solid; padding: 3px 3px 3px 3px"
          ><input type="file" @change="imageUpload" accept="image/*" />
        </label>
      </div>
    </div>
  </div>
</template>

<script>
import InputText from "primevue/inputtext";
import Dropdown from "primevue/dropdown";
import Calendar from "primevue/calendar";

export default {
  components: { Calendar, Dropdown, InputText },
  data: function () {
    return {
      imageUrl: null,
      date: new Date(),
      selectedEntity: { entity: "" },
      fileName: null,
      projectName: null,
      entities: [
        { entity: "Company A" },
        { entity: "Company B" },
        { entity: "Company C" },
        { entity: "Company D" },
      ],
    };
  },
  methods: {
    imageUpload: function (event) {
      const file = event.target.files[0];
      this.fileName = file;
      this.imageUrl = URL.createObjectURL(file);
    },
    setBasicData: function () {
      this.$emit(
        "set-basic-data",
        this.selectedEntity.entity,
        this.date.toLocaleDateString(),
        this.projectName,
        this.imageUrl
      );
    },
  },
};
</script>

<style>
.p-datepicker {
  background-color: hsl(200, 30%, 30%) !important;
  color: white !important;
  font-family: "Sora", sans-serif !important;
}
.p-inputtext {
  color: hsl(200, 30%, 30%) !important;
  font-size: 15px !important;
  font-family: "Sora", sans-serif !important;
}
.p-dropdown-panel {
  background-color: hsl(200, 30%, 30%) !important;
  color: white !important;
  font-family: "Sora", sans-serif !important;
  border: 2px white solid !important;
  display: flex !important;
}
.p-dropdown-label {
  color: hsl(200, 30%, 30%) !important;
}
.p-dropdown-item {
  color: white !important;
}
</style>

<style scoped>
.inputContainer {
  align-self: left;
  margin: 1% 1% 1% 1%;
  text-align: center;
}
</style>