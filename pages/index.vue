<template>
  <div class="flex flex-col h-full">
    <HeroBanner @scrollToSection="scrollToSection" />
    <Introduction @scrollToSection="scrollToSection" />
    <Video @scrollToSection="scrollToSection" />
    <Schedule @scrollToSection="scrollToSection" />
    <Prizes @scrollToSection="scrollToSection" />
    <Rules @scrollToSection="scrollToSection" />
    <Testimonials @scrollToSection="scrollToSection" />
    <Registration @scrollToSection="scrollToSection" />
    <Photos @scrollToSection="scrollToSection" />
    <ProblemsArchive @scrollToSection="scrollToSection" />
    <Contact @scrollToSection="scrollToSection" />
  </div>
</template>

<script>
export default {
  mounted() {
    this.disableScroll();
  },
  methods: {
    disableScroll() {},
    scrollToSection(sectionName) {
      if (process.browser) {
        const section = document.getElementById(sectionName);
        section.scrollIntoView({
          behavior: "smooth",
        });
      }
    },
  },
};
</script>
