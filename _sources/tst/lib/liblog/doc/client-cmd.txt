Client Commands
===============

Here is a list of client commands for liblog::

   gosh # log <tab>          
     print               Set printmask
     store               Set storemask
     list                Show groups
     insert              Insert log message
     hist                Show history

Furthermore there is an alias for 'log print'::

   nanocom-ax # help debug     
     debug               log: Alias of 'log print'

print & store
-------------

The 'log print', 'debug' and 'log store' commands will change the logging levels for different groups, either for the console (print) target or the ram/fram (store) target. Here is an example of setting the debug flag for the 'mac' group::

   gosh # log print mac
   usage: print <group>[,group] <Err|Wrn|Inf|Dbg|Trc|Std|All|No>
   gosh # log print mac debug     
   Set mask of group mac from 0x18 to 0x1E
 
list
----

The 'list' commands shows all groups and their 'print' and 'store' targets::

   nanocom-ax # log list
   Group           Print Store
   axsem           EWIDT EW...
   event           ..... .....
   spidma          EWIDT EW...
   ...

insert
------

The insert command will create a new logging entry in the 'user' group of the logging system. This can be used to test the logging system and during testing to mark the begining or the result of a certain test::

   gosh # log insert         
   usage: insert <level> <message>
   gosh # log insert info "Beginning of some test"   
   3120366290.557 user: Beginning of some test
   
The accepted log level names are: 'error', 'warn', 'info', 'debug', trace' 

hist
----

The hist command will show the latest stored log entries::

   nanocom-ax # log insert error "Test error msg"
   3120367702.941 user: Test error msg
   nanocom-ax # log insert warn "Test warning"
   3120367708.950 user: Test warning
   nanocom-ax # log hist
   3120367708.950395 user: Test warning
   3120367702.941871 user: Test error msg
