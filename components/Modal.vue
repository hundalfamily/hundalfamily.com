<template>
  <div>
    <!-- Modal backdrop -->
    <transition
      enter-active-class="transition ease-out duration-200"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition ease-out duration-100"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-show="show"
        class="fixed inset-0 z-50 bg-black bg-opacity-75 transition-opacity"
        aria-hidden="true"
      ></div>
    </transition>

    <!-- Modal dialog -->
    <transition
      enter-active-class="transition ease-out duration-200"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="transition ease-out duration-200"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <div
        v-show="show"
        :id="id"
        class="
          fixed
          inset-0
          z-50
          overflow-hidden
          flex
          justify-center
          transform
          px-4
          py-48
        "
        role="dialog"
        aria-modal="true"
        :aria-labelledby="ariaLabel"
      >
        <div
          class="overflow-auto max-w-6xl w-full max-h-full"
          ref="modalContent"
          v-on:click="test($event)"
        >
          <slot />
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Modal",
  emits: ["handleClose"],
  props: {
    id: {
      type: String,
      default: null,
    },
    ariaLabel: {
      type: String,
      default: null,
    },
    show: {
      type: Boolean,
      default: false,
      required: true,
    },
  },
  methods: {
    clickOutside(e) {
      if (!this.show || this.$refs.modalContent.contains(e.target)) return;
      this.$emit("handleClose");
    },
    keyPress() {
      if (!this.show || event.keyCode !== 27) return;
      this.$emit("handleClose");
    },
    test(e) {
      console.log("Tetst called", e);
    },
  },
  mounted() {
    document.addEventListener("click", this.clickOutside);
    document.addEventListener("keydown", this.keyPress);
  },
  beforeUnmount() {
    document.removeEventListener("click", this.clickOutside);
    document.removeEventListener("keydown", this.keyPress);
  },
};
</script>