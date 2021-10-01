<template>
  <div>
    <div class="primary-bg">
      <div class="container mx-auto pt-20 pb-10">
        <div class="bg-white">
          <div class="flex items-center">
            <div class="min-w-max">
              <h2 class="text-2xl font-bold text-black uppercase px-6">
                <nuxt-link to="/">TIKA</nuxt-link>
              </h2>
            </div>

            <div class="w-full">
              <ul class="flex justify-center">
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/"
                    >Home</nuxt-link
                  >
                </li>
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/registration"
                    >Registration</nuxt-link
                  >
                </li>
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/verify"
                    >Verity</nuxt-link
                  >
                </li>
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/tika-card"
                    >Tika Card</nuxt-link
                  >
                </li>
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/help"
                    >Help</nuxt-link
                  >
                </li>
                <li>
                  <nuxt-link class="py-10 px-5 inline-block" to="/faqs"
                    >Faqs</nuxt-link
                  >
                </li>
              </ul>
            </div>

            <div class="min-w-max">
              <div class="px-6">
                <nuxt-link
                  class="primary-bg text-2xl text-white px-6 py-2 rounded-2xl"
                  to="/"
                  >Register Now</nuxt-link
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  setup() {}
};
</script>

<style scoped></style>
