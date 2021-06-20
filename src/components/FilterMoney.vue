<template>
    <div class="filter">
        {{ tongTien | dauChamPhanTach}}
        <button @click="tongTien += 2000000">Click increase money</button>
    </div>
</template>

<script>
export default {
    name: 'input',
    data() {
        return {
            tongTien: 1000000
        }
    },
    filters: {
        dauChamPhanTach: (soTien) => {
            return soTien.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,');
        }
    }
}
</script>

<style scoped>

</style>