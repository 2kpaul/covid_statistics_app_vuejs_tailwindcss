<template>
    <div>
        <select v-model="selected" @change="changeData()">
            <option value="">Select Country</option>
            <option v-for="item in dataCountries" :value="item.ID">{{item.Country}}</option>
        </select>
        <button
            v-if="resetButton"
            class="bg-indigo-400 text-white rounded p-2 ml-5 focus:outline-none hover:bg-indigo-500"
            @click="$emit('clear-select')"
            >
            reset
        </button>
    </div>
</template>

<script>
export default {
    props: ['dataCountries', 'resetButton'],
    data() {
        return {
            selected: ''
        }
    },
    methods: {
        changeData() {
            const country = this.dataCountries.find((item) => item.ID === this.selected)
            this.$emit('get-country', country);
        }
    },
}
</script>