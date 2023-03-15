<template>
  <div class="flex flex-col h-full">
    <HeroBanner @scrollToSection="scrollToSection" />
    <Introduction @scrollToSection="scrollToSection" />
    <Schedule @scrollToSection="scrollToSection" />
    <Rules @scrollToSection="scrollToSection" />
    <Testimonials @scrollToSection="scrollToSection" />
  </div>
</template>

<script>
export default {
  methods: {
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
