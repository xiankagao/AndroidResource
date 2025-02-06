1. Kotlin 语言基础与进阶

1.1 语言基础

	1.	Kotlin 协程的 launch 和 async 有什么区别？在什么情况下选择 async 而不是 launch？
	2.	suspend 函数可以在哪些作用域中调用？如何在非协程作用域中调用 suspend 函数？
	3.	withContext 和 launch 的作用有什么不同？它们在 CoroutineScope 内部如何工作？
	4.	runBlocking 的作用是什么？它的使用场景是什么？为什么在 Android 中尽量避免使用？
	5.	Kotlin 中 inline 关键字的作用是什么？为什么 crossinline 和 noinline 关键字会一起使用？
	6.	解释 Kotlin 作用域函数 (let, apply, run, also, with) 的区别，并举例说明适用场景。
	7.	Kotlin 编译流程是怎样的？什么是 Kotlin Bytecode？

1.2 高级特性

	8.	Kotlin Flow 和 LiveData 的区别？什么情况下应该选择 Flow？
	9.	Kotlin StateFlow 和 SharedFlow 的区别？SharedFlow 适合什么场景？
	10.	Kotlin 的 Sealed Class 和 Enum 有什么区别？为什么 Sealed Class 更适合建模 UI 状态？
	11.	Kotlin object 关键字的三种用法是什么？如何在 Compose 中利用 object 进行优化？

2. Jetpack 组件

2.1 基础

	12.	在 ViewModel 中如何正确管理 CoroutineScope？为什么 viewModelScope 适合 UI 逻辑？
	13.	WorkManager 和 Foreground Service 有什么区别？在什么场景应该选择 WorkManager？
	14.	DataStore 相比 SharedPreferences 有哪些优势？如何在 Compose 中高效使用 DataStore？
	15.	Room 数据库如何保证数据变更时 UI 自动更新？

2.2 进阶

	16.	Paging 3 如何与 Jetpack Compose 结合使用？
	17.	Navigation Component 在 Compose 和 View 中的实现有何不同？
	18.	在 Jetpack Compose 中如何优雅地管理生命周期？例如 onStart/onResume 如何在 Composable 中处理？

3. Jetpack Compose UI 组件

3.1 基础

	19.	LazyColumn 和 RecyclerView 的底层实现有什么不同？
	20.	在 Compose 中 remember 和 rememberSaveable 有什么区别？什么时候应该使用 rememberSaveable？
	21.	如何在 Jetpack Compose 中监听 TextField 的输入变化？
	22.	Modifier 在 Compose 中的作用是什么？如何自定义 Modifier？
	23.	Compose 中 Box, Column, Row 的 Modifier 作用域有什么区别？

3.2 进阶

	24.	LazyColumn 如何高效支持 diffing？
	25.	DerivedStateOf 和 remember 在 Compose 中的区别？如何使用 DerivedStateOf 进行优化？
	26.	在 Compose 中如何高效处理大量 UI 组件的 State ？
	27.	Compose 中如何使用 produceState 处理异步状态？

4. Jetpack Compose 重组优化

	28.	什么是 Jetpack Compose 的 重组（Recomposition）？什么情况下会触发 重组？
	29.	如何避免 Jetpack Compose 组件的 过度重组？
	30.	Stable 注解的作用是什么？为什么 data class 在 Compose 中比 MutableState 更高效？
	31.	remember 和 rememberUpdatedState 有什么区别？如何避免 remember 带来的 重组 问题？
	32.	CompositionLocal 适用于什么场景？它如何影响 重组 ？
	33.	subcomposition 是什么？它如何影响 Compose 的 重组？

5. Jetpack Compose 手势事件处理

	34.	Modifier.pointerInput 和 Modifier.clickable 的区别？如何自定义 Compose 手势？
	35.	如何在 Compose 中实现复杂的 Drag 和 Swipe 交互？
	36.	MotionEvent 在 Compose 中是如何工作的？如何实现 NestedScrolling？

6. Compose & 原生 View 交互

	37.	如何在 Compose 中嵌套 AndroidView？如何在 AndroidView 中嵌套 Compose？
	38.	Compose 的 Canvas 和 Android View 的 Canvas 有什么不同？
	39.	Compose 如何与 XML 布局进行混合开发？有哪些性能问题需要注意？
	40.	在 Compose 中如何自定义 View ？

7. Compose 动画

	41.	updateTransition 和 animate*AsState 有什么区别？
	42.	如何在 Compose 中实现 Shared Element 动画？
	43.	AnimatedVisibility 是如何实现的？如何优化 AnimatedVisibility？
	44.	Compose 如何优化 动画性能，减少 重组？

8. Compose & 原生路由栈

	45.	Compose Navigation 和 Activity/Fragment 管理 Back Stack 的区别？
	46.	Compose 如何实现 多层 Fragment 嵌套导航？
	47.	Compose 如何与 深层链接（Deep Link） 结合使用？

9. Android View 体系

	48.	View.draw() 方法的调用流程是怎样的？
	49.	onMeasure, onLayout, onDraw 这三个方法分别在什么时候执行？
	50.	ViewGroup 如何处理 TouchEvent ？onInterceptTouchEvent 的作用是什么？
	51.	Handler、Looper、MessageQueue 之间的关系？
	52.	ThreadPoolExecutor 如何优化 Android 线程调度？

10. 综合实践与优化

	53.	在 Compose 开发中，如何优化 内存占用 和 布局过度重组？
	54.	你在 Compose 开发中遇到过哪些性能问题？是如何解决的？
	55.	如何在 Jetpack Compose 中正确使用 hilt 进行依赖注入？
	56.	如何在 Compose 组件 Previews 时模拟不同的 UI 状态？
	57.	你如何设计 Compose 组件，使其能够复用且性能最佳？






1. Kotlin 语言基础与进阶

1.1 语言基础

1. Kotlin 协程的 launch 和 async 有什么区别？

	•	launch 用于启动一个协程，但不返回结果（返回 Job）。
	•	async 用于启动一个协程，并返回 Deferred<T>，可以用 .await() 获取结果。
	•	选择 async 而不是 launch 的情况：
	•	需要并行计算多个值，并在后续合并它们的结果。
	•	例如：

val result1 = async { fetchData1() }
val result2 = async { fetchData2() }
val finalResult = result1.await() + result2.await()



2. suspend 函数可以在哪些作用域中调用？

	•	suspend 函数只能在协程作用域或其他 suspend 函数中调用，不能在普通函数中直接调用。
	•	在非协程作用域调用时，需要 CoroutineScope.launch 或 runBlocking：

fun main() {
    runBlocking {
        mySuspendFunction()
    }
}

suspend fun mySuspendFunction() {
    delay(1000)
    println("Hello from suspend function")
}



3. withContext 和 launch 的作用有什么不同？

	•	withContext 切换协程的执行线程，但不会创建新协程，执行完后会返回结果。
	•	launch 创建一个新的协程，但不会阻塞当前协程的执行。

示例：

suspend fun fetchData() {
    withContext(Dispatchers.IO) {
        // 在 IO 线程池执行
        val data = database.loadData()
    }
}

fun main() = runBlocking {
    launch {
        fetchData()
    }
}

4. runBlocking 的作用是什么？为什么应避免使用？

	•	runBlocking 会阻塞当前线程，直到协程执行完毕，因此不推荐在 Android UI 线程中使用。
	•	适用于 测试 或 同步启动协程环境，但在 Android 中应尽量避免使用。

fun main() {
    runBlocking {
        delay(1000)
        println("Hello, Coroutine!")
    }
}

5. Kotlin inline 关键字的作用是什么？

	•	inline 在编译时将函数代码复制到调用处，减少函数调用开销。
	•	crossinline 用于禁止 return 从 lambda 直接返回外部函数。
	•	noinline 用于防止某些 lambda 进行内联。

inline fun execute(action: () -> Unit) {
    println("Before action")
    action()
    println("After action")
}

6. Kotlin 作用域函数 (let, apply, run, also, with) 的区别？

函数	作用	适用场景
let	作为 it 传入，返回 lambda 结果	可用于链式调用或非空判断
apply	作为 this 传入，返回原对象	修改对象属性后返回自身
run	作为 this 传入，返回 lambda 结果	单次对象操作（如初始化）
also	作为 it 传入，返回原对象	日志记录、调试
with	作为 this 传入，返回 lambda 结果	适用于不需要返回 this 的场景

示例：

val user = User().apply {
    name = "Alice"
    age = 25
}.also {
    println("User created: $it")
}

7. Kotlin 编译流程是怎样的？

	1.	Kotlin 源代码（.kt）
	2.	编译为字节码（.class）
	3.	JVM 执行
	4.	Android DEX 转换（.dex）
	5.	ART（Android 运行时）执行

2. Jetpack 组件

2.1 基础

8. viewModelScope 为什么适合 UI 逻辑？

	•	viewModelScope 绑定 ViewModel 生命周期，避免内存泄漏。
	•	当 ViewModel 被清理时，协程会自动取消。

9. DataStore 与 SharedPreferences 的区别？

特性	DataStore	SharedPreferences
存储方式	基于 protobuf 或 Preferences	基于 XML
线程安全	完全线程安全	存在同步问题
读写方式	Flow 订阅更新	get 和 put

示例：

val userPreferences: Flow<Int> = dataStore.data.map { it[USER_AGE] ?: 0 }

10. Paging 3 如何与 Jetpack Compose 结合使用？

	•	结合 LazyColumn 和 collectAsLazyPagingItems()：

val items = viewModel.pager.flow.collectAsLazyPagingItems()

LazyColumn {
    items(items) { item ->
        Text(text = item.title)
    }
}

3. Jetpack Compose UI 组件

11. LazyColumn 与 RecyclerView 的区别？

特性	LazyColumn	RecyclerView
复用机制	Compose 采用 记忆化	RecyclerView 采用 ViewHolder
布局方式	Modifier	LayoutManager

12. remember 和 rememberSaveable 的区别？

	•	remember 仅在 重组（Recomposition） 期间保持状态。
	•	rememberSaveable 在 进程死亡（Process Death）后仍可恢复。

val count = remember { mutableStateOf(0) }
val savedCount = rememberSaveable { mutableStateOf(0) }

13. 如何避免 Jetpack Compose 组件的 过度重组？

	1.	使用 remember 记住状态
	2.	拆分 Composable，降低 Composition 影响范围
	3.	使用 DerivedStateOf 避免 State 不必要的 重组

val filteredList = remember { derivedStateOf { items.filter { it.isVisible } } }

继续解答剩余部分的面试题：

4. Jetpack Compose 重组优化

14. 什么是 Jetpack Compose 的 重组（Recomposition）？

	•	重组（Recomposition） 指的是 Jetpack Compose 重新执行 Composable 函数，以更新 UI 状态。
	•	触发条件：
	1.	State 发生变化
	2.	remember 之外的数据更新
	3.	LaunchedEffect 重新触发

示例：

var count by remember { mutableStateOf(0) }

Button(onClick = { count++ }) {
    Text("点击次数: $count")
}

	•	当 count 更新时，Button 和 Text 组件会被重组。

15. 如何优化 Jetpack Compose 组件的 重组？

	1.	拆分 Composable，降低 重组 影响范围
	2.	使用 remember 避免不必要的 重组
	3.	使用 DerivedStateOf 处理派生状态
	4.	使用 Stable 确保数据结构优化
	5.	使用 Immutable 避免 State 变化触发不必要 重组

示例：

@Composable
fun Counter() {
    var count by remember { mutableStateOf(0) }
    Column {
        Text("Count: $count") // 只会在 `count` 更新时重组
        Button(onClick = { count++ }) {
            Text("Increment")
        }
    }
}

	优化点：如果 Button 逻辑不变，就不会因 count 变化而 重组。

5. Jetpack Compose 手势事件处理

16. Modifier.pointerInput 和 Modifier.clickable 的区别？

方法	作用	适用场景
pointerInput	监听 PointerEvent 事件	复杂手势（滑动、长按）
clickable	处理 Click 事件	简单点击

示例：

Box(
    modifier = Modifier
        .pointerInput(Unit) {
            detectTapGestures(onDoubleTap = { println("Double tapped") })
        }
)

17. 如何在 Compose 中实现复杂的 Drag 和 Swipe 交互？

	•	使用 Draggable 或 detectDragGestures 处理拖拽：

var offsetX by remember { mutableStateOf(0f) }

Box(
    Modifier
        .offset { IntOffset(offsetX.roundToInt(), 0) }
        .draggable(
            orientation = Orientation.Horizontal,
            state = rememberDraggableState { delta -> offsetX += delta }
        )
)

6. Compose & 原生 View 交互

18. 如何在 Compose 中嵌套 AndroidView？

AndroidView(
    factory = { context -> TextView(context).apply { text = "Hello, View!" } }
)

	场景：需要复用原生 View 组件时，如 MapView。

19. Compose 的 Canvas 和 Android View 的 Canvas 有什么不同？

	•	Compose 的 Canvas 通过 Modifier.drawWithCache 进行增量绘制，避免不必要的 invalidate()。

示例：

Canvas(modifier = Modifier.size(100.dp)) {
    drawCircle(Color.Red, radius = size.minDimension / 2)
}

7. Compose 动画

20. updateTransition 和 animate*AsState 的区别？

方法	作用	适用场景
updateTransition	管理多个动画状态	多个状态过渡
animate*AsState	处理单个值的动画	简单数值变化

示例：

val size by animateDpAsState(if (expanded) 200.dp else 100.dp)

8. Compose & 原生路由栈

21. Compose Navigation 和 Activity/Fragment 的区别？

	•	Compose 通过 NavHost 管理导航，而 Fragment 依赖 FragmentManager。

示例：

NavHost(navController, startDestination = "home") {
    composable("home") { HomeScreen() }
}

9. Android View 体系

22. View.draw() 方法的调用流程是怎样的？

	1.	measure()
	2.	layout()
	3.	draw()

23. ViewGroup 如何处理 TouchEvent？

	•	事件传递流程：
	•	dispatchTouchEvent()
	•	onInterceptTouchEvent()
	•	onTouchEvent()

10. 综合实践与优化

24. 在 Compose 开发中，如何优化 内存占用 和 布局过度重组？

	1.	尽量使用 remember
	2.	避免 过度重组
	3.	使用 LazyColumn 避免 无必要的组件创建
	4.	使用 produceState 处理异步数据


