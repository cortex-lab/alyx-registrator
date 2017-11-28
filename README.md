# alyx-registrator

* Gateway server in a lab that (1) runs the Globus server, (2) has access to all lab data drives within the local network, (3) controls all local recording computers, (4) registers files on the Alyx database via the Alyx REST API, (5) serves a lightweight [flask](http://flask.pocoo.org/) REST API that the recording computers can use.
* alyx-registrator is Python module that runs on the Gateway server and that implements (4) and (5). It also talks to Globus via the [Globus SDK for Python](http://globus-sdk-python.readthedocs.io/en/latest/)

## Workflow

* Press "start experiment" on the Gateway server
    * The Gateway server registers the experiment by making a REST API call to the Alyx database
    * The experiment starts, the recording computers start to write files on disk
* When the experiment stops:
    * The Gateway server signals the end of the experiment to Alyx via a REST API call?
    * The Gateway server lists all files in the experiment working directories
    * For every file:
        * the Gateway server registers it on Alyx via a REST API call
        * the Gateway server initiates a Globus data transfer from the experiment working directory to the central data repository
        * When a data transfer finishes, the Gateway server is notified by Globus (?) and notifies Alyx via a REST API call
