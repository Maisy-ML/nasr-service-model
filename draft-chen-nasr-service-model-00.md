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

This document describes the service model of Network Attestation for Secure foRwarding (NASR). It lists security capabilities and characteristics of connectivity services that operators can offer and clients can choose from.

--- middle

# Introduction

The NASR goal is to allow clients to choose desired security attributes of his received network service, achieving dependable forwarding by routing on top of only devices that satisfies certain security requirements. NASR then provides proof that packets or flows have traversed a network path with defined security properties.

The service model enables users to specify their security requirements. The network service provider translates these requirements into network configurations, which are then used to prepare the network for transmission. After delivering the service, the provider returns proof of compliance to the user.

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

Destination: Used to indicate the destination of the visit, such as IP.  

Path: selected router ID list or IP list on Path.

Sevice type: used to indicate the type of data, such as eMBB data, mMTC data or uRLLC data.

Geographic: used to indicate users' requirements for geographic location or restrictions, a customer may request certain geographic limits are applied to how the provider routes traffic for the network forwarding, due to policy reasons or security considerations, For example, some countries have regulations that explicitly prohibit data from leaving the country.

### Trusted Path Provision

ISPs can provide secure forwarding service by selecting a trusted path for users, including choosing trusted routers that can provide the security services required by the user;

The trusted path provision includes but is not limited to the following parameters.

Node Type: NFV or Hardware, this field is used to identify whether the node is of hardware type or virtualization software type, different node type have different security configurations.

Node Security Configuration: the node's basic security configuration baseline possessed by the node(such as router) itself, include security hardening, attack perception and so on. 

L2/L3 Security Feature: used to identify whether to enable authentication and encryption on L2 or L3. L2 authentication can based on the device's MAC address and encryption can use MACsec; L3 can provide end-to-end authentication and encryption, such as VPN. 

Connection Reliability Feature: Maximal occupancy level, Isolation, Diversity.<RFC 9543>. The maximal occupancy level specifies the number of flows to be admitted and optionally a maximum number of countable resource units (e.g., IP or MAC addresses). Isolation refers to the division of traffic , a customer may request that its traffic is isolated from the other network traffic supported by the same provider. Diversity allows connections based on different underlying network constructions.

Security Services Configuration: Security services that can be provided based on traffic, such as firewall,IDS/IPS,attack-mitigation(anti-DDos), access control, Integrity Protection. Each type of security service requires two SLE parameters, processing latency and performance of security capabilities.

## service model to user

When users are very proficient in security configuration and requirements, they can directly fill in a fixed format list, the operator can provide feedback on whether the requirements are met; Users may not be security experts, they will propose vague security requirements, and the ISP generates one or more fixed format lists for users to choose from, there is an additional interaction process with the user here.

## Service result model to user

Path attestation result: after generating a path that meets the specific forwarding requirements of the user, it is used to record the initial path attestation result as a baseline for future verification, contains at least four fields: Identity, initial attestation result, verification reference and auxillary information.
						
Forwarding Path validation result: formed during the actual forwarding process both in-situ and out-of-band modes, it will be verified with path attestation result,  contains at least two fields: Identity, PoTs.

# IANA Considerations {#IANA}

This memo includes no request to IANA. 


# Security Considerations {#Security}

There is a risk of tampering for Path attestation result and Forwarding Path validation result, Especially in the scenario of third-party auditing, it is required that both data transmission and storage cannot be tampered with.


--- back



