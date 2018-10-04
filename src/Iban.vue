<template>
  <stripe-element
    ref='element'
    type='iban'
    :stripe='stripe'
    :value='value'
    :options='defaultOptions'
    @blur='$emit("blur")'
    @focus='$emit("focus")'
    @change='$emit("change", $event)'
  />
</template>

<script>
import props from './props'
import StripeElement from './StripeElement'

export default {
  props,
  computed: {
    defaultOptions() {
      return Object.assign({ supportedCountries: ['SEPA'] }, this.options || {})
    }
  },
  components: { StripeElement },
  methods: {
    blur () { this.$refs.element.blur() },
    clear () { this.$refs.element.clear() },
    focus () { this.$refs.element.focus() },
    update (options) { this.$refs.element.update(options) }
  }
}
</script>
