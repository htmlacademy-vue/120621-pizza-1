<template>
  <div
    :draggable="allowDrag"
    @dragstart.self="onDrag"
    @dragover.prevent
    @dragenter.prevent
  >
    <slot />
  </div>
</template>

<script>
import { DATA_TRANSFER_PAYLOAD, EFFECT_MOVE } from "@/common/constants";

export default {
  name: "AppDrag",
  props: {
    transferData: {
      type: Object,
      required: true,
    },
    allowDrag: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    onDrag({ dataTransfer }) {
      dataTransfer.effectAllowed = EFFECT_MOVE;
      dataTransfer.dropEffect = EFFECT_MOVE;
      dataTransfer.setData(
        DATA_TRANSFER_PAYLOAD,
        JSON.stringify(this.transferData)
      );
    },
  },
};
</script>
