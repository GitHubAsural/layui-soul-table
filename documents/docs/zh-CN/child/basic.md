## 基础子表
通过设置 `children` 字段，将子表配置读取进来
### 1.展开方式 （默认方式）
通过设置 `show: 1` 或 不设置 
:::demo
```html
<table id="myTable" lay-filter="myTable"></table>
<script>
layui.use(['form', 'table','soulTable'], function () {
    var table = layui.table,
        soulTable = layui.soulTable;

    table.render({
        elem: '#myTable'
        ,url: 'data-1.json'
        ,height: 500
        ,page: false
        ,cols: [[
            {title: '#', width: 50, children:[
                {
                    title: '表格一'
                    ,url: 'data-1.json'
                    ,height: 300
                    ,page: false
                    ,cols: [[
                        {type: 'checkbox', fixed: 'left'},
                        {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
                        {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
                        {field: 'author', title: '作者', width: 165 , filter: true},
                        {field: 'content', title: '内容', width: 123, filter: true},
                        {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
                        {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true},
                        {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
                        {title: '操作', width: 156, templet: '#childBar'}
                    ]]
                    ,done: function () {
                        layui.soulTable.render(this);
                    }
                },
                {
                    title: '表格二'
                    ,height: 300
                    ,limit: 1000000
                    ,data: function (d) {
                        // d 为当前行数据
                        console.log(d)
                        return [d];
                    }
                    ,page: false
                    ,cols: [[
                        {type: 'checkbox', fixed: 'left'},
                        {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
                        {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
                        {field: 'author', title: '作者', width: 165 , filter: true},
                        {field: 'content', title: '内容', width: 123, filter: true},
                        {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
                        {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true},
                        {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
                        {title: '操作', width: 156, templet: '#childBar'}
                    ]]
                    ,done: function () {
                        layui.soulTable.render(this);
                    }
                }
            ]},
            {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
            {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
            {field: 'author', title: '作者', width: 165 , filter: true},
            {field: 'content', title: '内容', width: 123, filter: true},
            {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
            {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true},
            {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
        ]]
        ,done: function () {
            soulTable.render(this)
        }
    });
})
</script>
```
:::

### 2.弹窗方式
通过设置 `show: 2`
:::demo 设置 `show: 2`
```html
<table id="myTable2" lay-filter="myTable2"></table>
<script>
layui.use(['form', 'table','soulTable'], function () {
    var table = layui.table,
        soulTable = layui.soulTable;

    table.render({
        elem: '#myTable2'
        ,url: 'data-1.json'
        ,height: 500
        ,page: false
        ,cols: [[
            {title: '#', show: 2, width: 50, children:[
                {
                    title: '表格一'
                    ,url: 'data-1.json'
                    ,height: 300
                    ,page: false
                    ,cols: [[
                        {type: 'checkbox', fixed: 'left'},
                        {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
                        {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
                        {field: 'author', title: '作者', width: 165 , filter: true},
                        {field: 'content', title: '内容', width: 123, filter: true},
                        {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
                        {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true},
                        {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
                        {title: '操作', width: 156, templet: '#childBar'}
                    ]]
                    ,done: function () {
                        layui.soulTable.render(this);
                    }
                },
                {
                    title: '表格二'
                    ,height: 300
                    ,limit: 1000000
                    ,data: function (d) {
                        // d 为当前行数据
                        console.log(d)
                        return [d];
                    }
                    ,page: false
                    ,cols: [[
                        {type: 'checkbox', fixed: 'left'},
                        {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
                        {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
                        {field: 'author', title: '作者', width: 165 , filter: true},
                        {field: 'content', title: '内容', width: 123, filter: true},
                        {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
                        {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true},
                        {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
                        {title: '操作', width: 156, templet: '#childBar'}
                    ]]
                    ,done: function () {
                        layui.soulTable.render(this);
                    }
                }
            ]},
            {field: 'title', title: '诗词', width: 200, sort: true, filter: true},
            {field: 'dynasty', title: '朝代', width: 100, sort: true, filter: true},
            {field: 'author', title: '作者', width: 165 , filter: true},
            {field: 'content', title: '内容', width: 123, filter: true},
            {field: 'type', title: '类型', width: 112,  filter: {split:','}, sort:true},
            {field: 'heat', title: '点赞数', width: 112,  filter: true, sort:true, excel:{cellType: 'n'}},
            {field: 'createTime', title: '录入时间', width: 165, filter: {type: 'date[yyyy-MM-dd HH:mm:ss]'}, sort:true},
        ]]
        ,done: function () {
            soulTable.render(this)
        }
    });
})
</script>
```
:::
