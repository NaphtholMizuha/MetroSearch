<template>
    <a-tabs v-model:activeKey="activeKey">
          <a-tab-pane key="1" tab="时间最短">

          </a-tab-pane>
          <a-tab-pane key="2" tab="换乘最少">

          </a-tab-pane>
        </a-tabs>
</template>

<script>
export default {
    props: ['bestTime', 'leastTransfer'],
    data: function() {
        return {
            activeKey: '1'
        }
    }
}
</script>