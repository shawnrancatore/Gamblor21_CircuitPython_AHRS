Introduction
============


.. image:: https://readthedocs.org/projects/circuitpython-ahrs/badge/?version=latest
    :target: https://circuitpython-ahrs.readthedocs.io/
    :alt: Documentation Status

.. image:: https://img.shields.io/discord/327254708534116352.svg
    :target: https://adafru.it/discord
    :alt: Discord

.. image:: https://github.com/gamblor21/CircuitPython_AHRS/workflows/Build%20CI/badge.svg
    :target: https://github.com/gamblor21/CircuitPython_AHRS/actions
    :alt: Build Status

.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://github.com/psf/black
    :alt: Code Style: Black

AHRS library for CircuitPython

This library contains right now one alogrithm for AHRS - Attitude and Heading Reference System.
It is used to combine multiple sensor values to give a heading, pitch and roll value such as used
by aircraft.

See the `Wiki <https://github.com/gamblor21/CircuitPython_AHRS/wiki>`_ for a more complete description.

Dependencies
=============
This library depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://circuitpython.org/libraries>`_.


Usage Example
=============

Create the filter, set the parameters and start feeding it sensor data

.. code-block:: shell

	filter = mahony.Mahony(Kp, Ki, sample_frequency)
	
	while True:
		filter.update(gx, gy, gz, ax, ay, az, mx, my, mz)

Caution
========
The calculations are very processor intensive. I have tested this on an Adafruit Feather M4 Express.
Mahony was able to do about 300 samples/sec
Madgwick was only able to about 15 samples/sec

Also be careful which values you feed the filter and the orientation of your sensor.
I turned the gryoscope/accelerometer off to make sure magnetic fields were correct and then
turned on only the gyroscope/accelerometer to ensure they were correct.

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/gamblor21/CircuitPython_AHRS/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Documentation
=============

Rebuild
