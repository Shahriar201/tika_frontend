<template>
  <div class="text-center">
    <Tutorial />

    <div class="primary-bg text-white py-10">
      <div class="container mx-auto">
        <h2 class="text-4xl font-bold mb-6">Vaccine Registration</h2>
        <p>
          Complete the registration by verifying your national identity card and
          mobile number in the form below. The place and date of delivery of the
          vaccine will be informed in due course through SMS message on the
          mobile phone.
        </p>
      </div>
    </div>

    <div class="py-20">
      <div class="small-container mx-auto">
        <VaccineSteps theme="step_1" />

        <div class="bg-white px-20 py-10 border border-gray-100">
          <h3 class="font-bold text-4xl mb-6 text-center">
            Identity Verification
          </h3>

          <div
            v-if="peopleData.hasOwnProperty('success') && !peopleData.success"
            class="bg-red-200 text-red-900 p-4 mb-6 text-left"
          >
            {{ peopleData.message }}
          </div>

          <p>
            <label
              class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
              for="category_id"
              >Select Category</label
            >
            <select
              v-model="verifyData.category_id"
              class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
              name=""
              id="category_id"
            >
              <option selected="selected" value="">Select a category</option>
              <option
                v-for="item in categories"
                :key="item.id"
                :value="item.id"
                >{{ item.name }}</option
              >
            </select>
            <!-- <input
              class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
              id="nid"
              type="text"
              placeholder="National Id Card Number"
            /> -->
          </p>

          <div v-if="verifyData.category_id" class="flex -mx-4">
            <div class="w-2/3 px-4 py-4">
              <p>
                <label
                  for="id_no"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >National ID Number</label
                >
                <input
                  v-model="verifyData.id_no"
                  type="number"
                  id="id_no"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl"
                  placeholder="Type your national ID card number"
                />
              </p>
            </div>

            <div class="w-1/3 px-4 py-4">
              <p>
                <label
                  for="dob"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >Date of Birth</label
                >
                <input
                  v-model="verifyData.dob"
                  type="date"
                  id="dob"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl"
                  placeholder="Type your date of birth"
                />
              </p>
            </div>
          </div>

          <p class="text-left mt-6">
            <button
              @click.prevent="checkMyInformation"
              class="primary-bg text-2xl text-white px-6 py-2 rounded-2xl"
            >
              Check my Information
            </button>
          </p>
        </div>
      </div>
    </div>

    <div class="container mx-auto">
      <ThreeSteps />
    </div>
  </div>
</template>

<script>
import VaccineSteps from "../components/VaccineSteps";
import ThreeSteps from "../components/ThreeSteps";
export default {
  name: "registration",
  components: { VaccineSteps, ThreeSteps },
  data() {
    return {
      categories: [],
      peopleData: [],
      verifyData: {
        category_id: "",
        id_no: "",
        dob: ""
      }
    };
  },

  mounted() {
    this.getAvailableCategory();
  },

  methods: {
    getAvailableCategory() {
      this.$axios.get("/categories").then(res => {
        this.categories = res.data;
        console.log(res.data);
      });
    },

    checkMyInformation() {
      this.$axios.post("/verify", this.verifyData).then(res => {
        this.peopleData = res.data;
      });
    }
  }
};
</script>

<style scoped></style>
