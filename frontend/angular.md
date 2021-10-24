### 程序

视图View
    包含指令、绑定和表达式的 HTML 元素区域
    angular最小的UI单

属性指令：
    改变元素，组件，其他指令外观和行为的类
    放在普通元素，以属性的方式出现
    方括号[]被Angular解释成属性指令

结构型指令：
    通过添加，移除DOM元素改变DOM布局的类
    放在ng-template元素上，以属性的方式出现
    普通元素上的星号*和ng-template上的方括号[]被Angular解释成结构型指令

组件component：
    拥有模板的指令，是一个MVC单元

模块module：
    一个加载单元



```angular2html
<template>  : HTML的标准标签，不建议使用
<ng-template>:   <ng-template> tag will be rendered as a comment element, but is's content will be inserted
<ng-container>:The Angular <ng-container> is a grouping element that doesn't interfere with styles or layout because Angular doesn't put it in the DOM.
<ng-content></ng-content> 宿主元素的内容
```


当一个属性有星号
    将其展开成ng-template 和 方括号的形式
当一个属性有方括号
    寻找这个属性对应的指令定义
如果没有找到，匹配标准属性、属性、class或者style
如果找到了对应的指令定义，按照指令定义执行

属性指令（不动宿主元素，只操作其属性和内容）：
结构型指令（在宿主元素外套了一层ng-template，将宿主元素按内容操作）
组件（一般是自己定义了一个宿主元素）


1、确定宿主元素
    如果是属性指令，所在的元素是宿主元素
    如果是结构型指令，在外面展开成ng-template作为宿主元素
    如果是组件，（一般而言）本身就是宿主元素
2、指令和组件都有：宿主元素、子内容；组件比指令多了模板
3、指令、组件和关联的元素如何互动：（指令的宿主元素不是自己的，指令没有模板）
    关联宿主元素？constructor(element: ElementRef)
    获取宿主元素的其他属性的初始值？constructor(..., @Attribute("some-name")someAttr: string)
    关联宿主元素的其他属性的值？@HostBinding("class") someAttr: string
    监听宿主元素上的事件？@HostListener("click", ["$event.target.value"]) triggerEvent(newValue: string) { ... }
    指令属性的值？@Input("some-name") someName: someType
    定义一个事件钩子？@Output("some-event") someEvent = new EventEmitter<string>();
    通过这个钩子回调一个句柄？someEvent.emit(this.....)
    指令获得宿主元素的内容？@ContentChild(SomeDirType) contentChild: SomeDirType 或者 @ContentChildren(SomeDirType) contentChildren: QueryList<SomeDirType>
    组件获取模版的内容：@ViewChild(class) viewChild 或者 @ViewChildren(class) viewChildren


一个宿主元素可以有多个属性指令，但只能有一个结构指令
属性：[prop]
结构：*direct 会被展开成 <template></template>


服务引用
ElementRef
TemplateRef
ViewContainerRef
ViewRef

ComponentRef<C>
ApplicationRef
    tick()
EmbeddedViewRef



TS代表数据及其的变化
HTML，CSS代表数据的呈现

第一步，通过class定义一个类
第二步，通过装饰器，将这个类装饰成一个构造块
第三步，通过import和export机制，遍历整个代码，加载所有的构造块

内置指令
*ngIf
*ngFor
[ngClass]
[ngStyle]
[ngSwitch] *ngSwitchCase *ngSwitchDefault
[ngTemplateOutlet] [ngOutletContext]

```angular2html
<host *ngIf="expr" ...>...</host>
```
```angular2html
<ng-template ngIf="expr">
    <host ...>...</host>
</ng-template>
```

```angular2html
<host *ngFor="let item of items; let i=index; let odd=odd; trackBy:getKey" ...>...</host>
```

```angular2html
<ng-template ngFor [ngForOf]="items" let-item let-i="index" let-odd="odd">
    <host ...>...</host>
</ng-template>
```

```angular2html
<ng-template #name let-some="expr">...</ng-template>
<ng-template [ngTemplateOutlet]="name" [ngOutletContext]="map">...</ng-template>

<div *ngTemplateOutlet="some" [ngOutletContext]="expr">...</div>

<ng-template [ngTemplateOutlet]="some">
    <div [ngOutletContext]="expr">...</div>
</ng-template>
```

模版变量：index, odd, even, first, last





属性绑定
[property]="expr" 标准DOM属性绑定
[attr.name]="expr" 元素属性绑定（非标准DOM属性）

[class]="string expr"
[class.name]="bool expr"
[ngClass]="map[string]bool | string | array"

[style.name]="string expr"
[style.name.unit]="string expr"
[ngStyle]="map expr"

### 单向数据绑定：

求表达式的值，将值传给指令，指令根据值控制宿主元素

三要素：宿主元素、表达式、目标（指令或属性）
<host [target]="expr">

事件绑定（单向绑定）
三要素：宿主元素、表达式、目标（事件）
<host (event)="expr">

双向绑定
三要素：宿主元素、表达式、目标（ngModel指令）
<host [(ngModel)]="expr">

插值绑定：
{{expr}}

插值绑定的等价模式：
<foobar>some {{expr}} other</foobar>
<foobar [textContent]="'some '+{{expr}}+' other'"></foobar>


### 自定义属性指令
```typescript
@Directive({
    selector:"[name]"
})
export class SomeDirective{
    @Input("some-name")  someName: string
    @HostBinding("class") someAttr: string
    constructor(element: ElementRef, @Attribute("some-name")someAttr: string) { ... }
}
```

### 自定义事件
```typescript
@Directive({
    selector:"[name]",
})
export class SomeDirective{
    @Output("some-name") click = new EventEmitter<string>();
    constructor(element: ElementRef) {
        this.element.nativeElement.addEventListener("click", e=>{
            this.click.emit( ... )
        })
    }
}
export class SomeDirective{
    @Output("some-name") click = new EventEmitter<string>();
    @HostListener("click", ["$event.target.value"]) triggerEvent(newValue: string) { ... }
}
```

### 自定义双向绑定
```typescript
@Directive({
    selector:"[name]",
    exportAs: "SomeName",
})
export class SomeDirective{
    @HostBinding("value") someAttr: string //宿主属性的值
    @HostListener("input", ["$event.target.value"]) updateValue(newValue: string) { ... } //宿主的事件
    @Input("some-name")  someName: string //自定义属性的值
    @Output("some-name-change") update = new EventEmitter<string>(); //自定义的事件
    ngOnchange(change : {[property:string]:SimpleChange}){ ... } //当属性变化时执行
}
```

### 自定义结构指令
```typescript
@Directive({
    selector:"[name]",
})
export class SomeDirective{
    constructor(private container: ViewContainerRef, private template: TemplateRef<Object>) {...}
}
this.container.createEmbeddedView(this.template, new IteratorContext(){ ... } )
class IteratorContext {
    constructor(public $implicit: any, public ... ){
        this.a = ...
    }
}
```

### 自定义组件
```typescript
@Component({
    selector:"some-name",
    template:"",
    templateUrl:"",
    styles:"",  
    styleUrls:"",
    animations:"",
    encapsulation:"",
    moduleId:"",
    providers:"",
    viewProviders:"",
})
export class SomeComponent{
    constructor(
        private componentFactoryResolver: ComponentFactoryResolver,
        private elementRef: ElementRef,
        private injector: Injector,
        private appRef: ApplicationRef
    ){ ... }
    @ViewChild(SomeClass) viewChild
    @ViewChildren(SomeClass) viewChildren
    @ContentChild(SomeClass) contentChild: SomeClass // 宿主元素的第一个匹配的指令
    @ContentChildren(SomeClass) contentChildren: QueryList<SomeClass> // 宿主元素的匹配的指令
    ngOnInit(){}
    ngOnChanges(){}
    ngDoCheck(){}
    ngOnDestroy(){}
    ngAfterContentInit(){}
    ngAfterContentChecked(){}
    ngAfterViewInit(){}
    ngAfterViewChecked(){}
}
```

### 管道

#### 使用
```typescript
{{someValue | pipeName:param1:param2}}
```

#### 定义
```typescript
@Pipe({
    name:"someName",
    pure:bool,
})
export class SomePipe {
    transform(value:any, param1?:any, param2?:any){ ... }
}
```

### 服务

#### 使用
```typescript
constructor(@Inject() someService){ ... }
```

#### 定义
```typescript
@Injectable({
})
export class SomeService {
}
```

### 服务提供
```typescript
providers:[ 
    aService, 
    {provider:someToken, multi:true, useClass:someClass},
    {provider:someToken, multi:true, useValue:someValue},
    {provider:someToken, multi:true, useFactory:()=>{ ... }, deps:[aValue, bValue]},
    {provider:someToken, multi:true, useExisting:someToken},
]
```

### 模块
#### 定义
```typescript
@NgModule({
    imports:[AModule, BModule, CRounteModule],
    declarations:[ADirective, BComponent, CPipe],
    providers:[AService, BService],
    bootstrap:[AComponent],
    exports:[ADirector, BComponent, CPipe]
})
```

### 程序



