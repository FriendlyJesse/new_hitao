<template>
    <div class="user">
        <div class="user__container">
            <header class="user__info">
                <div class="user__icon">
                    <router-link to="setting" tag="i" class="iconfont icon-shezhi" append></router-link>
                    <i class="iconfont icon-xinxi"></i>
                </div>
                <figure class="user__content">
                    <img class="user__avatar" v-lazy="'http://hitao.dev.onebound.cn/' + userInfo.touxiang" />
                    <figcaption class="user__detailed">
                        <h4 class="user__name">{{userInfo.uname}}</h4>
                        <div class="user__level">
                            会员等级 <v-star :size="4" :score="Number(userInfo.level)"></v-star>
                        </div>
                    </figcaption>
                    <router-link to="checkin" tag="div" append>
                        <v-checkin></v-checkin>
                    </router-link>
                </figure>
            </header>
            <section class="data elastic_module">
                <h4 class="elastic_module__title">
                    <span>代购订单</span>
                    <router-link to="order" tag="span" class="elastic_module__aside" append>
                        全部<i class="iconfont icon-right"></i>
                    </router-link>
                </h4>
                <div class="elastic_module__content">
                    <router-link :to="{path: 'order', query: {modules: 'unpaid'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-gerenzhongxindingdandaifukuan"></i>
                        <figcaption class="elastic_module__description">
                            待付款
                        </figcaption>
                    </router-link>
                    <router-link :to="{path: 'order', query: {modules: 'arrived'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-icon2"></i>
                        <figcaption class="elastic_module__description">
                            已到库
                        </figcaption>
                    </router-link>
                    <router-link :to="{path: 'order', query: {modules: 'Ordered'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-1huojian"></i>
                        <figcaption class="elastic_module__description">
                            已邮寄
                        </figcaption>
                    </router-link>
                    <router-link :to="{path: 'order', query: {modules: 'pending'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-gerenzhongxindingdandaishouhuo"></i>
                        <figcaption class="elastic_module__description">
                            处理中
                        </figcaption>
                    </router-link>
                </div>
            </section>
            <section class="data elastic_module">
                <h4 class="elastic_module__title">
                    <span>转运订单</span>
                </h4>
                <div class="elastic_module__content">
                    <router-link :to="{path: 'waybill', query: {modules: 'mypackage'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-baoguoxia"></i>
                        <figcaption class="elastic_module__description">
                            我的包裹
                        </figcaption>
                    </router-link>
                    <router-link :to="{path: 'waybill', query: {modules: 'submit'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-liebiao1"></i>
                        <figcaption class="elastic_module__description">
                            提交代购订单
                        </figcaption>
                    </router-link>
                    <router-link :to="{path: 'waybill', query: {modules: 'other'}}" tag="figure" class="elastic_module__wrap" append>
                        <i class="iconfont icon-zongheyewudingdan"></i>
                        <figcaption class="elastic_module__description">
                            其他订单
                        </figcaption>
                    </router-link>
                </div>
            </section>
            <section class="assets elastic_module">
                <h4 class="elastic_module__title">
                    <span>我的资产</span>
                </h4>
                <div class="elastic_module__content">
                    <router-link :to="{path: 'wallet', query: {money: userInfo.money}}" tag="figure" class="elastic_module__wrap" append>
                        <figcaption class="elastic_module__description">
                            ￥{{userInfo.money}}<br />
                            当前余额
                        </figcaption>
                    </router-link>
                    <router-link to="integral" tag="figure" class="elastic_module__wrap" append>
                        <figcaption class="elastic_module__description">
                            {{userInfo.score}}<br />
                            会员积分
                        </figcaption>
                    </router-link>
                    <figure class="elastic_module__wrap">
                        <figcaption class="elastic_module__description">
                            ￥{{userInfo.commission}}<br />
                            佣金
                        </figcaption>
                    </figure>
                </div>
            </section>
            <section class="grid elastic_module">
                <div class="elastic_module__content">
                    <router-link to="coupon" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            优惠券
                        </figcaption>
                    </router-link>
                    <router-link to="collection" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            我的收藏
                        </figcaption>
                    </router-link>
                    <router-link to="alipay" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            支付宝代充
                        </figcaption>
                    </router-link>
                    <router-link to="notice" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            通知
                        </figcaption>
                    </router-link>
                    <router-link to="invite" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            邀请好友
                        </figcaption>
                    </router-link>
                    <figure class="elastic_module__wrap">
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            在线客服
                        </figcaption>
                    </figure>
                    <router-link to="help" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            帮助中心
                        </figcaption>
                    </router-link>
                    <router-link to="warehouse" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            仓库地址
                        </figcaption>
                    </router-link>
                    <router-link to="feedback" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            意见反馈
                        </figcaption>
                    </router-link>
                    <router-link to="address" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            地址管理
                        </figcaption>
                    </router-link>
                    <router-link to="calculation" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            运费试算
                        </figcaption>
                    </router-link>
                    <router-link to="user_info" class="elastic_module__wrap" append>
                        <div class="icon"></div>
                        <figcaption class="elastic_module__description">
                            我的信息
                        </figcaption>
                    </router-link>
                </div>
            </section>
        </div>
        <v-footer></v-footer>
    </div>
</template>

<script>
import vFooter from '@/components/footer/footer';
import vCheckin from '@/components/checkin/checkin';
import vStar from '@/components/star/star';
import {postJSON} from '@/assets/js/common';  //公共函数库

export default
{
    components:
    {
        vFooter,
        vCheckin,
        vStar
    },
    data()
    {
        return {
            userInfo: {}
        }
    },
    created()
    {
        this.getUser();
    },
    methods:
    {
        getUser()
        {
            let userId = localStorage.getItem('userId');
            postJSON(this.API.USER_INDEX, {userId}, data => this.userInfo = data.userInfo)
        }
    }
}
</script>

<style scoped lang="scss" rel="stylesheet/scss">
@import "../../assets/scss/mixin";
$animal-list:
(
    "(1)": "mine_tool_coupon",
    "(2)": "mine_tool_collect",
    "(3)": "mine_tool_alipay",
    "(4)": "mine_tool_notice",
    "(5)": "mine_tool_invite",
    "(6)": "mine_tool_online",
    "(7)": "mine_tool_helpcenter",
    "(8)": "mine_tool_house",
    "(9)": "mine_tool_feedback",
    "(10)": "mine_tool_address",
    "(11)": "mine_tool_freight",
    "(12)": "mine_tool_info"
);
.user__container
{
    position: absolute;
    top: 0;
    bottom: 50px;
    width: 100%;
    overflow: auto;
}
.elastic_module
{
    background: #fff;
    margin-bottom: 10px;

    &__title
    {
        display: flex;
        justify-content: space-between;
        font-size: 16px;
        margin: 0;
        padding: 14px 12px;
        font-weight: normal;
        border-bottom: 1px solid #efefef;
    }
    &__aside
    {
        font-size: 13px;
        color: #9c9c9c;

        .iconfont
        {
            font-size: 15px;
            vertical-align: top;
        }
    }
    &__content
    {
        display: flex;
    }
    &__wrap
    {
        flex: auto;
        text-align: center;
        padding: 10px;

        .iconfont
        {
            font-size: 21px;
        }
    }
    &__description
    {
        color: #666666;
        font-size: 12px;
    }
}
.user
{
    display: flex;
    flex-direction: column;
    background: #efeff4;

    &__info
    {
        height: 140px;
        padding: 10px 12px;
        position: relative;
        @include bg-img('./mine_bg');
    }
    &__icon
    {
        display: flex;
        justify-content: space-between;

        .iconfont
        {
            font-size: 21px;
            color: #fff;
        }
    }
    &__content
    {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        margin-top: -13.5px;
    }
    &__avatar
    {
        width: 65px;
        height: 65px;
        border-radius: 50%;
        border: 2px solid #f5b9c2;
    }
    &__detailed
    {
        text-align: center;
    }
    &__name
    {
        font-weight: normal;
        font-size: 16px;
        color: #fff;
        margin: 5px 0;
    }
    &__level
    {
        color: #ffef68;
        font-size: 12px;
    }
    .data
    {

    }
    .assets
    {

    }
    .grid
    {
        .elastic_module
        {
            &__content
            {
                flex-wrap: wrap;
                align-content: space-between;
            }
            &__wrap
            {
                flex: 1 1 25%;
                border: 1px solid #efefef;
                border-right: none;
                border-bottom: none;
                padding: 0;
                height: 88px;
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;

                .icon
                {
                    width: 26px;
                    height: 26px;
                    margin-bottom: 10px;
                }
            }
            @each $index, $animal in $animal-list
            {
                &__wrap:nth-child#{$index}
                {
                    .icon
                    {
                        @include bg-img($animal);
                    }
                }
            }
        }
    }
}
</style>