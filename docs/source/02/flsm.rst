FLSM (Fixed-Length Subnet Mask)
===============================
A network can be divided into multiple smaller networks.
Two of the division methods are called **Fixed-Length Subnet Mask (FLSM)** and **Variable-Length Subnet Mask (VLSM)**.

**FLSM** works by **dividing the network into equal subnets**, while VLSM divides the network as small as possible.

FLSM is easier to calculate because the subnets are equal.

FLSM is divided into several steps:

1. (Optional) Find the network address.
2. Divide the network ``subnet`` by the largest Endpoint demand.
3. Assign each network.

Example
-------
Suppose an organization with the **network address** ``192.168.100.0/24`` wants to divide the network into 3 parts:

- **Finance**, with ``30 Endpoints``.
- **Marketing**, with ``15 Endpoints``.
- **IT**, with ``60 Endpoints``.

(Optional) Find the network address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Since we already know the **network address** is ``192.168.100.0/24``, we can skip this step.

Divide the network by the largest Endpoint demand
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The largest endpoint demand is ``60 endpoints``.
Therefore, we need a subnet that could support ``60 endpoints + 1 network address + 1 broadcast address``.

We can use the formula ``E+2 <= 2^n``, where ``E`` is the amount of endpoints, and ``n`` is the smallest ``wildcard`` value.

Since ``E = 60``, we can determine that ``n >= 6``.

To determine the ``subnet``, we can simply subtract ``32`` with the smallest ``n``, where ``32-6 = /26``.

Assign each network
~~~~~~~~~~~~~~~~~~~
Now that we have found the correct subnet, we can assign each network into their respective parts.

We know that the subnet ``/26`` can support ``64 Addresses`` (from ``2^n``), this means every network could support ``64 addresses``.

Finance
^^^^^^^
=================   ==================================
Subnet Mask         ``255.255.255.192 (/26)``
Network Address     ``192.168.100.0``
Usable IP Range     ``192.168.100.1 - 192.168.100.62``
Broadcast Address   ``192.168.100.63``
=================   ==================================

Marketing
^^^^^^^^^
=================   ==================================
Subnet Mask         ``255.255.255.192 (/26)``
Network Address     ``192.168.100.64``
Usable IP Range     ``192.168.100.65 - 192.168.100.126``
Broadcast Address   ``192.168.100.127``
=================   ==================================

IT
^^^
=================   ==================================
Subnet Mask         ``255.255.255.192 (/26)``
Network Address     ``192.168.100.128``
Usable IP Range     ``192.168.100.129 - 192.168.100.190``
Broadcast Address   ``192.168.100.191``
=================   ==================================

.. note::

    Gateway is included within the Usable IP Range.