<template>
  <div>
    <b-form submit="submit">
      <b-container fluid>
        <h1>Candidate Info</h1>
        <p>Please fill in this form to apply for a job.</p>
        <b-row>
          <b-col cols="2">
            <label for="name">Name</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="name"
              placeholder="Name"
              v-model="shortcuts['name']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="college_name">College Name</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="college_name"
              placeholder="College Name"
              v-model="shortcuts['college_name']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="company_names">Company Names</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="company_names"
              placeholder="Company Names"
              v-model="shortcuts['company_names']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="degree">Degree</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="degree"
              placeholder="Degree"
              v-model="shortcuts['degree']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="designation">Designation</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="designation"
              placeholder="Designation"
              v-model="shortcuts['designation']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="email">Email</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="email"
              placeholder="Email"
              v-model="shortcuts['email']"
            >
            </b-form-input>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="experience">Experience</label>
          </b-col>
          <b-col cols="10">
            <b-form-textarea
              class="input"
              id="experience"
              placeholder="Experience"
              v-model="shortcuts['experience']"
              rows="6"
            >
            </b-form-textarea>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="skill">Skills</label>
          </b-col>
          <b-col cols="10">
            <b-form-textarea
              class="input"
              id="skills"
              placeholder="Skills"
              v-model="shortcuts['skills']"
              rows="4"
            >
            </b-form-textarea>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="2">
            <label for="total_experience">Skills</label>
          </b-col>
          <b-col cols="10">
            <b-form-input
              class="input"
              id="total_experience"
              placeholder="Total Experience"
              v-model="shortcuts['total_experience']"
            >
            </b-form-input>
          </b-col>
        </b-row>
      </b-container>
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
    submit() {
      alert("Successfully saved resume");
      console.log("Successfully saved");
    },
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
