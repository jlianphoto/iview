<template>
    <div>
        <button @click="addData">add data</button>
        <button @click="removeData">remove</button>
        <Table border draggable fixedHeadTop transition :columns="columns5" :data="data5"></Table>
    </div>
</template>
<script>
    import etable from '../components/table.vue';
    import test from '../components/test.vue';
    export default {
        data () {
            return {
                columns5: [
                    {
                        type: 'expand',
                        render: (h) => {
                            return h(etable);
                        },
                        width: 50
                    },
                    {
                        title: '日期',
                        key: 'date',
                        sortable: true
                    },
                    {
                        title: '姓名',
                        key: 'name'
                    },
                    {
                        title: '年龄',
                        key: 'age',
                        sortable: true
                    },
                    {
                        title: '地址',
                        key: 'address'
                    },
                    {
                        title: '操作',
                        key: 'name',
                        render: (h, params) => {
                            return h(test, {
                                props: {
                                    row: params.row
                                }
                            });
                        }
                    }
                ],
                data5: [
                    {
                        name: '小明',
                        age: 18,
                        address: '北京市朝阳区芍药居',
                        date: '2016-10-03',
                        id : "1"
                    },
                    {
                        name: '张小刚',
                        age: 25,
                        address: '北京市海淀区西二旗',
                        date: '2016-10-01',
                        id : "2"
                    },
                    {
                        name: '李小红',
                        age: 30,
                        address: '上海市浦东新区世纪大道',
                        date: '2016-10-02',
                        id : "3"
                    },
                    {
                        name: '周小伟',
                        age: 26,
                        address: '深圳市南山区深南大道',
                        date: '2016-10-04',
                        id : "4"
                    },
                ]
            }
        },
        methods:{
            addData(){
                let data = {
                    name: '垃圾'+new Date().getTime(),
                    age: 18,
                    address: '北京市朝阳区芍药居',
                    date: '2016-10-03'
                }
                function randomnum(smin, smax) {// 获取2个值之间的随机数
                    var Range = smax - smin;
                    var Rand = Math.random();
                    return (smin + Math.round(Rand * Range));
                }
                data['id'] = randomnum(6, 10000);
                this.data5.splice(0, 0, data)
                
            },
            removeData(){
                this.data5.splice(this.data5.length-1, 1)
            }

        }
    }
</script>
