# alyx-registrator

* Gateway server in a lab that (1) runs the Globus server, (2) has access to all lab data drives within the local network, (3) controls all local recording computers, (4) registers files on the Alyx database via the Alyx REST API, (5) serves a lightweight [flask](http://flask.pocoo.org/) REST API that the recording computers can use.
* alyx-registrator is Python module that runs on the Gateway server and that implements (4) and (5). It also talks to Globus via the [Globus SDK for Python](http://globus-sdk-python.readthedocs.io/en/latest/)
