<template>
  <li class="ingredients__item">
    <AppDrag
      :transfer-data="filling"
      :allow-drag="filling.count < MAX_COUNT_TYPE_INGREDIENT"
    >
      <span
        class="filling"
        :class="`filling--${filling.value}`"
      >{{
        filling.name
      }}</span>
    </AppDrag>
    <ItemCounter
      class="ingredients__counter"
      :value="filling.count"
      :max="MAX_COUNT_TYPE_INGREDIENT"
      @change="change"
    />
  </li>
</template>

<script>
import AppDrag from "@/common/components/AppDrag";
import { MAX_COUNT_TYPE_INGREDIENT } from "@/common/constants";
import { mapMutations } from "vuex";
import { UPDATE_INGREDIENT_COUNTER } from "@/store/mutation-types";

export default {
  name: "BuilderIngredientsItem",
  components: { AppDrag },
  props: {
    filling: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      MAX_COUNT_TYPE_INGREDIENT,
    };
  },
  methods: {
    ...mapMutations("Builder", {
      updateIngredientCounter: UPDATE_INGREDIENT_COUNTER,
    }),
    change(operation) {
      this.updateIngredientCounter({ ...this.filling, operation });
    },
  },
};
</script>
