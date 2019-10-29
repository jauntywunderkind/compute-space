# spaces and flows

> Notes on representing information & processes in virtual space; a collection of computing cosmogenies.

# field survey

## DOM

element tree. events bubble from root up the tree then down.

## node-red

Flow based programming system

**[Components](https://nodered.org/docs/user-guide/concepts#node)** are JS functions that call the node-red api to send/receive/reply. At most one input port (?) and multiple output ports.

**Flows** are diagrams of wired componenets.
**[Context](https://nodered.org/docs/user-guide/concepts#context)**
**[Configuration Node](https://nodered.org/docs/user-guide/concepts#config-node)** 

## noflo

Flow-based programming system

[`getComponents()` export](https://noflojs.org/documentation/components/#component-api) is used to define noflo Components. Components define:

* description/icon
* inPorts/outPorts **[ports](https://noflojs.org/api/Ports/) extend EventEmitter,** with a datatype
* process
** input with hasData/getData/hasStream
** output with send/done

[Information Packet/IP](https://noflojs.org/api/IP/) is transmitted through. A stream is designated via an openBracket & closeBracket packet. Cloneable is an option. Schema, scope, datatype, owner, cloneable, port-index metadata.

## node-machine

A userland abstraction for processes:

* friendlyName/description/extendedDescription/moreInfoUrl/sideEffects (string)/sync
* inputs object
** friendlyName/description/extendedDescription/moreInfoUrl/sideEffects again
** required/example/whereToGet
* exits
** name
** outputFriendlyName/outputDescription/description/moreInfoUrl/extendedDescription
* fn(inputs, exits) the thing itself

## mozilla WoT capabilities

IoT service with basic ReST interface

Defines a `https://iot.mozilla.org/schemas/` JSON-LD context. Capabilities (MotionSensor), Properties (OnOffProperty), Actions (ToggleAction), events (AlarmEvent).

## OpenServiceBroker

interface between platforms & service brokers. service broker advertises catalog of services & plans.

## Wayland

Display server, hosts a number of uniquely identified objects talked to over Wayland protocol. [Object types](https://wayland.freedesktop.org/docs/html/ch04.html):

* wl_display
* wl_registry - the registry singleton
* wl_callback - callback object
* wl_compositor - compositor singleton
* wl_shm_pool - shared memory pool
* wl_shm
* wl_buffer - content for a wl_surface
* wl_data_offer - offer to transfer data
* wl_data_source - offer to transfer data
* wl_data_device - data transfer device
* wl_data_device_manager - data transfer interface
* wl_shell - replaced by xdg_shell
* wl_shell_surface - desktop style metadata interface
* wl_surface - an onscreen interface
* wl_seat - group of input devices
* wl_pointer - pointer input device
* wl_keyboard - keyboard input device
* wl_touch - touchscreen input device
* wl_output - compositor output region
* wl_region
* wl_subcompositor - subsurface compositing
* wl_surface - subsurface interface to a wl_surface

## SOLID

* WebID
* JSON-LD

## OpenAPI

Define apis.

Uses JSON-Schema for schemas, JSON Reference for Reference object.

object types:

* info
* contact
* license
* server - url, desc, vars
* server variable - enum array, default
* components - schemas, responses, parameters, examples, requestBodies, headers, securitySchemes, links, callbacks
* paths
* path item - http verb "operation", servers, parameters
* operation
* external docs
* parameter
* request body
* media type
* encoding
* responses
* response
* callback
* Example
* link
* header
* tag
* reference
* schema - json schema
* discriminator
* xml
* security scheme
* oauth flows
* oauth flow
* security requirements

## LwM2M

Lightweight Machine-to-Machine is a COAP protocol for rpc &c. Has a big **[registry](https://github.com/OpenMobileAlliance/lwm2m-registry)** of defined object types. Data Input objects and Log objects well represented. 

client objects bootstrap themselves with the server to come online.

Some interesting specs:
* [EventLog](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/test/LwM2M_EventLog-V1_0.xml)
* [SoftwareManagement](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/test/LWM2M_Software_Management-v1_0.xml) with update state/supportd objects/result, checkpoint, activate, package settings
* [Virtual Observe/Notify](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/test/LWM2M_VirtualObserveNotify-v1_0.xml) defines ObserveLinks which fire Reports
* [oA Basic Control](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/test/3387.xml): "ghost mode", executing object, resource injection

## UPnP

auto-confniguring network protocol for home net services.

* DHCP/AutoIP
* SSDP discovery
* description xml
* soap control
* GENA eventing (multicast 

## Second Screen protocol

## Systemd

Master control process for a Linux system, manages all programs running. Has a variety of abstractions.

Manager, the singleton representing systemd daemon at large:

* units: running things. list units, get units, start unit, start unit replace, stop unit, reload unit, restart unit, try restart unit, reload or restart unit, reload or try restart unit, kill unit, set unit properties, start transient unit, signal: new, removed
* unit files: list unit files, get unit file state, enable unit files, disable, reenable, link, preset, mask, unmask, signal changed
* job: single-shot executions. get job, cancel job, clear jobs. signal: new, removed
* snapshot: file system checkpoints? create, remove
* general: reload, reexecute, exit, reboot, poweroff, halt, kexec, switchroot, signal: startup finished, reloading.
* environment: set environment, unset environment, unset and set
* target: set default, get default
* props: version, features, tainted, firmware timestamp, loader timestamp, kernel timestamp, initrd timestamp, usrspace timestamp, finish timestmap, generators start/finish timestmap, units loads start/finish timestamp, security start/finish timestamp, loglevel (rw), nnames, njobs, ninstalled jobs, n failed jobs, progress, environment, confirm spawn, show status, unit path, default std out/stderr, runtime watchdog usec, virtualization, arch

Unit, a systemd resource of some kind
* lifecycle: start/stop/reload/restart/tryrestart/reload restart/ reload or try restart/kill/ reset failed/ set properties
* props: id, name, following, requires, requiresoverridable, requisite, requisiteoverridable, wants, bindsto, partof, required by, requiredbyoverrides...

Unit types:
* serivce: a resident daemon.
* socket: an endpoint which will be passed to the service, potentially starting the service on demand. 
* device: a system device
* mount: information about how file systems are mounted
* automount: a link to automatically create a mount on demand
* swap
* target: a grouping of units with a well known synchronization point
* path: a file path
* timer: a cron like regularly running thing
* slice: hierharchitically managed resources of a group of processes
* scope

## CloudEvents

[CloudEvents](https://github.com/cloudevents/spec/blob/master/spec.md) defines abstract data for events.

required:
* id
* source (uri)
* specversion
* type

optional:
* datacontentencoding
* datacontenttype
* dataschema
* subject 
* time
* "data"

## WSDL

[WSDL](https://www.w3.org/TR/2001/NOTE-wsdl-20010315#_document-s):

* type schemas, with elememnts
* messages, with typed parts. abstract.
* operation, with input/output/part. abstract.
* portType, holding operation
* binding, holding operations
* service, with port

## Corba


## UML

[UML](https://www.omg.org/spec/UML/2.2/About-UML/)

## jPDL

Processing language/format

[jBPM Process Definition Language](https://docs.jboss.org/jbpm/v3/userguide/jpdl.html) models jBPM, chiefly it's [Process Modelling](https://docs.jboss.org/jbpm/v3/userguide/processmodelling.html).

* Node: enter/execute/leave ExecutionContext, from/to Transition which "take" ExecutionContext to run
* State, Start/End state
* Task node
* process state
* super state
* fork/join/decision
* Event
* Transition
* Action
* Script
* Expression
* Variable
* Handler
* Timer/create/cancel
* Task: blocking, signalling, swim lane, priority, assignment, event, exception, timer, controller
* Swim lane
* Assignment: expression, actor-id, pooled-actors, class, config-type
* Controller: class, config-type, variable
* Sub-process
* Condition
* Exception Handler


## xpdl

[Process Definition Interface](http://www.xpdl.org/standards/xpdl-2.2/XPDL%202.2%20(2012-08-30).pdf)

[XPDL & BPMN](https://www.omg.org/bpmn/Documents/XPDL_BPMN.pdf) examples

process: data association, dataobject, data-field, type-decl, data-store
data association
activity: application/participant performer, lane
task-tool/blockactivity/route-gateway/subflow/event
pool: holds swimlanes, events occur within
application/participant/artifact
message/message-flow
aassociation: associate info/artifacts with flow-objects
artifact: data-object/group/annotation
resource-repo
data-field

## BPAF

[Business Process Analytics Format](http://www.wfmc.org/standards/bpaf)

* open: ready/not-running (ready/assigned/reserved)/in-progress, suspended flag
* closed: cancelled (error/exited/obsolete, aborted/terminated)/completed (sucess/failed)

General info:
* EventID
* Timestamp
* ServerID

Process Context:
* ProcessDefinitionID
* ProcessInstanceID
* ProcessName

Activity Context:
* ActivityDefinitionID
* ActivityInstanceID
* ActivityName

EventDetails sequence:
* CurrentState
* PreviousState
* DataElement

## BM*

### BPMN

### BPDM

### BMM

[Business Motivation Model 1.0](https://www.omg.org/spec/BMM/1.0/About-BMM/)

* End: categories, vision, desired, goal, objective, facts
* Mean: category, mission, course of action, strategy, tactic, directive, rule enforcement level, directives/regulation, buisness policy, facts
* Course of Action
* Directive
* Influences: categories, org, directive, assessmenet, potential impact
* Assessments
* External model elements
* OU
* Business Process
* Business Rule
* Association between concepts

## OASIS

https://www.oasis-open.org/standards

* [Content Managmeent Interoperability Service (CMIS)](http://docs.oasis-open.org/cmis/CMIS/v1.1/os/CMIS-v1.1-os.html)
* [Directory Services Markup Language (DSML) 2](http://www.oasis-open.org/committees/dsml/docs/DSMLv2.doc), [schema](http://www.oasis-open.org/committees/dsml/docs/DSMLv2.xsd)
* [ebXML Business Process Spec](http://docs.oasis-open.org/ebxml-bp/2.0.4/OS/spec/ebxmlbp-v2.0.4-Spec-os-en-html/ebxmlbp-v2.0.4-Spec-os-en.htm)
* SAML
* [Extensible Access Control Markup Language 3 (XACML)](http://docs.oasis-open.org/xacml/3.0/xacml-3.0-core-spec-os-en.html), [json](https://docs.oasis-open.org/xacml/xacml-json-http/v1.1/os/xacml-json-http-v1.1-os.html)
* [Key Managmeent Interoperability Protocol (KMIP)](http://docs.oasis-open.org/kmip/spec/v1.4/os/kmip-spec-v1.4-os.html)
* [MQTT](http://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html)
* [OData](http://docs.oasis-open.org/odata/odata/v4.0/os/part1-protocol/odata-v4.0-os-part1-protocol.doc)
* [Service Metadata Publishing (SMP)](http://docs.oasis-open.org/bdxr/bdx-smp/v1.0/os/bdx-smp-v1.0-os.html)
* Serviec Provisioning Markup Language (SPML)
* [Solution Deployment Descriptor](http://docs.oasis-open.org/sdd/v1.0/os/sdd-spec-v1.0-os.html)
* [Test Assertions Model](http://docs.oasis-open.org/tag/model/v1.0/os/testassertionsmodel-1.0-os.html)
* [Symptoms Automation Framework](http://docs.oasis-open.org/saf/saf/v1.0/os/saf-v1.0-os.html)
* [Topology and Orchestration Specificaiton for Cloud Applications (TOSCA)](http://docs.oasis-open.org/tosca/TOSCA/v1.0/os/TOSCA-v1.0-os.html). nodes, requirements/capabilities, templates, nodes, relationships, artifacts, policy
* [Universal Business Language 2.2](http://docs.oasis-open.org/ubl/os-UBL-2.2/UBL-2.2.html)
* [Unstructured Information Management Architecture (UIMA)](http://docs.oasis-open.org/uima/v1.0/os/uima-spec-os.html)
* [WS-Context](http://docs.oasis-open.org/ws-caf/ws-context/v1.0/OS/wsctx.html)
* [WS Distribution Management](http://docs.oasis-open.org/wsdm/wsdm-muws1-1.1-spec-os-01.htm)
* [WS-Discovery](http://docs.oasis-open.org/ws-dd/discovery/1.1/os/wsdd-discovery-1.1-spec-os.html)
* [WS-Federation](http://docs.oasis-open.org/wsfed/federation/v1.2/os/ws-federation-1.2-spec-os.html)
* [WS-notification](http://docs.oasis-open.org/wsn/wsn-ws_base_notification-1.3-spec-os.htm), [ws-brokered-notification](http://docs.oasis-open.org/wsn/wsn-ws_brokered_notification-1.3-spec-os.htm), [ws-topics](http://docs.oasis-open.org/wsn/wsn-ws_topics-1.3-spec-os.htm)
* [ws-reliable](http://docs.oasis-open.org/ws-rx/wsrm/200702/wsrm-1.2-spec-os.html)
* [ws-service-resource-framework (WSRF)](http://docs.oasis-open.org/ws-rx/wsrm/200702/wsrm-1.2-spec-os.html): [ws-resource](http://docs.oasis-open.org/wsrf/wsrf-ws_resource-1.2-spec-os.pdf), [ws-resource-properties](http://docs.oasis-open.org/wsrf/wsrf-ws_resource_properties-1.2-spec-os.pdf), [ws-resource-lifetime](http://docs.oasis-open.org/wsrf/wsrf-ws_resource_lifetime-1.2-spec-os.pdf), [ws-service-group](http://docs.oasis-open.org/wsrf/wsrf-ws_service_group-1.2-spec-os.pdf), [ws-base-faults](http://docs.oasis-open.org/wsrf/wsrf-ws_base_faults-1.2-spec-os.pdf)
* [ws-remote-portlet](http://docs.oasis-open.org/wsrp/v2/wsrp-2.0-spec-os-01.html)
* [ws-transaction](http://docs.oasis-open.org/ws-tx/wstx-wscoor-1.1-spec-errata-os/wstx-wscoor-1.1-spec-errata-os.html), [ws-atomic-transaction](http://docs.oasis-open.org/ws-tx/wstx-wsat-1.1-spec-errata-os/wstx-wsat-1.1-spec-errata-os.html), [ws-business-activity](http://docs.oasis-open.org/ws-tx/wstx-wsba-1.1-spec-errata-os/wstx-wsba-1.1-spec-errata-os.html)
* [ws-security-policy](http://docs.oasis-open.org/ws-sx/ws-securitypolicy/v1.2/errata01/os/ws-securitypolicy-1.2-errata01-os.html)
* [ws-trust](http://docs.oasis-open.org/ws-sx/ws-trust/v1.4/errata01/os/ws-trust-1.4-errata01-os.html)
* [xml interchange language for system dynamics (XMILE)](http://docs.oasis-open.org/xmile/xmile/v1.0/os/xmile-v1.0-os.html)

committee:
* [ws-Basic Profile](http://docs.oasis-open.org/ws-brsp/BasicProfile/v1.2/cs01/BasicProfile-v1.2-cs01.html)
* [classification of everyday living (coel)](http://docs.oasis-open.org/coel/COEL/v1.0/cs01/COEL-v1.0-cs01.html) and [2](http://docs.oasis-open.org/coel/COEL/v1.0/cs02/COEL-v1.0-cs02.html)
* [Cloud Applicaiton Managmeent For Platforms (CAMP)](http://docs.oasis-open.org/camp/camp-spec/v1.2/cs01/camp-spec-v1.2-cs01.html)
* [digital Signature Service Core (DSS-X)](https://docs.oasis-open.org/dss-x/dss-core/v2.0/cs01/dss-core-v2.0-cs01.html), [metadata](https://docs.oasis-open.org/dss-x/dss-md/v1.0/cs01/dss-md-v1.0-cs01.html)
* [Identity Provider Discovery Service Protocol & Profile](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-idp-discovery-cs-01.html)
* [OSLC](http://docs.oasis-open.org/oslc-core/oslc-core/v3.0/cs01/part1-overview/oslc-core-v3.0-cs01-part1-overview.html)

Interesting random models:
* [Election Markup Language 5.0 (EML)](http://docs.oasis-open.org/election/eml/v5.0/os/EML-Process-Data-Requirements-v5.0.htmlhttp://docs.oasis-open.org/election/eml/v5.0/os/EML-Process-Data-Requirements-v5.0.html)
* [Electronic Court Filing](http://docs.oasis-open.org/legalxml-courtfiling/specs/ecf/v4.01/ecf-v4.01-spec/os/ecf-v4.01-spec-os.html)
* [Emergency Data Exchange](http://docs.oasis-open.org/emergency/edxl-de/v1.0/EDXL-DE_Spec_v1.0.pdf), [dist element](http://docs.oasis-open.org/emergency/edxl-de/v2.0/cs02/edxl-de-v2.0-cs02.html), [sitrep](http://docs.oasis-open.org/emergency/edxl-sitrep/v1.0/cs02/edxl-sitrep-v1.0-cs02.html)
* [Energy Interoperation](http://docs.oasis-open.org/emergency/edxl-de/v1.0/EDXL-DE_Spec_v1.0.pdf) price, reliability, emergency, bids, load
* [Energy Market Information Exchange](http://docs.oasis-open.org/emix/emix/v1.0/emix-v1.0.html)
* [Field Force Managmeent Integration Interface](http://docs.oasis-open.org/ffm/FFMII-SPEC/v1.0/cs01/FFMII-SPEC-v1.0-cs01.html)

### BPEL

"Process orchestration". [Primer](https://www.oasis-open.org/committees/download.php/23964/wsbpel-v2.0-primer.htm)

[WSBPEL](http://docs.oasis-open.org/wsbpel/2.0/OS/wsbpel-v2.0-OS.html)


Verbs:
* invoke
* receive -- sources, correlation
* reply
* assign (to a variable)
* throw
* wait
* terminate
* compensate
* validate
* empty

Things:
* partnerLink thing being interacted with, has roles, portType.
* Variable
* fault handler
* correlation

Control Flow:
* Sequence (sequential)
* Flow (parallel activities)
* Switch (branch)
* While (loop), repeatUntil, forEach
* Pick

### XRD

[Extensible Resource Descriptor](http://docs.oasis-open.org/xri/xrd/v1.0/os/xrd-1.0-os.html) and [schema](http://docs.oasis-open.org/xri/xrd/v1.0/os/xrd-1.0-os.xsd)

* xml:id
* Expires
* Subject
* Alias
* Property
* Link
* ds:Signature
* Title

### UDDI 3.0

[Universal Description Discovery and Integration](http://www.oasis-open.org/committees/uddi-spec/doc/spec/v3/uddi-v3.0.2-20041019.htm) and [schema](http://lists.oasis-open.org/archives/tc-announce/200501/msg00000.html).

## BPSS

## UBL 2.0

## Petri-Nets

## Workflow Nets

## YAWL Eindhoven

## Event Driven Process Chain

[EPC cheat sheet](https://www.ariscommunity.com/system/files/EPC-Cheat-Sheet_Final_2019.pdf)

Event-driven process chain: model of business process
Value-add chain diagram: detail procedural level

Event - state that controls or influences progression of a process. trigger functions, are result of functions
Function - task or activity performed to deliver outputs / support objective

Connectors: split/join. xor/and/or
Linking/hierarchy:
* process interfaces: link EPCs horizontally
* low level EPCs: vertical link

org: ou, position, role, group
raci/rasci connections:
* responsible -> carries out
* accountable -> decides on
* supportive -> contributes to
* consulted -> has consulting role
* informed -> must be informed about

Data & risk:
* information carrier: stores knowledge/data
* cluster: collection of entity types representing business objects
* kpi: degree of goal acomplished
* risk: possible danger or hazard
* business policy: directive, to guide/govern
* requirement: documented need

Enterprise architecture:
* application system type: the software system to support execution of a function
* application system: represent a concrete identifiable applicaiton system within a company
* software roboto is app system type that carries out function autonomously (rpa)
* attended software robot: software robot (RPA) that requires intervention
* iot object: what it says


## OpenTelemetry

## OpenMetrics

## Open Application Model

## Jini/ApacheRiver/JavaSpaces

[Gigaspaces' Intro to Jini docs](https://docs.gigaspaces.com/xap/12.2/overview/about-jini.html)

Jini defines:

* Lookup service - registry system
* Discovery & join
* Entry interface. Core construct to enable three operations:
** store
** match
** fetch
* Leasing
* Remote Events
** registrant registers listener with generator
** generator returns registration for registrant/listener
** registrant returns registration to the listener
** generator fires event to listener
* Transaction Processing Service


## Service Modeling Language

Applications as instances of models, 

## wf-net

## SORCER

> Service ORiented Computing EnviRonment

> Everything anywhere/anytime (AWAT) as a service for you (EaaaaSY)


[sorcer](http://sorcersoft.org/project/site/) site, [papers](https://github.com/pfirmstone/SORCER/tree/master/docs/papers)

> A service mogram represents a service model that is executed by a dynamic federation of services. In other words a mogram exerts the collaborating service providers in a service federation created at runtime as specified by the mogram. Mograms are written in the Service Modeling Language (SML) that consists of two parts: Context Modeling Language (CML) and Exertion-Oriented Language (EOL). The former is used to specify data models (data contexts) for exertions and collections of interrelated functional compositions - context models. While CML is used for declarative service-oriented programming, EOL is focused on object-oriented composites of services - exertions. A model is a declarative representation of something, especially a system, phenomenon, or service that accounts for its properties and is used to study its characteristics expressed in terms of service variables associated with functional compositions.
- [Context modeling language](http://sorcersoft.org/project/site/context-models.html)


* context
** aggregates multipled named "entries" aka variables
** subcontexts
* entry
* name/value pair
** can be tagged input/output
** can be referential 
** optionally positional
* model
** again an aggregation of entries
** itself can be value()'d / run
** return can be a context
** "active relationships between entries that can implement Evaluation interface"
** "in contrast to data contexts, an ent-model entry is evaluated and then the value of the entry of the Evaluation type is getValue()"
** itself is evaluated
* par-model?
* srv-model
** from running exert() on a mogram
** mogram is result of a service 
** exertions, context, data contexts are all mograms
** therefore all can provide services for srv-model

> Exertion-oriented Language (EOL) ... is a metamodel in the form of collection of concepts that are the vocabulary with which you are talking about creating and requesting services.

## workflow-nets

a petri-net

## causal-nets

elaboration on workflow nets that show 

## xstate & scxml

state-charts

## workflow management coalition (WfMC)

[workflow management coalition model](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.198.5206&rep=rep1&type=pdf) doc. has pre

defines pieces of a model, and talks to the pieces, and some times has specs for these interfaces. "workflow api" (wapi)

workflow reference model:
* workflow enactment service
	* this is the core "executor" which has the various interfaces
	> The  workflow  enactment  service  provides  the  run-time  environment  in  which  process  instantiationand   activation   occurs,   utilising   one   or   more   workflow   management   engines,   responsible   forinterpreting  and  activating  part,  or  all,  of  the  process  definition  and  interacting  with  the  externalresources necessary to process the various activities.
* process definition - see: WPLD
** workflow type definition
** activity
** workflow relevant data
** invoked application
** transition conditions
** role
* workflow client functions
* invoked application functions
* workflow interoperability
* systems administration
	* user management
	* role management
	* audit management
	* resource control
	* process supervisory functions


## mxml 

from [a meta model for process mining data](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.79.3760&rep=rep1&type=pdf)

> Modern process-aware information systems store detailed in-formation about processes as they are being executed. This kind of infor-mation can be used for very different purposes. The termprocess miningrefers to the techniques and tools to extract knowledge (e.g., in the formof models) from this. 

> We give the requirements for the datathat should be available, both informally and formally. Furthermore, weback our meta model up with an XML format called MXML

* cites WFMC's model & particularly the systems admin "interface 5"
* thesis also begat the process mining tool [ProM](http://www.promtools.org/doku.php?id=tutorial:start)

### model

WorkflowLog has Processes
Process has ProcessInstances
ProcessInstance composes AuditTrailEntry
audit-trail-entry composes WorkflowModelElements
process aggregates WorkflowModelElements

## xes

[Extensible event system](https://xes-standard.org/xesstandarddefinition)

> The XES standard defines a grammar for a tag-based language whose aim is to provide designers of information systems with a unified and extensible methodology for capturing systems behaviors by means of event logs and event streams is defined in the XES standard.

It's own xml-schema system for defining log schemas, with a variety of extensions. also has a processing model.

log has traces
traces have event
events aggregate a set of attributes. attributes on log are "global" attributes to events.
attributes can either be simple things (string, date, boolean, id), or lists/containers
nested attributes
classifiers fire "activity" 

calls MXML it's precedessor

Also defines extensions for various tasks:
* artifact lifecycle
* concept
* [cost](http://www.xes-standard.org/cost.xesext)
** total
** drivers
** currency
** amount
** type
* [identity](http://www.xes-standard.org/identity.xesext)
** id
* [lifecycle](http://www.xes-standard.org/lifecycle.xesext)
** model
** transition
** state
* [micro](http://www.xes-standard.org/micro.xesext)
** level
** parentId
** length
* organizational
* semantic
* software communication
* [software event](http://www.xes-standard.org/swevent.xesext)
	* exhaustive caller/callee field
	* return value 
	* app
		* name
		* tier
		* node
		* session
	* ex thrown/caught
	* params / param value 
	* value-type
* software telemetry
* time

## OMG Workflow Facility


## XPLD

## Workflow Process Definition Language (WPDL)

## Rrocess Interchange Framework

## Process Specification Langauge - PSL

NIST

## w3c distributed-tracing

[distributed tracing wg](https://www.w3.org/2018/distributed-tracing/) maintains [trace context](https://www.w3.org/TR/trace-context) and a [trace context registry](https://www.w3.org/TR/trace-context-protocols-registry/) spec. 

From an [explainer](https://medium.com/@AloisReitbauer/trace-context-and-the-road-toward-trace-tool-interoperability-d4d56932369c) article's section **Context propagation: Core building block of distributed tracing**,

> In order to make distributed tracing work, we need a way to pass context information from one transaction to the next. Such transaction context, or simply “context” for short, is represented by one or more unique identifiers that enable linkage between the client-side and the server-side of each transaction.

## Yet Another Workflow Language (YAWL)

[yawl](http://www.yawlfoundation.org/) maintains a [book](http://www.yawlfoundation.org/yawlbook/downloads.html), and is an integrated IDE.

## Workflow Patterns

[workflow patterns](http://workflowpatterns.com/) has patterns & evaluations of workflow systems.

### [patterns categories](http://workflowpatterns.com/patterns/)
* data
* resource
* control-flow
* exception
* presentation
* event-log imperfections

### [evalutions](http://workflowpatterns.com/evaluations/standard/)
* bpel
* bpmn
* xpdl
* uml
* epc
