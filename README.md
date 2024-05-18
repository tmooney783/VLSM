<h2>Variable Length Subnet Masks</h2>

**This project taught me how to use variable length subnetting to create subnetworks with different amounts of hosts.**

----

I created this mock startup business with 4 departments, all with different amounts of computers and other devices that need internet access:

                 |   Hosts
    Department   |   Required
        ------------------
     Guests      |     10 
     Robots      |     57
     Servers     |     26
     Workers     |     117


I chose this IP address to work with:
   
    172.21.42.0/24 
    
and started subnetting for the department that needed the **most hosts first**:  **'Workers'** - 117.

-------------------------------------------------------------------------------------------------------------------


I first converted /24 mask to binary:

    11111111.111111111.11111111.00000000

Then used this binary chart:


    256 128 64 32 16 8 4 2 
          ^  ^  ^  ^ ^ ^ ^  
          7  6  5  4 3 2 1  


to find how many hosts bits I needed to save.

So the new subnet mask would be: 

    11111111.11111111.11111111.10000000

new CIDR notation is:

    /25

converted back to decimal:

    255.255.255.128

and the increment is:

    128

so the 1st range is:

    172.21.42.0 - 172.21.42.127
             
and I assigned it to the **'Workers'** subnet. 

----

The **2nd range** starts at:

    172.21.42.128 

I then subnetted this for 57 hosts (the second highest, needed for **'Robots'**) using the new subnet mask:

    11111111.11111111.11111111.10000000

and the binary chart:


    256 128 64 32 16 8 4 2
             ^  ^  ^ ^ ^ ^
             6  5  4 3 2 1


and found that i needed to save 6 host bits.

So this departments new subnet mask would be: 

    11111111.11111111.11111111.11000000

new CIDR: /26

increment: 64

converted back to decimal: 255.255.255.192

so the new network range is:

    172.21.42.128 - 172.21.42.191   
                or   
        172.21.42.128 /26


----

Using the same method I gave the **'servers'** department the ranges of: 

    172.21.42.192 - 172.21.42.223  
                  or  
           172.21.42.192 /27

and the **'guest'** department:

    172.21.42.224 - 172.21.42.239  
                 or  
          172.21.42.224 /28








 

