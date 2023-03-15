<template>
  <div class="flex flex-col">
    <span v-if="label" class="font-mono font-bold">
      {{ label }}
      <span v-if="required"
        >(<span class="text-red-500 font-bold">*</span>)</span
      >
    </span>
    <input
      v-model="internalValue"
      type="text"
      class="px-4 py-3 border-2 focus:border-orange-500 border-slate-500 rounded-xl cursor-pointer transition-all font-bold"
    />
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
    value: String,
    placeholder: String,
    label: String,
    required: Boolean,
    errors: Array,
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