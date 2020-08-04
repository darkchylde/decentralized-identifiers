# Decentralized identifiers

A DID is functionally a URN (a persistent name for a resource that will never change, unlike URLs which changes based on the location of the resource it is pointing to) that in many cases can be resolved into one or more URLs. These URLs can then be used to interact with the resource through the web.

4 core properties of a DID

1. A permanent(persistent) identifier - It never changes
2. A resolvable identifier - Can resolved to metadata
3. A cryptographically-verifiable identifier - Prove the control(or ownership) using cryptography
4. A decentralized identifier - No centralized registration authority is required

* Verifiable
* Decentralized
* Can represent anything (decided by the controller)
* Controller can prove ownership without any other party involved
* DIDs are URLs that associate a DID subject with a DID document


## DID document

* Cryptographic material, service endpoints, verification methods
* Service endpoints enable trusted interactions associated with a subject
* Can contain semantics about a DID subject or may be the document itself (a data model)

* Anyone can generate DIDs for their usecase
* Specification for a type of DID is called DID method

## DID structure

* A simple string containing 3 parts
	a. URL scheme identifier (did)
	b. Method identifier (for e.g. sov, eth, jlinc)
	c. Method specific identifier ( So far, I understand this as a random string, maybe UUID)
* This string resolved to a DID document. This is similar to website url resolving to the website content

## What is being achieved with DID ?

* Decentralization
	1. Eliminate single point of failure
* Control
	1. You can control your own DIDs (no external parties required for e.g. On contrary for a www domain name it is controlled by domain name registrar)
* Privacy
	1. Data minimisation 
	2. Control the amount of information disclosed
* Security
	1. As defined in DID document (Didn't really understand how this works so far !)
* Proof based
	1. Controllers will be able to provide proof to other parties if required
* Discoverability
	1. DID of one entity can lead you to DID of other entity (Maybe DID document will DID of other entity)
* Interoperatibility
	1. Should be capable of working with existing systems
* Portability
	1. A DID should be able to work with any system that support DIDs and DID methods
	2. for e.g. jlinc DID must be able to work with sovrin DID (Is this achieved already ?)
	3. Is portability achieved through resolvers ??
* Simplicity
* Extensibility

## DID architecture

![Architecture](https://w3c.github.io/did-core/diagrams/did_architecture_overview.svg)

Components

* DIDs and DID URLs
	
	* DID or decentralized identifier is a URI composed of three parts (scheme, method identifier, unique id)
	* DID URLs is DID + some features of standard URI for e.g. path, query, fragment
* DID subject (Entity represented by the DID)
* DID controllers (entity with capability to make changes to DID document)
* Verifiable data registries (Where the DIDs are recorded for e.g. distributed ledger)
* DID documents (meta data associated with a DID)
* DID methods - interact with DID and DID documents (CRUD operations)
* DID resolvers and DID resolution
	* Taking DID as input and outputting the DID document, this process is called DID resolution
* DID URL dereferencer and dereferencing (What is this ??)

## Terminology

* **authentication**

    Process by which an entity can prove it has a specific attribute or controls a specific secret using one or more verification methods.
    for e.g. Proving control of private key associated with the public key defined in DID document

* **decentralized identifier** (DID)

    Globally unique persistent identitier
    Does not require centralized registration authority because it is registered/generated cryptographically

* **decentralized identity management**

    ??

* **DID controller**

    Enttity capable to make changes to DID document.
    DID can have more than one controller
    Can be idenitified using **controller** property in DID document (optional)
    DID controller can also be the subject of the DID

* **DID delegate**

    An entity to whome a DID controller has granted permission to use verification method associated with a DID via a DID document. 
    for e.g. a parent allowing the child to authenticate using a DID
    (Interesting aspect of delegating. Need to explore this)

* **DID document**

    Set of data describing DID subject.
    It will contain information such as public key and pseudonymous biometrics, that DID subject or DID delegate can use to authenticate itself and prove its association with the DID.
    DID document can also contain other attributes or claims describing the subject

* **DID fragment**

    The section of DID URL that follows the first hash sign charaction
    for e.g. did:sov:12345678#keys-1 , here keys-1 is the fragment, it is similar to URI fragment syntax for e.g. wikipedia.com/india#capital

* **DID method**

    Definition of how DID scheme must be implemented to work with a specific verifiable data registry.
    A DID method is defined by DID method specification, which must specify the precise operations by which DIDs are created, resolved and deactivated and DID documents are written and updated.

* **DID path**

    The portion of DID URL that begins with and includes the forward slash (\) character ends with either a question mark (?) or a fragment hash sign (#) character (or the end of the DID URL). 
    It is similar to URI path. for e.g. https://wikipedia.org/documents/india/kerala.html , here /documents/india/kerala.html is the path

* **DID query**

    The portion of DID URL that follows and includes the first question mark character (?). It is similar to URI query. for e.g. www.google.com?search=india where query is ?search=india

* **DID resolution**

    The function that takes as its input a **DID** and set of input metadata and **returns a DID document**in a **conforming representation** plus additional metadata. 
    This function relies on **READ** operation of the applicable DID method.

* **DID resolver**

    Software/hardware that performs DID resolution i.e. taking DID as input and produces conforming DID document as output

* **DID scheme**

    Syntax of DID.
    Generic DID scheme begins with prefix **did:**
    Each DID method specification must define a specific DID scheme that works with that specific DID method.
    In a specific DID method scheme, the DID method name must follow the first colon and terminate with the second colon for e.g. did:sov:, did:jlinc:, did:igrant:

* **DID subject**





# Reference(s)

1. https://w3c.github.io/did-core/
2. https://identity.foundation/
3. https://github.com/decentralized-identity
4. https://sovrin.org/faq/what-is-self-sovereign-identity/
5. https://ssimeetup.org/decentralized-identifiers-dids-fundamentals-identitybook-info-drummond-reed-markus-sabadello-webinar-46/
