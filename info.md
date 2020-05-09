# Managing Software supply chain
On an Enterprise scale, a software product involves millions of line of code. With majority of them being added from Opensource. Does all these Free software really comes with zero cost? May be no money, but there is cost of security vulnerabilities, license infringments. Without gating or timely checks these may cause Data/privacy voilations and financial penalities.

Software delivery begins from design, writing code to its distribution, deployment and its eventual usage. At each stage there should be sufficient data available for developing confidence and trust in final delivery. This is achieved have methodologies like code quality analysis, vulnerability checks, attack vector recognition and reducing exploit surface area.

Software supply chain management should be a rigours process which should have observaibility should be built around it. 
How do we add trust
Have centralized component and avoid blockage at any step


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

## Grafeas
Open artifact metadata standard. Audit and govern software suppoly chain. Knowledge base for onpremises and cloud clusters. Api with plyggable strogare backends.

- Universal metadata store
- Notes: high level descripton of types of metdata
  - e.g. CVE as vulnerability note
- Occurrences: instance of note in an artifact
  - e.g. CVE presence in an image
- Integrate third party providers/consumers
- Providers: e.g. Scanners/Analysers :
  - Stores Notes and its occr
- Consumers: Read and Checks against the occurances

Resource URL: identifier for artifact in occurence
Kind: specific schemas for providers

Support:
- Helm chart for grafeas and plyished image
- Standalone Grafeas server with pestgres strogae backend
- Basic support for go client library
