# 需同时修改的文件位于同一目录下

<div style="margin-top: 16px">
<Badge type="info" text="内聚性" />
</div>

在项目中编写代码时，通常会将 Hook、组件和工具函数等拆分到多个文件进行管理。为了更轻松地创建、查找和删除这些文件，设计一个合适的目录结构至关重要。

将需要一起修改的源文件放在同一目录下，可以更直观地展现代码的依赖关系。这不仅可以防止随意引用不应被引用的文件，还能一次性删除相关文件。

## 📝 代码示例

以下代码是按照模块类型(如 Presentational 组件、Container 组件、Hook、常量等)分类的目录结构。

```text
└─ src
   ├─ components
   ├─ constants
   ├─ containers
   ├─ contexts
   ├─ remotes
   ├─ hooks
   ├─ utils
   └─ ...
```

## 👃 闻代码

### 内聚性

如果按照这种方式按类划分文件，就很难确定代码之间的引用关系。代码文件之间的依赖关系需要开发者在分析代码时自行掌握和处理。
此外，如果某个组件、Hook 或工具函数不再使用而被删除，相关代码可能未被同时删除，从而留下未使用代码。

项目的规模往往会逐步扩大，随着项目规模的增加（比如 2 倍、10 倍甚至 100 倍），代码之间的依赖关系也将变得更加复杂。一个目录可能包含 100 多个文件。

## ✏️ 尝试改善

以下是一个实例，展示了如何通过将需要一起修改的代码文件放在同一目录下，来优化项目结构。

```text
└─ src
   │  // 整个项目中使用的代码
   ├─ components
   ├─ containers
   ├─ hooks
   ├─ utils
   ├─ ...
   │
   └─ domains
      │  // 只在 Domain1 中使用的代码
      ├─ Domain1
      │     ├─ components
      │     ├─ containers
      │     ├─ hooks
      │     ├─ utils
      │     └─ ...
      │
      │  // 只在 Domain2 中使用的代码
      └─ Domain2
            ├─ components
            ├─ containers
            ├─ hooks
            ├─ utils
            └─ ...
```

将一起修改的代码文件放在同一目录下，很容易理解代码之间的依赖关系。

例如，假设一个域(`Domain1`)的子代码中引用另一个域(`Domain2`)的源代码，如下所示：

```typescript
import { useFoo } from '../../../Domain2/hooks/useFoo'
```

如果遇到这样的 import 语句，就能很容易地意识到引用了错误的文件。

此外，当删除与特定功能相关的代码时，只需删除整个目录即可一并清理所有相关代码，从而确保项目中不会遗留未使用的代码。
