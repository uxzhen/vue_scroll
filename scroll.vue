<template>
    <div>
        {{arr}}
        <div v-for="(item,index) in arr" :key="index" class="aa">{{item}}</div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            arr: [1],
        };
    },
    mounted() {
        window.addEventListener("scroll", this.gundong);
    },
    methods: {
        gundong() {
            // 是否到顶
            var dis =
                document.documentElement.scrollTop ||
                window.pageYOffset ||
                document.body.scrollTop;
            if (dis < 200) {
                console.log("到顶了");
            }
            //变量scrollTop是滚动条滚动时，距离顶部的距离
            var scrollTop =
                document.documentElement.scrollTop || document.body.scrollTop;
            //变量windowHeight是可视区的高度
            var windowHeight =
                document.documentElement.clientHeight ||
                document.body.clientHeight;
            //变量scrollHeight是滚动条的总高度
            var scrollHeight =
                document.documentElement.scrollHeight ||
                document.body.scrollHeight;
            //滚动条到底部的条件
            if (scrollTop + windowHeight == scrollHeight) {
                //写后台加载数据的函数
                console.log(
                    "距顶部" +
                        scrollTop +
                        "可视区高度" +
                        windowHeight +
                        "滚动条总高度" +
                        scrollHeight
                );
                this.arr.push("1");
                console.log(this.arr);
            }
        },
    },
    destroyed() {
        window.removeEventListener("scroll", this.gundong);
    },
};
</script>

<style scoped>
.aa {
    height: 150vh;
    width: 7.5rem;
    /* border: 2px solid #fff; */
}
</style>
