# desktop-pet

## 参数说明

### 精灵位置

控制精灵的位置，最大只能填写&nbsp;4&nbsp;位数字 ，其**顶部**参数的优先级比**底部**优先级高，**左侧**参数的优先级比**右侧**优先级高

### 精灵大小

控制精灵的尺寸，最大只能填写&nbsp;3&nbsp;位数字

### 精灵模型

渲染精灵的资源链接，链接格式为以**http**或**https**开头，以**.model.json**或**.model3.json** 结尾，或者本地资源的**绝对路径**也可

### 点击区域

控制精灵可点击区域，一般查看模型的&nbsp;json&nbsp;文件中的<strong>hit_areas</strong>字段中的<strong>name</strong>属性的值即可，填写格式为每隔区域之间用<strong>英文逗号(,)</strong>进行分隔，且<strong>不能以英文逗号结尾</strong>，例如&nbsp;head,body

### 精灵表情

控制精灵点击不同区域时触发的表情列表，只会保存在<strong>点击区域出现过的</strong>值，如果不填写默认从所有表情中<strong>随机选取一个</strong>表情进行展示。一般查看模型的&nbsp;json&nbsp;文件中的<strong>expressions</strong>字段中的<strong>name</strong>或<strong>序号(从&nbsp;0&nbsp;开始)</strong>即可，填写格式为区域名用<strong>英文中括号([])</strong>包裹，表情序号名用<strong>英文小括号(())</strong>包裹，且序号之间用<strong>英文逗号(,)</strong>进行分隔，且<strong>不能以英文逗号结尾</strong>同时每一组结束必须加上<strong>英文分号(;)</strong><strong>且不能有任何空格</strong>，可查看正则规则:

```js
/^(\[([\w_]+?)\]\(([\w_]+)(,([\w_]+))*\);)+$/
```

，例如：

```
[head](1,f03);[body](f01);
```

### 精灵动作

控制精灵点击不同区域时触发的动作列表，<strong>随机从动作列表中选取一个动作进行执行</strong>，只会保存在<strong>点击区域出现过的</strong>值，如果不填写默认<strong>不执行动作</strong>。一般查看模型的&nbsp;json&nbsp;文件中的<strong>motions</strong>字段中的<strong>&nbsp;key&nbsp;值</strong>即可，填写格式为区域名用<strong>英文中括号([])</strong>包裹，表情动作用<strong>英文小括号(())</strong>包裹，如果是单个动作名，那么则从这个动作下随机选取某一个动作进行展示，如果后续跟上<strong>动作的序号(从&nbsp;0&nbsp;开始)</strong>那么则从给定序号中选取某一个动作进行展示，<strong>且不能有任何空格</strong>，可查看正则规则:

```js
/^(\[([\w_]+?)\]\((([\w_]+((,\d+)*)?))(;(([\w_]+((,\d+)*)?)))*\);)+$/
```

，例如:

```
[body](tap_body;pinch_out,0,1);[head](idle);
```

## 编译结果

展示将<strong>点击区域</strong>、<strong>精灵表情</strong>、<strong>精灵动作</strong>的内容处理后保存至备至文件中的结果内容，可以根据编译结果中的内容查看是否符合预期
