<template>
  <main class="layout">
    <div class="layout__content">
      <ProfileTitle />
      <ProfileUserInfo />
      <ProfileAddress
        v-for="address in addresses"
        :key="address.id"
        :address="address"
      />
      <ProfileEditAddress v-if="expandAddressForm" />
      <ProfileAddAddress />
    </div>
  </main>
</template>

<script>
import ProfileUserInfo from "@/modules/profile/ProfileUserInfo";
import ProfileAddress from "@/modules/profile/ProfileAddress";
import ProfileEditAddress from "@/modules/profile/ProfileEditAddress";
import ProfileTitle from "@/modules/profile/ProfileTitle";
import ProfileAddAddress from "@/modules/profile/ProfileAddAddress";
import { mapState } from "vuex";
import { addressList } from "@/common/mixins";
export default {
  name: "Profile",
  components: {
    ProfileAddAddress,
    ProfileTitle,
    ProfileEditAddress,
    ProfileAddress,
    ProfileUserInfo,
  },
  mixins: [addressList],
  computed: {
    ...mapState("Addresses", ["expandAddressForm", "addresses"]),
  },
};
</script>
