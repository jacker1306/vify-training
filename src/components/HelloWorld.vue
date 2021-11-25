<template>
  <h1 class="my-10 text-3xl">FORM</h1>
  <div class="">
    <form action="" class="w-1/3 mx-auto">
      <div class="uppercase text-sm my-6 flex justify-between">
        <label for="firstname" class="">First Name</label>
        <input class="border-b w-3/4 outline-none" type="text" name="firstname" id="firstname" v-model="firstName">
      </div>
      <div class="uppercase text-sm my-6 flex justify-between">
        <label for="lastname" class="">Last Name</label>
        <input class="border-b w-3/4 outline-none" type="text" name="lastname" id="lastname"  v-model="lastName">
      </div>
      <div class="uppercase text-sm my-6 flex justify-between">
        <label for="address" class="">Address</label>
        <input class="border-b w-3/4 outline-none" type="text" name="address" id="address"  v-model="address">
      </div>
      <div class="uppercase text-sm my-6 flex justify-between">
        <label for="email" class="">Email</label>
        <input class="border-b w-3/4 outline-none" type="email" name="email" id="email"  v-model="email">
      </div>
      <div class="uppercase text-sm my-6 flex justify-between">
        <label for="phone" class="">Phone No</label>
        <input class="border-b w-3/4 outline-none" type="text" name="phone" id="phone"  v-model="phone">
      </div>
      <div class="">
        <input class="mx-2" type="radio" name="gender" id=""  v-model="gender" value="Male">Male
        <input class="mx-2" type="radio" name="gender" id=""  v-model="gender" value="Female">Female
        <input class="mx-2" type="radio" name="gender" id=""  v-model="gender" value="Gay">Gay Lọ
      </div>
      <div class="flex flex-col justify-between my-2">
        <div class="flex justify-between my-2">
          <label for="province" class="">Province</label>
          <select name="" id="" class="w-3/4 text-center border" v-model="province">
            <option v-for="province in provinces" :key="province.id" :value="province.name">{{province.name}}</option>
          </select>
        </div>
        <div class="flex justify-between my-2">
          <label for="province" class="">District</label>
          <select name="" id="" class="w-3/4 text-center border" v-model="dist">
            <option v-for="district in filterDistricts" :key="district.id" :value="district.name">{{district.name}}</option>
          </select>
        </div>
      </div>
      <button @click.prevent="showData = true" class="px-4 py-2 border border-black rounded-lg my-4 hover:scale-110 transform text-white bg-indigo-600">Show Table</button>
    </form>
    <Profile v-if="showData" :data="data" @closeTable="showData = false"></Profile>
  </div>
</template>

<script>
import { computed, ref } from '@vue/reactivity'
import Profile from './Profile.vue'


export default {
    name: "HelloWorld",
    setup() {
        const provinces = [{ id: 1, name: "Hà Nội" }, { id: 2, name: "TP. HCM" }];
        const districts = [
            { id: 1, province_id: 1, name: "Ba Đình" },
            { id: 2, province_id: 1, name: "Bắc Từ Liêm" },
            { id: 3, province_id: 1, name: "Cầu Giấy" },
            { id: 4, province_id: 1, name: "Đống Đa" },
            { id: 5, province_id: 1, name: "Hà Đông" },
            { id: 6, province_id: 1, name: "Hai Bà Trưng" },
            { id: 7, province_id: 1, name: "Hoàn Kiếm" },
            { id: 8, province_id: 1, name: "Hoàng Mai" },
            { id: 9, province_id: 1, name: "Long Biên" },
            { id: 10, province_id: 1, name: "Nam Từ Liêm" },
            { id: 11, province_id: 1, name: "Tây Hồ" },
            { id: 12, province_id: 1, name: "Thanh Xuân" },
            { id: 13, province_id: 2, name: "Bình Tân" },
            { id: 14, province_id: 2, name: "Bình Thạnh" },
            { id: 15, province_id: 2, name: "Gò Vấp" },
            { id: 16, province_id: 2, name: "Phú Nhuận" },
            { id: 17, province_id: 2, name: "Tân Bình" },
            { id: 18, province_id: 2, name: "Tân Phú" },
            { id: 19, province_id: 2, name: "Thủ Đức" },
            { id: 20, province_id: 2, name: "Bình Chánh" },
            { id: 21, province_id: 2, name: "Cần Giờ" },
            { id: 22, province_id: 2, name: "Củ Chi" },
            { id: 23, province_id: 2, name: "Hóc Môn" },
            { id: 24, province_id: 2, name: "Nhà Bè" },
        ];
        const firstName = ref();
        const lastName = ref();
        const address = ref();
        const phone = ref();
        const email = ref();
        const gender = ref();
        const province = ref();
        const provinceID = ref();
        const dist = ref();
        const showData = ref(false)

        const data = {firstName: firstName, lastName: lastName, address: address, phone: phone, email: email, gender: gender, province: province, dist: dist}

        const districtData = () => {
            for (let i = 0; i < provinces.length; i++) {
                if (provinces[i].name === province.value) {
                    provinceID.value = provinces[i].id;
                }
            }
            return districts.filter((dist) => dist.province_id === provinceID.value);
        };
        const filterDistricts = computed(() => districtData());
        return { provinces, districts, firstName, lastName, address, phone, email, gender, province, provinceID, dist, filterDistricts, showData, data };
    },
    components: { Profile, }
}
</script>

<style>

</style>