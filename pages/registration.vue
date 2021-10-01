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
        <VaccineSteps theme="step-1" />
      </div>
    </div>
  </div>
</template>

<script>
import VaccineSteps from "../components/VaccineSteps";
export default {
  name: "registration",
  components: { VaccineSteps }
};
</script>

<style scoped></style>
