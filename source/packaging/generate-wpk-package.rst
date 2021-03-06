.. Copyright (C) 2019 Wazuh, Inc.

.. _create-wpk:

WPK
===

Wazuh provides an automated way of building WPK packages using docker so there is no need for any other dependency.

You can see how to generate a WPK package, an X509 certificate and CA :ref:`here <create-wpk-key>`.

To create a WPK package follow these steps:

Requirements
^^^^^^^^^^^^

 * Docker
 * Git

Download our wazuh-packages repository from GitHub and go to the wpk directory.

.. code-block:: console

 $ git clone https://github.com/wazuh/wazuh-packages && cd wazuh-packages/wpk

Execute the ``generate_wpk_package.sh`` script, with the different options you desire. This script will build a Docker image with all the necessary tools to create the WPK and run a container that will build it:

.. code-block:: console

  $ ./generate_wpk_package.sh -h

  Usage: ./generate_wpk_package.sh [OPTIONS]

      -t,   --target-system <target>              [Required] Select target wpk to build [linux/windows]
      -b,   --branch <branch>                     [Required] Select Git branch or tag e.g.
      -d,   --destination <path>                  [Required] Set the destination path of package.
      -k,   --key-dir <path>                      [Required] Set the WPK key path to sign package.
      -a,   --architecture <arch>                 [Optional] Target architecture of the package [x86_64].
      -j,   --jobs <number>                       [Optional] Number of parallel jobs when compiling.
      -pd,  --package-directory <directory>       [Required for windows] Package name to pack on wpk.
      -o,   --output <name>                       [Required] Name to the output package.
      -c,   --checksum <path>                     [Optional] Generate checksum
      -h,   --help                                Show this help.

To use this tool, the previously required :ref:`certificate <create-wpk-key>` and the key must be in the same directory.

Linux WPK
^^^^^^^^^

Below, you will find an example of Linux WPK package building.

.. code-block:: console

  # ./generate_wpk_package.sh -t linux -b v3.11.3 -d /tmp/wpk -k /tmp/keys -o LinuxAgent.wpk

This will build a 3.11.3 Wazuh Linux WPK package named LinuxAgent.wpk, using the  with the previously generated keys that are saved in ``/tmp/keys`` and store it in ``/tmp/wpk``.

Windows WPK
^^^^^^^^^^^

To build a WPK for Windows you need to first download an MSI package of the desired version:

.. code-block:: console

  # curl -O https://packages.wazuh.com/3.x/windows/wazuh-agent-3.11.3-1.msi

Below, you will find an example of Windows WPK package building.

.. code-block:: console

  # ./generate_wpk_package.sh -t windows -b v3.11.3 -d /tmp/wpk -k /tmp/keys -o WindowsAgent.wpk -pd /tmp/wazuh-agent-3.11.3-1.msi

This will build a 3.11.3 Wazuh Windows WPK package named WindowsAgent.wpk, using the  with the previously generated keys that are saved in ``/tmp/keys`` and store it in ``/tmp/wpk``.

If the ``-c`` or ``--checksum`` option is used there will be a file containing the SHA512 checksum in the same output path or you can indicate where you want to store it.

Here you can see an example of how to build a WPK generation with checksum:

.. code-block:: console

  # ./generate_wpk_package.sh -t linux -b v3.11.3 -d /tmp/wpk -k /tmp/keys -o LinuxAgent.wpk -c /tmp/wpk_checksum
