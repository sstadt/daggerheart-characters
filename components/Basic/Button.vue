<template lang="pug">
  button.text-lg.rounded-md.uppercase.font-bold.border.transition-colors(
    class="hover:shadow-md active:shadow-md"
    :class="buttonClass"
    :type="type"
  )
    slot
</template>

<script>
  export default {
    name: 'BasicButton',
    props: {
      type: {
        type: String,
        default: 'button',
      },
      size: {
        type: String,
        default: 'md',
        validator(value) {
          return ['sm', 'md', 'lg'].includes(value);
        },
      },
      priority: {
        type: String,
        default: 'primary',
        validator(value) {
          return ['primary', 'secondary'].includes(value);
        },
      },
    },
    computed: {
      buttonClass() {
        return {
          'text-sm py-1 px-4': this.size === 'sm',
          'py-4 px-6 text-lg': this.size === 'md',
          'py-5 px-7 text-xl': this.size === 'lg',
          'text-white bg-emerald-500 border-emerald-400 hover:bg-emerald-600': this.priority === 'primary',
          'bg-slate-100 border-slate-300 hover:bg-slate-300': this.priority === 'secondary',
        };
      },
    },
  };
</script>
