<template>
  <section class="relative">
    <!-- Background image -->
    <div class="absolute inset-0">
      <img
        class="w-full h-full object-cover"
        src="../assets/images/family-member-bg.jpg"
        width="1440"
        height="394"
        alt="About"
      />
      <div
        class="absolute inset-0 bg-gray-900 opacity-75"
        aria-hidden="true"
      ></div>
    </div>

    <!-- Hero content -->
    <div class="max-w-6xl mx-auto px-4 sm:px-6 relative">
      <div class="pt-32 pb-12 md:pt-40 md:pb-20">
        <div class="max-w-3xl mx-auto text-center">
          <h1 class="h1 mb-4 text-white" data-aos="fade-up">
            {{ history.header }}
          </h1>
          <p
            class="text-xl text-gray-400 mb-8"
            data-aos="fade-up"
            data-aos-delay="200"
          >
            {{ history.paragraph }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeroAbout",
  data() {
    return {
      history: {},
    };
  },
  async mounted() {
    this.history = await this.fetchHistoryHeader();
  },
  methods: {
    async fetchHistoryHeader() {
      return this.$content("history", "history-header")
        .fetch()
        .catch((err) => console.error(err) || []);
    },
  },
};
</script>