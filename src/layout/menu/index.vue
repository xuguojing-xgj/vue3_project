<script lang="ts" setup>
import MyTree from '../../components/Tree/index.vue'
import { TreeListType } from '../../components/types/index'
import { reactive } from 'vue'


/**
 * 类型
 * reactive(target: TreeList[]): 
 * { name?: string | undefined; 
 *   icon?: string | undefined; 
 *   children?: ...[] | [] | undefined; 
 * }[]
 */
const dataTree = reactive<TreeListType[]>([
    {
        name: 'no.1',
        children: [{
            name: 'no.1-1',
            children: [{
                name: 'no.1-1-1',
            }]
        }]
    },
    {
        name: 'no.2',
        children: [{
            name: 'no.2-1   ',
        }]
    },
    {
        name: 'no.3'
    },
    {
        name: 'no.4',
        children: []
    },
    {
        name: 'no.5',
        children: [{
            name: "no.5-1",
            children: [{
                name: 'no.5-1-1'
            }]
        }]
    }
])

/**
 * 接收子组件传递 方法 getTreeData
 */
const getFatherTreeFn = (item: TreeListType) => {
    console.log('父组件log', item);
}
</script>


<template>
    <div>
        <div class="menu">
            菜单区域
            <MyTree @on-son-click="getFatherTreeFn" :SonTreeData="dataTree"></MyTree>
        </div>

    </div>
</template>



<style scoped lang="less">
@border: #ccc;

.menu {
    width: 300px;
    border-right: 1px solid @border;
}
</style>