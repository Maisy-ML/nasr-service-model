---
stand_alone: true
ipr: trust200902
cat: info # Check
submissiontype: IETF
area: Security
wg: Internet Engineering Task Force

docname: draft-chen-nasr-service-model-00

title: the service model of NASR 
abbrev: serviceModel-nasr
lang: en
kw:
  - Internet-Draft
  - keyword2
# date: 2024-11-20 -- date is filled in automatically by xml2rfc if not given
author:
- name: Meiling Chen
  org: China Mobile
  city: BeiJing
  country: China
  email: chenmeiling@chinamobile.com
- name: Li Su
  org: China Mobile
  city: BeiJing
  country: China
  email: suli@chinamobile.com



--- abstract

This document describes the service model of Network Attestation for Secure Routing(NASR). Operators offer security capabilities that can be added to the connectivity service, and clients make choices.

--- middle

# Introduction

The NASR goal is to allow clients to choose desired security attributes of his received network service, then achieve dependable forwarding by routing on top of only devices that satisfies certain trust requirements, finally prove to the clients that certain packets or flows traversed a network path that has certain trust or security properties.

The service model help users to describe their desired security attributes, after receiving the service model, the network service provider converts the requirements of service model into executable configurations, the network completes the preparation work before network transmission according to the configurations. Until the completion of the network service, the ISP feedback the service results to the user, which will be used as evidence of service satisfaction.

The security services here refers to the resources that can be provided during connection, it should be noted that the security services at the application layer is out of scope.

# Abbreviations

The following abbreviations are used in this document.

NVF: Network Functions Virtualization.

IDS: Intrusion Detection System.

IPS: Intrusion Prevention System.

PoT: Proof of Transit.

SLA: Service Level Expectation.

# NASR service model

## Service model from user

### Destination

Destination: Used to indicate the destination of the visit, such as IP,FQDN or URL, it's mandatory attribute.  

Path: selected router ID list or IP list on Path, it's optional.

Data sevice type: used to indicate the type of data, such as games or videos, it's mandatory attribute.

Geographic: used to indicate users' requirements for geographic location or restrictions, it's optional;

### Security environment

NASR is to route data on top of trusted devices, trusted operating environments, trusted links and trusted services only, therefore, users can have security requirements for each node in the path, including software and hardware. 

The security environment here refers to the security of logical nodes.

Node Type: NFV or Hardware.

Path: Authentication, Encryption.<RFC 8049>

Connection: Maximal occupancy level, Isolation, Diversity.<RFC 9543>

Security service type: Access control, Integrity Protection, firewall,IDS/IPS,attack-mitigation(anti-DDos) and so on. Each type of security service requires two SLE parameters, processing latency and performance of security capabilities.

Defense perception: self defense perception, responsible for dynamically discovering security issues caused by self defects and external attacks.


## Service result model to user

Path attestation result: after generating a path that meets the specific forwarding requirements of the user, it is used to record the initial path attestation result as a baseline for future verification, contains at least four fields: Identity, initial attestation result, verification reference and auxillary information.
						
Forwarding Path validation result: formed during the actual forwarding process both in-situ and out-of-band modes, it will be verified with path attestation result,  contains at least two fields: Identity, PoTs.

PoT tag: used to flag the currently used PoT algorithm.

# IANA Considerations {#IANA}

This memo includes no request to IANA. 


# Security Considerations {#Security}

There is a risk of tampering for Path attestation result and Forwarding Path validation result, Especially in the scenario of third-party auditing, it is required that both data transmission and storage cannot be tampered with.


--- back



