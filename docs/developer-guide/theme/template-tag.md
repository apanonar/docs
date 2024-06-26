---
title: 自定义标签
description: 本文档介绍 Halo 为模板引擎提供的专有标签。
---

Halo 为满足部分代码注入和模板扩展点的需求，提供了一些专有标签，本文档将列出已支持的标签以及介绍这些标签的使用方法。

## halo:comment

### 描述

此标签用作评论组件的扩展点，如果有插件实现了这个扩展点，那么将在编写了此标签的模板中显示插件提供的内容。

### 使用示例

```html title="/templates/post.html"
<!-- 需要判断当前评论组件是否满足显示的条件，这个变量可能是是否安装评论插件、文章是否开启评论等条件的组合 -->
<div th:if="${haloCommentEnabled}">
    <halo:comment
        group="content.halo.run"
        kind="Post"
        th:attr="name=${post.metadata.name}"
    />
</div>
```

参数详解：

1. `group` - 自定义模型的分组，目前已支持的模型请参考下面表格。
2. `kind` - 自定义模型的类型，目前已支持的模型请参考下面表格。
3. `name` - 自定义模型数据的唯一标识。

已支持的模型列表：

| 对应模型   | group            | kind       |
| ---------- | ---------------- | ---------- |
| 文章       | content.halo.run | Post       |
| 自定义页面 | content.halo.run | SinglePage |

## halo:footer

### 描述

支持将系统设置中的页脚代码注入内容插入到此标签。

### 使用示例

```html
<footer>
    <halo:footer />
</footer>
```

:::info 注意
为了保证 Halo 的功能完整性，建议主题开发者尽可能在主题中实现此标签。
:::
