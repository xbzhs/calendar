calendar
======

该日历组件适用于移动web端开发，轻量简洁，灵活配置，如项目中使用jqmobi或zepto作为底层库，可直接使用。提供基础的样式选择，为满足具体使用场景，可在此基础上对样式做定制修改。

[先点击查看demo](http://zhangchen2397.github.io/dialog/) (建议扫描下方二维码手机上体验效果更佳)

![qr code](http://zhangchen2397.github.io/dialog/qr_code.png)

###组件主要功能
1. 日历范围选择，不在范围内的日期置灰
2. 节假日显示，可配置是否显示节假日
3. 自由配置初始化生成多日历
4. 各种操作事件自由监听，选择日期、显示、隐藏事件

###配置参数说明
```javascript
this.defaultConfig = {
    /**
     * 日历外层容器ID
     * type {string|jq object} id字符串或jq对象
     */
    el: '#calendar',

    /**
     * 初始化日历显示个数
     */
    count: 5,

    /**
     * 用于初始化日历开始年月
     * type {date object} 日期对象
     */
    date: new Date(),

    /**
     * 日期最小值，当小于此日期时日期不可点
     * type {date object} 日期对象
     */
    minDate: null,

    /**
     * 日期最大值，当大于此日期时日期不可点
     * type {date object} 日期对象
     */
    maxDate: null,  //日期对象

    /**
     * 初始化当前选中日期，用于高亮显示
     * type {date object} 日期对象
     */
    selectDate: new Date(),

    /**
     * 选中日期时日期下方文案
     * type {string}
     */
    selectDateName: '入住',

    /**
     * 是否显示节假日
     * type {boolean}
     */
    isShowHoliday: true,

    /**
     * 在日历中是否显示星期
     * type {boolean}
     */ 
    isShowWeek: true
};
```

###对外调用接口及自定义事件
```javascript
/**
 * 对外调用接口及自定义事件
 * @method render 渲染日历
 * @method nextMonth 上一月
 * @method prevMonth 下一月
 * @method show 显示日历
 * @method hide 隐藏日历
 * @method setSelectDate 设置当前选中日期

 * @customEvent selectDate 选择日期时派发事件
 * @customEvent show 显示日历时派发事件
 * @customEvent hide 隐藏日历时派发事件
 */
 ```

###组件初始化及使用
```javascript
( function() {
    calendarIns = new calendar.calendar( {
        count: 4,
        selectDate: new Date(),
        selectDateName: '入住',
        minDate: new Date(),
        maxDate: new Date( +new Date() + 100 * 86400000 ),
        isShowHoliday: true,
        isShowWeek: false
    } );

    $.bind( calendarIns, 'afterSelectDate', function( event ) {
        var curItem = event.curItem,
            date = event.date,
            dateName = event.dateName;

        calendarIns.setSelectDate( date );
    } );

    $( '#prevMonth' ).on( 'click', function() {
        calendarIns.prevMonth();
    } );

    $( '#nextMonth' ).on( 'click', function() {
        calendarIns.nextMonth();
    } );
} )();
```

[点击查看更多demo](http://zhangchen2397.github.io/dialog/)
