# VsCode插件汇总

## 1.Project Manager

### `引用`

推荐文章：[Vscode使用插件Project Manager管理项目](https://blog.csdn.net/weixin_39493668/article/details/127071322)

### `摘要`

```
每次在vscode中更换项目时，都需要更换虚拟环境，编译器以及编译路径非常麻烦，所以可以使用vscode中的插件Project Manager来快捷转换。
```

### `部署`

首先在Extensions中搜索并下载插件

![picture 1](../images/7cf4288544437beb10b3a3ce85222d27627ee9bcab6bd2b8b1ac296f34f20485.png)  

下载后出现右侧的标签，就是project manager项目管理器

### `使用`

1. 在文件中选择打开文件夹，打开你想要管理的项目文件

    ![picture 2](../images/db3d469462bec1e2ec57be1f48923f371bb78412d28bfc752a190a40ea4f7737.png)  

2. ctrl+shift+p打开如下命令面板，并输入project manager找到save project这一项
   
    ![picture 3](../images/939ffa13c35cc8aee9dda8850c7e91fad6e0cb19e9407371d2c2a585d7c5439d.png) 

<br> 

## 2.Markdown Image

### `摘要`

```
在 Visual Studio Code 中，快捷上传图片
那么我们就需要一款插件，来实现快捷键快速粘贴图片等操作，照例打开EXTENSIONS选项卡，这里推荐两款，Markdown Image 和 PicGo。本文以Markdown Image为例（因为它能自定义上传接口）。
```

### `部署`

首先在Extensions中搜索Markdown Image并下载插件

![picture 4](../images/66c737ba25dd7c1f2baaae987ae7c2a8dda2ec1f667bd9de2ac5e10db7526fa0.png) 

### `使用`

安装后打开设置，我们可以看到这样一个选项，我们可以根据需求选择图床。直接推送到你的托管平台可以选择 Local ，不想折腾，对速度要求不高的可以选择 SM.MS Imgur 这两个图床，点开 Options ，根据提示注册并填入字段即可。

![picture 5](../images/31d9b8ca6ed6b5c148a17df82ab06722dd134dcb8a833f84ac81d89695b9588e.png)  

```
现在，我们新建一个 Markdown 文件，应该就可以看到md源文件和预览啦~现在我们测试一下是否能上传。右键看到快捷键是 Shift+Alt+V 测试一下，就能粘贴啦~
```

<br>

## 3.MybatisX

### `摘要`

```
MybatisX 弥补了在 VSCode 下没有高效、功能强大的 Mybatis 辅助功能插件，该插件当前还处于预览版本，特性与BUG会持续修复，请放心安装，让你拥有比 Idea 更强大的 MybatisX 增强功能。
```

### `部署`

首先在Extensions中搜索MybatisX并下载插件

![picture 6](../images/7f82d85a629c3aed6198c43a9b3fdd08e1956636fc000276959b4cc5c1ae06a9.png)  


### `使用`

点击下图此处即可实现mapper之间的跳转

![picture 7](../images/5c206f3e6f5b48808e973f74c84d58adb846614de9e2496585d01a4538505ab1.png)  

<br>

## 4.Todo Tree

### `引用`

推荐文章：[Vscode 插件：Todo Tree 简介和使用方法](https://blog.csdn.net/weixin_52739099/article/details/136619442)

### `摘要`

```
Todo Tree 是 Visual Studio Code（VS Code）中一款强大的插件，可以帮助你管理项目中的 TODO 注释和其他标记。通过扫描你的项目文件，并将其中包含的待办事项和自定义标记显示在一个树状视图中，Todo Tree 使得跟踪项目中的任务变得更加容易。
```

### `部署`

你可以通过以下步骤在 VS Code 中安装 Todo Tree 插件：
1. 打开 VS Code。
2. 点击左侧的扩展图标或按 Ctrl+Shift+X 打开扩展视图。
3. 在搜索栏中输入 “Todo Tree”。
4. 在搜索结果中找到 Todo Tree，然后点击 “安装” 按钮。

### `使用`

安装完 Todo Tree 插件后，你可以按照以下步骤使用它：

1. **启用 Todo Tree**： 打开任何项目文件后，按 Ctrl+Shift+P 打开命令面板，然后输入 “Toggle Todo Tree” 并选择该命令以启用 Todo Tree 视图。

2. **查看待办事项**： 在 Todo Tree 视图中，你将看到项目中的所有待办事项和标记按照文件结构呈现为树状列表。每个待办事项都附带文件路径和行号信息。

3. **筛选待办事项**： Todo Tree 支持快速筛选待办事项。你可以在搜索框中输入关键字来过滤显示的待办事项，以便更快地找到你感兴趣的内容。

4. **自定义标记**： 除了默认的 TODO 标记外，你还可以在项目中使用自定义的标记。只需按照注释的格式书写自定义标记，Todo Tree 将会识别并在树状视图中显示。

5. **配置选项**： Todo Tree 提供了丰富的配置选项，你可以根据自己的需要调整插件的行为。你可以通过点击 Todo Tree 视图右上角的齿轮图标或者在 VS Code 的设置中找到 Todo Tree 进行配置，也可以在setting.json文件中自定义更改todo tree的配置。

6. 更多详情请查看 TODO Tree 官方链接

<br>

## 5.Dracula Theme Official

### `摘要`

```
Dracula Theme Official是一款VS Code的主题插件，推荐使用这款插件的“Dracula Theme”主题。
```

### `使用`

安装后直接可以使用，没什么太多可以说明的。