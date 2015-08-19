

# Alloy 快速入门 #

## 概述 ##

本文提供了对安装Alloy命令行界面(CLI)及创建项目的基本介绍。

## 命令行界面安装 ##

Alloy命令行界面及插件应该是被Titanium Studio更新器自动安装的，可以参考此[快速入门](http://docs.appcelerator.com/titanium/latest/#!/guide/Quick_Start)。

如果安装出了问题或者你想独立安装Alloy CLI，可以参考以下的指导。

### 手动安装 ###

在安装Alloy CLI之前，需要安装配置好了Titanium SDK的3.0.x或更新版本。

然后下载并安装Node.js，下载地址：http://nodejs.org/#download ,我们将用它的npm包管理器来安装Alloy。

打开控制台窗口，运行下面的命令：
```bash

sudo npm install -g alloy
```

默认情况下，会安装最新的Alloy版本。要想安装一个指定的版本，使用同样的方法，在'alloy'后加上'@'符合及版本号。比如运行```
sudo npm install -g alloy@1.0.0```将安装1.0.0版本。

## 创建项目 ##

### 使用Titanium Studio的方式 ###

To create a new Alloy project, start Titanium Studio, then

From the menu, select File > New > Titanium Project. The New Titanium Project wizard appears.

Select Alloy in the Available Templates box, choose a template, then click the Next button.

Complete all of the fields, then click the Finish button.

A new skeleton Alloy project will be generated. Note that the Resources folder is hidden from the App and Project Explorer.

### 使用命令行的方式 ###

To create a new Alloy project, run the following commands:

```bash

titanium create --name=appname --id=com.domain.appname --platforms=android,ipad,iphone,mobileweb
cd appname
alloy new
```

A new skeleton Alloy project will be generated in the appname directory.

## 简单实例 ##

The following example converts the image\_view\_file.js file from the Titanium KitchenSink sample application to an Alloy project.

To see the example in the KitchenSink application, click on the Base UI tab, then navigate to Views > Images Views > Image File.

### 视图 ###

The view file declares the structure of the GUI. For example, the file below defines a window with an image and label.

Replace the contents of app/views/index.xml with the following:

```xml


<Alloy>
<Window>
<ImageView id="imageView" onClick="clickImage"/>
<Label id="l">Click Image of Apple Logo

Unknown end tag for &lt;/Label&gt;




Unknown end tag for &lt;/Window&gt;




Unknown end tag for &lt;/Alloy&gt;



```

### 样式 ###

The style file formats and styles the components in the view file. For example, the style below defines the background color of the window; position, dimensions and color of the label; and position, dimensions and location of the image.

Replace the contents of app/styles/index.tss with the following:

```json

"Window": {
backgroundColor:"white"
},
"#l":{
bottom:20,
width: Ti.UI.SIZE,
height: Ti.UI.SIZE,
color:'#999'
},
"#imageView":{
image:"/images/apple_logo.jpg",
width:24,
height:24,
top:100
}
```

### 控制器 ###

The controller file contains the presentation logic, which responds to input from the user. For example, the controller code below creates an alert dialog when the user clicks on the image and opens the window when the application starts.

Replace the contents of app/controllers/index.js with the following:
```javascript

function clickImage(e) {
Titanium.UI.createAlertDialog({title:'Image View', message:'You clicked me!'}).show();
}

$.index.open();
```

### 资源文件 ###

Create a folder called app/assets/images and copy the apple\_logo.jpg file from the KitchenSink project. This file will be copied to Resources/images/apple\_logo.jpg by Alloy during the build process.

### 编译与运行 ###

#### Using Titanium Studio ####

For the Mobile Web platform, compile the application using the CLI, then run it with Titanium Studio. Run the following command from a console to compile the application:

```

alloy compile --config platform=mobileweb
```

In the App Explorer view, click the Run button and select the device to launch the application. Alloy will generate the Titanium files from the Alloy project files, which will then be compiled by Titanium Studio and launched on the device simulator.

#### Using the CLI ####

For the Mobile Web platform, run the application from Titanium Studio after compiling it.

From a console window, go to the root directory of the project, then
```

titanium build [-p platform]
```

Refer to the Titanium Command-Line Interface Reference for more information about using the titanium build command.

## 更多实例 ##

For more simple usage examples of Alloy, go to the alloy/test/app directory on the Alloy github project.