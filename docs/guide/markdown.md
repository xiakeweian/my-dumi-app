---
title: Markdown 增强
nav:
  title: 指南
  order: 1
  path: /guide
toc: menu
isShowPreview: true
group:
  title: 基础
  order: 3
---

# Markdown 增强
## embed
dumi 对 HTML 默认的 <code>embed</code> 标签做了扩展，允许在 Markdown 文档中嵌入另一个 Markdown 文档的内容
1. **引入全量的 Markdown 文件内容**
<embed src="../path/to/some.md"></embed>
2. **根据行号引入指定行的 Markdown 文件内容**
<embed src="../path/to/some.md#L3"></embed>
3. **根据行号引入部分 Markdown 文件内容**
<embed src="../path/to/some.md#L1-L7"></embed>
4. **根据正则引入部分 Markdown 文件内容**
<embed src="../path/to/some.md#RE-/^[0-9]+/"></embed>

## Badge
dumi 内置了 Badge 组件，可以为 Markdown 内容（例如标题）添加标签，例如：
```markdown
### Info Badge <Badge>info</Badge>

### Warning Badge <Badge type="warning">warning</Badge>

### Error Badge <Badge type="error">error</Badge>

### Success Badge <Badge type="success">success</Badge>
```

会被渲染为:

### Info Badge <Badge>info</Badge>

### Warning Badge <Badge type="warning">warning</Badge>

### Error Badge <Badge type="error">error</Badge>

### Success Badge <Badge type="success">success</Badge>

:::info{title=普通的信息}
这是一条普通信息
:::

:::info{title=成功}
这是一条成功信息
:::

:::warning
这是一条警告信息
:::

:::error
这是一条错误信息
:::

```jsx {5-7} | pure
import React from 'react';

export default () => (
  <div>
    <h1>Hello dumi!</h1>
  </div>
);
```

```yml {3,6-9,12,13}
features:
  - title: 更好的编译性能
    emoji: 🚀
  - title: 内置全文搜索
    emoji: 🔍
  - title: 全新主题系统
    emoji: 🎨
  - title: 约定式路由增强
    emoji: 🚥
  - title: 资产元数据 2.0
    emoji: 💡
  - title: 继续为组件研发而生
    emoji: 💎
```
# Tree
使用 Tree 组件可以创建文件树，使用语法如下：
```
<Tree>
  <ul>
    <li>
      src
      <ul>
        <li>index.md</li>
      </ul>
    </li>
    <li>package.json</li>
  </ul>
</Tree>
```
渲染为：

<Tree>
  <ul>
    <li>
      src
      <ul>
        <li>index.md</li>
      </ul>
    </li>
    <li>package.json</li>
  </ul>
</Tree>
通过添加 small 元素可以为节点添加注释内容。
<Tree>
  <ul>
    <li>
      src
+     <small>这是 src 文件夹</small>
      <ul>
        <li>
          index.md
+         <small>这是 index.md</small>
        </li>
      </ul>
    </li>
    <li>
      package.json
+     <small>这是 package.json</small>
    </li>
  </ul>
</Tree>

# CodeGroup 2.3.0+
需要将多代码块合并成一个分组进行展示时，可以使用 CodeGroup 语法，例如：
```


:::code-group
```
```bash [npm]
npm install -D dumi
```

```bash [yarn]
yarn add -D dumi
```

```bash [pnpm]
pnpm add -D dumi
```

```ts [.dumirc.ts] {3}
import { defineConfig } from 'dumi';

export default defineConfig({
  // ...
});

```
:::

```

:::code-group

```bash [npm]
npm install -D dumi
```

```bash [yarn]
yarn add -D dumi
```

```bash [pnpm]
pnpm add -D dumi
```

```ts [.dumirc.ts] {3}
import { defineConfig } from 'dumi';

export default defineConfig({
  // ...
});
```
:::


将会被渲染为：