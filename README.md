# cs214-project-i-my-little-malloc-solved
**TO GET THIS SOLUTION VISIT:** [CS214  Project I-My little malloc() Solved](https://www.ankitcodinghub.com/product/cs214-project-i-my-little-malloc-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;100125&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS214&nbsp; Project I-My little malloc() Solved&nbsp;&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
<div class="page" title="Page 1">
<div class="layoutArea">
<div class="column">
&nbsp;

&nbsp;

For this assignment, you will implement your own versions of the standard library functions malloc() and free(). Unlike the standard implementations, your versions will detect common usage errors and report them.

For this assignment, you will create

<ol>
<li>A library mymalloc.c with header mymalloc.h, containing the functions and macros described below.</li>
<li>A program memgrind.c that includes mymalloc.h.</li>
<li>Additional test programs that include mymalloc.h, along with the necessary Make-files forcompiling these programs.</li>
<li>A test plan, describing:(a) What properties your library must have for you to consider it correct (b) How you intend to check that your code has these properties
(c) The specific method(s) you will use to check each property
</li>
<li>A README file containing the test plan, descriptions of your test programs (including any arguments they may take), which of your design properties you able to prove, and any design notes you think are worth pointing out. This should be a plain text file or a PDF.</li>
</ol>
Submit all files to Canvas in a single Tar archive.

1 Background

malloc() and free() are used to manage the heap: a program’s primary location for dynamically allocated data. The versions in the C standard library obtain regions of memory from the operating system and then portion pieces of it as requested. To do so, they maintain a data structure indicating (1) how memory has been divided into chunks and (2) which chunks are currently in use (allocated) or not in use (free). This metadata is itself dynamically sized, since its complexity depends on the number of chunks that memory has been divided into, so it is also stored in the heap.

malloc() is called with a single integer, indicating the requested number of bytes. It searches for a free chunk of memory containing at least that many bytes. If it finds a chunk that is large

1

</div>
</div>
</div>
<div class="page" title="Page 2">
<div class="layoutArea">
<div class="column">
enough, it may divide the chunk into two chunks, the first large enough for the request, and returns a pointer to the first chunk. The second chunk remains free.

free() is called with a single pointer, which must be a pointer to a chunk created by malloc(). free() will mark the chunk free, making it available for subsequent calls to malloc().

1.1 Memory fragmentation

Consider a case where we repeatedly call malloc() and request, say, 20-byte chunks until all of memory has been used. We then free all these chunks and request a 40-byte chunk. To fulfil this request, we must coalesce two adjacent 20-byte chunks into a single chunk that will have at least 40 bytes.

Coalescing can be done by malloc(), when it is unable to find space, but it is usually less error-prone to have free() automatically coalesce adjacent free chunks.

1.2 Your implementation

Your mymalloc.c will allocate memory from a global array declared like so:

<pre>static char memory[4096];
</pre>
The use of static will prevent client code from accessing your storage directly. You are free to name the array something else, if you prefer. It is recommended that you use a macro to specify the array length and use that macro throughout, to allow for testing scenarios with larger or smaller memory banks.

Your malloc() and free() functions MUST use the storage array for all storage purposes. You may not declare other global variables or static local variables or use any dynamic memory features provided by the standard library.

In other words: both the chunks provided to client code and the metadata used to track the chunks must be stored in your memory array.

Do not be fooled by the type of the array: all data is made up of bytes, and an array of chars is just an array of bytes. The address of any location in the array can be freely converted to a pointer of any type.

The simplest structure to use for your metadata is a linked list. Each chunk will be associated with the client’s data (the payload) and the metadata used to maintain the list (the header). Since the chunks are continuous in memory, it is enough for the header to contain (1) the size of the chunk and (2) whether the chunk is allocated or free. Given the location of one chunk, you can simply add its size to the location to get the next chunk. The first chunk will always start at the beginning of memory.

Note the pointer returned by malloc() must point to the payload, not the chunk header.

Note that your memory array, as a global variable, will be implicitly initialized to all zeros. Your malloc() and free() functions must be able to detect when they are running with uninitialized memory and set up the necessary data structures. You are not permitted to require clients to call an initialize function before calling malloc().

2

</div>
</div>
</div>
<div class="page" title="Page 3">
<div class="layoutArea">
<div class="column">
2 Detectable errors

The standard malloc() and free() do no error detection, beyond returning NULL if malloc() cannot find a large enough free chunk to fulfil the request.

In addition, your library must detect and report these usage errors:

<ol>
<li>Calling free() with an address not obtained from malloc(). For example,
<pre>     int x;
     free(&amp;x);
</pre>
</li>
<li>Calling free() with an address not at the start of a chunk. int *p = malloc(sizeof(int)*2);free(p + 1);</li>
<li>Calling free() a second time on the same pointer.
<pre>     int *p = malloc(sizeof(int)*100);
     int *q = p;
     free(p);
     free(q);
</pre>
</li>
</ol>
You may provide a function that can be called before a program exits to determine whether any memory chunks remain allocated (that is, to detect possible memory leaks).

3 Reporting errors

We will use features of the C pre-processor to allow malloc() and free() to report the source file and line number of the call that caused the error. To do this, your “true” functions will take additional parameters: the source file name (a string) and line number (an int).

Use these function prototypes and macros in your mymalloc.h: void *mymalloc(size_t size, char *file, int line);

<pre>void free(void *ptr, char *file, int line);
</pre>
<pre>#define malloc(s) mymalloc(s, __FILE__, __LINE__)
#define free(p) myfree(p, __FILE__, __LINE__)
</pre>
The C pre-processor will replace the pseudo-macros __FILE__ and __LINE__ with appropriate string and integer literals, which will give your functions the source locations from which they were called.

Note that we are stealing the names of functions defined in the standard library. For this reason, make sure that mymalloc.h is included later than stdlib.h. For example,

<pre>#include &lt;stdlib.h&gt;
#include "mymalloc.h"
</pre>
The content and format of your error messages is up to you. Describe your design in your project’s README file.

3

</div>
</div>
</div>
<div class="page" title="Page 4">
<div class="layoutArea">
<div class="column">
4 Testing

Include a file memgrind.c that includes mymalloc.h. The program should perform the following tasks:

<ol>
<li>malloc() and immediately free() a 1-byte chunk, 120 times.</li>
<li>Use malloc() to get 120 1-byte chunks, storing the pointers in an array, then use free() todeallocate the chunks.</li>
<li>Randomly choose between• Allocating a 1-byte chunk and storing the pointer in an array • Deallocating one of the chunks in the array (if any)
Repeat until you have called malloc() 120 times, then free all remaining allocated chunks.
</li>
<li>Two more stress tests of your design. Document these in your README.</li>
</ol>
Your program should run each task 50 times, recording the amount of time needed for each task, and then reporting the average time needed for each task. You may use gettimeofday() or similar functions to obtain timing information.

</div>
</div>
<div class="layoutArea">
<div class="column">
4

</div>
</div>
</div>
