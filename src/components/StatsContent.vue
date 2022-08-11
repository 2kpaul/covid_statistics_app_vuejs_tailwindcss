<template>
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 my-6">
        <div class="bg-indigo-300 p-10 text-center shadow-lg rounded-lg">
            <h3 class="text-xl font-bold">Cases</h3>
            <div>
                <span class="font-bold">New: </span> {{ formatNumber(data.NewConfirmed) }}
            </div>
            <div>
                <span class="font-bold">Total: </span> {{ formatNumber(data.TotalConfirmed) }}
            </div>
        </div>
        <div class="bg-indigo-500 p-10 text-center shadow-lg rounded-lg">
            <h3 class="text-xl font-bold">Deaths</h3>
            <div>
                <span class="font-bold">New: </span> {{ formatNumber(data.NewDeaths) }}
            </div>
            <div>
                <span class="font-bold">Total: </span> {{ formatNumber(data.TotalDeaths) }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['data'],
    methods: {
        formatNumber(nr) {
            return nr.toString()
            .replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        } 
    },
}
</script>