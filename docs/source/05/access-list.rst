Access List
===========
Access-list (ACL) is **a set of rules defined for controlling network traffic** and reducing network attacks.
ACLs are used to **filter traffic based on the set of rules defined** for the incoming or outgoing of the network. 

There are 2 types of ACLs: **Standard** and **Extended Access List**.

Standard Access List
--------------------
Standard Access Lists are made using the source IP address only.
This ACL **permits and denies the entire protocol suite**; They **do not distinguish between protocols** such as TCP, UDP, HTTPS, ICMP, etc.

Standard Access List number ranges are ``1 - 99`` and ``1300 - 1999``.

.. note::
   The standard Access-list is generally applied **close to the destination** (but not always).

Extended Access List
--------------------
Extended Access Lists are made using source IP, destination IP, source Port, and destination Port.
This ACL **can permit and deny specific protocols** such as TCP, UDP, HTTPS, ICMP, etc.

Extended Access List number ranges are ``100 - 199`` and ``2000 - 2699``.

.. note::
   The extended Access-list is generally applied **close to the source** (but not always).

Inbound and Outbound Traffic
----------------------------
Inbound and outbound traffic refers to the direction of the traffic flowing between interfaces.

Inbound traffic means the traffic is **flowing into** the interface, while Outbound traffic means the traffic is **flowing from** the interface.

.. image:: /images/05/traffic_0-1.png
   :width: 800

.. figure:: /images/05/traffic_1-0.png
   :width: 800

   Example Inbound and Outbound traffic of each interface in the network. 

.. note::
   We can assign only one ACL per interface per protocol per direction, i.e., **only one inbound and outbound ACL is permitted per interface**.

Configure Access List in Packet Tracer
----------------------------------------

.. note::
    You can download the example network `here <https://binusianorg-my.sharepoint.com/personal/winner_pranata_binus_edu/_layouts/15/guestaccess.aspx?docid=0fcd7a044b6b246f69fe71da58d5767ef&authkey=AfC8IQX4gRkLpCdjjJu9zGM&e=ksUckD>`_.

In this example, we are trying to **prevent communication between PC-IT-1 and PC-Marketing-2** by creating an **Extended Access List**, with **ACL number 101**, on an **inbound traffic** on **Router 1 FastEthernet 0/0 interface**.

First, setup the network according to the supplied information.

Open **Router 1**, go to **CLI**.

We will be inputting the commands required to setup the ACL.

Opening the Configuration Terminal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
First, we have to open the configuration terminal.
We can achieve this by using the ``enable`` and ``configure terminal`` command.

.. code-block:: console

   Router>enable
   Router#configure terminal
   Enter configuration commands, one per line.  End with CNTL/Z.
   Router(Config)#

.. important::
   Notice the symbols changing at the end of each line, ``>`` and ``#``.

Setting up Access List Rules
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We can specify the Access List rule by using the command:

.. code-block:: console

   access-list <ACL number> <permit|deny> <protocol> <source type> <source address> <destination type> <destination address>

.. code-block:: console

   Router(config)#access-list 101 deny ip host 192.168.100.2 host 192.168.100.99
   Router(config)#access-list 101 permit ip any any

.. important::
   We specify 2 rules: ``deny`` and ``permit``.
   
   As there is an implicit ``deny`` at the end of every access list, we should have at least a ``permit`` statement in our Access-list; otherwise all traffic will be denied.

.. note::
   We can type ``?`` at every argument part of the command to show the list of available arguments.

Applying Access List Into the Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
After establishing the Access List rule, we can apply it into our interface.

Still in the Router CLI, navigate into the FastEthernet 0/0 interface.

.. code-block:: console

   Router(config)#interface FastEthernet 0/0
   Router(config-if)#

Apply the Access List by supplying its Access List Number and in/out rule.

.. code-block:: console

   Router(config-if)#ip access-group 101 in
   Router(config-if)#
