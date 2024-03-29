Backend documentation
=====================

Here is the documentation for Backend code. The documentation is not complete, and is 
automatically generated using the :code:`sphinx` python package, meaning there can be 
weird formatting in places, since not all documentation is strictly adhering to a specfic
documentation style. To run backend after doing first time  initialization, you simply run
(from root folder) the below command

.. code-block::

  python -m src.backend.main

This will spawn an instance of :code:`src.backend.mqttclient` using the configurations
of the project.

For first time initialization, you want to place a :code:`metadata.xlsx` file in the root
location that is configured according to the attached :code:`metadata_example.xlsx`. Once
that is in place, you can initalize backend as so:

.. code-block::

   python -m src.backend.main -i
   [...] Do you wish to convert metadata from an excel (xlsx) file? [y/n]: y
   Please input ip-address: 127.0.0.1
   and port number: 1883
   username: mqttuser
   Password: mqttpassword

You will be prompted to fill in :code:`mqtt` broker information. After the information has
been filled out :code:`src.backend.main` will attempt to spawn :code:`src.backend.mqttclient`
as a subprocess. Whenever it crashes it will attempt to respawn the process. That means that
if the mqqt-client is unable to connect to the broker, it will keep respawning the client.
If this is the case, kill the process, and then run :code:`python -m backend.src.main` again
with the :code:`-i` flag, or both the :code:`-i` and :code:`-r` flag. You will be 
prompted to fill out the MQTT broker configuration again. Alternatively, you can edit the 
MQTT configuration directly inside :code:`src/backend/.config/config.toml`.

To see all arguments that :code:`src.backend.main` supports, run 

.. code-block::
    
    python -m src.backend.main -h

Again, make sure to have an excel file in the root location that is named :code:`metadata.xlsx`.
Otherwise, the init cannot convert the project metadata to its own internal metadata files.
Without them, frontend cannot work, and features of backend will not work either, such as raw 
data conversion and positioning. 

.. figure:: images/backend_flow.png
    :width: 100%
    :align: center
    :alt: Backend MQTT client logic flow


Top-level modules
-----------------

main
~~~~


.. automodule:: src.backend.main
    :members:
    :undoc-members:

mqttclient
~~~~~~~~~~

.. automodule:: src.backend.mqttclient
    :members:
    :undoc-members:

initbackend
~~~~~~~~~~~

.. automodule:: src.backend.initbackend
    :members:
    :undoc-members:

Message handling
----------------

conversion
~~~~~~~~~~

.. automodule:: src.backend.msghandler.conversion
    :members:
    :undoc-members:

msghandler
~~~~~~~~~~

.. automodule:: src.backend.msghandler.msghandler
    :members:
    :undoc-members:

packet
~~~~~~

.. automodule:: src.backend.msghandler.packet
    :members:
    :undoc-members:

protocol
~~~~~~~~

.. automodule:: src.backend.msghandler.protocol
    :members:
    :undoc-members:

Databasemanager
---------------

dbformat
~~~~~~~~

.. automodule:: src.backend.dbmanager.dbformat
    :members:

dbinit
~~~~~~

.. automodule:: src.backend.dbmanager.dbinit
    :members:

dbmanager
~~~~~~~~~

.. automodule:: src.backend.dbmanager.dbmanager
    :members:


msgbackup
~~~~~~~~~

.. automodule:: src.backend.dbmanager.msgbackup
    :members:

msgconversion
~~~~~~~~~~~~~

.. automodule:: src.backend.dbmanager.msgconversion
    :members:

positioning
~~~~~~~~~~~

.. automodule:: src.backend.dbmanager.positioning
    :members:

tdoa
~~~~

.. automodule:: src.backend.dbmanager.tdoa
    :members:

