Invocation
==========


Test multiples hosts
~~~~~~~~~~~~~~~~~~~~

By default Testinfra launch tests on local machine, but you can also
test remotes systems using `paramiko <http://www.paramiko.org>`_ (a
ssh implementation in python)::

    $ pip install paramiko
    $ testinfra -v --hosts=localhost,root@webserver:2222 test_myinfra.py

    ====================== test session starts ======================
    platform linux -- Python 2.7.3 -- py-1.4.26 -- pytest-2.6.4
    plugins: testinfra
    collected 3 items 

    test_myinfra.py::test_passwd_file[localhost] PASSED
    test_myinfra.py::test_nginx_is_installed[localhost] PASSED
    test_myinfra.py::test_nginx_running_and_enabled[localhost] PASSED
    test_myinfra.py::test_passwd_file[root@webserver:2222] PASSED
    test_myinfra.py::test_nginx_is_installed[root@webserver:2222] PASSED
    test_myinfra.py::test_nginx_running_and_enabled[root@webserver:2222] PASSED

    =================== 6 passed in 8.49 seconds ====================


Parallel execution
~~~~~~~~~~~~~~~~~~

If you have a lot of tests, you can use the pytest-xdist_ plugin to run tests using multiples process::


    $ pip install pytest-xdist

    # Launch tests using 3 processes
    $ testinfra -n 3 -v --host=web1,web2,web3,web4,web5,web6 test_myinfra.py


Advanced invocation
~~~~~~~~~~~~~~~~~~~

::

    # Test recursively all test files (starting with `test_`) in current directory
    $ testinfra

    # Filter function/hosts with pytest -k option
    $ testinfra --hosts=webserver,dnsserver -k webserver -k nginx


For more usages and features, see the Pytest_ documentation.


Nagios plugin
~~~~~~~~~~~~~

You can turn your test session into a nagios check::

    $ testinfra test_myinfra.py --nagios -qq
    TESTINFRA OK - 3 passed, 0 failed, 0 skipped in 0.14 seconds
    ...

.. _Pytest: http://pytest.org
.. _pytest-xdist: http://pytest.org/latest/xdist.html
