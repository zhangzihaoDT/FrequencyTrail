# FrequencyTrail
[参考来源](https://flowingdata.com/2019/12/16/frequency-trails-d3js/)How to Make Interactive Frequency Trails with D3.js

step1-加载数据
webpack.config.js设置
```
{
        test: /\.(csv|tsv)$/,
        use: [
          {
            loader: "csv-loader",
            options: {
              dynamicTyping: true,
              header: true,
              skipEmptyLines: true
            }
          }
        ]
      },
```
```
/*加载数据*/
import activity from "../data/activity.csv";
```
step2-转换数据
创建一个名为的函数processData()和一个名为的全局数组lineData：
```
var lineData = [];
 
function processData(data) {
}
```
有两个步骤。首先使用lodash groupBy()基于活动创建数据组：
```
function processData(data) {
    // Group items according to activity
    var grouped = _.groupBy(data, function(d) {
        return d.activity;
    });
}
```
step3-绘制数据
step4-平滑和规范化数据
```
function smoothed(values) {
    var smoothed = [];
    var lastIndex = values.length - 1;
     
    for (var i = 1; i < lastIndex; i++) {
        smoothed[i] = (values[i - 1] + values[i] + values[i + 1]) / 3;
    }
 
    smoothed[0] = values[0];
    smoothed[lastIndex] = values[lastIndex];
 
    return smoothed;
}
```
step5-添加标签
step6-排序线并添加时间轴
step7-风格与交互
