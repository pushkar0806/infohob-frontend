<template>
  <div>
    <Header />
    <div class="form-steps main-height">
      <a-steps :current="current">
        <a-step v-for="item in steps" :key="item.title" :title="item.title" />
      </a-steps>
      <div class="steps-content">
        <ProfileSummary :nextStep="next" v-if="steps[current].id === 1" />
        <education-details
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 2"
        />
        <experience-details
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 3"
        />
        <projects
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 4"
        />
        <documents
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 5"
        />
        <key-skills
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 6"
        />
        <personal-info
          :nextStep="next"
          :previousStep="prev"
          v-if="steps[current].id === 7"
        />
      </div>
      <!-- <div class="steps-action">
        <a-button
          v-if="current < steps.length - 1"
          type="primary"
          @click="next"
        >
          Next
        </a-button>
        <a-button
          v-if="current == steps.length - 1"
          type="primary"
          @click="$message.success('Processing complete!')"
        >
          Done
        </a-button>
        <a-button v-if="current > 0" style="margin-left: 8px" @click="prev">
          Previous
        </a-button>
      </div> -->
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from "./Footer";
import ProfileSummary from "./ProfileSummary";
import Header from "../Header.vue";
import EducationDetails from "./EducationDetails.vue";
import ExperienceDetails from "./ExperienceDetails.vue";
import Projects from "./Projects.vue";
import Documents from "../Documents.vue";
import KeySkills from "./KeySkills.vue";
import PersonalInfo from "./PersonalInfo.vue";
export default {
  name: "RegistrationIndex",
  components: {
    Footer,
    Header,
    ProfileSummary,
    EducationDetails,
    ExperienceDetails,
    Projects,
    Documents,
    KeySkills,
    PersonalInfo,
  },
  data() {
    return {
      current: 0,
      steps: [
        {
          id: 1,
          title: "Profile Summary",
          content: "First-content",
        },
        {
          id: 2,
          title: "Education",
          content: "Second-content",
        },
        {
          id: 3,

          title: "Experience",
          content: "Last-content",
        },
        {
          id: 4,

          title: "Projects",
          content: "Last-content",
        },
        {
          id: 5,

          title: "Documents",
          content: "Last-content",
        },
        {
          id: 6,

          title: "Key Skills",
          content: "Last-content",
        },
        {
          id: 7,

          title: "My Profile",
          content: "Last-content",
        },
      ],
    };
  },
  methods: {
    next() {
      this.current++;
    },
    prev() {
      this.current--;
    },
  },
};
</script>

<style scoped>
.form-steps {
  padding: 50px;
}
.ant-steps-item-finish
  > .ant-steps-item-container
  > .ant-steps-item-tail::after {
  background-color: red !important;
}
.ant-steps-item-finish .ant-steps-item-icon > .ant-steps-icon {
  color: #ffffff;
}
.steps-content {
  /* margin-top: 16px; */
  /* border: 1px dashed #e9e9e9; */
  border-radius: 6px;
  /* background-color: #fafafa; */
  min-height: 200px;
  display: flex;
  text-align: center;
  padding-top: 80px;
}

.steps-action {
  margin-top: 24px;
}
.display-flex {
  display: flex;
}
.main-height {
  min-height: calc(100vh - 110px);
}
</style>