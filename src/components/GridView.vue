<script setup>
// eslint-disable-next-line
const props = defineProps({
    data: Array,
    columns: Array
})

function capitalize(str) {
    return str.charAt(0).toUpperCase() + str.slice(1).toLowerCase()
}

</script>

<template>
    <div>
        <table class="table gridView">
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
                        {{ capitalize(entry[key]) }}
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<style>
#gridView {
    width: "85vw";
    padding: 3em;

}
</style>