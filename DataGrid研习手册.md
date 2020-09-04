# EasyUI-DataGrid-冻结列-研习手册

经过两天的API研究，最终实现了微服务下使用DataGrid表格。

官方API地址：[官方API地址链接](http://www.jeasyui.net/plugins/183.html)

* **获取某数据字段**

  ```html
  row['requirtCompanyName']
  ```

- **单元格的格式化函数：formatter**

  - 基本用法

    - value：字段值。row：行记录数据。index: 行索引。

    - ```js
      用法1：
      $('#dataTest').datagrid({
          columns:[[
              {field:'dataTest',title:'需求单位', width:80,
                  formatter: function(value,row,index){
                     return value;
                  }
              }
          ]]
      });
      用法2：
      <th data-options="field:'quantity',width:100,align: 'center',
      formatter: function(value,row,index){
          return numFormat(value,8);
      }">数量</th>
      ```

      ***Attention！***

      1. value：可以在formatter函数中修改value的值，并在界面上展示修改后的值。
         		**注意:** 在这里对value的修改并不会改动后台数据，这个改动仅相当于对value的渲染。
      2. row：可以通过 row["field值"] 或者 row.field值 得到同一行其他列的值。可以是前面的列，也可以是后面的列。
      3. index：行索引。（项目中没用到过）
      4. 有时我们需要添加一列数据，这列数据是通过其他列数据计算后得到的，接口没有给我们这列数据的字段时，此时field的值可以自定义，但是不能和其他列字段的field命名相同。

- **隐藏DataGrid某一列**

  1. $("#dataTest").datagrid('hideColumn', filedname);

  **e.g.**

  ​	$("#dataTest").datagrid('hideColumn', 'requirtCompanyName');

  ![image-20200811100046258](C:\Users\Zoe Zuo\AppData\Roaming\Typora\typora-user-images\image-20200811100046258.png)

   2. 设置属性 hidden:true 

       	1. (data-options配置方法)

      ```html
      <th data-options="field:'requirtCompanyName',width:85,align:'center',hidden:true">需求单位</th>
      ```

      2. html属性方法

      ```html
      <th field="requirtCompanyName" hidden="true">需求单位</th>
      ```

      3. 初始化方法

      ```js
      $("#dataTest").datagrid({
                 columns:[[    
                      {field:'requirtCompanyName',width:150，hidden:'true'}
                  ]]
                  }
              });
      ```

- **显示DataGrid隐藏的某一列**

  1. $("#dataTest").datagrid('showColumn', filedname);

  **e.g.**

  ​	$("#dataTest").datagrid('showColumn', 'requirtCompanyName');

![image-20200811095958060](C:\Users\Zoe Zuo\AppData\Roaming\Typora\typora-user-images\image-20200811095958060.png)

* **给列赋值**

  因为需求是使前四列冻结，若像datagrid官方demo那样改写，会改变列表样式，原有代码上每列还有其他触发事件等，我从后台拿到的数据是一个list，将其变成json文件我觉得有点太麻烦，因此我采用了不改动html代码，直接用js遍历赋值的方式。

  ```
  loadData ： 参数(data) 加载本地数据，旧的行会被移除。
  ```

  如下：

  

```js
function reLoadDataGrid(rtn) {
            var values = [];
            for ( var i = 0; i <rtn.data.size; i++) {
                var a = {
                    'lineNum' : rtn.data.list[i].lineNum
                    .......
                };
                values.push(a);
            }
            $('#dataTest').datagrid('loadData', values);
        }
```

* **具体实现**

  * 在所要实现冻结列的表格中，加入**class=“easyui-datagrid"**
  * 将要冻结的列头与其他列头分别用<thead>包裹，冻结的列头加属性**frozen="true"**
  * 所有列头都要改为data-options=""的形式，field是要传入的数据，有其他事件，用formatter另写事件，要改变样式，用rowStyler，具体可参考官方API

  ```html
  <table id="dataTest" class="easyui-datagrid" >
    <thead frozen="true">
      <tr>
        <th data-options="field:'lineNum',width:50,align: 'center'" >行号</th>
        <th data-options="field:'categoryName',width:150,align: 'center',formatter:formatContent">MMMM</th>
        <th data-options="field:'segment10',width:100,align: 'center',formatter: segmentformat">NNNN</th>
      </tr>
    </thead>
    <thead>
      <tr>
        <th data-options="field:'quantity',width:100,align: 'center',
   formatter: function(value,row,index){return numFormat(value,8);}">数量</th>
        <th data-options="field:'needByDate',width:120,align: 'center',formatter: function(value,row,index){return dateFormat(value,'yyyy-MM-dd');}">时间</th>
        <th data-options="field:'unitMeasLookupCode',width:100,align: 'center',rowStyler: function(index,row){if (row['strategyType']==1){return 'color:red;';}}" >单位</th>
        <th data-options="field:'cancelFlag',width:150,align: 'center',
         formatter: function(value,row,index){
             return value=='Y'?'是':'否';
         }" >行状态</th>
         <th data-options="field:'projectSegment',width:150,align: 'center',
         formatter: function(value,row,index){
            return value;
          }">编号</th>
         <th data-options="field:'expendedDate',width:150,align: 'center',
                           formatter: function(value,row,index){
                           if(row['inventoryItemFlagDesc']=='库存'){
                           return '未涉及';
                           }else{
                           return dateFormat(value,'yyyy-MM-dd');
                           }
                           }" class="selectProject">日期</th>
                              
      </tr>
    </thead>
  <tbody id="pageList" style="display: none" action="/api-product/requestForm/queryAllPoLines">
    <tr>
    <!--<td class="text-center">{{$i+1}}</td>
      <td title="{{$obj.categoryName}}">{{$obj.categoryName}}</td>
      <td title="{{$obj.segment10}}">
        {{if $obj.offerSetId}}
          <b style="cursor:pointer;color: #0c91dd "  
  onclick="showOfferSet('{{$obj.offerSetId}}','{{$obj.segment10}}','{{$obj.itemDescription}}')">{{$obj.segment10}}</b>
        {{else}}
           {{$obj.segment10}}
        {{/if}}
      </td>
      <td class="text-right quantity" title="{{$obj.quantity | numFormat:8}}"> {{$obj.quantity | numFormat:8}} </td>
      <td class="text-right quantity"> {{$obj.needByDate | dateFormat:'yyyy-MM-dd'}} 	</td>
      <td class="text-center"> {{$obj.unitMeasLookupCode}} </td>
      <td class="text-center">{{$obj.cancelFlag=='Y'?'是':'否'}}</td>
      <td title="{{if $obj.projectId != null}}
          {{$obj.projectSegment}}
          {{else}}  {{$obj.budgetCode}}
          {{/if}}">
          {{if $obj.projectId != null}}
          {{$obj.projectSegment}}
          {{else}}
          {{/if}}
          {{if $obj.projectId==0|| $obj.projectId==null}}
          {{$obj.budgetCode}}
          {{/if}}
     </td>
     <td class="selectProject">
          {{if $obj.inventoryItemFlagDesc=='库存'}} 未涉及
          {{else}}
          {{$obj.expendedDate | dateFormat:'yyyy-MM-dd'}}
          {{/if}}
      </td> -->
      </tr>
    </tbody>
  </table>
  ```

  
