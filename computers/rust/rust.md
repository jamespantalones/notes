### Rust stuff (in progress learning)


#### Mean/avg/mode

```rust
fn avg(numbers: &[i32]) -> f32 {
    let mut sum = 0;
    for x in numbers {
        sum += x;
    }
    sum as f32 / numbers.len() as f32
}


fn main(){
    let v = vec![9203,12,594,2395,23,5];
    let a = avg(&v);
    println!("{}", a);
    
    
}
```

#### Struct setup
```rust
//allow println! to handles struct formatting
#[derive(Debug)]

//declare struct
struct Rectangle {
    width: u32,
    height: u32
}

//methods and associated functions on structs
impl Rectangle {
    //method. is borrowing ref from original struct
    fn area(&self) -> u32 {
        self.width * self.height
    }
    
    //another method, passing in another struct instance as param
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width >= other.width && self.height >= other.height
    }
    
    //associated function, called in a similar way to String::from
    fn square(size: u32) -> Rectangle {
        Rectangle{width: size, height: size}
    }
}

fn main(){
    let rect1 = Rectangle{width: 30, height: 50};
    let rect2 = Rectangle{width: 10, height: 40};
    let rect3 = Rectangle{width: 60, height: 45};
    let sq = Rectangle::square(3);
    
    println!("Can rect hold rect2? {}", rect1.can_hold(&rect2));
    println!("Can rect hold rect3? {}", rect1.can_hold(&rect3));
    println!("Area is still {}", rect1.area());
    println!("Area of square is {}", sq.area());
}
```
