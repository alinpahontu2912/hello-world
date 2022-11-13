<script setup>
import { ref, computed } from 'vue'
// eslint-disable-next-line
const props = defineProps({
    data: Array,
    columns: Array
})

const sortKey = ref('')
const sortOrders = ref(
    props.columns.reduce((o, key) => ((o[key] = 1), o), {})
)

console.log(props.columns.reduce((o, key) => ((o[key] = 1), o), {}))

function capitalize(str) {
    return str.charAt(0).toUpperCase() + str.slice(1).toLowerCase()
}

function sortBy(key) {
    sortKey.value = key
    sortOrders.value[key] *= -1
}

const filteredData = computed(() => {
  let { data } = props
  const key = sortKey.value
  if (key) {
    const order = sortOrders.value[key]
    data = data.slice().sort((a, b) => {
      a = a[key]
      b = b[key]
      return (a === b ? 0 : a > b ? 1 : -1) * order
    })
  }
  return data
})

</script>

<template>
    <div>
        <table class="table gridView">
            <thead>
                <tr>
                    <!--eslint-disable-next-line -->
                    <th v-for="key in columns" @click="sortBy(key)">{{ key }}</th>
                </tr>
                <!--eslint-disable-next-line -->
                <span class="arrow">

                </span>
            </thead>
            <tbody>
                <!--eslint-disable-next-line -->
                <tr v-for="entry in filteredData">
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

#arrow {
    display: inline-block;
    vertical-align: middle;
    width: 0;
    height: 0;
    margin-left: 5px;
    opacity: 0.66;
}
</style>