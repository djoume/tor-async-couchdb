#Samples
The samples below demonstrate how to use the capabilities
of ```tor-async-couchdb```.
The first sample ([basic sample](basic)) is very simple and uses only the fundamental
features of ```tor-async-couchdb```. Subsequent samples build on
[basic sample](basic) excercising increasingly more advanced features
of ```tor-async-couchdb```.

In terms of the structure of the samples.
Each of the samples is structured in the same way and follows
a [Data, context and interaction (DCI)](http://en.wikipedia.org/wiki/Data,_context_and_interaction)
style of paradigm.
	* model.py contains model classes (DCI's *data*)
	* async_action.py contains classes that implement async operations which operate on models (DCI's *interaction*)
	* service.py contains all Tornado request handlers and the service's mainline - request handlers
	  create instances of async actions to async'ly operate on models (DCI's *context*)

##[basic](basic)
This service implements a simple RESTful service that
demonstrates how the foundational features of ```tor-async-couchdb```
are intended to be used.

##[retry](retry)
This service implements a simple RESTful service that
builds on the [basic](basic) sample.
Specifically, this sample illustrates how
to implement on-write retry logic that works with CouchDB's
Multi-Version Concurrency Control (MVCC) approach to conflicts.

##[exponential backoff](exp_backoff)
This service implements a simple RESTful service that
builds on the [retry](retry) sample.
Specifically, this sample illustrates how
to refine [retry](retry)'s retry logic using
and an exponential backoff strategy.

##[multi-master](multi_master)
...

##[tampering](tampering)
...

##[hash and encrypt](hash_and_encrypt)
...

#Utilities

##[db_installer](db_installer)
[db_installer](db_installer) demonstrates how to use ```tor-async-couchdb```
to create a CouchDB database installer. The database created by
the installer is used for each of the ```tor-async-couchdb```
samples.

##[tests.py](tests.py)
Once you have spun up one of the sample services you can run
a sanity test suite against the service using a
[nose](https://nose.readthedocs.org/en/latest/) runnable
integration test suite in [tests.py](tests.py).
The test suite is hard-coded to talk to a service at
[http://127.0.0.1:8445](http://127.0.0.1:8445) so edit
the test if you are running the service at a different
endpoint.

```bash
>nosetests tests.py
...
----------------------------------------------------------------------
Ran 3 tests in 0.646s

OK
>
```

##[loadgen](loadgen)
A [locust](http://locust.io/) based utility which drives CRUD style
load through the sample services to demonstrate ```tor-async-couchdb```'s
conflict resolution logic.
