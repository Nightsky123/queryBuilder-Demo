# queryBuilderDemo

背景：
queryBuilder官网的demo比较少，而且api中的介绍也不是很详细，有些搜不到的也只能向作者提问，作者人很好，只是很忙。近期我花了点时间搞清楚了一点api
并搞成了个demo供需要的人参考。


--------------关于样式--------------
* 可自定义，具体参考css文件夹下的样式代码


----------目前我的demo的效果---------
* 可在data属性下随意定义自己所需的数据格式、内容
* 可以监听字段切换事件，点击addRule事件，afterCreateRuleFilters、beforeDeleteRule、beforeAddRule、afterAddRule、afterCreateRuleInput...
* 可以在rule行添加自己自定的按钮事件，并可以获取该行的rule数据
* 任何一个输入框的数据发生变化时，都要实时更新active_rule.data(这个data是你自己定义的)下对应的属性，以便你在通过插件的方法导出数据时的正确
* add_rule 和 add_group 的英文可以通过 如：lang:{add_rule:'中文'} 更改


-----------如何挂自定义数据结构-------
* 插件根据数据生成的每一行上都有个class为rule-container的div,你可以在$('.rule-container').data('queryBuilderModel').data，这个data下自定义自己的数据，结构任意，他是跟你的每一行绑定好的，当你要修改数据时，也要到这个data下去修改他下面的内容。


-------------数据回显思路------------
* 配置完成后的数据回显思路：配置完成时，首先要将配置好的 basic_rules，也就是你的数据， 存入缓存，然后再将你自己生成的那些dom结构存在当你再次进来时拿到的地方，当你再次进入界面，要重新讲这个之前配置好的rules挂在插件进行初始化，这个初始化是保证你的行数和之前的配置一致，然后在每一行逐行插入你之前存好的dom结构


------------导出的数据结构如下----------
<!--
{
  "condition": "AND",
  "rules": [
    {
      "id": "category",
      "field": "category",
      "type": "integer",
      "input": "select",
      "operator": "equal",
      "value": "1",
      "data": {
        "inputVal": "dfs"
      }
    }
  ],
  "not": false,
  "valid": true
}
-->
其中rules是个数组，数组中的每个对象下的data是由个人自定义的数据。属性名和数据都可自己定义。

