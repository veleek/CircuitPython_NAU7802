Introduction
============




.. image:: https://img.shields.io/discord/327254708534116352.svg
    :target: https://adafru.it/discord
    :alt: Discord


.. image:: https://github.com/CedarGroveStudios/CircuitPython_NAU7802/workflows/Build%20CI/badge.svg
    :target: https://github.com/CedarGroveStudios/CircuitPython_NAU7802/actions
    :alt: Build Status


.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://github.com/psf/black
    :alt: Code Style: Black

An async CircuitPython driver class for the NAU7802 24-bit ADC.  This is a fork of the original
`NAU7802 driver <https://github.com/adafruit/CircuitPython_NAU7802>`_ that converts certain operations into
async methods.  This allows the driver to play nice with other async code especially if you're doing potentially long
running operations such as reading and averaging dozens of samples.  The original driver blocks all code execution
while waiting for data to become available while this one will yield (a zero async sleep) to allow other code to run.

Since checking the availability of and reading data from the load cell is already non-blocking this is mostly useful for
enabling non-blocking initialization, but also serves as a good example of how to read data in an async friendly way.


Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_
* `Bus Device <https://github.com/adafruit/Adafruit_CircuitPython_BusDevice>`_
* `Register <https://github.com/adafruit/Adafruit_CircuitPython_Register>`_
* `Asyncio <https://github.com/adafruit/Adafruit_CircuitPython_asyncio>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://circuitpython.org/libraries>`_
or individual libraries can be installed using
`circup <https://github.com/adafruit/circup>`_.

Installing to a Connected CircuitPython Device with Circup
==========================================================

Make sure that you have ``circup`` installed in your Python environment.
Install it with the following command if necessary:

.. code-block:: shell

    pip3 install circup

With ``circup`` installed and your CircuitPython device connected use the
following command to install:

.. code-block:: shell

    circup install cedargrove_nau7802_async

Or the following command to update an existing version:

.. code-block:: shell

    circup update

Usage Example
=============

.. code-block:: py

    import asyncio
    import board
    from cedargrove_nau7802_async import NAU7802

    # Instantiate NAU7802 ADC
    nau7802 = await NAU7802.create_async(board.I2C(), address=0x2A, active_channels=2)

``nau7802_simpletest.py`` and other examples can be found in the ``examples`` folder.


Documentation
=============
`NAU7802 CircuitPython Driver API Class Description <https://github.com/CedarGroveStudios/CircuitPython_NAU7802/blob/main/media/pseudo_readthedocs_cedargrove_nau7802.pdf>`_


`Clue Coffee Scale (Adafruit Learning Guide) <https://learn.adafruit.com/clue-coffee-scale>`_


`CedarGrove NAU7802 FeatherWing OSH Park Project (16-SOIC version) <https://oshpark.com/shared_projects/qFvEU3Bn>`_

`CedarGrove NAU7802 FeatherWing OSH Park Project (16-DIP version) <https://oshpark.com/shared_projects/ZfryHYnc>`_

.. image:: https://github.com/CedarGroveStudios/CircuitPython_NAU7802/blob/main/media/glamor_shot.jpeg

.. image:: https://github.com/CedarGroveStudios/CircuitPython_NAU7802/blob/main/media/Clue_scale_trim.png

Needing a calibration weight? The `U.S. Mint coin specifications <https://www.usmint.gov/learn/coin-and-medal-programs/coin-specifications>`_ might have some information that could help -- if you have some spare change.


Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/CedarGroveStudios/Cedargrove_CircuitPython_NAU7802/blob/HEAD/CODE_OF_CONDUCT.md>`_
before contributing to help this project be welcoming to everyone.
