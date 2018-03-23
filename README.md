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

| Options         | Type     | Description                 | Result |
|-----------------|:--------:|:---------------------------:|-------:|
| options.isShow  | boolean | 强制显示(true)或隐藏(false) | |
| options.preShow | function | 选择框弹出前执行（强制显示时无效） | |
| options.onShow  | function | 选择框弹出后执行 | |
| options.preDismiss | function | 选择框消失前执行（强制隐藏时无效）| (startDate, endDate) |
| options.onDismiss | function | 选择框消失后执行| (startDate, endDate) |
| options.onStartDateChanged | function | 开始日期变更时执行 | (startDate) |
| options.onEndDateChanged | function | 结束日期变更时执行 | (endDate) |
| options.placeholder | string | 无日期内容时的占位符 | |