1. 介绍
TypeScript是微软开发的javaScript超集,主要用于类型规范和检查,方便开发大型项目,可以编译成纯JavaSript代码,运行在任意浏览器上
2. 和NodeJs的关系
nodejs是javaScript的运行环境,可以安装TypeScript和其编译工具,在我们编写了TypeScript代码后,只有使用tsc将TypeScript代码编译为javaScript代码,才能在Nodejs的环境中运行.
3. TypeScript添加关键字
    1) 基础语法
    const hello : string = "Hello World!" // : string
    2) 基本数据类型
        any/number/string/boolean 
    3) 添加接口类型
    4) 增加类
    TypeScript 是面向对象的 JavaScript。
    类描述了所创建的对象共同的属性和方法。
    //
    class Person {
    }
    //
    var Person = /** @class */ (function () {
        function Person() {
        }
        return Person;
    }());
    5) 使用namespace解决重名的问题,export之后才能被外部模块使用
    namespace SomeNameSpaceName { 
    export interface ISomeInterfaceName {      }  
    export class SomeClassName {      }  
    }
    //
    SomeNameSpaceName.SomeClassName;
    6) .ts文件是标准的TypeScript文件,.tsx是包含JSX语法的TypeScript文件





 








    






