<template>
  <div class="user">
    <picture>
      <source
        type="image/webp"
        :srcset="`${urlWithoutExtension}@2x.webp 1x, ${urlWithoutExtension}@4x.webp 2x`"
      >
      <img
        :src="`${urlWithoutExtension}@2x.jpg`"
        :srcset="`${urlWithoutExtension}@4x.jpg`"
        :alt="user.name"
        width="72"
        height="72"
      >
    </picture>
    <div class="user__name">
      <span>{{ user.name }}</span>
    </div>
    <p class="user__phone">
      Контактный телефон: <span>{{ user.phone }}</span>
    </p>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "ProfileUserInfo",
  computed: {
    ...mapState("User", ["user"]),
    urlWithoutExtension() {
      return this.user?.avatar?.replace(/\.jpg/, "");
    },
  },
};
</script>
