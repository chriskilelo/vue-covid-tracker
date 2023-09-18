<template>
    <select @change="onChange" v-model="selected" class="form-select mt-10 block w-full border border-green-700 p-3 rounded">
        <option value="0">Select Country</option>
        <option v-for="country in countries" :value="country.id" class="text-red-600">
            {{ country.country }}
        </option>
    </select>
</template>

<script>
export default {
    name: 'CountrySelect',
    props: [
        'countries'
    ],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onChange(){
            const countryData  = this.countries.find((item) => item.id === this.selected)
            this.$emit('get-country', countryData )
        }
    }
}
</script>