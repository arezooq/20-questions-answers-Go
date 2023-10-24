# 20 Questions language Go

## Questions

<a href="#1">1. What is the primary purpose of a Go module file(go.mod)?</a><br>
<a href="#2">2. How do declare a variable in Go?</a>
<a href="#3">3. How to handling error in Go?</a>
<a href="#4">4. What does the `range` keyword do in a `for` in Go?</a>
<a href="#5">5. How do handle multiple conditions in a single `if` statement in Go?</a>
<a href="#6">6. What is the purpose of the `switch` statement in Go?</a>
<a href="#7">7. How do create a slice from an array in Go?</a>
<a href="#8">8. In Go map, what is the key used for?</a>
<a href="#9">9. How do define a function that takes two integer parameters and returns their sum in Go?</a>
<a href="#10">10. What is the output of the following code?</a>
<a href="#11">11. How to declare and use a pointer to an integer in Go?</a>
<a href="#12">12. How can represent a rune literal in Go source code?</a>
<a href="#13">13. Can a struct have fields with different data types in Go?</a>
<a href="#14">14. How do define a method for a type in Go?</a>
<a href="#15">15. In a Go interface definition, can a type implement multiple interface?</a>
<a href="#16">16. How do access fields from an embedded struct within the outer struct Go?</a>
<a href="#17">17. How to create a new channel for communication between goroutines?</a>
<a href="#18">18. How to `json` tags used for in Go structs?</a>
<a href="#19">19. How can access an environment variable in Go?</a>
<a href="#20">20. How can specify the port on which Go HTTP server listens?</a>

## Answers the questions

<div id="1">
1. What is the primary purpose of a Go module file(go.mod)?

  ANSWR:
        Each Go module is defined by a go.mod file that describes the module’s properties, including its dependencies on other modules and on versions of Go.

        Go generates a go.mod file when you run the go mod init command. The following example creates a go.mod file, setting the module’s module path to example/mymodule:

        $ go mod init example/mymodule
</div>
<div id="2">
2. How do declare a variable in Go?

  ANSWR:  
        In Go language variables are created in two different ways:

        1. Using var keyword: In Go language, variables are created using var keyword of a particular type, connected with name and provide its initial value.

        var variable_name type = expression

        2. Using short variable declaration: The local variables which are declared and initialize in the functions are declared by using short variable declaration.

        variable_name:= expression
</div>
<div id="3">
3. How to handling error in Go?

  ANSWR:  
        Go does not have the try, catch, and finally features used by other programming languages like Java, Python, JavaScript, etc. However, Go has a feature that can be compared to these features. Defer, Panic, and Recover are used in Golang programs for handling exceptions, although the use case might be slightly different.

        func HandlePanic() {
            r := recover()

            if r != nil {
                fmt.Println("RECOVER", r)
            }
        }

        func divide(divisor int, divider int) {

            defer HandlePanic()

            if divisor < divider {
                panic("start is greater than end")
            } else {
                fmt.Println(divisor / divider)
            }
        }
</div>
<div id="4">
4. What does the `range` keyword do in a `for` in Go?

  ANSWR: 
        In Golang Range keyword is used in different kinds of data structures in order to iterates over elements. The range keyword is mainly used in for loops in order to iterate over all the elements of a map, slice, channel, or an array.

        func main() {

            student_rank_map := map[string]int{"John": 3,
                                "Smith": 2, "Mickel": 1}

            for student := range student_rank_map {
                fmt.Println("Rank of", student, "is: ",
                            student_rank_map[student])
            }

            for student, rank := range student_rank_map {
                fmt.Println("Rank of", student, "is: ", rank)
            }
        }
</div>
<div id="5">
5. How do handle multiple conditions in a single `if` statement in Go?

  ANSWR:  
        The And (&&) is a way of combining conditional statement has the following syntax:

        if (condition1) && (condition2) {
        ......
        }
</div>
<div id="6">
6. What is the purpose of the `switch` statement in Go?

  ANSWR:  
        A switch statement is a shorter way to write a sequence of if - else statements. It runs the first case whose value is equal to the condition expression.

        func main() {
            fmt.Print("Go runs on ")
            switch os := runtime.GOOS; os {
            case "darwin":
                fmt.Println("OS X.")
            case "linux":
                fmt.Println("Linux.")
            default:
                // freebsd, openbsd,
                // plan9, windows...
                fmt.Printf("%s.\n", os)
            }
        }
</div>
<div id="7">
7. How do create a slice from an array in Go?

  ANSWR:  
        Create a slice by slicing an array:

        var myarray = [length]datatype{values} // An array
        myslice := myarray[start:end] // A slice made from the array
</div>
<div id="8">
8. In Go map, what is the key used for?

  ANSWR:  
        Golang Maps is a collection of unordered pairs of key-value. It is widely used because it provides fast lookups and values that can retrieve, update or delete with the help of keys.
</div>
<div id="9">
9. How do define a function that takes two integer parameters and returns their sum in Go?

  ANSWR:  
        func add(a int, b int) int {
          return a + b
        }
</div>
<div id="10">
10. What is the output of the following code?

    func main() {
        functions := []func(){}
            for i := 0; i < 3 ; i++ {
                x := i
                functions = append(functions, func() {
                    fmt.Print(x)
                })
            }
            for _, fn := range functions {
                fn()
            }
    }

  ANSWR:
   output:   012
</div>
<div id="11">
11. How to declare and use a pointer to an integer in Go?

  ANSWR:  

        Declaring a pointer:

        var pointer_name *Data_Type

        var a = 45
        var s *int = &a
</div>
<div id="12">
12. How can represent a rune literal in Go source code?

  ANSWR:  
        rune in Go is a data type that stores codes that represent Unicode characters. Unicode is actually the collection of all possible characters present in the whole world. In Unicode, each of these characters is assigned a unique number called the Unicode code point. This code point is what we store in a rune data type.

        func main() {

          emoji := '😀' 

          fmt.Printf("Data type of %c is %T and the rune value is %U \n", emoji, emoji, emoji);   
        }

        Output:
                Data type of 😀 is int32 and the rune value is U+1F600
</div>
<div id="13">
13. Can a struct have fields with different data types in Go?

  ANSWR:  
        In Go, create a struct with fields of different types by specifying the field names and their corresponding data types within the struct definition.

        example:

        type Person struct {
          FirstName string
          LastName string
          Age int
          BirthDate string
        }
</div>
<div id="14">
14. How do define a method for a type in Go?

  ANSWR:  
        Go language support methods. Go methods are similar to Go function with one difference, i.e, the method contains a receiver argument in it. With the help of the receiver argument, the method can access the properties of the receiver.

        example:

        type Person struct {
          FirstName string
          LastName string
          Age int
          BirthDate string
        }

        func (p Person) Greet() {
          fmt.Printf("Hello, my name is %s %s. \n", p.FirstName, p.LastName)
        }

        func main() {
          johnDoe := Person{
            FirstName: "John",
            LastName: "Doe",
            Age: 31,
          }

          johnDoe.Greet()
        }
</div>
<div id="15">
15. In a Go interface definition, can a type implement multiple interface?

  ANSWR:  
        In Go language, the interface is a collection of method signatures and it is also a type means you can create a variable of an interface type. In Go language, you are allowed to create multiple interfaces in your program with the help of the given

        example: 

        type Person struct {
          FirstName string
          LastName string
          Age int
          BirthDate string
        }

        func (p Person) Greet() {
          fmt.Printf("Hello, my name is %s %s. \n", p.FirstName, p.LastName)
        }

        func (p Person) PersonDetail() {
	        fmt.Printf("Your Name %v %v (born on %v)\n", p.FirstName, p.LastName, p.Age, p.BirthDate)
        }

        type GreetPerson interface {
          Greet()
        }

        type OutputPersonDetails interface {
          PersonDetail()
        }

        func main() {
          johnDoe := Person{
            FirstName: "John",
            LastName: "Doe",
            Age: 31,
            BirthDate: 16/11/2002
          }

          var i1 GreetPerson = johnDoe
          i1.Greet()

          var i2 PersonDetail = johnDoe
          i2.OutputPersonDetails()
        }
</div>
<div id="16">
16. How do access fields from an embedded struct within the outer struct Go?

  ANSWR:
        Without having to explicitly declare them, fields and methods of another type can be inherited by a struct using a technique called “type embedding” in Go.
        To get to the embedded struct’s fields, we may either use the struct field name or the struct name followed by a dot to denote the field name.

        example

        type Address struct {
          street string
          City string 
          ZipCode string
        } 

        type Person struct {
          FirstName string
          LastName string
          Age int
          BirthDate string
          Contact Address
        }

        func (p Person) Greet() {
          fmt.Printf("Hello, my name is %s %s in city %s . \n", p.FirstName, p.LastName, p.Contact.City)
        }

        func main() {
          johnDoe := Person{
            FirstName: "John",
            LastName: "Doe",
            Age: 31,
            Contact: Address{
              Street: "1 Main St",
              City: "Mashhad",
              ZipCode: "123456",
            }
          }

          johnDoe.Greet()
        } 
</div>
<div id="17">
17. How to create a new channel for communication between goroutines?

  ANSWR:  
        In Go language, a channel is a medium through which a goroutine communicates with another goroutine and this communication is lock-free. Or in other words, a channel is a technique which allows to let one goroutine to send data to another goroutine.

        example :

        func main() {
          ch := make(chan int)

          go func() {
            for i:= 0; i < 5; i++ {
              ch <- i
              time.Sleep(time.Millisecond * 500)
            }
            close(ch)
          }()

          for val := range ch {
            fmt.Printf("Received: %d\n", val)
          }

          fmt.Println("All data received. Done!)
        }
</div>
<div id="18">
18. How to `json` tags used for in Go structs?

  ANSWR:  
        In Go, you can use JSON tags in struct fields to specify how those fields should be encoded or decoded when working with JSON data.

        example: 

        type Person struct {
          FirstName string `json:"firstname"`
          LastName string `json:"lasttname"`
          Age int `json:"age"`
          BirthDate string `json:"birthdate"`
        }
</div>
<div id="19">
19. How can access an environment variable in Go?

  ANSWR:  
        In Go, you can access environment variables using the `os` package.

        func main() {

          os.Setenv("envVarName", "YOUR_ENV_VARIABLE") 

          value := os.Getenv("envVarName")

          fmt.Printf("The value of is: %v\n", value)
        }
</div>
<div id="20">
20. How can specify the port on which Go HTTP server listens?

  ANSWR:  
        To specify the port on which your Go HTTP server listens, you can use the `http.listenAndServe` function.

        func helloHandler(w http.ResponseWriter, r *http.Request) {
          fmt.Fprintln(w, "Hello, word!")
        }

        func main() {
          http.HandleFunc("/hello", helloHandler)

          port := "localhost:8080"

          err := http.listenAndServe(port, nil)

          if err != nil {
            fmt.Printf("Server error: %v \n", err)
          }
        }
</div>