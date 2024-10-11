1. ##### go语言中make和new的区别是什么

   `Golang slice、map、channel都是引用类型，他们的值是指向实际value地址的指针，函数传参都是传值，但是引用类型的传值实际上是是传递的指针副本，实际指向同一份数据`

   1. 作用变量类型不同，new给string,int和数组分配内存，make给切片，map，channel分配内存；
   2. new分配空间后，是将内存清零，并没有初始化内存；而make分配空间后，是初始化内存，而不是清零
   3. new 分配返回的是指针，即类型 *Type；make 返回引用，即 Type。

2. ##### rune类型是什么

   golang中的字符串底层实现是通过byte数组的，中文字符在unicode下占2个字节，在utf-8编码下占3个字节，而golang默认编码正好是utf-8

   byte 等同于int8，常用来处理ascii字符

   rune 等同于int32,常用来处理unicode或utf-8字符

   ```go
   sample := "我爱GO"
   runeSamp := []rune(sample)
   runeSamp[0] = '你'
   fmt.Println(string(runeSamp))  // "你爱GO"
   fmt.Println(len(runeSamp))  // 4
   ```

3. ##### 逃逸分析

   编译器决定内存分配位置的方式，就称之为逃逸分析，逃逸分析由编译器完成，作用于编译阶段

   `go build -gcflags="-m -l"`

   1. 函数返回局部变量指针。
   2. interface类型逃逸。
   3. 切片底层数组逃逸。
   4. 闭包捕获外部变量。

4. ##### 什么是函数式编程

   函数式编程是一种编程范式，和其他数据类型一样，函数可以作为参数，返回值

5. ##### Golang闭包是什么？

   闭包是**一个可以引用其作用域之外变量的函数**，是一种函数式编程

   ```go
   func adder() func(int) int {
   	sum := 0
   	return func(x int) int {
   		sum += x
   		return sum
   	}
   }
   
   func main() {
   	pos := adder()
   	for i := 0; i < 10; i++ {
   		fmt.Println(pos(i))
   	}
   }
   ```

6. ##### Go的泛型是什么？

   

7. 内存对齐

8. 屏障机制

