1. Parameter values (answer based on the assembly instructions for `main`)

    - Which of the assembly lines place the values of the two parameters into the registers
    before the `max_char` function is called. 
27
0x0000000000400555 : be 41 00 00 00 mov $0x41,%esi
0x000000000040055a : bf 61 00 00 00 mov $0x61,%edi

    - Which of the assembly lines place the values of the two parameters into the registers
    before the `max_int` function is called.


0x0000000000400587 bf 54 06 40 00 mov $0x400654,%edi
0x000000000040058c b8 00 00 00 00 mov $0x0,%eax


    - Which of the assembly lines place the values of the two parameters into the registers
    before the `max_long` function is called.  



    - What did you notice about sizes of the registers in each case?
    integer uses rdi, rsi, rdx registers 
    and others use 64 bit registers. 
    

    - What did you notice about the values stored in those registers in each case?
    values represent the size of the parameters. 


2. The following three functions are equivalent to `max_char`, `max_int` and
`max_long`, but your job is to figure out which one is which. (Do not compare them
  to the assembly generated by the compiler. Try to figure out the matching on your own.)


    ```
    function1:
        movsbl	%sil, %esi
        movl	%edi, %eax
        cmpl	%edi, %esi
        cmovge	%esi, %eax
        ret


    function2:
        cmpq    %rsi, %rdi
        movq    %rsi, %rax
        cmovge  %rdi, %rax
        ret
    ```

    ```
    function3:
        cmpb    %sil, %dil
        movl    %esi, %eax
        cmovge  %edi, %eax
        ret



function 1 is max_int 
function 2 is max_long
function 3 is max_char