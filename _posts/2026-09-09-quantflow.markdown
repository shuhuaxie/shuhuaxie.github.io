- flutter 有多少种key
	- 全局
		一个引擎只有一个widget树，引擎唯一
		- GlobalKey 
			- GlobalKey
			- GlobalObjectKey
	- 本地
		只在【同一个直接父节点的子节点】之间生效，
		不同父节点之间互不干扰、互不比较！
		这就是 “局部” 的真正含义。
		- Key
			- ValueKey
			- ObjectKey
			- UniqueKey
			- PageStorageKey

flutter 语法
- const 和 final 的区别
	1. 赋值时机不同
		- const 必须在编译时赋值，final 可以在运行时赋值
	2. 可修改性：都不能二次赋值
	3. 变量是否可以改变
		- const 是彻底不可变：变量 + 对象内容 全锁死
			const 构造函数的类，所有字段必须是 final
		- final 只是「变量不可变」，对象内部还能变
	4. 实例复用（const 缓存）
		- const 构造的对象，会全局复用同一个实例，const Widget 能减少重建、提升性能
	5. 使用场景
		- const 是编译时常量，限制极多
		- final 是运行时只读，限制宽松，兼容所有 const 场景
包引用的区别
	- import 'package:jw_pos_client/apps/inits/inits.dart';
	- import 'path/to/my_other_file.dart';
	相对路径：以当前文件位置为基准，依赖文件间的层级关系。
	Package 路径：以 ** 项目根包（lib/）** 为基准，与当前文件位置无关，是 “绝对定位”。
	大型项目统一用 Package 路径，避免使用相对路径，因为相对路径会依赖当前文件的位置，不方便重构。
类
	- 单继承
	- mixin 混入，类似于继承，但是可以同时继承多个类
		- 语法：class 类名 with 混入类1, 混入类2, ...
		- 作用：在类中添加额外的功能，而不会改变类的继承关系
		- 注意：mixin 类不能直接实例化，只能被其他类混入
		- on 关键字：指定混入的类，必须是 mixin 类的子类
		- 例如：class 类名 with 混入类1, 混入类2, ... on 父类
	- extends 和 implements 区别
		- extends 继承，implements 实现
		- extends 只能继承一个父类，implements 可以实现多个接口
		用 extends 抽象类
			是继承关系
			可以复用父类已实现的方法
			只需要重写抽象方法
		用 implements 抽象类
			是接口契约
			完全不复用父类代码
			所有方法（抽象 + 已实现的）全都要手动重写
flutter和原生通讯的方法
	MethodChannel 方法通道（最常用） 调原生功能、要返回值
	BasicMessageChannel 基础消息通道 传二进制 / 大文件 / 自定义报文
	EventChannel 事件通道 原生持续回调、状态监听


