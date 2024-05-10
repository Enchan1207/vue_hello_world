<!-- ルートコンポーネント -->
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    data() {
        return {
            count: 0
        };
    }
});
</script>

<template>
    <h2>Button Clicker</h2>
    <div id="clicker">
        <button @click="count++">Click me!</button>
        <span>{{ count }}</span>
    </div>
</template>

<style scoped>
#clicker{
    max-width: 200px;
    display: flex;
    justify-content: space-between;
}
</style>
