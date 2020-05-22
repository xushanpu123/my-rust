# Day 1（2020-05-22）

目标：完成rustlings所有练习并记录下关键语法。

1、变量声明关键字:

```rust
let x=10;
```

2、声明数据类型(let x ：数据类型)

let x :u32=10;

3、if语句(不加括号）

```rust
if 表达式

{

 

}

else

{

 

}
```

4、输出（{}类似于C++中的”%d”等）

 

```rust
println!(“the value is {}”,x);//自动换行，如果不换行使用print!。
```

5、可更新数值的变量的定义（加入关键字mut，不加入的话默认为不可变更）：

 let mut x=3;

6、rust可以重复定义变量使得之前定义的变量被隐藏

```rust
fn main() {

  let mut number = "3";

  println!("Number {}", number);

  let  number = 3;

  println!("Number {}", number);

}
```

7、函数参数(fn function(x: 参数类型)

```rust
fn main() {

  call_me(3);

}

 

fn call_me(num: u32) {

  for i in 0..num {

​    println!("Ring! Call number {}", i + 1);

  }

}
```

8、循环语句for i in lo..hi（具体代码参考7）

9、带返回值的函数 fn function(参数) -> 返回值类型（返回值可以直接写单独的返回变量【但是不能加分号变成语句】，也可以加return）

```rust
fn main() {

  let original_price = 51;

  println!("Your sale price is {}", sale_price(original_price));

}

 

fn sale_price(price: i32) ->i32 {

  if is_even(price) {

​    price - 10

  } else {

​    price - 3

  }

}

 

fn is_even(num: i32) -> bool {

  num % 2 == 0

}
```

此处第一次出现了问题：sale_price()的返回值我开始设置的是u32，但是它却报错了，说明rust并没有C语言那样能够自动进行数据类型转换的功能。

10、字符型变量的接口（判断是否为数字或者字母）

```rust
let my_first_initial = 'C';

  if my_first_initial.is_alphabetic() {

​    println!("Alphabetical!");

  } else if my_first_initial.is_numeric() {

​    println!("Numerical!");

  } 
```

11、数组

 Rust数组的声明方式为let a:[type;size]，而且必须给元素初始化,一个简单初始化的方式为

```rust
 let a: [type; size]=[default;size];

 fn main() {

  let a: [i32; 100]=[0;100];

 

  if a.len() >= 100 {

​    println!("Wow, that's a big array!");

  } else {

​    println!("Meh, I eat arrays like that for breakfast.");

  }

}
```

12、截取数组元素

```rust
  let a = [1, 2, 3, 4, 5];

 

  let nice_slice = &a[1..4];
```

13、tuple类型：(访问tuple中的元素为tuple.index【此处index与数组访问类似】)

  元组是一个将多个其他类型的值组合进一个复合类型的主要方式。元组长度固定：一旦声明，其长度不会增大或缩小。

 

```rust
 fn main() {

  let cat = ("Furry McFurson", 3.5);

  let (name,age)= cat;

 

  println!("{} is {} years old.", name, age);

}

fn main() {

  let numbers = (1, 2, 3);

  println!("The second number is {}", numbers.1);

}
```

14、classic_c struct 

定义：

```rust
fn main() {

struct User {

  username: String,

  email: String,

  sign_in_count: u64,

  active: bool,

}

}
```

初始化实例：

 

```rust
#![allow(unused_variables)]

fn main() {

struct User {

  username: String,

  email: String,

  sign_in_count: u64,

  active: bool,

}

 

let user1 = User {

  email: String::from("someone@example.com"),

  username: String::from("someusername123"),

  active: true,

  sign_in_count: 1,

};

}
```

15、tuple结构体

struct strc(类型1,类型2....)

初始化：

strc S=(对应类型的数据)

调用:strc.0,strc.1..

16、字符串相关问题

形如“abc”默认为&’static &str型，转化为String 需要调用String::from()。\

String s2=s1之后，s1的引用就无效了。如果需要深度克隆，需要调用s2=s1.clone()

 

