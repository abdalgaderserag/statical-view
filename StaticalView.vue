<template>
    <div class="money-view card view-stat" :style="'background-color: ' + color">
        <!--<canvas id="statical" style="height: inherit;width: inherit">-->

        <!--</canvas>-->
        <svg style="width: inherit;height: inherit;fill:">
            <path v-for="number in horLine"
                  :d="'M '+ number * horSpace +',0 '+ number * horSpace +',200'"
                  :style="'fill:none;stroke:'+ lineColor +';stroke-width:'+ strokeWidth +'px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1'"/>

            <path v-for="number in verLine"
                  :d="'m 0,'+ number * horSpace +' 100,0'"
                  :style="'fill:none;stroke:'+lineColor+';stroke-width:'+strokeWidth+'px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1'"/>
        </svg>
    </div>
</template>

<script>
    export default {
        name: "MoneyView",
        data() {
            return {
                verLine: 2,
                horLine: 24,
                lineColor: '#c4cdd17d',
                color: '#fff',
                strokeWidth: 2,
                horSpace: 0,
                // verSpace: 0,
            }
        },
        mounted() {
            // let canvas = document.getElementById('statical');
            // let ctx = canvas.getContext("2d");
            // ctx.fillRect(20, 20, 100, 100);
            this.showView();
        },
        updated() {
            this.showView();
        },
        methods: {
            showView: function () {
                let view = this.$el;
                let width;
                if ((width = view.offsetWidth % this.horLine) !== 0) {
                    width = 24 - width;
                    width = view.offsetWidth + width;
                }
                this.horSpace = width / this.horLine;
                
            }
        }
    }
</script>

<style>

</style>