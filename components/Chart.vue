<template>
    <div class="chart"></div>
</template>

<script>
    import Highcharts from 'highcharts/highstock';
    import HighchartsMore from 'highcharts/highcharts-more';
    import HighchartsDrilldown from 'highcharts/modules/drilldown';
    import Highcharts3D from 'highcharts/highcharts-3d';
    HighchartsMore(Highcharts);
    HighchartsDrilldown(Highcharts);
    Highcharts3D(Highcharts);

    import avocado from "../themes/avocado";
    import blackWhite from '../themes/black-white';
    import darkBlue from '../themes/dark-blue';
    import darkGreen from '../themes/dark-green';
    import darkUnica from '../themes/dark-unica';
    import gray from '../themes/gray';
    import grid from '../themes/grid';
    import gridLight from '../themes/grid-light';
    import oliveGreen from '../themes/olive-green';
    import sandSignika from '../themes/sand-signika';
    import skies from "../themes/skies";
    import sunset from "../themes/sunset";

    import Data from 'highcharts/modules/data';
    Data(Highcharts);
    // 宽度可变环形图
    import Vary from 'highcharts/modules/variable-pie';
    Vary(Highcharts);
    // 旭日图
    import Sunburst from 'highcharts/modules/sunburst';
    Sunburst(Highcharts);
    import Venn from 'highcharts/modules/venn';
    Venn(Highcharts);

    // 漏斗图
    import Funnel from 'highcharts/modules/funnel';
    Funnel(Highcharts);
    // 贝尔曲线
    import Bell from 'highcharts/modules/histogram-bellcurve';
    Bell(Highcharts);
    // 时序图
    import TimeLine from 'highcharts/modules/timeline';
    TimeLine(Highcharts);
    // 柏拉图
    import Pareto from 'highcharts/modules/pareto';
    Pareto(Highcharts);
    // 会议图
    import Item from 'highcharts/modules/item-series';
    Item(Highcharts);
    // 甘特图
    import Xrange from 'highcharts/modules/xrange';
    Xrange(Highcharts);
    // 词云图
    import Word from 'highcharts/modules/wordcloud';
    Word(Highcharts);
    // 哑铃图
    import Dumbbell from 'highcharts/modules/dumbbell';
    Dumbbell(Highcharts);
    // 棒棒糖图
    import Lollipop from 'highcharts/modules/lollipop';
    Lollipop(Highcharts);

    export default {
        name: "Chart",
        props: {
            config: {
                type: Object,
                default: () => ({})
            },
            theme: {
                type: Object,
                default: () => ({})
            }
        },
        data () {
            return {
                options: {
                    chart: this.config.chart,
                    colors: this.config.colors || ['#7cb5ec', '#434348', '#90ed7d', '#f7a35c', '#8085e9',
                        '#f15c80', '#e4d354', '#2b908f', '#f45b5b', '#91e8e1'],
                    credits: {
                        enabled: false
                    },
                    series: this.config.series,                         // 数据列
                    subtitle: this.config.subtitle,                     // 副标题
                    title: this.config.title,                           // 标题
                    xAxis: this.config.xAxis,                           // x 轴
                    yAxis: this.config.yAxis,                           // y 轴
                    zAxis: this.config.zAxis,                           // z 轴
                }
            }
        },
        mounted () {
            this.confShow();
            this.useTheme();
            this.initChart();
        },
        computed: {

        },
        methods: {
            initChart () {
                // console.log(this.$el);
                // this.$el.style.width = (this.styles.width || 800) + 'px';
                // this.$el.style.height = (this.styles.height || 400) + 'px';
                this.chart = new Highcharts.Chart(this.$el, this.options);
            },
            confShow () {
                if (this.config.chart) {                                // 图表配置
                    this.options.chart = this.config.chart
                }
                if (this.config.colors) {                               // 颜色集合
                    this.options.colors = this.config.colors
                }
                if (this.config.credits) {                              // 版权信息
                    this.options.credits = this.config.credits
                }
                if (this.config.series) {                               // 数据列
                    this.options.series = this.config.series
                }
                if (this.config.title) {                                // 标题
                    this.options.title = this.config.title
                }
                if (this.config.subtitle) {                             // 副标题
                    this.options.subtitle = this.config.subtitle
                }
                if (this.config.xAxis) {                                // x 轴
                    this.options.xAxis = this.config.xAxis
                }
                if (this.config.yAxis) {                                // y 轴
                    this.options.yAxis = this.config.yAxis
                }
                if (this.config.zAxis) {                                // z 轴
                    this.options.zAxis = this.config.zAxis
                }
                if (this.config.accessibility) {                        // 无障碍设计
                    this.options.accessibility = this.config.accessibility
                }
                if (this.config.data) {                                 // 数据功能模块
                    this.options.data = this.config.data
                }
                if (this.config.drilldown) {                            // 钻取
                    this.options.drilldown = this.config.drilldown
                }
                if (this.config.exporting) {                            // 导出
                    this.options.exporting = this.config.exporting
                }
                if (this.config.labels) {                               // 标签
                    this.options.labels = this.config.labels
                }
                if (this.config.legend) {                               // 图例
                    this.options.legend = this.config.legend
                }
                if (this.config.loading) {                              // 加载
                    this.options.loading = this.config.loading
                }
                if (this.config.navigation) {                           // 导航
                    this.options.navigation = this.config.navigation
                }
                if (this.config.noData) {                               // 没有数据
                    this.options.noData = this.config.noData
                }
                if (this.config.pane) {                                 // 面板配置
                    this.options.pane = this.config.pane
                }
                if (this.config.plotOptions) {                          // 数据列配置
                    this.options.plotOptions = this.config.plotOptions
                }
                if (this.config.responsive) {                           // 响应式
                    this.options.responsive = this.config.responsive
                }
                if (this.config.tooltip) {                              // 数据提示框
                    this.options.tooltip = this.config.tooltip
                }
                if (this.config.global) {                               // 全局参数
                    this.options.global = this.config.global
                }
                if (this.config.lang) {                                 // 语言文字
                    this.options.lang = this.config.lang
                }
            },
            useTheme () {
                if (this.theme) {
                    Highcharts.setOptions(this.theme)
                }
                if (this.theme.type === 'avocado') {
                    this.chart = new Highcharts.setOptions(avocado)
                }
                if (this.theme.type === 'black-white') {
                    this.chart = new Highcharts.setOptions(blackWhite)
                }
                if (this.theme.type === 'dark-blue') {
                    this.chart = new Highcharts.setOptions(darkBlue)
                }
                if (this.theme.type === 'dark-green') {
                    this.chart = new Highcharts.setOptions(darkGreen)
                }
                if (this.theme.type === 'dark-unica') {
                    this.chart = new Highcharts.setOptions(darkUnica)
                }
                if (this.theme.type === 'gray') {
                    this.chart = new Highcharts.setOptions(gray)
                }
                if (this.theme.type === 'grid') {
                    this.chart = new Highcharts.setOptions(grid)
                }
                if (this.theme.type === 'grid-light') {
                    this.chart = new Highcharts.setOptions(gridLight)
                }
                if (this.theme.type === 'olive-green') {
                    this.chart = new Highcharts.setOptions(oliveGreen)
                }
                if (this.theme.type === 'sand-signika') {
                    this.chart = new Highcharts.setOptions(sandSignika)
                }
                if (this.theme.type === 'skies') {
                    this.chart = new Highcharts.setOptions(skies)
                }
                if (this.theme.type === 'sunset') {
                    this.chart = new Highcharts.setOptions(sunset)
                }
            },
        }
    }
</script>

<style scoped>

</style>