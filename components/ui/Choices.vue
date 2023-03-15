<template>
  <div class="flex flex-col">
    <span v-if="label" class="font-mono font-bold">
      {{ label }}
      <span v-if="required"
        >(<span class="text-red-500 font-bold">*</span>)</span
      >
    </span>
    <div class="flex justify-center gap-2">
      <div
        v-for="(choice, i) in choices"
        :key="i"
        @click="internalValue = choice.value"
        class="cursor-pointer transition-all border-2 border-slate-200 px-8 py-2 rounded-xl"
        :class="[
          {
            'bg-stone-300': internalValue === choice.value,
          },
        ]"
      >
        {{ choice.label }}
      </div>
    </div>
    <div
      v-for="(error, i) in errors"
      :key="i"
      class="flex p-1 px-2 bg-red-100 border-l-4 border-red-600 text-red-600 font-semibold"
    >
      <!-- <span>🚫</span>&nbsp; -->
      {{ error }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: [Number, String],
    placeholder: String,
    label: String,
    required: Boolean,
    errors: Array,
    choices: Array,
  },
  computed: {
    internalValue: {
      get() {
        return this.value;
      },
      set(val) {
        this.$emit("input", val);
      },
    },
  },
};
</script>