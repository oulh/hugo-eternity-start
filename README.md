# hugo-eternity-start

Hugo主题  [Eternity](https://github.com/boratanrikulu/eternity) 的构建模板，作了一点自定义修改。预览：[https://oulh.github.io/hugo-eternity-start](https://oulh.github.io/hugo-eternity-start)

修改内容都位于`static`目录和`layouts`目录里，删除掉里面的内容即可恢复到示例 [eternity](https://eternity.bora.sh/) 的样子。

当前主题版本：v1.5.1

## 网站配置：Config.yaml 的用法

翻译自：[Usage of Config.yaml](https://github.com/boratanrikulu/eternity/blob/main/doc/config.md)

示例配置在这里：[**config.yaml**](https://github.com/boratanrikulu/eternity/blob/main/config.example.yaml)

您可以为您的网站使用`image`、`logo`和`title`变量`subtitle`。

```
title: Eternity
params:
  subtitle: Eternity is a minimalist Hugo theme designed for portfolio sites with a fresh feel.
  image: '/images/about.png'
  logo: 'logo.png'
```



您可以使用`googleAnalytics`变量来设置 Analytics。

```
googleAnalytics: ''
```



您可以使用`plausible`变量来设置 Plasible。

```
params:
  plausible: ''
```



您可以使用`copyright`和`author`变量来设置版权声明。

```
params:
  copyright: ''
  author: ''
```



您可以将源通知设置为隐藏。但是，请不要这样做。

```
params:
  dontShowSource: false
```



您可以分别更改桌面和移动设备的列数。如果没有为页面类型定义值，则将使用默认值。

```
params:
  portfolio:
    columns:
      desktop:
        nature: 4
        archive: 6
        people: 2
        default: 3
      mobile:
        default: 2
        archive: 3
        people: 1
```



您可以使用`socials`数组来设置您的社交帐户。

- `icon`是一个非常棒的字体图标代码。
- `landing: true`使图标在登陆页面上不可见，但在网站内部可见。
- `rel_me: true`将 HTML 属性添加`rel="me"`到链接中。这对于验证您的 Mastodon 个人资料的链接很有用。

```
params:
  socials:
    - icon: 'far fa-envelope fa-lg'
      url: 'mailto:eternity@bora.sh'
      landing: true
    - icon: 'fab fa-github fa-lg'
      url: 'https://github.com/boratanrikulu/eternity'
      landing: true
    - icon: 'fab fa-instagram fa-lg'
      url: 'https://instagram.bora.sh/eternity'
    - icon: 'fab fa-linkedin-in fa-lg'
      url: 'https://linkedin.bora.sh/in/eternity'
```



您可以更改`homepage`链接。

```
params:
  homepage: "/work"
```



您可以更改特殊页面名称。

```
params:
  specialPages:
    - work
    - archive
```



如果需要，您可以绕过欢迎页面。它将“/”重定向到“主页”。

```
params:
  bypassWelcomePage: true
```



您可以禁用欢迎页面上的背景图像。

```
params:
  disableWelcomePageBackground: false
```



您可以使用`disableRadius`变量禁用徽标的半径。

```
params:
  disableRadius: true
```



您可以禁用调整帖子页面上的图片大小。

```
params:
  disableAlwaysResize: true
```



您可以向下移动标题和元，以仅在滚动时显示它们。

```
params:
  moveIt: true
```



您可以使用`menu.main`数组来设置导航栏链接。

```
menu:
  main:
    - name: work
      url: /work/
      weight: 1
    - name: people
      url: /tags/people/
      weight: 2
    - name: nature
      url: /tags/nature/
      weight: 3
    - name: archive
      url: /tags/archive/
      weight: 4
    - name: about
      url: /about/
      weight: 5
```



## 文章编辑

翻译自：[Usage of Posts](https://github.com/boratanrikulu/eternity/blob/main/doc/posts.md)

Eternity 是可配置的，您可以通过设置变量来更改功能行为。

这是基本的帖子结构。您基本上可以用来`tags`设置哪些页面将包含此帖子。我们建议用于`work`主页和`archive`所有帖子。（注意：您也可以更改他们的名称）。
如果您想创建新页面，只需将其添加为新标签即可。（`my-image-1.jpg`应位于`/assets/images`您项目的文件夹中）

```yaml
---
images:
- /images/my-image-1.jpg
title: Here's my first post!!
tags:
- work
---
```



您可以`date`为您的帖子设置价值。它将用于帖子页面和帖子排序。如果需要，您可以使用`weight`值进行排序。（注意：如果您不设置 a `date`，我们会检查`exif`要在帖子中使用的图像的值。）

```yaml
---
weight: 9
images:
- /images/my-image-1.jpg
title: Here's my first post!!
tags:
- work
- first
date: 2022-07-24
---
```



您可以通过将多个图像添加到数组来使用它们`images`。默认视图是`row`. 但如果你想将它们设置为`column`，你可以使用`multipleColumn`value。支持本地镜像和远程镜像。如果您使用远程图像，则会下载该图像。

```yaml
---
weight: 9
images:
- /images/my-image-1.jpg
- /images/my-image-2.jpg
multipleColumn: true
title: Here's my first post!!
tags:
- work
- first
date: 2022-07-24
---
```



当您使用多个图像时，第一个图像将用作帖子页面中的缩略图。如果你想使用不同的图像，你可以使用`mainImage`变量。

```yaml
---
weight: 9
images:
- /images/my-image-1.jpg
- /images/my-image-2.jpg
mainImage: /images/different-image.jpg
multipleColumn: true
title: Here's my first post!!
tags:
- work
- first
date: 2022-07-24
---
```



如果你想隐藏帖子的 exif 值，你可以使用`hideExif`变量。还有可用`hidetitle`和`hideDate`变量。我们在“关于”页面中使用该变量，以便能够使用相同的布局创建单个页面。

```yaml
---
weight: 9
images:
- /images/my-image-1.jpg
- /images/my-image-2.jpg
multipleColumn: true
title: Here's my first post!!
tags:
- work
- first
date: 2022-07-24
hideExif: true
---
```



您可以在帖子中使用`title`, `subtitle`,变量。`url`

```yaml
---
images:
- /images/about.png
title: About!!
subtitle: Here's who am I.
url: me
hideTitle: true
hideExif: true
hideDate: true
---
```



完全支持 Markdown。

```yaml
---
weight: 9
images:
- /images/my-image-1.jpg
- /images/my-image-2.jpg
multipleColumn: true
title: Here's my first post!!
tags:
- work
- first
date: 2022-07-24
---

## Markdown

You can use **Markdown** format to write **your story**.

### Subtitle

Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni dolorem, laborum impedit doloremque ducimus repellat sapiente aut qui quae provident, cum vitae atque eius earum labore. Quae quod rem aliquid!

Some list

1. A b c
2. A b c
3. A b c 
```



对于登陆页面（_index.md），您可以`desc`在输入按钮下使用数组来设置描述。

```yaml
---
desc:
- Eternity is a minimalist Hugo theme
- designed for portfolio sites with a fresh feel.
---
```



对于登陆页面（_index.md），您可以使用`featuredTags`数组在登陆页面中显示一些标签。

```yaml
featuredTags:
  - title: people
    image: https://source.unsplash.com/random?people&1649630128
    url: /tags/people/
  - title: nature
    image: https://source.unsplash.com/random?nature&17346933
    url: /tags/nature/
```

## 个性化定制

翻译自 [Edit default statics](https://github.com/boratanrikulu/eternity/blob/main/doc/style.md)

Hugo 允许您在使用主题时编辑静态数据。因此，您可以覆盖任何文件。

我们建议更换这些静态数据；[**/static/logo.png**](https://github.com/boratanrikulu/eternity/blob/main/static/logo.png)、[**/static/background.jpeg**](https://github.com/boratanrikulu/eternity/blob/main/static/background.jpeg)、[**/static/CNAME**](https://github.com/boratanrikulu/eternity/blob/main/static/CNAME)、[**/static/favicon.ico**](https://github.com/boratanrikulu/eternity/blob/main/static/favicon.ico)。

您只需在项目中创建相关文件即可。他们应该在同一条路径上。
不要直接编辑主题，否则可能会破坏您将来的升级。

### 改变颜色

在您的存储库中创建[**/static/css/colors.css**](https://github.com/boratanrikulu/eternity/blob/main/static/css/colors.css)以便能够更改主题中使用的颜色。

### 更改宽度值

在您的存储库中创建[**/static/css/width.css**](https://github.com/boratanrikulu/eternity/blob/main/static/css/width.css)以便能够更改宽度值。

### 更改字体

在您的存储库中创建[**/layouts/partials/fonts.html**](https://github.com/boratanrikulu/eternity/blob/main/layouts/partials/fonts.html)以便能够更改字体。

### 高级定制

在您的存储库中创建[**/static/css/custom.css**](https://github.com/boratanrikulu/eternity/blob/main/static/css/custom.css)以便能够添加或覆盖 CSS 指令。

