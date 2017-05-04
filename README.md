# Examples for JGrid 插件

Jquery.JGrid 分页列表插件，可以快速做分页功能,插件化，支持多个对象
简单的基本分页方法
------------
简单调用方式
------------
```
var Grid1= $("#tt").Grid({
        method: 'GET',//提交方式GET|POST
        pageSize: 10,
        pageDetail:true,
        url: '/post/getdata',//数据来源Url
        rows: [//数据列
            { width: '20%', field: 'name', title: '姓名', align: 'left' },
            { width: '15%', field: 'age', title: '年龄', align: 'left' },
            { width: '22%', field: 'school', title: '毕业学校', align: 'left' },
            { width: '15%', field: 'address', title: '地址', align: 'left' },
            {
                width: '10%', field: 'states', title: '状态', align: 'left',
                formatter: function (value, rowData) {
                    if (rowData.states == "1") {
                        return "已启用"
                    }
                    else {
                        return "已停用"
                    }
                }
            },
            {
                width: '15%', field: 'states', title: '删除', align: 'left',
                formatter: function (value, rowData) {
                    if (rowData.states == "1") {
                        return "<a href='#' style='margin-right:10px;'>删除</a>" +
                            "<a href='#' style='margin-right:10px;'>停用</a>"
                    }
                    else {
                        return "<a href='#' style='margin-right:10px;'>删除</a>" +
                           "<a href='#' style='margin-right:10px;'>启用</a>"
                    }
                }
            }
        ]
    });

```
#Jquery.JGrid 支持Post和Get方式加载分页列表，同时也支持不分页列表加载,支持第三方模版引擎解析数据,通过简单的配置属性即可实现以下，详细说明个配置属性的用处
------------
```
var grid=$("#id").Grid({
            order: "",//设置排序方式
            form: "form",//请求表单ID,可以使用提交表单方式来传递数据到后台，也可以使用参数方式,参考dataParam参数说明
            dataParam:{key,value,key2,value,.....}//传递到后台的参数
            method: "POST",//请求数据模式
            width: "100%", //默认10%
            height: "auto",//高度默认auto
            page: 1, //请求的页码
            pageSize: 20,//每页展示数据的大小
            showCheck: false,//是否显示复选框默认为false
            showOrder: false,//是否排序，默认false
            showRadio: false,//是否显示单选框,默认false(跟showCheck只能拥有一个)
            doubleLine: true,//是否显示双行颜色,默认true
            pageDetail: false,//是否显示页码详情,默认false
            pagerCount: 10,//展示页码数pageDetail为true有效
            isPager: true,//是否分页模式，默认true
            TotalPage: 0, //总页码数outPut(输出参数)
            Total: 0,   //总记录数outPut(输出参数)
            Currpage: 0,//当前页码outPut(输出参数)
            rows: [],//设置没列的详细情况,并可以做格式化数据操作,使用第三方模版引擎该参数可以忽略
            dataType: "json",//返回数据类型默认Json方式,可支持jsonp方式
            showNumber: true//是否显示序号
            url: "",  //数据源地址
            key: "",//数据主键暂时可以忽略
            callback: callback,//回调方法,每次加载数据后的回调方法
            onClick: function () { },//点击记录行激发的事件
            isTemplate: false,//是否为模版方式
            resolveTemplate: function(){},//模版引擎解析数据方法,必须把解析的数据模版返回出去
            template: "",//模版
            noneData:""//没有数据时展示的信息
})
```
# 方法说明:

Grid 初始化列表方法：
------------
```
$("#id").Grid(setting,callback)//方法,第一个参数为配置信息,第二个参数为回调方法
```
reLoad 方法:
------------
```
$("#id").reLoad(setting)//该方法用于重新刷新数据方法，可以把setting参数重新传递进去,可以实现搜索等功能
```

例如前面获得了grid对象则可以如下实现搜索功能：
------------
```
var option = {    
    enabled: $("#pageType2").val(),//搜索的参数一    
    name: $("#pageName2").val(),    //搜索的参数二
    scope: 1    
}    
grid.reLoad(option);
```

Refresh方法:

var option = {    
    dataParam:{
        enabled: $("#pageType2").val(),//搜索的参数一    
        name: $("#pageName2").val(),    //搜索的参数二
        scope: 1  
    } 
}    
grid.Refresh(option);