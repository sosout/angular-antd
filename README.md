# Angular 标准参考教程（alpha）

此项目是基于Angular脚手架 [Angular CLI](https://github.com/angular/angular-cli) 搭建的。Angular CLI是一个命令行界面工具，它可以创建项目、添加文件以及执行一大堆开发任务，比如测试、打包和发布，此版本为1.7.3。

## 1、快速上手

### 1.1 设置开发环境

在开始工作之前，请先在终端/控制台窗口中运行命令 node -v 和 npm -v， 来验证一下你正在运行 node 6.9.x 和 npm 3.x.x 以上的版本，更老的版本可能会出现错误，更新的版本则没问题。如果你的电脑里没有Node.js®和npm，请安装[它们](https://nodejs.org/en/download/)。

然后全局安装 [Angular CLI](https://github.com/angular/angular-cli)：

```javascript
$ npm install -g @angular/cli
```

### 1.2 启动开发服务器

进入项目目录，并启动服务器。

```javascript
$ cd my-app
$ ng serve --open 或 npm start
```

ng serve命令会启动开发服务器，监听文件变化，并在修改这些文件时重新构建此应用。使用--open（或-o）参数可以自动打开浏览器并访问http://localhost:4200/。

### 1.3 用命令快速创建 Angular 对应内容

运行 `ng generate component component-name` 命令生成组件。 你也可以使用 `ng generate directive|pipe|service|class|guard|interface|enum|module` 生成相对应内容。

### 1.4 构建

运行 `ng build`命令生成项目。生成的工件将存储在 `dist/` 目录中。使用`-prod` 标志构建生成环境项目。

### 1.5 单元测试

运行 `ng test` 通过 [Karma](https://karma-runner.github.io) 执行单元测试。

### 1.6 单点测试

运行 `ng e2e` 通过 [Protractor](http://www.protractortest.org/) 执行单元测试。

### 1.7 帮助

运行 `ng help` 获得 Angular CLI 更多帮助或者去查看 [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md)。

## 2、基本语法

### 2.1 常用命令

```javascript
$ npm install -g @angular/cli // 安装 Angular CLI 命令行工具

$ ng new appName // 创建应用

$ ng serve --open // 启动应用服务器

$ ng generate component componentName // 创建组件

$ ng generate service serviceName // 创建服务

ng generate service serviceName --module=app // 创建服务，通过 --module=app 选项让 CLI 自动把它提供给 AppModule
```

### 2.2 概念

1、ngOnInit 是一个生命周期钩子，Angular 在创建完组件后很快就会调用 ngOnInit。这里是放置初始化逻辑的好地方。

2、Angular 需要知道如何把应用程序的各个部分组合到一起，以及该应用需要哪些其它文件和库。 这些信息被称为元数据（metadata）。有些元数据位于 @Component 装饰器中，你会把它加到组件类上。 另一些关键性的元数据位于 @NgModule 装饰器中。最重要的 @NgModule 装饰器位于顶级类 AppModule 上。

CLI 自动生成了三个元数据属性：

selector— 组件的选择器

templateUrl— 组件模板文件的位置。

styleUrls— 组件私有 CSS 样式表文件的位置。

4、管道（ | ） 是格式化字符串、金额、日期和其它显示数据的好办法。 Angular 发布了一些内置管道，而且你还可以创建自己的管道。比如绑定表达式中的 uppercase 位于管道操作符（ | ）的右边，用来调用内置管道 UppercasePipe

### 2.3 属性绑定

1、{{ }}(双花括号)语法是 Angular 的插值绑定语法。

2、[(ngModel)] 是 Angular 的双向数据绑定语法。注意：ngModel 是一个有效的 Angular 指令，不过它在默认情况下是不可用的。它属于一个可选模块FormsModule，你必须自行添加此模块才能使用该指令。

3、(click) 这是 Angular 事件绑定 语法的例子。

4、Angular 的 CSS 类绑定机制让根据条件添加或移除一个 CSS 类变得很容易。 只要把 [class.some-css-class]="some-condition" 添加到你要施加样式的元素上就可以了。

### 2.4 指令

1、*ngFor 是一个 Angular 的复写器（repeater）指令。 它会为列表中的每项数据复写它的宿主元素。

2、*ngIf 是一个 Angular 的条件指令。

### 2.5 装饰器

1、@NgModule模块装饰器

2、@Component装饰器

@Component装饰器，用于为该组件指定 Angular 所需的元数据。

3、@Input() @Output() @HostBinding @HostListener @ContentChild装饰器

4、@Injectable装饰器

@Injectable() 装饰器告诉 Angular 这个服务本身可能拥有被注入的依赖。

5、@Pipe({...})管道装饰器

6、@SkipSelf装饰器

7、@Directive指令装饰器

## 常见错误

1、安装 Angular CLI 命令行工具` npm install -g @angular/cli ` 出现4058错误。

原因：可能是网路问题，可以尝试使用淘宝镜像。

```javascript
$ npm install -g cnpm --registry=https://registry.npm.taobao.org

$ cnpm install -g @angular/cli
```

2、` ng generate ` 出现Error: ELOOP: too many symbolic links encountered, stat。。。错误

原因：可能是因为使用 cnpm 安装导致的，可以把项目中 使用cnpm安装的node_modules文件夹 删掉，然后 在 package.json 同级目录 下，使用 npm install 安装