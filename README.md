# 基于Vuejs+Webpack定义了开发规范的网页开发框架的日期选择器
## 使用方式（Usage）
### 安装（Install）
``
npm install optimat-vue-date-picker -save
``

### 导入（Import）
#### *.js
```javascript
import DatePicker from 'optimat-vue-date-picker'
```
#### *.vue
```vue
<script>
    import DatePicker from 'optimat-vue-date-picker'
</script>
```
### 标签（Target）
#### *vue
```html
<DatePicker :options="datePickerOptions"></DatePicker>
```

### 功能（Api）

| Options         | Type     | Description                 | Default | Result   |
|-----------------|:--------:|:---------------------------:|:--------:|:--------:|
| options.isShow  | boolean | 强制显示(true)或隐藏(false) | false | |
| options.preShow | function | 选择框弹出前执行（强制显示时无效） | undefined | |
| options.onShow  | function | 选择框弹出后执行 | undefined | |
| options.preDismiss | function | 选择框消失前执行（强制隐藏时无效）| undefined | (startDate, endDate) |
| options.onDismiss | function | 选择框消失后执行| undefined | (startDate, endDate) |
| options.onStartDateChanged | function | 开始日期变更时执行 （单选模式必须加入该事件）| undefined | (startDate) |
| options.onEndDateChanged | function | 结束日期变更时执行（单选模式不会执行） | undefined | (endDate) |
| options.placeholder | string | 无日期内容时的占位符 | undefined | |
| options.align | string | 选择框位置：居左(left)，居中(center)，居右(right) | left | |
| options.type | string | 选择器类型：单选(single)，范围(range) | single | |
| options.mode | string | 选择器模式：单个日历(single)，两个日历(double) | type == single ? single : double | |
| options.autoClear | boolean | 是否自动清空（范围选择时有效） | false | |