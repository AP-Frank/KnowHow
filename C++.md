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
	
Generally each attribute is aligned to its own size. Additionally the the struct itself is aligned with the size of its biggest member -> additional trailing padding (to allow stride access in arrays)