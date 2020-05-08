# Open Money development roadmap

#### Clarification of terms:

The term _open money_ (all lower case) refers to the concept of user-created 
"monies". This is described in a number of writings, many of which can be 
found at https://docs.google.com/document/d/1gVuolh6TV7fH5tNTyZMCDGTsFFJeOWCP-X0Diwnj7MA/edit

In this sense, _open money_ is a particular case of _open metrics_.

The name _Open Money_ (capitalized) refers to specific software used to 
implement _open money_ or, more generally, _open metrics_.

## The Open Money (OM) suite

The current implementation of _Open Money_ was created by Dominique Legault and
comprises (so far) four main components:

#### openmoney-api (OM API)

https://github.com/jethro-swan/openmoney-api (forked from https://github.com/deefactorial/openmoney-api)

This provides a REST API to a Couchbase DB in which recursively nested 
namespaces enclose _stewards_, _currencies_ and _accounts_. This is intended as
a component with an expanding collection of tools.

All users are responsible for the management of their own records so every user
is termed a _steward_.

The _stewards_ are self-registering and each can create _currencies_, _accounts_
and _namespaces_.

A _currency_ is any value representable by a scalar. Therefore the term _open
money_ is unnecessarily restrictive. It is maintained partly for historical 
reasons, but also because _monies_ of various type are important cases of 
_currency_ in this sense.

#### openmoney-network

https://github.com/jethro-swan/openmoney-network (forked from https://github.com/deefactorial/openmoney-network)

This is a small client designed to access the OM API. Its display is sufficiently
compact to make it usable on a smartphone or in an iFrame.

This is essentially a proof-of-concept prototype.

#### openmoney-gift-api

https://github.com/jethro-swan/openmoney-gift-api (forked from https://github.com/deefactorial/openmoney-gift-api)

An alternative API for the _merchants_' covestment system (OM Gift). This shares
some of the data from the OM API's Couchbase DB but also using an additional
key-value DB. 

#### openmoney-gift (OM gift)

https://github.com/jethro-swan/openmoney-gift (forked from https://github.com/deefactorial/openmoney-gift)

The user interface for the _merchants_' covestment system. This version supports
the design and printing of paper vouchers identifying the _merchant_, target 
_account_ and payment to be recorded via a QR code.

Any smartphone can be used to scan the QR code, redirecting the payer to the _OM
Gift_ instance.

### The current state of development

The _OM suite_ described above is very much a work in progress, and is intended
primarily as a proof-of-concept demonstration system. This version has been
written for use only on Ubuntu (and possibly Debian) and runs Couchbase in a 
Docker container.

Although Couchbase scales well and can replicate very quickly if clustered, the
user-centred design of the _OM suite_ would probably make Holochain a more 
natural fit in due course.

  
### Short-term development

#### openmoney-api

- extend and complete the test suite

- API sequence diagram

- document code

- resolve lost password bug

- update the code

- isolate Couchbase calls from API in preparation for replacement of back end
  with Holochain-based storage

#### openmoney-network

- extend and complete the test suite

- document code

- resolve lost password bug

- extend capabilities

- update the code

#### openmoney-gift-api

- extend and complete the test suite

- update the code

#### openmoney-gift

- extend and complete the test suite

- update the code

### Medium-term development

- develop user feedback systems

- complete Swagger-generated client libraries (Python initially)

- develop a richer collection of clients

- re-implement storage on Holochain (using Swagger generated Rust client)

- design and develop simulation/modelling/visualization suite

### Longer-term development

?

### Alternative implementation

Because the recursive namespace structure naturally mirrors the structure of a 
Unix-like filesystem, that is used as the basis of an alternative implementation
currently under development as a Python module (RNSSA). The purpose of that is 
to provide a quicker route to development of
- a richer collection of OM clients 
- a simulation and visualization suite
- support for compound/vector currencies (information-retentive)
- modelling, forecasting and algedonic tools 

Another objective here is to provide an API consistent with, but a superset of, that of the _Open Money_ suite described above. This will simplify development of portable and re-usable components.

The recursively-nested, holonic structure of the OM suite reflects the 
structure of the Viable System Model, so a suite of tools will be developed over
time to support its application.
