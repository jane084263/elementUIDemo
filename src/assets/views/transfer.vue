<template>
    <el-container>
        <el-header class="text-center">
            <h3>this is transfer 穿梭框 Demo</h3>
        </el-header>
        <el-main>
            <div class="block">
                <span>穿梭框</span>
                <el-transfer v-model="value1" :data="data"></el-transfer>
            </div>
            <div class="block">
                <span>带搜索的穿梭框</span>
                <el-transfer filterable :filter-method="filterMethod" filter-placeholder="请输入城市拼音" v-model="value2" :data="data2">
                </el-transfer>
            </div>
        </el-main>
    </el-container>
</template>
<script>
    export default {
        data() {
            const generateData = _ => {
                const data = [];
                for (let i = 1; i <= 15; i++) {
                    data.push({
                        key: i,
                        label: `备选项 ${ i }`,
                        disabled: i % 4 === 0
                    });
                }
                return data;
            };
            const generateData2 = _ => {
                const data = [];
                const cities = ['上海', '北京', '广州', '深圳', '南京', '西安', '成都'];
                const pinyin = ['shanghai', 'beijing', 'guangzhou', 'shenzhen', 'nanjing', 'xian', 'chengdu'];
                cities.forEach((city, index) => {
                    data.push({
                        label: city,
                        key: index,
                        pinyin: pinyin[index]
                    });
                });
                return data;
            };
            return {
                data: generateData(),
                value1: [1, 4],
                data2: generateData2(),
                value2: [],
                filterMethod(query, item) {
                    return item.pinyin.indexOf(query) > -1;
                }
            };
        }
    };
</script>
<style lang="scss">

</style>