<template>
    <button
        @click="$emit('click')"
        class="fcw-button"
        :disabled="disabled || loading"
        :class="[
            type ? 'fcw-button--' + type : '',
            size ? 'fcw-button--' + size : '',
            plain?'fcw-' + type +'-plain':'',
            {
                'fcw-is-disabled': disabled,
            }
        ]"
    >
        <i class="iconfont gf-loading" v-if="loading"></i>
        <i class="iconfont fcw-button-icon" :class="icon" v-if="icon && !loading"></i>
        <slot></slot>
    </button>
</template>

<script>
export default {
    name:'fcw-button',
    props:{
        //按钮类型
        type:String,
        //是否禁用
        disabled:Boolean,
        //按钮大小 mini超小 small小型 medium中等
        size:String,
        //加载loading
        loading:Boolean,
        //icon
        icon:String,
        //是否朴素按钮
        plain:Boolean
    }
}
</script>

<style scoped lang="less">
    .fcw-button-icon{margin-right: 5px; padding: 0 5px;}
    .gf-loading{
        color: #fff;
        animation: rotate 2s linear infinite;
        font-size: 12px;
        transition: 0.5s;
        display: inline-block;
        margin-right: 5px;
    }
    .fcw-button{
        text-decoration: none;
        color: #606266;
        display: inline-block;
        position: relative;
        border-radius: 4px;
        outline: none;
        cursor: pointer;
        margin:5px 0px;
        white-space: nowrap;
        display: flex; justify-content: center; align-items: center;
        background: #fff;
        &:hover{
            color: #409eff;
            background-color: #ecf5ff;
            border-color: #c6e2ff;
        }
        border: 1px solid #004b9a;
        border-bottom-color: #003f81;
        -webkit-transition: 0.1s linear all;
        -moz-transition: 0.1s linear all;
        transition: 0.1s linear all;
        border-color: #0064cd #0064cd #003f81;
        border-color: rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.25);
        box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
        font-size: 14px;
        padding: 3px 10px;
    }
    .fcw-button:active{background:	#F5F5F5;}
    .fcw-button--danger{
        color:#fff;
        background: #f56c6c;
        background: -webkit-gradient(linear, 0 0, 0 100%, from(#f56c6c), to(#f56c6c));
        background: -webkit-linear-gradient(#f56c6c 0%, #f56c6c 100%);
        background: -moz-linear-gradient(#f56c6c 0%, #f56c6c 100%);
        background: -o-linear-gradient(#f56c6c 0%, #f56c6c 100%);
        background: linear-gradient(#f56c6c 0%, #f56c6c 100%);
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#fa5a5a', endColorstr='#e85151', GradientType=0 );
        &:active {background: rgba(250,90,90,0.7)}
        &:hover{ color: #fff; border-color: #f56c6c;}
    }
    .fcw-button--primary {
        color:#fff;
        background: #409eff;
        background: -webkit-gradient(linear, 0 0, 0 100%, from(#409eff), to(#409eff));
        background: -webkit-linear-gradient(#409eff 0%, #409eff 100%);
        background: -moz-linear-gradient(#409eff 0%, #409eff 100%);
        background: -o-linear-gradient(#409eff 0%, #409eff 100%);
        background: linear-gradient(#409eff 0%, #409eff 100%);
        filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#1bbcc2', endColorstr='#18a3a8', GradientType=0);
        &:active {background: rgba(64,158,255,0.7) }
        &:hover{ color: #fff; border-color: #409eff;}
    }
    .fcw-button--success{
        color:#fff;
        background: #67c23a;
        background: -moz-linear-gradient(top, #67c23a 0%, #67c23a 100%);
        background: -webkit-gradient(left top, left bottom, color-stop(0%, #67c23a), color-stop(100%, #67c23a));
        background: -webkit-linear-gradient(top, #67c23a 0%, #67c23a 100%);
        background: -o-linear-gradient(top, #67c23a 0%, #67c23a 100%);
        background: -ms-linear-gradient(top, #67c23a 0%, #67c23a 100%);
        background: linear-gradient(to bottom, #67c23a 0%, #67c23a 100%);
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#82c8a0', endColorstr='#82c79e', GradientType=0 );
        &:active {background:rgba(103,194,58,0.7)}
       &:hover{ color: #fff; border-color: #67c23a;}
    }
    .fcw-button--warning{
        color:#fff;
        background: #e6a23c;
        background: -webkit-gradient(linear, 0 0, 0 100%, from(#e6a23c), to(#e6a23c));
        background: -webkit-linear-gradient(#e6a23c 0%, #e6a23c 100%);
        background: -moz-linear-gradient(#e6a23c 0%, #e6a23c 100%);
        background: -o-linear-gradient(#e6a23c 0%, #e6a23c 100%);
        background: linear-gradient(#e6a23c 0%, #e6a23c 100%);
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#f0d264', endColorstr='#e5c960', GradientType=0 );
        &:active {background-color:rgba(2230,162,60,0.7);}
        &:hover{ color: #fff; border-color:#e6a23c;}
    }
    .fcw-button--info{
        color:#fff;
        background: #909399;
        background: -webkit-gradient(linear, 0 0, 0 100%, from(#909399), to(#909399));
        background: -webkit-linear-gradient(#909399 0%, #909399 100%);
        background: -moz-linear-gradient(#909399 0%, #909399 100%);
        background: -o-linear-gradient(#909399 0%, #909399 100%);
        background: linear-gradient(#909399 0%, #909399 100%);
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#f0d264', endColorstr='#e5c960', GradientType=0 );
        &:active {background:rgba(144,147,153,0.7) }
        &:hover{ color: #fff; border-color:#909399;}
    }
    .fcw-is-disabled{
        cursor: not-allowed;
        opacity: 0.6;
    }
    .fcw-button--mini{
        padding: 5px 10px;font-size: 12px;
    }
    .fcw-button--small{
        padding: 6px 15px;font-size: 14px;
    }
    .fcw-button--medium{
        padding: 7px 17px;font-size: 14px;
    }
    .fcw-success-plain{
        color: #67c23a;
        background: #f0f9eb;
        border-color: #c2e7b0;
        &:hover{
            background: #67c23a;
            border-color: #67c23a;
        }
    }
    .fcw-warning-plain{
        color: #e6a23c;
        background: #fdf6ec;
        border-color: #f5dab1;
        &:hover{
            background: #e6a23c;
            border-color: #e6a23c;
        }
    }
    .fcw-info-plain{
        color: #909399;
        background: #f4f4f5;
        border-color: #d3d4d6;
        &:hover{
            background: #909399;
            border-color: #909399;
        }
    }
    .fcw-primary-plain{
        color: #409eff;
        background: #ecf5ff;
        border-color: #b3d8ff;
        &:hover{
            background: #409eff;
            border-color: #409eff;
        }
    }
    .fcw-danger-plain{
        color: #f56c6c;
        background: #fef0f0;
        border-color: #fbc4c4;
        &:hover{
            background: #f56c6c;
            border-color: #f56c6c;
        }
    }
</style>