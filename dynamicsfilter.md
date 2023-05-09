## 属性

| 参数             | 说明                                                                                                                                             | 类型             | 默认值 |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------|------------------|--------|
| setting          | 查询项配置。详情见下表。                                                                                                                           | Array            | \[\]   |
| toggleShow       | 是否开启折叠功能                                                                                                                                 | Boolean          | false  |
| toggleStrategy   | 折叠模式。可设置height收起到一行高度， fixed收起只显示fixed的查询项，需要搭配setting中的fixed。                                                      | string           | height |
| defaultHidden    | 是否默认收起查询项                                                                                                                               | Boolean          | false  |
| labelWidth       | 设置标签文案的宽度，默认为自适应，根据最长的标题定宽。还可设置数字，固定宽度值。                                                                      | Number, String   | auto   |
| wrapperWidth     | 设置查询组件区域的宽度。                                                                                                                          | Number           | 260    |
| showQuery        | 是否显示查询按钮。                                                                                                                                | Boolean          | true   |
| showReset        | 是否显示重置按钮。                                                                                                                                | Boolean          | true   |
| buttonInline     | 查询按钮是否紧跟查询项，用于单行查询情况。                                                                                                         | Boolean          | false  |
| searchText       | 查询按钮文案                                                                                                                                     | String           | 查询   |
| loading          | 控制查询组件loading状态。                                                                                                                         | Boolean          | false  |
| canCustom        | 开启可配置功能                                                                                                                                   | Boolean          | false  |
| storageCustom    | 是否存储配置的查询项，存储需配合`storageKey`属性。为查询组件定义存储键值。                                                                          | Boolean          | false  |
| canSave          | 是否开启保存查询条件功能。需配合`storageKey`属性，定义存储键值。                                                                                    | Boolean          | false  |
| storageKey       | 定义存储键值                                                                                                                                     | String           |        |
| shortcutsLimit   | 保存查询后，最大可保存的查询条件个数。                                                                                                             | Number           | 10     |
| shortcutsMax     | 显示保存的查询条件时，超出改数，将以下拉模式显示剩余查询条件。                                                                                      | Number           | 5      |
| initStorage      | 用于初始化加载时赋予查询组件查询条件值，常用于外界存储了查询条件，<br>回填查询值操作。需要reslove一个对象数组，例如`{name:'userName',value: '张三'}` | Function：Promise |        |
| hideRequiredMark | 隐藏必填项的红星                                                                                                                                 | boolean          | true   |
| enterQuery       | 表单中所有input框enter后自动触发查询                                                                                                             | boolean          | false  |

### setting配置

| 参数  | 说明  | 类型  | 默认值 |
| --- | --- | --- | --- |
| name | 查询项名称。保证唯一。 | String |     |
| label | 查询项标签文本 | String |     |
| type | 查询项类型。可选`input`,`select`,`date`,<br>`dateTime`,`week`,`month`,<br>`year`,`dateRange`,`dateTimeRange`,<br>`monthRange`,`checkboxGroup`,<br>`radioGroup`,`radioButtonGroup`,<br>`cascader`,`numberRange`,`selectInput`,<br>`inputRange`,`slot` | String |     |
| options | 当组件类型需要数据源时用options传递。例如： select, checkboxGroup, radioGroup等组件 | String |     |
| defaultValue | 查询项默认值。设置默认值后，重置也会将改查询项值初始化到默认值。 | String |     |
| width | 可单独设置查询项组件区域的宽度。 | Number |     |
| placeholder | 设置查询组件的水印文案 | String,Array |     |
| props | 设置查询组件的其他属性值，详情见各组件的属性。 | Object |     |
| key | 字段别名。如果后面转换参数名不是name所制定的名称，可用key标明转换后名称 | String |     |
| convert | 提供后期转换方法。`{func, format, keys}`.<br>func可以利用函数将值转换。<br>format 在转换时间区间时的转换格式.默认格式`date,dateRange YYYY-MM-DD,`<br>`dateTime,dateTimeRange YYYY-MM-DD HH:mm:ss,`<br>`month,monthRange YYYY-MM,`<br>`week YYYY-ww,`<br>keys 可以设置区间类查询的，`[开始字段名，结束字段名]` | Object |     |
| onChange | 当前选项值变化后钩子函数。value变化后值，init是否初始化时调用。 | Function(value, init) |     |
| cascade | 指定该项将级联的查询项，可以设置多个。 | String,Array |     |
| cascadeMethod | 被级联，调用的方法。返回新的选项。参数为触发级联的查询项值。 | Function(value)：Promsie |     |
| remoteMethod | 如果当前查询options需要远程异步获取，可以使用该方法赋值给options | Function()：Promsie |     |
| autoQuery | 该查询项是否在值变化后，自动执行查询 | Boolean | false |
| custom | 如果组件设置了可配置查询项，custom为true的查询项将支持配置。 | Boolean |     |
| selected | 该查询项是可配置查询项时，selected为true可设置默认被选中。 | Boolean |     |
| slot | 如果Type配置了slot,需要指定slot名称，自定义查询项的内容。 | string |     |
| enterQuery | 当前input框enter后自动触发查询 | boolean | false |
| show | 控制当前查询项是否显示 | function(formData: any) => boolean |     |
| rules | 配置查询项校验规则。 | Array&lt;FormRule&gt; |     |
| fixed | 配置查询项是否为固定显示。设置为false将会到更多查询里展示 | Boolean |     |
| labelSlot | 可设置插槽名字，用于自定义查询标题内容。 | string |     |

### 事件

| 事件名 | 说明  | 回调参数 |
| --- | --- | --- |
| query | 点击查询后调用。参数为对象数组，要转换到查询对象需要用`DynmacisFilter.libs.getQueryParameters`方法转换。 | Function(queryCondition) |
| reset | 点击重置后事件。 | Function() |
| change | 任何一项查询值变化后触发，name 为设置的查询项名称，value 为变化后的值。 | Funciton({name, value}) |

### Slot

| 名称  | 说明  |
| --- | --- |
| setting中配置的名称 | setting中Type为slot时，可在组件内添加对应名称的slot. slot具名参数有{item: 配置信息， value: 查询值，change: 将外部组件值传入组件触发change} |
| buttonAppend | 按钮区域默认按钮之后添加自定义内容 |
| toggleButtonIcon | 替换展开收起icon |