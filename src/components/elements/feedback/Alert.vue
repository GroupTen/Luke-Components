<template>
  <div
    :class="[
      'transition transform fixed z-30 bottom-0 inset-x-0 pb-2 sm:pb-5 opacity-0 scale-100 translate-y-0 ease-out duration-500',
      { 'opacity-100': visible },
      { hidden: !visible },
    ]"
  >
    <div
      :class="[
        'rounded-md p-4 max-w-screen-sm mx-auto',
        { 'bg-red-50': type === 'error', 'bg-green-200': type === 'success' },
      ]"
    >
      <div class="flex">
        <div class="flex-shrink-0">
          <svg
            v-if="type === 'error'"
            class="h-5 w-5 text-red-400"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z"
              clip-rule="evenodd"
            />
          </svg>
          <svg
            v-if="type === 'success'"
            class="h-5 w-5 text-green-400"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
              clip-rule="evenodd"
            />
          </svg>
        </div>
        <div class="ml-3">
          <h3
            :class="[
              'text-sm leading-5 font-medium ',
              {
                'text-red-800': type === 'error',
                'text-green-800': type === 'success',
              },
            ]"
          >
            {{ message }}
          </h3>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      type: '',
      message: '',
      visible: false,
    }
  },
  methods: {
    showAlert(type, message) {
      const self = this
      self.type = type
      self.message = message
      self.visible = true
      setTimeout(function () {
        self.visible = false
      }, 4000)
    },
  },
}
</script>
