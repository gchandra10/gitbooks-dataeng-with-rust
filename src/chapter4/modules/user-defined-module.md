# User Defined Module

The Powerful module system can split the code into hierarchical logical units.

The module is a collection of items: functions, structs, and even other modules.

By default, items in a module are private; they can be changed to the public by adding **pub** before it.

Simple example

```
// Mod

mod sales{
    pub fn meet_customer(){
        println!("meet customer"); 
    }
       
}

fn main(){
    sales::meet_customer();
   
}
```

Pass params

```
    mod sales {
        pub fn meet_customer(num:i32) {
            println!("meet customer {num}");
        }
    }


fn main() {
    sales::meet_customer(1);
}
```



Companies have multiple depts so nesting the modules help in the hierarchy.

Note Sales module has to pub.

```

mod departments {
    pub mod sales {
        pub fn meet_customer(num:i32) {
            println!("meet customer {num}");
        }

    }
}

fn main() {
    departments::sales::meet_customer(1);
}

```

Exposing only limited functionality

```
// Here meet_customer calls get_number as that function is not 
// not exposed to main function

mod departments {
    pub mod sales {
        pub fn meet_customer(num:i32,requestedby:&str) {
            println!("meet customer {num}");
            let phone_number = get_number(num, requestedby);
            println!("calling {:?}", phone_number);
        }

        fn get_number(num:i32,requestedby:&str) -> String {
            println!("{requestedby}");
            let phonenumber = match num {
                1 => "123-456-7890".to_string(),
                2 => "987-654-3210".to_string(),
                _ => "000-000-0000".to_string()
            };
            
            if requestedby == "Manager"{
                return phonenumber
            }
            else if requestedby == "CustService"
            {
                return phonenumber[8..].to_string()
            }
            else{
                return "".to_string()
            }
        }
    }
}

fn main() {
    departments::sales::meet_customer(1,"Manager");
    departments::sales::meet_customer(1,"CustService");
}
```

Invoking the parent private function using super::

```
// super::

mod departments {
    fn get_number(num:i32) -> String {
        match num {
            1 => return "123-456-7890".to_string(),
            2 => return "987-654-3210".to_string(),
            _ => return "000-000-0000".to_string()
        }
    }


    pub mod sales {
        pub fn meet_customer(num:i32) {
            println!("Sales : meet customer {num}");
            let phone_number = super::get_number(num);
            println!("Sales calling {}", phone_number);
        }
    }

    pub mod service {
        pub fn meet_customer(num:i32) {
            println!("Service : meet customer {num}");
            let phone_number = super::get_number(num);
            println!("Service calling {}", phone_number);
        }
    }
}

fn main() {
    departments::sales::meet_customer(1);
    departments::service::meet_customer(3);
}
```

Example for self::

```
// self::

mod departments {
    fn get_number(num:i32) -> String {
        match num {
            1 => return "123-456-7890".to_string(),
            2 => return "987-654-3210".to_string(),
            _ => return "000-000-0000".to_string()
        }
    }


    pub mod sales {
        pub fn meet_customer(num:i32) {
            println!("Sales : meet customer {num}");
            let phone_number = super::get_number(num);
            println!("Sales calling {}", phone_number);
        }
    }

    pub mod service {
        pub fn meet_customer(num:i32) {
            println!("Service : meet customer {num}");
            let phone_number = super::get_number(num);
            let ticket_number = self::get_service_ticket_number(num);
            println!("Calling {phone_number} with ticket number {ticket_number}");
        }

        fn get_service_ticket_number(num:i32)->i32{
            match num {
                1 => return 2452423,
                2 => return 2341332,
                _ => return 6868765
            } 
        }
    }
}

fn main() {
    departments::sales::meet_customer(1);
    departments::service::meet_customer(3);
}


```

Putting it all together along with TEST Cases

```
// With Test Cases

mod departments {
    fn get_number(num: i32) -> String {
        match num {
            1 => return "123-456-7890".to_string(),
            2 => return "987-654-3210".to_string(),
            _ => return "000-000-0000".to_string(),
        }
    }

    pub mod sales {
        pub fn meet_customer(num: i32) {
            println!("Sales : meet customer {num}");
            let phone_number = super::get_number(num);
            println!("Sales calling {}", phone_number);
        }
    }

    pub mod service {
        pub fn meet_customer(num: i32) {
            println!("Service : meet customer {num}");
            let phone_number = super::get_number(num);
            let ticket_number = self::get_service_ticket_number(num);
            println!("Calling {phone_number} with ticket number {ticket_number}");
        }

        fn get_service_ticket_number(num: i32) -> i32 {
            match num {
                1 => return 2452423,
                2 => return 2341332,
                _ => return 6868765,
            }
        }
    }

    #[cfg(test)] // Only compiles when running tests
    mod tests {
        use crate::get_standard_greetings;

        #[test]
        fn test_customerphone() {
            assert_eq!("000-000-0000", super::get_number(4));
        }

        #[test]
        fn test_standard_greeting() {
            assert_eq!("Welcome to our store.", get_standard_greetings());
        }
    }
}

fn main() {
    println!("{:?}", get_standard_greetings());
    departments::sales::meet_customer(1);
    departments::service::meet_customer(3);
}

fn get_standard_greetings() -> String {
    return "Welcome to our store.".to_string();
}

```
