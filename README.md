

# Subnet Calculator - C#

- Verify an IP Address Belongs to a Subnet.
- Você pode utilizar o endereço de mascara de rede **(255.255.255.0)** ou utilize **CIDR (/24)**



## Using netmask

    var host = IPAddress.Parse("192.168.0.1");
    var network = IPAddress.Parse("192.168.0.0");
    
    if (host.checkInSubNet(network, IPAddress.Parse("255.255.255.0")))
    {
    	Console.WriteLine("Existing !! TRUE ");
    }
    
## Using CIDR

    var host = IPAddress.Parse("192.168.0.1");
    var network = IPAddress.Parse("192.168.0.0");
    
    if (host.checkInSubNet(network, 24)
    {
    	Console.WriteLine("Existing !! TRUE ");
    }
    

## LOGIC

Logic I used to develop the script


 ****AND LOGICAL - NETWORK  + NETMASK****  
11000000.10101000.00000000 .00000000	192.168.0.0 {rede}  
11111111.11111111.11111111 .00000000	255.255.255.0 {mask}  
11000000.10101000.00000000 .00000000	Result #1 !   

****AND LOGICAL - ADDRESS + NETMASK****  
11000000.10101000.00000000 .00001010	192.168.0.10 {host}  
11111111.11111111.11111111 .00000000	255.255.255.0  {mask}  
11000000.10101000.00000000 .00000000	192.168.0.0 {equal to #1}  

  
>comparing the results of the logics 

if and results match, address belongs to network

## Convert CIDR to NETMASK (LOGIC)
***Convert cidr /24 to netmask***  
Just *shift* the bits left X times  

 **x** = 24  
255.255.255.255 << (32 - x)  
11111111.11111111.11111111 .11111111  
 **Result:**  
 11111111.11111111.11111111 .00000000  (255.255.255.0)  


[View Code](https://github.com/luisfeliperm/checkSubNet-csharp/blob/master/CheckSubNet/Program.cs)