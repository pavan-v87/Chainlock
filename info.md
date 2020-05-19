# Software supply chain
Software delivery begins from design, writing code to its distribution, deployment and its eventual usage. Like the traditional supply chain, software supply chain is a system of organization and network connecting people, process, information and resources involved in delivering product to clients or customers.

### Problems at Enterprise scale
On an Enterprise scale, a software product involves millions of line of code. With majority of them being borrowed from Opensource. Does all these Free software really comes with zero cost? May be no money, but there is cost of  vulnerabilities, insecure data, privacy voilations, license infringments etc..

### Managing supply chain
At each stage of supply chain there should be sufficient data available for developing confidence and trust in final delivery. This is achieved by code quality analysis, vulnerability checks, reducing exploit surface area etc. Also We should have observaibility built around this using different tools.

### Strong governace with Grafeas
Grafeas is an open source initiative to define a uniform way for auditing and governing the modern software supply chain. Its main purpose is to maintain central, structured knowledge-base of the critical metadata. It provides a centralized mechanism to enforce policies across software delivery chain.
Following are the features and design points:
- Metadata is stored with components unique id
- Open and centralized standard for metadata
- Easy to add new metadata producers and consumers
- Structured metadata schemas available for common metadata types (e.g., vulnerability, build, attestation and package index metadata)
- Strong control access for multiple metadata producers and consumers
- API's to store, query, and retrieve comprehensive metadata on software components of all kinds.

### Defragmenting and centralizing metadata 
At each stage of the software supply chain (code, build, test, deploy and operate), different tools generate metadata about various software components. Examples include the identity of the developer, when the code was checked in and built, what vulnerabilities were detected, what tests were passed or failed, and so on. This metadata is then captured by Grafeas.
Below image demonstrates the use case:


- Notes: high level descripton of types of metdata
  - e.g. CVE as vulnerability note
  
- Occurrences: instance of note in an artifact
  - e.g. CVE presence in an image
- Integrate third party providers/consumers
- Providers: e.g. Scanners/Analysers :
  - Stores Notes and its occr
- Consumers: Read and Checks against the occurances
- pluggable strogare backends.

Resource URL: identifier for artifact in occurence
Kind: specific schemas for providers

Support:
- Helm chart for grafeas and plyished image
- Standalone Grafeas server with pestgres strogae backend
- Basic support for go client library

## Kritis
Kritis is admission controller for kubernetes. It runs checks against set of policies. Based on the voilations, deployment is admited or denied. 


- When pod is to be installed, Kritis recieves the webhook
- It checks if vulnerability scan is done (waits till its done)
- when scan completed, metadata is available from Grafeas api
- REtrieve vculernabilit data for images
- grafeas also stores and retieve attestations

### CRDS:
- Extension of k8s API
- containes whitelisted images and CVE


