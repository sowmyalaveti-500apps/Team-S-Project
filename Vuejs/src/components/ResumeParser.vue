<template>
  <div>
    <b-form submit="submit">
      <div class="container">
        <h1>Candidate Info</h1>
        <p>Please fill in this form to apply for a job.</p>
        <b-row v-for="field in shortcutFields" :key="field.key">
          <b-col>
            <label :for="field.key">{{ field.label }}</label>
          </b-col>
          <b-col>
            <b-form-textarea
              class="input truncate"
              :id="field.key"
              v-model="shortcuts[field.key]"
              :placeholder="field.label"
              type="text"
            ></b-form-textarea>
          </b-col>
        </b-row>
      </div>
      <b-button @click="submit()">Save</b-button>
    </b-form>
  </div>
</template>
<script>
import PredefinedShorcuts from "@/js/mixins/import-csv.js";
export default {
  name: "ResumeParser",
  data() {
    return {
      shortcuts: [],
      shortcutFields: [
        { key: "college_name", label: "College Name" },
        { key: "company_names", label: "Company Names" },
        { key: "degree", label: "Degree" },
        { key: "designation", label: "Designation" },
        { key: "email", label: "Email" },
        { key: "experience", label: "Experience" },
        { key: "name", label: "Name" },
        { key: "skills", label: "Skills" },
        { key: "total_experience", label: "Total Experience" },
      ],
    };
  },
  mounted() {
    // Get data Resume Metadata
    this.shortcuts = PredefinedShorcuts.items[0];
    this.filterData();
  },
  methods: {
    // filter data to avoid object format data to string
    filterData() {
      this.shortcutFields.forEach((field) => {
        if (typeof this.shortcuts[field.key] == "object") {
          this.shortcuts[field.key] = this.shortcuts[field.key].join(",");
        }
      });
    },
    submit(){
      alert("Successfully saved resume")
      console.log("Successfully saved")
    }
  },
};
</script>
<style scoped>
* {
  box-sizing: border-box;
}
.container {
  padding: 16px;
}
input,
textarea {
  width: 50%;
  padding: 10px;
  margin: 5px 0 22px 0;
  display: inline-block;
}
</style>
