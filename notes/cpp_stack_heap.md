Yes, that's correct. Regular, non-pointer variables typically use stack memory, while pointers created with the `new` keyword in C++ use heap memory. Here are the key differences between the stack and the heap:

**Stack:**

1. The stack is used for static memory allocation. This means that the size and lifetime of variables are known at compile time.
2. Each time a function is called, a block of memory is reserved for its variables. This block is pushed onto the stack. When the function returns, this block of memory is automatically deallocated.
3. Accessing memory on the stack is fast because the stack is a LIFO (last in, first out) data structure, and both pushing and popping from the stack have constant time complexity.
4. However, the size of the stack is limited and varies depending on the system. If you try to allocate more memory than is available on the stack, you will get a stack overflow.

**Heap:**

1. The heap is used for dynamic memory allocation, which means that you can allocate memory at runtime. The size or the lifetime of variables does not need to be known at compile time.
2. To allocate memory on the heap, you use the `new` keyword in C++. To deallocate memory, you use the `delete` keyword. This memory allocation and deallocation must be managed manually, but gives you more flexibility.
3. Accessing memory on the heap is slower than accessing memory on the stack because finding a block of unused memory large enough to satisfy the allocation request can take time.
4. The heap is usually much larger than the stack, so you can allocate more memory on the heap. However, if you fail to deallocate memory when you're done with it, you can use up all of the heap space, causing a memory leak.

In summary, the stack and the heap are both parts of memory, but they are used in different ways. The stack is fast, automatic, but limited in size, while the heap is slower, manual, but capable of handling much larger data sizes.

---

In C++, you might use the `new` keyword to dynamically allocate memory for a variable at runtime, creating a pointer to an object, for several reasons:

1. **Dynamic Allocation**: When the memory needed depends on user input or other runtime factors. Non-pointer variables have their memory allocated at compile time, so the size needs to be known beforehand.

2. **Object Persistence**: When you want an object to persist beyond the scope of the function where it was created. In C++, local (non-pointer) variables are destroyed once their scope ends. If you want to create an object that outlives the function it was created in, you might use `new` to create it on the heap instead of the stack.

3. **Polymorphism**: When you want to take advantage of polymorphism. Pointers to base class objects can be assigned addresses of derived class objects, which is essential for runtime polymorphism.

4. **Memory Efficiency**: Large objects can quickly use up stack space, which is typically much more limited than heap space. In such cases, allocating such objects on the heap (using `new`) is a better option.

5. **For Building Dynamic Data Structures**: Like linked lists, trees, graphs etc. These structures change over the course of execution and hence, require dynamic memory allocation.

It's important to remember, however, that any memory you allocate with `new` must eventually be deallocated with `delete`, or you will have a memory leak. Modern C++ encourages the use of smart pointers (like `unique_ptr` or `shared_ptr`) which handle this automatically.

---

Couldn’t I just scope those GUI components to the C++ frame subclass?

---

Yes, you could define these GUI components as non-pointer member variables (i.e., directly contained within the class). The choice between pointer and non-pointer members often depends on the specific design and requirements of your software.

If these GUI components are defined as non-pointer members:

1. **Lifetime Management**: They will be automatically created (constructed) when an instance of your `FfmpegFrame` class is created, and destroyed (destructed) when the instance is destroyed. This makes memory management automatic, reducing the risk of memory leaks. However, you have less control over their lifetimes compared to when you manage them manually with pointers.

2. **Initialization**: Non-pointer members must be initialized in the constructor's initialization list or at their point of declaration in the class, as C++ guarantees they are constructed before the body of the constructor is entered. This can be restrictive if, for example, the construction of these objects depends on some logic that needs to be executed in the constructor.

3. **Polymorphism**: If these GUI components are or might become part of a class hierarchy with virtual functions, they must be pointers or references to allow for polymorphic behavior.

In GUI applications, it's often convenient to use pointers for widgets because this allows for more flexible creation and destruction times and easier handling of ownership in cases where the lifetime of the widget doesn't exactly match the lifetime of the containing window.

Note: If you decide to use pointers, remember to follow the Rule of Three/Five/Zero, which states that if a class defines one (or more) of a destructor, copy constructor, or copy assignment operator, it should probably explicitly define all three. For modern C++, this can be extended to the Rule of Five by also considering the move constructor and move assignment operator. This is important for proper memory management and to avoid issues like memory leaks or shallow copying. In many cases, using smart pointers can simplify these rules.
