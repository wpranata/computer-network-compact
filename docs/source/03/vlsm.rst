VLSM (Variable-Length Subnet Mask)
==================================
A network can be divided into multiple smaller networks.
Two of the division methods are called **Fixed-Length Subnet Mask (FLSM)** and **Variable-Length Subnet Mask (VLSM)**.

**VLSM** works by **dividing the network as small as possible**, while FLSM divides the network into equal subnets.

VLSM is more efficient because it only divide subnets into its required sizes.

VLSM is divided into several steps:

1. (Optional) Find the network address.
2. Sort the division demands by the Endpoint demand, from largest to smallest.
3. Divide the network ``subnet`` according to each of their Endpoint demands.
4. Assign each network.

Example
-------
Suppose an organization with the **network address** ``192.168.100.0/24`` wants to divide the network into 3 parts:

- **Finance**, with ``30 Endpoints``.
- **Marketing**, with ``15 Endpoints``.
- **IT**, with ``60 Endpoints``.

(Optional) Find the network address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Since we already know the **network address** is ``192.168.100.0/24``, we can skip this step.

Sort the division demands by the Endpoint demand, from largest to smallest
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We will sort the organization parts by their endpoint demands, like so:

1. **IT**, with ``60 Endpoints``.
2. **Finance**, with ``30 Endpoints``.
3. **Marketing**, with ``15 Endpoints``.

This is done to preserve the division of the network, since VLSM needs to be done decrementally.
If it is not done decrementally, it would be very difficult to calculate.

Divide the network according to each of their Endpoint demands
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We will start from the largest to the smallest.

IT
^^^
The endpoint demand is ``60 endpoints``.
Therefore, we need a subnet that could support ``60 endpoints + 1 network address + 1 broadcast address``.

We can use the formula ``E+2 <= 2^n``, where ``E`` is the amount of endpoints, and ``n`` is the smallest ``wildcard`` value.

Since ``E = 60``, we can determine that ``n >= 6``.

To determine the ``subnet``, we can simply subtract ``32`` with the smallest ``n``, where ``32-6 = /26``.

Finance
^^^^^^^
The endpoint demand is ``30 endpoints``.
Therefore, we need a subnet that could support ``30 endpoints + 1 network address + 1 broadcast address``.

We can use the formula ``E+2 <= 2^n``, where ``E`` is the amount of endpoints, and ``n`` is the smallest ``wildcard`` value.

Since ``E = 30``, we can determine that ``n >= 5``.

To determine the ``subnet``, we can simply subtract ``32`` with the smallest ``n``, where ``32-5 = /27``.

Marketing
^^^^^^^^^
The endpoint demand is ``15 endpoints``.
Therefore, we need a subnet that could support ``15 endpoints + 1 network address + 1 broadcast address``.

We can use the formula ``E+2 <= 2^n``, where ``E`` is the amount of endpoints, and ``n`` is the smallest ``wildcard`` value.

Since ``E = 15``, we can determine that ``n >= 5``.

To determine the ``subnet``, we can simply subtract ``32`` with the smallest ``n``, where ``32-5 = /27``.

Assign each network
~~~~~~~~~~~~~~~~~~~
Now that we have found the correct subnets, we can assign each network into their respective parts.

IT
^^^
We know that the subnet ``/26`` can support ``64 Addresses`` (from ``2^n``), this means every network could support ``64 addresses``.

=================   ==================================
Subnet Mask         ``255.255.255.192 (/26)``
Network Address     ``192.168.100.0``
Usable IP Range     ``192.168.100.1 - 192.168.100.62``
Broadcast Address   ``192.168.100.63``
=================   ==================================

Finance
^^^^^^^
We know that the subnet ``/27`` can support ``32 Addresses`` (from ``2^n``), this means every network could support ``32 addresses``.

=================   ==================================
Subnet Mask         ``255.255.255.224 (/27)``
Network Address     ``192.168.100.64``
Usable IP Range     ``192.168.100.65 - 192.168.100.94``
Broadcast Address   ``192.168.100.95``
=================   ==================================

Marketing
^^^^^^^^^
We know that the subnet ``/27`` can support ``32 Addresses`` (from ``2^n``), this means every network could support ``32 addresses``.

=================   ==================================
Subnet Mask         ``255.255.255.224 (/27)``
Network Address     ``192.168.100.96``
Usable IP Range     ``192.168.100.97 - 192.168.100.126``
Broadcast Address   ``192.168.100.127``
=================   ==================================

.. note::

    Gateway is included within the Usable IP Range.