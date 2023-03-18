---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Function Overloading
linter-yaml-title-alias: Function Overloading
date-of-creation: 2023-02-07
mod-date: 2023-02-07
---

# Function Overloading

## Best Practices

### Member Functions
```cpp
class X {
	private:
		int x;
	public:
		void operator+(/* *this, */int y);
}
void X::operator+(int y) {
	this→ x += y;
}
```
- To be used for…
	- `=`,`[]`,`()` & `-\>`
	- Unary operators
	- Binary operators modifying the left operand (e.g. `+=`)

### Normal functions
#TODO
```cpp
class X {
		int x;
	public:
		int get() {return x;}
		int operator+(X x, int y);
}
int X::operator+(X x, int y){
	return x.get() + y;
}
```
- Te be used for…
	- Binary functions - not modifying the left operand (e.g. `+`)
	- Binary functions - where the left operands class definition is not accessible (e.g. `<<`)

### Friend functions
```cpp
class X {
		int x;
	public:
		friend int operator+(X x, int y);
}
int operator+(X x, int y){
	return x.x + y;
}
```
- Used when the use of normal functions require the creation of public access methods
