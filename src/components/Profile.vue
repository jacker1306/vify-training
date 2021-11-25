<template>
    <div class="fixed top-0 right-0 left-0 bottom-0 bg-black bg-opacity-50 flex flex-col justify-center items-center" v-if="show" @click.self="close">
        <!-- <span class="p-2 bg-red-500 text-white cursor-pointer rounded-md hover:bg-black" @click="close">X</span> -->
        <div class="w-1/3 mx-auto">
            <table class="w-full mt-3 border border-collapse bg-white">
                <thead>
                    <tr>
                        <th class="border w-1/4">Item</th>
                        <th class="border">Value</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="border">First Name</td>
                        <td class="border">{{data.firstName.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Last Name</td>
                        <td class="border">{{data.lastName.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Phone No</td>
                        <td class="border">{{data.phone.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Email</td>
                        <td class="border">{{data.email.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Address</td>
                        <td class="border">{{data.address.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Gender</td>
                        <td class="border">{{data.gender.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">Province</td>
                        <td class="border">{{data.province.value}}</td>
                    </tr>
                    <tr>
                        <td class="border">District</td>
                        <td class="border">{{data.dist.value}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
    props: ['data'],
    setup(props, context) {
        const show = ref(true)
        const close = () => {
            show.value = false
            context.emit('closeTable', false)
        }
        return {show, close}
    }
}
</script>

<style>

</style>