C++ Features and Facts
======================

Ordering of elements in a struct
--------------------------------

All elements within a struct must be aligned (compiler specific, for inte i++ see [here](https://software.intel.com/en-us/articles/coding-for-performance-data-alignment-and-structures)).
**Always** sort the members! Good idea to sort them biggest member first.

	struct ms_entry {
        uint64_t timestamp; // 8 bytes
        bool valid = false; // only 1 byte but will use up 8
    };
	
Generally each attribute is aligned to its own size. Additionally the the struct itself is aligned with the size of its biggest member -> additional trailing padding (to allow stride access in arrays). For more information look [here](http://www.catb.org/esr/structure-packing/).

Zero initialization of array of structs
---------------------------------------
To initialize all elements of a struct for each array element use the following code:

````C++
struct my_struct 
{
    int a, b;
};

int main (int argc, char const* argv[])
{
    struct my_struct array[10] = {{0,0}};
    return 0;
}
````