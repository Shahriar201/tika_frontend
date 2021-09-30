<template>
  <div>
    <Tutorial />

    <div class="realtive">
      <div class="container mx-auto small-container text-center py-20">
        <div class="top-small-container mx-auto">
          <h2 class="text-4xl font-bold mb-6">Registration for Vaccine</h2>
          <p class="text-lg">
            You will just need your NID card, Phone number and filling up some
            info
          </p>

          <div class="flex -mx-6 my-16">
            <div class="flex-1 px-6">
              <div class="h-32 flex justify-center items-center">
                <img class="mx-auto" src="img/promo-1.svg" alt="" />
              </div>
              <div
                class="border-4 w-6 h-6 rounded-full border-green-600 mx-auto mb-4 mt-8"
              ></div>
              <p class="font-bold text-lg">NID</p>
            </div>

            <div class="flex-1 px-6">
              <div class="h-32 flex justify-center items-center">
                <img class="mx-auto" src="img/promo-2.svg" alt="" />
              </div>
              <div
                class="border-4 w-6 h-6 rounded-full border-green-600 mx-auto mb-4 mt-8"
              ></div>
              <p class="font-bold text-lg">Phone</p>
            </div>

            <div class="flex-1 px-6">
              <div class="h-32 flex justify-center items-center">
                <img class="mx-auto" src="img/promo-3.svg" alt="" />
              </div>
              <div
                class="border-4 w-6 h-6 rounded-full border-green-600 mx-auto mb-4 mt-8"
              ></div>
              <p class="font-bold text-lg">Information</p>
            </div>
          </div>

          <div class="text-left mb-16">
            <h2 class="text-4xl font-bold mb-6">Get Updates</h2>
            <p class="text-lg">
              Check Your Registration Status, Vaccine card, Certificate and See
              Faqs .
            </p>
          </div>

          <div class="flex -mx-4">
            <div class="flex-1 px-4">
              <nuxt-link
                to=""
                class="block shadow-xl border border-gray-200 px-6 pt-16 pb-10 relative"
              >
                <div class="flex justify-center items-center h-32">
                  <img src="img/box-1.svg" alt="" class="" />
                </div>
                <p class="text-lg font-semibold">Check Status</p>

                <div class="absolute left-0 -bottom-5 w-full">
                  <img src="/img/enter-1.svg" alt="" class="mx-auto" />
                </div>
              </nuxt-link>
            </div>

            <div class="flex-1 px-4">
              <nuxt-link
                to=""
                class="block shadow-xl border border-gray-200 px-6 pt-16 pb-10 relative"
              >
                <div class="flex justify-center items-center h-32">
                  <img src="/img/box-2.svg" alt="" class="" />
                </div>
                <p class="text-lg font-semibold">Vaccine Card</p>
                <div class="absolute left-0 -bottom-5 w-full">
                  <img src="/img/enter-2.svg" alt="" class="mx-auto" />
                </div>
              </nuxt-link>
            </div>

            <div class="flex-1 px-4">
              <nuxt-link
                to=""
                class="block shadow-xl border border-gray-200 px-6 pt-16 pb-10 relative"
              >
                <div class="flex justify-center items-center h-32">
                  <img src="img/box-3.svg" alt="" class="" />
                </div>
                <p class="text-lg font-semibold">Certificate</p>
                <div class="absolute left-0 -bottom-5 w-full">
                  <img src="/img/enter-3.svg" alt="" class="mx-auto" />
                </div>
              </nuxt-link>
            </div>

            <div class="flex-1 px-4">
              <nuxt-link
                to=""
                class="block shadow-xl border border-gray-200 px-6 pt-16 pb-10 relative"
              >
                <div class="flex justify-center items-center h-32">
                  <img src="img/box-4.svg" alt="" class="" />
                </div>
                <p class="text-lg font-semibold">FAQ</p>
                <div class="absolute left-0 -bottom-5 w-full">
                  <img src="/img/enter-4.svg" alt="" class="mx-auto" />
                </div>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="container mx-auto">
      <div class="primary-bg text-white mx-auto rounded-3xl p-8">
        <div class="flex items-center">
          <div class="w-1/3 mr-10 font-bold">
            <h3 class="text-7xl uppercase">Hotline</h3>
            <p class="text-4xl">Numbers</p>
          </div>

          <div class="w-2/3">
            <div class="flex flex-wrap -mx-10">
              <div class="w-1/2 px-10 mb-10">
                <div class="bg-white p-4 rounded-lg text-black">
                  <div class="flex items-center">
                    <div class="min-w-max mr-2">
                      <img src="/img/phone-pink.svg" alt="" />
                    </div>

                    <div class="w-full">
                      <h4 class="text-red-400 text-4xl font-bold">333</h4>
                      <p class="text-xl">National Call Center</p>
                    </div>
                  </div>
                </div>
              </div>

              <div class="w-1/2 px-10 mb-10">
                <div class="bg-white p-4 rounded-lg text-black">
                  <div class="flex items-center">
                    <div class="min-w-max mr-2">
                      <img src="/img/phone-pink.svg" alt="" />
                    </div>

                    <div class="w-full">
                      <h4 class="text-red-400 text-4xl font-bold">333</h4>
                      <p class="text-xl">National Call Center</p>
                    </div>
                  </div>
                </div>
              </div>

              <div class="w-1/2 px-10">
                <div class="bg-white p-4 rounded-lg text-black">
                  <div class="flex items-center">
                    <div class="min-w-max mr-2">
                      <img src="/img/phone-pink.svg" alt="" />
                    </div>

                    <div class="w-full">
                      <h4 class="text-red-400 text-4xl font-bold">333</h4>
                      <p class="text-xl">National Call Center</p>
                    </div>
                  </div>
                </div>
              </div>

              <div class="w-1/2 px-10">
                <div class="bg-white p-4 rounded-lg text-black">
                  <div class="flex items-center">
                    <div class="min-w-max mr-2">
                      <img src="/img/phone-pink.svg" alt="" />
                    </div>

                    <div class="w-full">
                      <h4 class="text-red-400 text-4xl font-bold">333</h4>
                      <p class="text-xl">National Call Center</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  data() {
    return {};
  },

  mounted() {
    // this.testBackendRequest();
  },

  methods: {}
});
</script>
