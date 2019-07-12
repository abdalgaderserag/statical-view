<template>
    <div class="money-view card view-stat" :style="'background-color: ' + color">

        <div style="width: inherit;height: inherit;">
            <!--<div style="float: left">-->
                <!--<span v-for="num in 10" class="flex-box">{{ num }}</span>-->
            <!--</div>-->
            <svg style="width: inherit;height: inherit;">
                <path v-for="number in horLine"
                      :d="'M '+ number * horSpace +',0 '+ number * horSpace +',' + height"
                      :style="'fill:none;stroke:'+ lineColor +';stroke-width:'+ strokeWidthPx(number) +'px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1'"/>
                :style="'fill:none;stroke:'+ lineColor +';stroke-width:'+ strokeWidthPx(number)
                +'px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1'"/>


                <path v-for="number in verLine"
                      :d="'m 0,'+ (height - (number * horSpace)) +' ' + width + ',0'"
                      :style="'fill:none;stroke:'+lineColor+';stroke-width:'+strokeWidth+'px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1'"/>
            </svg>
        </div>

    </div>
</template>

<script>
    export default {
        name: "MoneyView",
        data() {
            return {
                verLine: 0,
                horLine: 58,
                lineColor: '#c4cdd17d',
                color: '#fff',
                height: 0,
                width: 0,
                strokeWidth: 1,
                horSpace: 0,
                // verSpace: 0,
            }
        },
        mounted() {
            this.showView();
        },
        updated() {
            this.showView();
        },
        methods: {
            strokeWidthPx: function (number) {
                return this.strokeWidth;
                if (number % 4 !== 0)
                    return this.strokeWidth;
                return 3;
            },
            showView: function () {
                let view = this.$el;
                let width;
                if ((width = view.offsetWidth % this.horLine) !== 0) {
                    width = 24 - width;
                    width = view.offsetWidth + width;
                }
                this.horSpace = width / this.horLine;
                this.verLine = Math.round(view.offsetHeight / this.horSpace);
                this.height = view.offsetHeight;
                this.width = view.offsetWidth;
            }
        }
    }
</script>

<style>

</style>