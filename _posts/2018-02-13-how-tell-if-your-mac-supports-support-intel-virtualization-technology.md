I was trying to see if my MacBook Air support HAXM for Android emulation and could not find a good resource to tell me how to find out what the processor number of my Mac was. So here you go! 

Open a Terminal 

  * Go to Finder and press Command + Shift + U 
      * Select Terminal 
          * Type the following:&nbsp;&nbsp; **sysctl machdep.cpu.brand_string**</ul> 
        This returns something like this: machdep.cpu.brand_string: Intel(R) Core(TM) **i7-5650U** CPU @ 2.20GHz 
        
        The **BOLD** part is the processor number so continue to follow the instructions starting at step 2 below: [Does My Processor Support Intel® Virtualization Technology?](https://www.intel.com/content/www/us/en/support/articles/000005486/processors.html) 
        
        In my case, yes this process does! 
        
        As a short cut (don’t have to look up the processor number) simply type: <font size="2"><strong>sysctl machdep.cpu.features</strong> </font> 
        
        > <font size="2">and see if it contains <strong>VMX</strong></font>