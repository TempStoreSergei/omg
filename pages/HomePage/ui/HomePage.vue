<script setup lang="ts">
import {Layout, LayoutContent} from 'ant-design-vue';
import {ref, computed} from 'vue';

const timeInSeconds = ref(0);

const randomNumber = computed(() => {
  timeInSeconds.value = Math.floor(Math.random() * 10000);
  return timeInSeconds.value;
});

setInterval(() => {
  timeInSeconds.value++;
}, 1000);
const list = Array.from({ length: 1000 }, (_, index) => ({
  id: `image-${index + 1}`,
}));

</script>

<template>
  <Layout class="wrapper">
    <LayoutContent class="content">
        <RecycleScroller
            class="scroller"
            :items="list"
            :item-size="100"
            :grid-items="12"
        >
          <template #default="{ item, index }">
            <span class="item">
               {{ randomNumber }}
            </span>
          </template>
        </RecycleScroller>
    </LayoutContent>
  </Layout>

</template>

<style scoped lang="scss">



.wrapper,
.scroller {
  height: 100%;
}
.scroller {
  flex: 1;
}

.scroller :deep(.hover) span {
  transition: transform ease 0.3s;
  transform: scale(.8);
}

.item {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  height: 100%;
  border: 1px solid black;
  background-color: transparent;
  color: black;
  border-radius: 12px;
}


</style>