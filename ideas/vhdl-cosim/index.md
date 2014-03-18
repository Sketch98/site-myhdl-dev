---
title:   VHDL Cosimulation with GHDL 
author:  Christopher Felton
layout:  wide_article
content: []
---

With the MyHDL release 0.6 VHDL conversion is supported.  At the
time of the release it was not known if there was an open-source
VHDL simulator that supported foreign interface for Cosimulation.  
This page was created to capture information needed to implemented the
foreign interface for [GHDL].

[GHDL]: http://ghdl.free.fr/
 
GHDL is a VHDL compiler / simulator built
on top of gcc.  It is actively supported 
and developed which makes it an ideal choice for a open-source
VHDL simulator to integrate with MyHDL.

The first item that needs to be determined is which foreign interface to 
use VPI or VHPI.  

VPI or VHPI
===========
This is an ongoing investigation below is essentially a log of recent information.

**03-Feb-2010**

**VPI** is part of the Verilog PLI standard and a subset
of VPI has been added to GHDL to support
[IVI](http://ivi.sourceforge.net/ ). According to a newsgroup post 
VPI might not be the best option because VPI has not been maintained
in many years. But on the GHDL website there
are some examples of the VPI interface available.  And using the examples
as a template the cver VPI implementation can be compiled and loaded 
into GHDL.  Nothing interesting was done with
the interface other than compiling and loading in a
simulation.  

[Here][ghdl-vpi] are the code modifications to compile
the MyHDL VPI interface and load it in GHDL.

**VHPI** is the VHDL standard equivalent of VPI. 
There is 
[some mention of VHPI](http://ghdl.free.fr/ghdl/Interfacing-to-other-languages.html#Interfacing-to-other-languages ) but I have not come across any examples or created 
a working example. 

At this point it is unclear which interface to use.  More information will be posted 
to this page as it is available.

Cver VPI Functions and GHDL Support
-----------------------------------
The following is a table of the VPI functions used as part of the
cver implementation and the known status in [ GHDL](http://ghdl.free.fr/ ).

VPI Function         | GHDL Status | MyHDL Usage | Comment 
---------------------|-------------|-------------|---------------------------------
vpi_printf           |supported    |             | Demonstrated in vpi1.c example |
vpi_control          |unknown      |             | |
vpi_get_time         |unknown      |             | |
vpi_handle           |supported    |             | Demonstrated in vpi1.c example|
vpi_iterate          |supported    |             | Demonstrated in vpi1.c example|
vpi_get              |supported    |             | Demonstrated in vpi1.c example|
vpi_get_str          |supported    |             | Demonstrated in vpi1.c example|
vpi_scan             |supported    |             | Demonstrated in vpi1.c example|
vpi_register_cb      |supported    |             | Demonstrated in vpi1.c example|
vpi_free_object      |unknown      |             | |
vpi_put_value        |unknown      |             | |
vpi_register_systf   |unknown      |             | |

GHDL VHPI Support
-----------------

If the VHPI was to be used a new set of C code will need to be implemented.
VHPI would be the secondary choice and only used if VPI support was too minimal
and required adding VPI to GHLD.  If that were the case VHPI would be used.

Quote from the GHDL manual:

"""

5.9 Interfacing to other languages


Interfacing with foreign languages is possible only on GNU/Linux systems.

You can define a subprogram in a foreign language (such as C or Ada) and import it in a VHDL design.
5.9.1 Foreign declarations

Only subprograms (functions or procedures) can be imported, using the foreign attribute. 
In this example, the sin function is imported:

     package math is
       function sin (v : real) return real;
       attribute foreign of sin : function is "VHPIDIRECT sin";
     end math;
     
     package body math is
       function sin (v : real) return real is
       begin
         assert false severity failure;
       end sin;
     end math;

"""


The VHPI seems too limiting at this point in time.

Conclusion
----------

No conclusion yet!

