/*
 * mm_alloc.c
 *
 * Stub implementations of the mm_* routines. Remove this comment and provide
 * a summary of your allocator's design here.
 */

#include "mm_alloc.h"

#include <stdlib.h>

/* Your final implementation should comment out this macro. */
#define MM_USE_STUBS

//part  question 3.1
typedef struct List_Pointer *t_block;
struct List_Pointer{
	size_t block_size; // size of the current block
	t_block next_block;
    int block_free; // either be 1 or 0, 1 is allocated and 0 is empty
}

// Question 3.2
t_block heap_base; // lets just declare the base address

t_block finding_a_fit(t_block current_block, size_t the_size){
	t_block my_base = heap_base;
	while(my_base && !(the_size <= my_base->block_size && my_base->block_free)){
		// the base block is not big enough
		*current_block = my_base;
		my_base = my_base->next_block;
		
	}
	return (my_base);
}

// Question 3.1
void* mm_malloc(size_t size)
{
	int page_size = 4096; // dividing the memory into blocks
	void *m, *i;
	i = sbrk(0);
	m = sbrk(size);
	while(i < m){
		i = sbrk(page_size);
	}
	return m;
}


/* Question 3.3
		I am compfortable with a list of memory sizes, each of which contain a linked list of free blocks of memory of that size.
  
*/

// Question 4.1

t_block solve_Fragmentation(t_block block){
	int page_size = 4096;
	if(block->next_block && block->next_block->block_free){
		b->block_size += page_size + block->next_block->block_size;
		block->next_block = block->next_block->next_block;
		if(block->next_block)
			block->next_block = block;
	}
	return(block);
}

void* mm_realloc(void* ptr, size_t size)
{


}

void mm_free(void* ptr)
{
	t_block my_base = heap_base;
	while(!(my_base->next_block == ptr)){
		my_base = my_base->next_block;
	}
	my_base->block_free = 1; // the block is free now.

}
