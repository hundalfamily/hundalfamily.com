<template>
  <section>
    <div class="max-w-6xl mx-auto px-4 sm:px-6">
      <div class="py-12 md:py-20">
        <!-- Section header -->
        <div class="max-w-3xl mx-auto text-center pb-12 md:pb-20">
          <h2 class="h2 mb-4">{{ history.title }}</h2>
          <div class="prose max-w-full">
            <nuxt-content :document="history" />
          </div>
          <!-- <p class="text-xl text-gray">
            {{ history.description }}
          </p> -->
        </div>

        <!-- Items -->
        <div class="max-w-3xl mx-auto -my-4 md:-my-6" data-aos-id-timeline>
          <!-- 1st item -->
          <!-- <div class="relative py-4 md:py-6 pl-24" data-aos="fade-up" data-aos-anchor="[data-aos-id-timeline]">
            <div class="pl-2">
              <div class="font-architects-daughter text-xl text-amber-400 mb-2">The seed</div>
              <div class="flex items-center mb-3">
                <div class="absolute left-0 inline-flex text-sm font-semibold py-1 px-3 text-green-600 bg-green-200 rounded-full">2016</div>
                <div class="absolute left-0 h-full px-px bg-gray-800 ml-20 self-start transform -translate-x-1/2 translate-y-3" aria-hidden="true"></div>
                <div class="absolute left-0 w-2 h-2 bg-amber-400 border-4 box-content border-gray-900 rounded-full ml-20 transform -translate-x-1/2" aria-hidden="true"></div>
                <h4 class="h4">Open PRO was founded in Milan, Italy</h4>
              </div>
              <p class="text-lg text-gray-400">Pretium lectus quam id leo. Urna et pharetra pharetra massa massa. Adipiscing enim eu neque aliquam vestibulum morbi blandit cursus risus.</p>
            </div>
          </div> -->

          <!-- 2nd item -->
          <!-- <div class="relative py-4 md:py-6 pl-24" data-aos="fade-up" data-aos-delay="200" data-aos-anchor="[data-aos-id-timeline]">
            <div class="pl-2">
              <div class="font-architects-daughter text-xl text-amber-400 mb-2">New features</div>
              <div class="flex items-center mb-3">
                <div class="absolute left-0 inline-flex text-sm font-semibold py-1 px-3 text-green-600 bg-green-200 rounded-full">2017</div>
                <div class="absolute left-0 h-full px-px bg-gray-800 ml-20 self-start transform -translate-x-1/2 translate-y-3" aria-hidden="true"></div>
                <div class="absolute left-0 w-2 h-2 bg-amber-400 border-4 box-content border-gray-900 rounded-full ml-20 transform -translate-x-1/2" aria-hidden="true"></div>
                <h4 class="h4">Launched the first Open PRO Advanced plan</h4>
              </div>
              <p class="text-lg text-gray-400">Pretium lectus quam id leo. Urna et pharetra pharetra massa massa. Adipiscing enim eu neque aliquam vestibulum morbi blandit cursus risus.</p>
            </div>
          </div> -->

          <!-- 3rd item -->
          <!-- <div class="relative py-4 md:py-6 pl-24" data-aos="fade-up" data-aos-delay="400" data-aos-anchor="[data-aos-id-timeline]">
            <div class="pl-2">
              <div class="font-architects-daughter text-xl text-amber-400 mb-2">Pivoting</div>
              <div class="flex items-center mb-3">
                <div class="absolute left-0 inline-flex text-sm font-semibold py-1 px-3 text-green-600 bg-green-200 rounded-full">2018</div>
                <div class="absolute left-0 h-full px-px bg-gray-800 ml-20 self-start transform -translate-x-1/2 translate-y-3" aria-hidden="true"></div>
                <div class="absolute left-0 w-2 h-2 bg-amber-400 border-4 box-content border-gray-900 rounded-full ml-20 transform -translate-x-1/2" aria-hidden="true"></div>
                <h4 class="h4">Transitioned to a SaaS business model</h4>
              </div>
              <p class="text-lg text-gray-400">Pretium lectus quam id leo. Urna et pharetra pharetra massa massa. Adipiscing enim eu neque aliquam vestibulum morbi blandit cursus risus.</p>
            </div>
          </div> -->

          <!-- 4th item -->
          <!-- <div class="relative py-4 md:py-6 pl-24" data-aos="fade-up" data-aos-delay="600" data-aos-anchor="[data-aos-id-timeline]">
            <div class="pl-2">
              <div class="font-architects-daughter text-xl text-amber-400 mb-2">Huge milestone</div>
              <div class="flex items-center mb-3">
                <div class="absolute left-0 inline-flex text-sm font-semibold py-1 px-3 text-green-600 bg-green-200 rounded-full">2019</div>
                <div class="absolute left-0 w-2 h-2 bg-amber-400 border-4 box-content border-gray-900 rounded-full ml-20 transform -translate-x-1/2" aria-hidden="true"></div>
                <h4 class="h4">1 million happy customers</h4>
              </div>
              <p class="text-lg text-gray-400">Pretium lectus quam id leo. Urna et pharetra pharetra massa massa. Adipiscing enim eu neque aliquam vestibulum morbi blandit cursus risus.</p>
            </div>
          </div> -->
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Timeline",
  data() {
    return {
      history: {},
    };
  },
  async mounted() {
    this.history = await this.fetchHistory();
  },
  methods: {
    async fetchHistory() {
      return this.$content("history", "history")
        .fetch()
        .catch((err) => console.error(err) || []);
    },
  },
};
</script>