Network Devices
===============
Commonly speaking, there are 3 types of network devices:

.. _endpoint:

Endpoint
--------

.. image:: /images/01/laptop.png
   :width: 400

Endpoints are the devices the network is trying to connect.

Typical endpoints include:

- Computers
- Laptops
- Servers
- Smartphones
- Printers

.. _switch:

Switch
------

.. image:: /images/01/switch.png
   :width: 400

Switch is a device used as a bridge between endpoints within the same network.

Switches can forward data from one device to another by their :ref:`MAC Address<mac>` (:ref:`OSI Layer 2 - Data Link<osi2>`).

.. note::

    Some switches have the capability to forward data by IP.

    They are called `Multilayer Switches <https://en.wikipedia.org/wiki/Multilayer_switch>`_.

.. _router:

Router
------

.. image:: /images/01/router.png
   :width: 400

Router is a device used as a bridge between different networks.

Routers can forward data from one network to another by their :ref:`IP Address<ip>` (:ref:`OSI Layer 3 - Network<osi3>`).

.. note::

    Some consumer-grade routers have a built-in switch.

    The first port (sometimes called WAN port) is usually used for the external network (internet), but the rest can be used for your internal network just as a switch.