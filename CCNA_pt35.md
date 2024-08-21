# CCNA Part 35

## Extended Access Control Lists

### Agenda

* Another way to configure numbered ACLs

* Edditing ACLs

* Extended Numbered and named ACLs

### Configuring numbered ACLs with subcommands

* In moderen IOS you can also configure numbered ACLs in the exact same way as named ACLs

* Advantages of named ACL config mode

    * You can easily delete individual entries in the ACL with no entry-number.

    * You can insert new entries inbetween other entries by specifiying the sequance number.

* Resequanceing ACLs.

    * There is a reseuqencing function that helps edit ACLs

    * The command is `ip access-list requeuance *acl-id*  *starting-seq-num* *increment*`.

### Extended ACLs

* Extended ACLs function mostly the same as standart ACLs

* They can be numbered or named, just like standart ACLs

    * Numbered ACLs use the following ranges: 100-199, 2000-2699.

* They are processed from top to bottom, just like standart ACLs

* However, the can match traffic based on more parameters, so they are more percise(and more complex) than standart ACLs.

* We will focus on matching based on these main parameters: Layer 4 protocol/port, source address, and destination address.

* use command `access-list *number* [permit|deny] *protocol* *src-ip* *dest-ip*.

* Extended ACLs can match based on protocol(ie. TCP, UDP, OSPF, EIGRP, etc.)

* Matching the source/destination IP address.

* Matching The TCP/UDP port numbers

    * When matching TCP/UDP, you can optionally specify the source and/or destination port numbers to match
