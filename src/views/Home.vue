<template>
    <div>
        <bounce-loader
        v-bind:loading="isLoading"
        v-bind:color="'#68d391'"
        v-bind:size="100"
        ></bounce-loader>
        <px-assets-table v-if="isLoading == false" v-bind:assets = "assets"></px-assets-table>
    </div>
</template>

<script>
import PxAssetsTable from '@/components/PxAssetsTable'
import api from '@/api'

export default {
    name: 'Home',
    components: {
        PxAssetsTable
    },
    data() {
        return {
            isLoading: false,
            assets: []
        }
    },
    created() {
        this.isLoading = true
        api.getAssets()
        .then(assets => (this.assets = assets))
        .catch(error => console.log(error))
        .finally(() => this.isLoading = false)
    }

}
</script>

