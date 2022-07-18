OSI Model
=========
The **Open Systems Interconnection model (OSI model)** is a conceptual model that describes the universal standard of communication functions, without any regard to the system's underlying internal technology and specific protocol suites.

In theory, every communication between devices can be described within the OSI Model.

There are 7 layers within the OSI Model:

.. _osi7:

OSI Layer 7 - Application
-------------------------
Application is the software that initiated the communication.

Application is the closest layer to the user, since users typically use applications to interact with the network.

Common examples include:

- Internet Browser (Chrome, Firefox, Brave, etc.)
- Online Games (more specifically, the networking library used within the code)
- Remote Applications
- Remote File Managers

.. _osi6:

OSI Layer 6 - Presentation
--------------------------
Presentation layer establishes data formatting and translation into a specific format.

Common examples include:

- HTTP / HTTPS
- FTP
- SSH
- SMB
- SMTP

.. _osi5:

OSI Layer 5 - Session
---------------------
Session layer establishes, maintans, and terminates the 'connection' between 2 devices.

Common examples include:

- Name lookups using DNS
- Authentication
- Session establishment

.. _osi4:

OSI Layer 4 - Transport
-----------------------
Transport layer provides the procedural means of transferring data.

Some parameters, such as **connection reliability** and **packet size** are considered in this layer.

This is where the data might require chunking into data segments, since the :ref:`Network Layer (OSI Layer 3)<osi3>` imposes a maximum packet size.

Common examples include:

- TCP
- UDP
- TLS (technically TLS belongs in the HTTPS :ref:`Presentation Layer<osi6>`)

.. _osi3:

OSI Layer 3 - Network
---------------------
Network layer provides the means of data transmission between networks, using :ref:`IP Addresses<ip>`.

:ref:`Routers<router>` operate in this layer.

.. _osi2:

OSI Layer 2 - Data Link
-----------------------
Data Link layer provides the means of data transmission between two connected nodes, using :ref:`MAC Addresses<mac>`.

:ref:`Switches<switch>` operate in this layer.

.. _osi1:

OSI Layer 1 - Physical
----------------------
Physical layer provides the means of data transmission between two components, typically through conductors, such as cables or copper pins.