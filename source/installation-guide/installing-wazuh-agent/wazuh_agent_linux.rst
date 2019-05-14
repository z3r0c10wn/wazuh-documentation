.. Copyright (C) 2019 Wazuh, Inc.

.. _wazuh_agent_linux:

Install Wazuh agent in Linux
============================

The Wazuh agent can be installed in the most of Linux Distribution. It's possible to use DEB packages or RPM packages depending on the target Operative System flavor. 

.. note:: All the commands described below need to be executed with root user privileges.

.. tabs::

    .. tab:: Debian
       
        1. To perform this procedure, the ``curl``, ``apt-transport-https`` and ``lsb-release`` packages must be installed on your system. If they are not already present, install them using the commands below:
        
          .. code-block:: console
        
            # apt-get install curl apt-transport-https lsb-release
        
        2. Add the repository:
        
          .. code-block:: console
        
            # curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | apt-key add - \
            echo "deb https://packages.wazuh.com/3.x/apt/ stable main" | tee /etc/apt/sources.list.d/wazuh.list \
            apt-get update
        
        3. On your terminal, install the Wazuh agent. You can choose installation or a deploy:
        
           .. tabs::
   
              .. tab:: Only installation
   
                 .. code-block:: console
   
                   # apt-get install wazuh-agent
   
                 Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.
   
              .. tab:: Deploy
   
                 .. code-block:: console
   
                   # WAZUH_MANAGER_IP="10.0.0.2" apt-get install wazuh-agent 
   
                 Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   

        
        4. **(Optional)** Disable the Wazuh updates:
        
          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:
        
          .. code-block:: console
        
            # sed -i "s/^deb/#deb/" /etc/apt/sources.list.d/wazuh.list
            # apt-get update
        
          Alternately, you can set the package state to ``hold``, which will stop updates (although you can still upgrade it manually using ``apt-get install``).
        
          .. code-block:: console
        
            # echo "wazuh-agent hold" | sudo dpkg --set-selections

    .. tab:: CentOS/RHEL

        1. Adding the Wazuh repository

          .. code-block:: console

            # rpm --import http://packages.wazuh.com/key/GPG-KEY-WAZUH 
            # cat > /etc/yum.repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
            enabled=1
            name=Wazuh repository
            baseurl=https://packages.wazuh.com/3.x/yum/
            protect=1
            EOF

        2. On your terminal, install the Wazuh agent. You can choose installation or a deploy:

        .. tabs::

           .. tab:: Only installation

              .. code-block:: console

                # yum install wazuh-agent

              Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.

           .. tab:: Deploy

              .. code-block:: console

                # WAZUH_MANAGER_IP="10.0.0.2" yum install wazuh-agent 

              Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   


        3. **(Optional)** Disable the Wazuh repository:

          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:

          .. code-block:: console

            # sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo

    .. tab:: Fedora

        1. Adding the Wazuh repository

          .. code-block:: console

            # rpm --import http://packages.wazuh.com/key/GPG-KEY-WAZUH 
            # cat > /etc/yum.repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
            enabled=1
            name=Wazuh repository
            baseurl=https://packages.wazuh.com/3.x/yum/
            protect=1
            EOF

        2. On your terminal, install the Wazuh agent. You can choose installation or a deploy:

        .. tabs::

           .. tab:: Only installation

              .. code-block:: console

                # dnf install wazuh-agent

              Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.

           .. tab:: Deploy

              .. code-block:: console

                # WAZUH_MANAGER_IP="10.0.0.2" dnf install wazuh-agent 

              Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   


        3. **(Optional)** Disable the Wazuh repository:

          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:

          .. code-block:: console

            # sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo


    .. tab:: Amazon/Oracle Linux

        1. Adding the Wazuh repository

          .. code-block:: console

            # rpm --import http://packages.wazuh.com/key/GPG-KEY-WAZUH
            # cat > /etc/yum.repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
            enabled=1
            name=Wazuh repository
            baseurl=https://packages.wazuh.com/3.x/yum/
            protect=1
            EOF

        2. On your terminal, install the Wazuh agent. You can choose installation or a deploy:

        .. tabs::

           .. tab:: Only installation

              .. code-block:: console

                # yum install wazuh-agent

              Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.

           .. tab:: Deploy

              .. code-block:: console

                # WAZUH_MANAGER_IP="10.0.0.2" yum install wazuh-agent 

              Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   


        3. **(Optional)** Disable the Wazuh repository:

          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:

          .. code-block:: console

            # sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo

    .. tab:: Centos 5

        1. Adding the Wazuh repository

          .. code-block:: console

            # rpm --import http://packages.wazuh.com/key/GPG-KEY-WAZUH-5 
            # cat > /etc/yum.repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=http://packages.wazuh.com/key/GPG-KEY-WAZUH-5
            enabled=1
            name=Wazuh repository
            baseurl=http://packages.wazuh.com/3.x/yum/5/$basearch/
            protect=1
            EOF

        2. On your terminal, install the Wazuh agent. You can choose installation or a deploy:

        .. tabs::

           .. tab:: Only installation

              .. code-block:: console

                # yum install wazuh-agent

              Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.

           .. tab:: Deploy

              .. code-block:: console

                # WAZUH_MANAGER_IP="10.0.0.2" yum install wazuh-agent 

              Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   


        3. **(Optional)** Disable the Wazuh repository:

          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:

          .. code-block:: console

            # sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo



    .. tab:: SUSE/OpenSUSE 

      .. tabs::

        .. tab:: SUSE 12, OpenSUSE 42, OpenSUSE Leap and OpenSUSE Tumbleweed

          .. code-block:: console

            # rpm --import https://packages.wazuh.com/key/GPG-KEY-WAZUH
            # cat > /etc/zypp/repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
            enabled=1
            name=Wazuh repository
            baseurl=https://packages.wazuh.com/3.x/yum/
            protect=1
            EOF

        .. tab:: SUSE 11

          .. code-block:: console
        
            # rpm --import https://packages.wazuh.com/key/GPG-KEY-WAZUH-5
            # cat > /etc/zypp/repos.d/wazuh.repo <<\EOF
            [wazuh_repo]
            gpgcheck=1
            gpgkey=http://packages.wazuh.com/key/GPG-KEY-WAZUH-5
            enabled=1
            name=Wazuh repository
            baseurl=http://packages.wazuh.com/3.x/yum/5/$basearch/
            protect=1
            EOF


        2. On your terminal, install the Wazuh agent. You can choose installation or a deploy:

        .. tabs::

           .. tab:: Only installation

              .. code-block:: console

                # zypper install wazuh-agent

              Now that the agent is installed, the next step is to register and configure it to communicate with the manager. For more information about this process, please visit the :doc:`user manual<../../user-manual/registering/index>`.

           .. tab:: Deploy

              .. code-block:: console

                # WAZUH_MANAGER_IP="10.0.0.2" zypper install wazuh-agent 

              Now that agent is installed, registered and configured. Using the variable ``WAZUH_MANAGER_IP`` without ``WAZUH_AUTHD_SERVER`` the agent will register and report to the indicated IP of ``WAZUH_MANAGER_IP``. If you want to register to different Wazuh Manager, you need to use ``WAZUH_AUTHD_SERVER``. See the following document for additional automated deployment options: :doc:`automated deployment variables <automated_deployment_variables>`.   


        3. **(Optional)** Disable the Wazuh repository:

          It is recommended that the Wazuh repository be disabled in order to prevent accidental upgrades. To do this, use the following command:

          .. code-block:: console

            # sed -i "s/^enabled=1/enabled=0/" /etc/zypp/repos.d/wazuh.repo

Alternatively, if you want to download the wazuh-agent package directly, or check the compatible versions, you can do it from :ref:`here <packages>`.