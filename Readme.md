# PHP Coding Exercises 🚀
### Basic Interview Assigments 
#### By Navneet Sharma
---

## 🔹 1. Sort Array ASC (Swap Elements)

```php
<?php
$a = [10, 90, 20, 70, 50, 20];
$n = count($a);

for($i=0; $i<$n; $i++){
    for($j=$i+1; $j<$n; $j++){
        if($a[$i] > $a[$j]){
            $temp = $a[$i];
            $a[$i] = $a[$j];
            $a[$j] = $temp;
        }
    }
}
print_r($a);
?>
```

## 🔹 2. Fibonacci Sequence (Upshift Numbers)
```php
<?php 
$num = 9;
$a = 0; $b = 1;

for($i=0; $i<$num; $i++){
    echo $a . "\n";
    $c = $a + $b;
    $a = $b;
    $b = $c;
}
?>
```
## 🔹 3.Largest & second number => downShift number

```php

<?php
 $a = [4,7,9,20,10,13,8];
 $count = count($a);
 $firstL = 0; $secondL = 0;
 
 for($i=0;$i<$count;$i++){
     $num = $a[$i];
     if($num > $firstL){
         $secondL = $firstL;
         $firstL = $num;
     }elseif($num > $secondL){
         $secondL = $num;
     }
 }
 
 echo "First Largest".$firstL."\n";
 echo "Second Largest".$secondL."\n";
```
## 🔹 4.Factorial number 
```php
<?php
$num = 5;
$fact = 1;
for($i= 0 ;$i<$num;$i++){
   $fact *= $num-$i;
}
echo $fact;


?>
```
## 🔹 5.Reverse String = str_split convert str to array 
```php
<?php
$str = 'Navneet';
$spltStr = str_split($str);
$len = count($spltStr);
$revStr = '';

for($i = $len-1; $i >=0; $i--){
 $revStr .= $spltStr[$i]; 
}
echo $revStr;

?>
```
## 🔹 6.Palindrom String = MADAM
```php
<?php
$str = 'madam'; //Navneet
$checkStr = strrev($str);
if($str == $checkStr){
    echo "Palidrome";
}else{
    echo "Not Palindrome";
}

?>
```
## 🔹 7. Swap Two Number without 3rd varibale
```php
<?php
$a= 6; $b= 5;
echo "Before Swap $a,$b";
$c = $a+$b;
$a= $c-$a;
$b = $c-$b;
echo "After Swap $a,$b";

?>
```
## 🔹 8. Remove duplicate from array
```php
<?php
$dupliArr = [10,20,40,60,30,20,60];
$len      = count($dupliArr);
$duplicate = false;
$uniqArr = [];

for($i=0;$i<$len; $i++){
    for($j=0;$j<count($uniqArr);$j++){
       
        if($dupliArr[$i] == $dupliArr[$j]){
            $duplicate = true;
            break;
        }
    }
    if(!$duplicate){
        $uniqArr[] = $dupliArr[$i];
    }
}
print_r($uniqArr);

?>
```

# 🔹 Oops and other concept
### 1. Class & Object:- 
    we can say class is just like a blueprint/structure of object, similarly for home we can build as many home as we want via using the same blueprint. We can defined the mehtod and property inside the class
    Object is the instance of class we can assing value to class property via using object. If we want to use class mehtod or property then we need to first create an object of that class

### 2. Encapsulation:- Where Data and property bundle together and access is controller through access modifier (Public, Private, Protected)
```php
    class BankAccount {
        // Properties (data)
        private $balance;
    
        // Constructor
        public function __construct($initialBalance) {
            $this->balance = $initialBalance;
        }
    
        // Method to deposit money
        public function deposit($amount) {
            if ($amount > 0) {
                $this->balance += $amount;
            }
        }
    
        // Method to withdraw money
        public function withdraw($amount) {
            if ($amount > 0 && $amount <= $this->balance) {
                $this->balance -= $amount;
            }
        }
    
        // Method to get current balance
        public function getBalance() {
            return $this->balance;
        }
    }
    
    // Usage
    $account = new BankAccount(1000);
    $account->deposit(500);
    $account->withdraw(200);
We can't access balance directly $account->balance that will hide the internal state  
```
### 3. Inheritance:- Reusing a parent class by extending.
```php
<?php
// Parent class
class Animal {
    public $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function speak() {
        echo $this->name . " makes a sound.<br>";
    }
}

// Child class (inherits Animal)
class Dog extends Animal {
    public function speak() {
        echo $this->name . " barks!<br>";
    }
}

// Usage
$dog = new Dog("Tommy");
$dog->speak(); // Output: Tommy barks!
?>
```
### 4. Traits:- A Trait is like a container of methods that you can include in multiple classes.If two trait have same mehtod then you can resolve conflicts with insteadof-> USE A,B
```php
<?php
trait A {
    public function sayHello() { echo "Hello from A<br>"; }
}

trait B {
    public function sayHello() { echo "Hello from B<br>"; }
}

class MyClass {
    use A, B {
        A::sayHello insteadof B;   // Use A’s method
        B::sayHello as sayHelloB;  // Alias B’s method
    }
}

$obj = new MyClass();
$obj->sayHello();   // Hello from A
$obj->sayHelloB();  // Hello from B

```
### 5. Abstraction:- Abstraction means hiding the implementation details and showing only the essential features of an object.->Cannot be instantiated directly.-> Method with body or wihtout body
```php
<?php
// Abstract class
abstract class Animal {
    abstract public function sound(); // abstract method (no body)

    public function sleep() {
        echo "Sleeping...<br>";
    }
}

// Child class must implement abstract method
class Dog extends Animal {
    public function sound() {
        echo "Bark!<br>";
    }
}

class Cat extends Animal {
    public function sound() {
        echo "Meow!<br>";
    }
}

$dog = new Dog();
$dog->sound(); // Bark!
$dog->sleep(); // Sleeping...

$cat = new Cat();
$cat->sound(); // Meow!
?>
```
### 6. Interface:- Only abstract methods (till PHP 7.x). From PHP 8 → can have default methods. Property Not allowed -> implement multiple
```php
<?php
interface PaymentGateway {
    public function pay($amount);
}

class PayPal implements PaymentGateway {
    public function pay($amount) {
        echo "Paid $amount using PayPal.<br>";
    }
}

class Stripe implements PaymentGateway {
    public function pay($amount) {
        echo "Paid $amount using Stripe.<br>";
    }
}

$payment1 = new PayPal();
$payment1->pay(100);

$payment2 = new Stripe();
$payment2->pay(200);
?>
```
### 7.Magic Methods in PHP:- __construct(), __destruct(), __get(), __set(), __call(), __toString()
#### __get() is a magic method that is automatically called when you try to access an inaccessible (private/protected/non-existing) property of an object.
#### __set() when you try to set a value to an inaccessible property

### 8.Static Keyword:- Belongs to the class, not object.Accessed using ClassName::methodName().
### 9.Final Keyword:- final class → Cannot be inherited.final method → Cannot be overridden.
### 10.Namespace:- Avoids class/method name conflicts.Declared with namespace keyword.


