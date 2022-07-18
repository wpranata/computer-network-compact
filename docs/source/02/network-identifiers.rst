Network Identifiers
===================
A typical device that is connected to a network has the following properties:

- ``MAC Address``
- ``IP Address``
- ``Subnet Mask``
- ``Network Address``
- ``Broadcast Address``

Example of a typical device network information:

.. code-block:: console

    Physical Address. . . . . . . . . : DC-41-A9-4A-EE-03
    IPv4 Address. . . . . . . . . . . : 10.20.184.12
    Subnet Mask . . . . . . . . . . . : 255.255.252.0
    Network Address . . . . . . . . . : 10.20.184.0
    Broadcast Address . . . . . . . . : 10.20.187.255
    Default Gateway . . . . . . . . . : 10.20.184.1


.. _mac:

MAC Address
-----------
**Media Access Control (MAC) address** (also known as **physical address**) is a unique identifier assigned to a device as a network address in communications within a network segment.
MAC Address acts as the 'device ID' within a network.
MAC Address work in :ref:`OSI Layer 2 - Data Link<osi2>`.

MAC addresses are primarily assigned by device manufacturers in hardware, such as the card's read-only memory, or by a firmware mechanism.
Many network interfaces, however, support changing their MAC address.

Currently, there are 2 formats of MAC Address: ``EUI-48`` and ``EUI-64``.
Both are composed of pairs of Hexadecimals, seperated by dash ``-``, semicolon ``:``, or dot ``.``, or not separated at all.

``EUI-48`` has ``6`` pairs of Hexadecimals, while ``EUI-64`` has ``8`` pairs.

Example of ``EUI-48 MAC address``:

- ``00-10-FA-6E-38-4A``
- ``00:10:FA:6E:38:4A``
- ``0010.FA6E.384A``
- ``0010FA6E384A``

Example of ``EUI-64 MAC address``:

- ``2F-A2-09-5E-FF-83-B2-34``
- ``2F:A2:09:5E:FF:83:B2:34``
- ``2FA2.095E.FF83.B234``
- ``2FA2095EFF83B234``


.. _ip:

IP Address
----------
**Internet Protocol (IP) address** is a numerical label assigned to a device as a network address in communications between network segments.
IP Address acts as the 'device location' between networks.
IP Address work in :ref:`OSI Layer 3 - Network<osi3>`.

.. TODO: :ref: DHCP Server

IP addresses can be manually assigned, or automatically assigned by a DHCP Server.

Currently, there are 2 formats of IP Address: ``IPv4`` and ``IPv6``.

``IPv4`` addresses has a size of ``32-bits``, and are divided into ``4 octets``, each ranging between ``0 - 255``, separated by dot ``.``.

``IPv6`` addresses has a size of ``128-bits``, and are divided into ``8 octets``, each comprised of 2 pairs of Hexadecimal characters, separated by semicolon ``:``.

Example of ``IPv4 address``:

- ``192.168.233.134``
- ``172.168.15.23``
- ``36.26.17.231``
- ``8.0.0.8``

Example of ``IPv6 address``:

- ``EF5A:11A9:2499:53E2:04B5:7713:2494:9EBD``
- ``F342:3A0D:9563:FEEB:2604:F0E2:E77E:C64D``
- ``5780:BDF0:41BC:3293:6204:8E31:3F6A:4CDF``
- ``FED8:D7A7:E193:AAEA:6A11:2147:F835:C9EC``

.. _subnet:

Subnet Mask
-----------
**Subnet mask** is a ``32-bit`` number correlated with a host's network.

**Subnet mask** can be used to:

- find the amount of endpoints a network can support.
- find the network and broadcast address (using ``wildcard``) from an ``IPv4 address``.

**Subnet mask** is created by setting host bits to all ``0`` and setting network bits to all ``1``.

**Subnet mask** can be represented using a ``4-octet`` system (just like ``IPv4 addresses``), or using ``CIDR Notation``, which counts the number of ``1`` s within the subnet mask, lead by slash ``/``.

Example of ``subnet mask``:

- ``255.255.255.0`` ``/24``
- ``255.255.0.0`` ``/16``
- ``255.255.252.0`` ``/22``
- ``255.0.0.0`` ``/8``

.. note::

    ``Wildcard`` is the reverse of a subnet mask.
    It can be used to find the ``Broadcast Address`` of a network.

Network Address
---------------
**Network Address** is the address of the network a host resides.

**Network Address** can be calculated from the ``AND`` operation between a host's ``IPv4 address`` and its subsequent ``subnet mask``.

For Example, to find the **network address** of an IPv4 Address ``10.20.184.12/22`` with the subnet ``/22`` or ``255.255.252.0``:

1. Convert the ``IP Address`` and the ``subnet mask`` into bits

.. code-block:: console

     10. 20.184.12 = 00001010.00010100.10111000.00001100
    255.255.252. 0 = 11111111.11111111.11111100.00000000

2. Do an ``AND`` operation, and convert the result back into ``IPv4 address``

.. code-block:: console

     10. 20.184.12 = 00001010.00010100.10111000.00001100
    255.255.252. 0 = 11111111.11111111.11111100.00000000
    ----------------------------------------------------&
                     00001010.00010100.10111000.00000000 = 10.20.184.0

The **Network address** of ``10. 20.184.12/22`` is ``10.20.184.0``.

Broadcast Address
-----------------
**Broadcast Address** is the address used to broadcast message within a network.

**Broadcast Address** can be calculated from the ``OR`` operation between a host's ``IPv4 address`` and its subsequent ``wildcard``.

For Example, to find the **broadcast address** of an IPv4 Address ``10.20.184.12/22`` with the subnet ``/22`` or ``255.255.252.0``:

1. Find the ``Wildcard`` of the ``subnet mask``:

.. code-block:: console

    subnet   255.255.252.  0 = 11111111.11111111.11111100.00000000
    wildcard   0.  0.  3.255 = 00000000.00000000.00000011.11111111

2. Do an ``OR`` operation, and convert the result back into ``IPv4 Address``

.. code-block:: console

    10. 20.184. 12 = 00001010.00010100.10111000.00001100
     0.  0.  3.255 = 00000000.00000000.00000011.11111111
    ----------------------------------------------------|
                     00001010.00010100.10111011.11111111 = 10.20.187.255

The **Broadcast address** of ``10. 20.184.12/22`` is ``10.20.187.255``.

Gateway Address
---------------
**Gateway** acts as the access point for the network.

When a packet wants to enter / exit the network, it has to go through the **Gateway**.

In most cases, the **Gateway Address** is the first address of the network, although this is completely configurable.

.. note::

    If you are having a hard understanding these concepts, try the Apartment Terminology;

    Imagine an apartment filled with rooms.

    - ``Network Address`` is the address of the actual apartment.
    - ``Broadcast Address`` is the announcement room, used to broadcast announcement to all of the tenants. It is always on the top floor.
    - ``Gateway Address`` is the lobby / receptionist of the apartment. It is usually on the first floor, although it can be on any floor.
    - ``Host IPv4 Address`` is the rooms of the tenants within the apartment.
    - ``MAC Address`` is your actual ID number. Your room may change, but you can never change your own ID.