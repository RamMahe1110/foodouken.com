<template>
  <div
    class="w-full text-center my-4 flex sticky lg:relative inset-x-0 bottom-0 z-10"
  >
    <Button
      title="◄ Back"
      :width="hideNext ? 'flex-grow' : 'w-1/3'"
      :backgroundColor="'bg-footer'"
      :fontSize="'text-sm'"
      :fontWeight="'font-semibold'"
      :textAlign="'text-left'"
      :textTransform="'uppercase'"
      :paddingLeft="'px-4'"
      :paddingRight="'py-4'"
      :borderRadius="'rounded-none'"
      @clicked="$emit('previousStep')"
      v-if="page != 1"
    />
    <Button
      :title="nextStepText"
      :width="'flex-grow'"
      :backgroundColor="'bg-button'"
      :fontSize="'text-sm'"
      :fontWeight="'font-semibold'"
      :textAlign="'text-right'"
      :textTransform="'uppercase'"
      :paddingLeft="'px-4'"
      :paddingRight="'py-4'"
      :borderRadius="'rounded-none'"
      @clicked="$emit('nextStep')"
      v-if="!hideNext"
    />
  </div>
</template>

<script>
import Button from '@/components/Button.vue';
import { mapGetters } from 'vuex';

export default {
  name: 'CheckoutNavBar',
  components: {
    Button
  },
  props: {
    nextStepText: {
      type: String
    },
    hideNext: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    ...mapGetters('form', ['page'])
  }
};
</script>
