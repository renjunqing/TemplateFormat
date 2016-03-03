# TemplateFormat
一个简单的依赖underscore和jQuery的模板约定，依赖jquery和underscore

## _render方法

使用了underscore的template方法
模板：
```html
<script id="_template" type="text/_template">
	<span><%= value %></span>
</script>
```
调用：
```javascript
template._render('#_template', {
	value: '这是value值'
}, {
	renderMode: 'replace'
});
```
说明：
_render方法包含3个参数：模板的选择器、数据、额外的配置项（可选）
replace：会将生成的dom插入到模板前边，如果再次调用会将之前插入的删除
before: 会将生成的dom插入到模板后边，如果重复调用不会删除之前插入的，主要用于异步加载的列表，新数据在列表的前边
after：同before，用于加载到列表的后边
默认不传opt，则函数返回生成的dom

## $render方法

就是jQuery的html方法，只是添加了dom节点与数据对象key的一个约定,从而免去对每个节点分别替换的步骤
dom：
```html
<div id="$template" $template-key="key"></div>
```
调用：
```javascript
template.$render('$template', {
	key: '这是value值'
});
```
说明：与_render方法不同，这个并没有模板，是直接在dom上修改的
