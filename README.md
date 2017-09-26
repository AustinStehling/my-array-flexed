# My Array Flexed

A fun project to show the power of Ruby's dynamic arrays.

## Background

* Languages such as C offer limited flexibility with their arrays.
* In C, you must declare the size of your array upon implementation and it cannot be resized.
* You have the ability to get and set values in the cells of your static array.
* The get and set methods for our static array happen in constant time.
* In Ruby we have the ability to use methods such as push, pop, shift and unshift.
* Ruby's implementation language is C.
* The objective of this project was to create a flexible array that was not limited by a starting size.
* The second task was to maintain constant get and set times even if we needed to resize our array.
* The objective was accomplished by creating a ring buffer and doubling our array's length on each resize so the armotised time became O(1).

## Instructions

There are three files all with the ability to create arrays. The static_array represents something similar to what we'd find in C.

The flexed_array allows for all of our favorite Ruby methods, but performs in O(n) time for shift and unshift. This is because it does not implement a ring buffer. Instead shifting and unshifting causes the entire array to be reformatted moving all of the elements an index ahead if we are unshifting onto the array, or an index behind if we are shifting off of the array.

To make things more efficient I implemented a ring buffer in flexed_array_with_buffer. The ring buffer keeps track of a starting index. Essentially if index 0 is filled and we want to unshift onto the array, we can push onto the end of the array and set our starting index at that point. It is easy to unshift onto the array even with a starting index greater than 0, because we can decrement the starting index down by one, and increment the count. If we push onto the array, we don't have to change the starting index.

* Without Ring Buffer
```Ruby
def initialize
  self.store = StaticArray.new(4)
  self.capacity = 4
  self.length = 0
end
```
* With Ring Buffer
```Ruby
def initialize
  self.store = StaticArray.new(4)
  self.capacity = 4
  self.start_idx = 0
  self.length = 0
end
```
* Open pry or irb in your terminal and load the desired array you'd like to test.
* Set a variable equal to a new instance of the specified class.
* Use the methods push, pop, shift and unshift. I encourage you to add enough values to see the array resized. The starting array is of capacity 4.

## Future Direction

* Add more methods, such as include?, index, delete_at and other highly utilized Ruby array class methods.
