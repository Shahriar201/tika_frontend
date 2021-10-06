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
        <VaccineSteps :theme="step" />

        <div class="bg-white px-20 py-10 border border-gray-100">
          <div v-if="step == 'step_1'" class="">
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

          <div v-if="step == 'step_2'">
            <h3 class="font-bold text-4xl mb-6 text-center">
              User Information
            </h3>

            <p class="mb-6">
              <label
                class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                for="district_id"
                >Select Division</label
              >
              <select
                @change.prevent="getAvailableDistricts"
                v-model="division_id"
                class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
                name=""
                id="division_id"
              >
                <option selected="selected" value="">Select a division</option>
                <option
                  v-for="item in divisions"
                  :key="item.id"
                  :value="item.id"
                  >{{ item.name }}</option
                >
              </select>
            </p>

            <p v-if="districts.length" class="mb-6">
              <label
                class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                for="district_id"
                >Select District</label
              >
              <select
                @change.prevent="getAvailableUpazilas"
                v-model="district_id"
                class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
                name=""
                id="district_id"
              >
                <option selected="selected" value="">Select a district</option>
                <option
                  v-for="item in districts"
                  :key="item.id"
                  :value="item.id"
                  >{{ item.name }}</option
                >
              </select>
            </p>

            <p v-if="upazilas.length" class="mb-6">
              <label
                class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                for="upazila_id"
                >Select Upazila</label
              >
              <select
                @change.prevent="getAvailableCenters"
                v-model="upazila_id"
                class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
                name=""
                id="upazila_id"
              >
                <option selected="selected" value="">Select a upazila</option>
                <option
                  v-for="item in upazilas"
                  :key="item.id"
                  :value="item.id"
                  >{{ item.name }}</option
                >
              </select>
            </p>

            <p v-if="centers.length" class="mb-6">
              <label
                class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                for="center_id"
                >Select Vaccination Center</label
              >
              <select
                v-model="center_id"
                class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
                name=""
                id="center_id"
              >
                <option selected="selected" value="">Select a Center</option>
                <option
                  v-for="item in centers"
                  :key="item.id"
                  :value="item.id"
                  >{{ item.name }}</option
                >
              </select>
            </p>

            <p
              v-if="!centers.length && upazila_id"
              class="text-left text-red-400"
            >
              No Center Available.
            </p>

            <!-- Fillup user information if center id exist-->
            <div v-if="center_id">
              <p class="mb-6">
                <label
                  for="name"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >Name</label
                >
                <input
                  v-model="name"
                  type="text"
                  id="name"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl"
                  placeholder="Type your name"
                />
              </p>

              <p class="">
                <label
                  for="diabates"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >Do you have diabates</label
                >
                <select
                  v-model="diabates"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl focus:outline-none focus:border-gray-400"
                  name=""
                  id="diabates"
                >
                  <option selected="selected" value="">Select a value</option>
                  <option value="1">Yes</option>
                  <option value="0">No</option>
                </select>
              </p>
            </div>

            <p v-if="diabates" class="mt-6 text-left">
              <button
                @click.prevent="goToStepThree"
                class="primary-bg text-2xl text-white px-6 py-2 rounded-2xl"
              >
                Submit
              </button>
            </p>
          </div>

          <div v-if="step == 'step_3'">
            <h3 class="font-bold text-4xl mb-6 text-center">
              Phone Verification
            </h3>

            <div v-if="!smsSent">
              <p class="mb-6">
                <label
                  for="phone"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >Phone Number</label
                >
                <input
                  v-model="phone"
                  type="text"
                  id="phone"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl"
                  placeholder="Type your phone number"
                />
              </p>

              <p class="mt-6 text-left">
                <button
                  @click.prevent="sendVerificationSMS"
                  class="primary-bg text-2xl text-white px-6 py-2 rounded-2xl"
                >
                  Send SMS
                </button>
              </p>
            </div>

            <div v-if="smsSent">
              <p class="mb-6">
                <label
                  for="verify_code"
                  class="text-lg font-semibold text-black block mb-3 text-left cursor-pointer"
                  >Verification Code</label
                >
                <input
                  v-model="verify_code"
                  type="text"
                  id="verify_code"
                  class="block border bg-gray-100 border-gray-200 p-4 w-full rounded-3xl"
                  placeholder="Type your verification code"
                />
              </p>

              <p class="mt-6 text-left">
                <button
                  @click.prevent="verifyCode"
                  class="primary-bg text-2xl text-white px-6 py-2 rounded-2xl"
                >
                  Verify Code
                </button>
              </p>
            </div>
          </div>
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
      districts: [],
      divisions: [],
      upazilas: [],
      centers: [],
      step: "step_2",
      peopleData: [],
      verifyData: {
        category_id: "",
        id_no: "",
        dob: ""
      },

      division_id: "",
      district_id: "",
      upazila_id: "",
      center_id: "",
      name: "",
      diabates: "",
      phone: "",
      verify_code: "",
      smsSent: false
    };
  },

  mounted() {
    this.getAvailableCategory();
    this.getAvailableDivisions();
    // this.getAvailableDistricts();;
  },

  methods: {
    getAvailableCategory() {
      this.$axios.get("/categories").then(res => {
        this.categories = res.data;
      });
    },

    getAvailableDivisions() {
      this.$axios.get("/divisions").then(res => {
        this.divisions = res.data;
      });
    },

    getAvailableDistricts() {
      this.$axios
        .get("/districts?division_id=" + this.division_id)
        .then(res => {
          this.districts = res.data;
        });
    },

    getAvailableUpazilas() {
      this.$axios.get("/upazilas?district_id=" + this.district_id).then(res => {
        this.upazilas = res.data;
      });
    },

    getAvailableCenters() {
      this.$axios
        .get("/vaccination-centers?upazila_id=" + this.upazila_id)
        .then(res => {
          this.centers = res.data;
        });
    },

    checkMyInformation() {
      this.$axios.post("/verify", this.verifyData).then(res => {
        this.peopleData = res.data;

        if (res.data.success) {
          this.step = "step_2";
        }
      });
    },

    goToStepThree() {
      this.step = "step_3";
    },

    sendVerificationSMS() {
      this.$axios
        .post("/phone-verify", {
          phone: this.phone
        })
        .then(res => {
          if (res.data == "pending") {
            this.smsSent = true;
          }
        });
    }

    // verifyCode() {
    //   this.$axios
    //     .post("/phone-verify-code", {
    //       phone: this.phone,
    //       verify_code: this.verify_code
    //     })
    //     .then(res => {
    //       console.log(res.data);
    //     });
    // }
  }
};
</script>

<style scoped></style>
