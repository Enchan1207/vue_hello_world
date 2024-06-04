<!-- クリッカー -->
<script setup lang="ts">
import { ref, defineProps } from 'vue';
import type { PropType } from 'vue';

// コンポーネントが内部で持つデータ
let counter = ref(0);

// 親コンポーネントから渡されるデータ (props)
const props = defineProps({
    label: { type: String as PropType<string>, required: true }
});
</script>

<template>
    <div id="clicker">
        <button @click="counter++">Button {{ props.label }}</button>
        <span>count: {{ counter }}</span>
    </div>
</template>

<style scoped>
#clicker {
    max-width: 200px;
    display: flex;
    justify-content: space-between;
}
</style>
