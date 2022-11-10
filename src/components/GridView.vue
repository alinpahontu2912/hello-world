<script setup>
// eslint-disable-next-line
const props = defineProps({
    data: Array,
    columns: Array
})

</script>

<template>
    <table class="table">
        <thead>
            <tr>
                <!--eslint-disable-next-line -->
                <th v-for="key in columns">{{ key }}</th>
            </tr>
        </thead>
        <tbody>
            <!--eslint-disable-next-line -->
            <tr v-for="entry in data">
                <!--eslint-disable-next-line -->
                <td v-for="key in columns">
                    {{ entry[key] }}
                </td>
            </tr>
        </tbody>
    </table>
</template>
