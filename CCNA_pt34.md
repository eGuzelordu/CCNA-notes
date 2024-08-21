# CCNA Part 34

## Standart Access Control Lists

### Agenda:

* What Are ACLs?

* ACL Logic

* ACL Types

* Standart numbered ACLs

* Standart named ACLs

### What are ACLs?

* ACLs(Access contol lists) have multiple uses.

* This part will focus on the security perspective.

* ACLs funtion as a packet filter, instructing the router to permit or discard specific traffic.

* ACLs can filter traffic based on source/destination IP addresses, source/destination layer 4 ports, etc.

* How ACLs work:

    * Gather restriction requirments.

    * ACLs are configured globally on the router.

    * They are an ordered sequance of ACEs(Access Contrill Entries).

    * Configuring an ACL an ACL in global config mode will not make the ACL take effect.

    * The ACL must be applied to an interface.

    * ACLs are applied either inbound or outbound.

    * ACLs are made up of one or more ACEs.

    * When the router checks a packet against the ACL, it processes the ACEs in order, from top to bottom.

    * If the packet matches one of the ACEs in the ACL, the router takes the action and stops processing the ACL. All entries below the matching entry will be ignored.

    * Make sure to pay attention to the order of the rules when working with different netmasks.

    * Implicit deny: if traffic doesnt match any of the entries it will deny the packet.

### ACL Types

* Standart ACLs: Match based on source IP address only

    * Standart Numbered ACLs.

    * Standart Named ACLs.

* Extended ACLs: Match based on Source/Destination IP, Source/Destination Port, etc.

    * Extended numbered ACLs.

    * Extended Named ACLs.

### Standart ACLs

* Standart ACLs match traffic based only on the source IP address of the packet.

* Numbered ACLs are identified with a number (ie. ACL 1, ACL 2, ...).

* Diffrent types of ACLs have a diffrent range of numbers that can be used.

    * Standart ACLs can use 1-99 and 1300-1999.

* Basic command to config a standart numbered ACL is:

    * `access-list *number* {deny|permit} *ip* *wildcard-mask*`

    * `any` keywork can be used to target all ip addresses.

    * `remark` adds a note for the ACL

    * To apply ACL to interface go to interface on CLi and use command

        * `ip access-group *number* {in|out}`

* Standart name ACls

    * ACLs are identified with name.