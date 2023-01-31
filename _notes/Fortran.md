---
title: Fortran
---
up: [[Programming]]

Notes from video: https://www.youtube.com/watch?v=__2UgFNYgf8
## 1. Compilers
gfortran - opensourced
ifort - Intel's compiler


## 2. Variables
- Always put `implicit none` on top of the program
- Variables are case *in-sensitive*
- Variables need to be declared on top of the program
1. `real, parameter:: PI =3.1415`
2. `real:: r_num1 =0.0`
3. `double precision:: dbl_num = 1.111111111111111111d+0` -  d+0 is needed in doubles
4. `integer:: i_num = 1`
5. `logical:: can_vote = .true.`
6. `character (len=10):: month`
7. `complex:: com_num =(2.0, 4.0)`

## 3. Print Statement
The syntax of print statement is 
```fortran
print f [, iolist] ! and iolist is list of variables to print
! print 3 integers in one line each integer having 5 characters width
print "(3i5)", 7, 6, 8
! the width for the float also should include the decimal places
print "(2f8.5)", 3.1415, 1.234
! exponential notation
print "(e10.3)", 123.456 ! will output 0.123E+03
```

### 3.1. format identifier 
\* - list directed
Fortran format can be described in following notation

    w: the number of positions to be used
    m: the minimum number of positions to be used
    d: the number of digits to the right of the decimal point
    e: the number of digits in the exponent part 

## 4. Math operators and functions
Some key things to remember
- ** is raising the power to
- trignometric functions use radians not degrees (sin, cos, tan, etc)
- log(x) is natural log
- not equal to is /=

```fortran
    real(8) :: x = 2.7182818284590451_8
    complex :: z = (1.0, 2.0)
    
    x = log(x)    ! will yield (approximately) 1
    z = log(z)
    print *, "x value should be 1 ", x
    print *, "z value is??", z 
```
## 5. Conditionals
logical operators
.and.
.or.
.not.
.true.
etc..
Sample Code:
```fortran
integer :: age = 6
if ((age >= 5) .and. (age<=6)) then
  print *, "Kintergarden"
else if ((age >= 6) .and. (age<=7)) then
  print*, "First Grade"
else
  print*, "No School"
end if
```

```fortran
integer :: age = 6
select case(age)
	case (5)
		print *, "Kintergarden"
	case(6:13)
	    print *, "elementary school"
	case default
	    print *, "no school"
end select
   
```

## 6. Looping
### 6.1. Do  loop
``` fortran
integer :: n=0, m=1
integer :: secret_num = 7

! print only even numbers
do while (m < 20)
	if (mod(m,2) == 0) then
	    print "(i1)", m
	    m = m + 1
	    ! cyle is continue in python
	    cycle 
	end if
	m = m + 1
	if (m >= 10) then
		! exit is break in python
		exit
    end if
end do

```

## 7. Arrays

```fortran
	integer :: n,m,x,y
	integer :: num_vals = 0
	! Arrays
	integer, dimension(1:5) :: a1, a2, a3
	real, dimension(1:50) :: aR1
	! multi-dimensional
	integer, dimension(5,5) :: a4
	integer, dimension(:), allocatable :: a5
	integer, dimension(1:9) :: a6 = (/ 1, 2, 3, 4, 5 ,6, 7, 8, 9 /)
	integer, dimension(1:3, 1:3) :: a7

	! set and retrieve values
	a1(1) = 5
	print"(i1)", a1(1)
	! cycle through a range of 1 to 5
	do n = 1, 5 
		a1(n)= n
	end do
	! print them
	do n = 1, 5 
		print "(i1)", a1(n)
	end do	

    print "(3i2)", a1(1:3)
    print "(2i2)", a1(1:3:2)

    ! asssign values to multi-dimensional array
    do n = 1,5
        do m = 1,5
            a4(n,m)  = n
        end do
    end do

    ! implied do loop
    do n =1,5
        print "(5i1)", (a4(n,m), m = 1,5)
    end do

	! size and dimensions
	print "(i2)", rank(a4)
	print "(i2)", shape(a2)
	print "(i2)", size(a2)
	print "(i2)", count(a2)
	print "(i2)", maxval(a2)
	print "(i2)", minval(a2)

	! dynamic allocaiton
	print *, "Size of array? "
	read *, num_vals
	allocate(a5(1:numvals))

	do n =1, numvals
		a5(n) = n
	end do

	! reshape an array
	a7 = reshape(a6, (/ 3,3 /))

	! check if values are equal
	print "(l1)", all(a1 == a2, 1)

```

## 8. Strings

```fortran
character (len=30) :: str1 = "I'm a string"
character (len=30) :: str2 = " that is now longer"
character (len=30) :: str3

! trim and concatenate the two strings
str3 = trim(str1) // trim(str2)
! to trim only left or right side use adjustl() or adjustr() instead of trim()
print *, str3

print *, str3(1:3)
print "(a9, i1)", "Index at ", index(str1, "string")
print *, len(str)

```

## 9. Structures

```fortran
! declare customer
type Customer
	character (len=40) :: name
	integer :: age
	real :: balance
end type Customer

! create an array of customers
type(Customer), dimension(5) :: customers
integer :: n

! populate values for a customer
type(Customer) :: cust1
cust1%name = "Sally Smith"
cust1%age = 34
cust1%balance = 320.45
customers(1) = cust1

customers(2)%name = "Tom May"
customers(2)%age = 42
customers(2)%balance = 229.75

do n = 1,2
	print *, customers(n)

```

## 10. Functions

```fortran

integer :: ans, ans2
real :: r_ans

ans = get_sum(5,4)
print "(a8, i1)", "5 + 4 = ", ans
print "(a8, i1)", "5 + 4 = ", get_sum2(5,4)
print "(a8, i1)", "5 + ? = ", get_sum2(5)

contains
    integer function get_sum(n1, n2)
        inplicit none
        integer :: n1, n2, sum
        sum = n1 + n2
    end function get sum

	function get_sum2(n1,n2) result(sum)
	    implicit none
	    ! this is to set it up so the variable values that were passed inside cannot be changed
	    integer, intent(in) :: n1, n2
	    integer :: sum
	    sum = n1 + n2
	end function get_sum2

	! function cannot change input variable
	pure function get_sum3(n1, n2) result(sum)
	    implicit none
	    integer, intent(in) :: n1
	    ! if the argument is optional
	    integer, intent(in), optional :: n2
	    integer :: sum
	    if (present (n2)) then
	        sum = n1 + n2
	    else
	        sum = n1 + 1
	    end if
	end function get_sum3

```


## 11. Subroutines
Subroutines don't return values. They modify the variables that are passed to them. Its like a macro. you need to use "call" to call a subroutine but functions are called normally.

```fortran
integer :: i = 1, p1, p2

call plus_two(i, p1, p2)
print "(i1, /, i1, / , i1)", i , p1, p2

contains
	subroutine plus_two(n, plus1, plus2)
		integer, intent(in) :: n
		! tells we are going to return two values
		integer, intent(out) :: plus1, plus2
		plus1 = n + 1
		plus2 = n + 1
	end subroutine plus_two
	
```

## 12. Variable scope

Objects (variables, etc.) declared in main program/module can be accessed and modified (!!!) by any function/subroutine contained by them. name your variables carefully
### 12.1. Intent
Intent is a useful tool. 
- If you set a variable to be `intent(in)` it cannot be modified in the program.
- `intent(out)` seems more like a documentation thing than having actual purpose as a guardrail.
- `intent(inout)` is a thing.
### 12.2. Module
use `public` and `private` to declare variables with intention. all variables declared in module scope are public by default

### 12.3. Examples


```fortran
integer :: i = 1, p1, p2
integer :: j = 5

call plus_two(i, p1, p2)
print "(i1, /, i1, / , i1)", i , p1, p2

contains
	subroutine plus_two(n, plus1, plus2)
		integer, intent(in) :: n
		! tells we are going to return two values
		integer, intent(out) :: plus1, plus2
		plus1 = n + j
		plus2 = n + j
	end subroutine plus_two
	
```


```fortran
    integer :: i = 1, p1, p2
    integer :: j = 5
    
    p1 = plus_one(i)
    print "(i1, /, i1 )", i , p1
    print "(i1)", j  ! will return 6 and not 5
    
contains
    function plus_one(n) result(plus1)
        integer, intent(in) :: n
        integer :: plus1
        j = j + 1 ! this will modify the global variable
        plus1 = n + j
    end function plus_one
```

## 13. Procedures
https://annefou.github.io/Fortran/modules/modules.html
In Fortran, "procedures" is an umbrella term that mean "functions" or/and "subroutines".
Functions and subroutines are very similar except a function returns a value while a subroutine doesn't. 

There are 4 ways to define procedures:
- Internal procedures are defined within the program structure (CONTAINS)
- External procedures are independently declared and may be on another language(EXTERNAL) (*dont use them modules are better*)
- Module procedure are defined in a module 
- Procedures defined as part of an object 

## 14. Modules

### 14.1. Function overloading example
mult_mod.f90 contains
```fortran
module mult_mod
    implicit none
    ! private variables can be accessed only within the module
    private
    ! public variables can be accessed outside
    pubic :: mult

	interface mult
	    procedure mult_real, mult_int
	end interface mult

contains
    real function mult_real(n1,n2)
        real, intetn(in) :: n1, n2
        real :: product
        product = n1 * n2
    end function mult_real

	integer function mult_int(n1,n2)
        integer, intetn(in) :: n1, n2
        integer :: product
        product = n1 * n2
    end function mult_int
end module mult_mod
```

first.f90 contains
```fortran
use mult_mod
implicit none
real :: r_ans

print "(a8,i2)", "5 * 4 = ", mult(5,4)
r_ans = mult(5.3, 4.4)
print "(a12, f 6.2)", "5.3 * 4.4 = ", rans

```

to run this
```powershell
ifort mult_mod.f90 first.f90 /exe:first.exe
```

### 14.2. Another simple example
first.f90 file contains
```fortran
use shape
implicit none

call set_shape(10.4, 20.5)
call get_area()

```

shape.f90 file contains
```fortran
module shape
    implicit none
    real, private :: height =1
    real, private :: width =1

	public :: set_shape, get_area

contains
	subroutine set_shape(h,w)
	    implicit none
	    real, intent(in) :: h,w
	    height = h
	    width = w
	end subroutine set_shape

	subroutine get_area()
	     print *,  "Area: ", (height* width)
	end subroutine get_area
end module shape
```

to run this
```powershell
ifort shape.f90 first.f90 /exe:first.exe
```

### 14.3. Inherit from one module to another
shape_mod.f90 file contains
```fortran
module shape_mod
    implicit none
    ! this is like a class definition
    ! set supertype (which is shape) as abstract so that it can be inherited from
    type, abstract :: shape_m
	    real :: x, y
	contains
		! procedure means it is defined as part of an object it can be a function or subroutine
		! deferred means it will be defined in all of the subtypes
		procedure(shape_area), deferred :: get_area
    end type shape_m

	interface
		function shape_area(this) result(area)
		    import :: shape_m
		    class(shape_m) :: this
		    real :: area
		end function shape_area
	end interface
end module shape_mod
```

triangle_mod.f90 contains
```fortran
module triangle_mod
    use shape_mod
    implicit none
    type, extends(shape_m), public :: triangle_m
	contains
		procedure :: get_area
    end type triangle_m

contains
    function get_area(this) result(area)
	    class(triangle_m) :: this
	    real :: area
	    area = 0.5 * this%x * this%y
    end function get_area
end module triangle_mod
```

first.f90 file now contains
```fortran
use shape_mod
use triangle_mod
implicit none

type(triangle_m) :: tri
tri%x = 10
tri%y = 20
print "(a3, f5.2)", "X: ", tri%x
print "(a3, f5.2)", "Y: ", tri%y
print "(a6, f6.2)", "Area: ", tri%get_area()
```

to run this
```powershell
ifort shape_mod.f90 triangle_mod.f90 first.f90 /exe:first.exe
```



## 15. Pointers
```fortran
integer, pointer :: ptr1, ptr2
! pointer to an array integer
integer, pointer, dimension(:) :: a_ptr1 
! target whose value will change as the pointers value changes
integer, target :: target1
! allocate space for the pointer
allocate(ptr1)
! assign a value in the memory location
ptr1 = 5
print "(a5,i1)", "ptr1", ptr1
!-- another way --!
! associate a pointer with its target
ptr2 => target1
! change the value of the target
ptr2 = 1
ptr2 = ptr2 + 2
print "(a5, i1)", "ptr2", ptr2
print "(a7, i1)", "target1", target1
! dereference a pointer from its target
nullify(ptr2)
! deallocate storage
deallocate(ptr1)
```

## 16. File I/O

```fortran
character (len=100) :: str1 = "I'm a string"
character (len=100) :: str2

! if err_status is not zero then a error has occured
integer :: err_status
character(256) :: err_iomsg
! 10 is unit number which must be unique to every file and it must be above 9
! status can be new, old, scratch. scratch means delete after using. new is a new file. old is an existing file
open(10, file="data.dat", status="new", iostat=err_status, iomsg=err_iomsg)
if (err_stat /=0) then 
    write(*,*) "Error", trim(err,io_msg)
    stop
end if

write(10, "(A)") str
close(10)

open(11, file="data.dat", status="old")
read(11, "(A)") str2
write(*, "(A)") trim(str2)
! delete the file after closing it
close(11, status="Delete")

```