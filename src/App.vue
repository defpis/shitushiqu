<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
    mpType: 'app',
    onLaunch() {
        console.log('App Launch')
        uni.switchTab({
            url: '/pages/about/about'
        });
    },
    onShow() {
        console.log('App Show')
    },
    onHide() {
        console.log('App Hide')
    }
});
</script>

<style lang="scss">
page {
    height: 100%;
}

.container {
    display: flex;
    flex-direction: column;
    height: 100%;
    box-sizing: border-box;
    background-color: #F9F9F9;
    overflow-x: hidden;
    overflow-y: auto;
}
</style>
