<template>
    <div>
        <h3 class="text-xl font-bold">{{ title }}</h3>
        <span>{{ formatedDate }}</span>
    </div>
</template>

<script>
import dayjs from 'dayjs';

export default {
    name: 'StatsTitle',
    props: ['title', 'date'],
    computed: {
        formatedDate() {
            return dayjs(this.date).format('MMMM D YYYY');
        }
    },
}
</script>