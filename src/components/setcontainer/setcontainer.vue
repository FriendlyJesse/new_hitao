<template>
    <div class="setting">
        <header v-if="titleShow" class="mui-bar mui-bar-nav">
            <a class="mui-action-back mui-icon mui-icon-left-nav mui-pull-left"></a>
            <h1 class="mui-title animated" :class="transitionTitle" style="position: absolute">{{title}}</h1>
        </header>
        <transition :name="transitionName">
            <router-view class="child-child-view"></router-view>
        </transition>
    </div>
</template>

<script>
export default
{
    data()
    {
        return {
            title: '设置',
            transitionName: '',
            transitionTitle: '',
            titleShow: true
        }
    },
    watch:
    {
        '$route' (to, from)
        {
            //设置标题
            let query = to.query;
            this.title = typeof query.title != 'undefined' ? query.title : '设置';
            this.titleShow = query.title == 'null' ? false : true;

            //监听路由的路径，可以通过不同的路径去选择不同的切换效果
            const toDepth = to.path.split('/').length,
                  fromDepth = from.path.split('/').length;
            this.transitionName = toDepth < fromDepth ? 'slide-right' : 'slide-left';
            this.transitionTitle = toDepth < fromDepth ? 'flipInY' : 'flipInX';
        }
    }
}
</script>

<style scoped lang="scss" rel="stylesheet/scss">
.child-child-view
{
    transition: all 0.3s cubic-bezier(0.55, 0, 0.1, 1);
}
.mui-bar-nav
{
    position: relative;
}
</style>