## Infrastructure  as Code

Infrastructure as Code enables DevOps teams to test applications in production-like environments early in the development cycle.

Infrastructure as Code (IaC) is the management of infrastructure (networks, virtual machines, load balancers, and connection topology) in a descriptive model, using the same versioning as DevOps team uses for source code.

Like the principle that the same source code generates the same binary, an IaC model generates the same environment every time it is applied. Few example assets types that should follow this principle are mentioned below:

-   Production-ready IaC for an angular frontend.
-   Single click setup for demo instances.
-   Infrastructure stack creation of the clustered and non-clustered environments.

#### Principles of IaC

##### **Systems Can Be Easily Reproduced**
It should be possible to effortlessly and reliably rebuild any element of an infrastructure. Effortlessly means that there is no need to make any significant decisions about how to rebuild the infrastructure. Decisions about which software and versions to install on a server, how to choose a hostname, and so on should be captured in the scripts and tooling that provision it.

##### **Systems Are Disposable**
Systems should be designed to assume that the infrastructure will always be changing. The ability to handle changes gracefully makes it easier to make improvements and fixes to running infrastructure. It also makes services more tolerant to failure.

##### **Systems Are Consistent**
Given two infrastructure elements providing a similar service—for example, two application servers in a cluster—the servers should be nearly identical. The system software and configuration should be the same, except for those bits of configuration that differentiate them, like their IP addresses.

##### **Processes Are Repeatable**
Building on the reproducible principle, any action you carry out on your infrastructure should be repeatable. This is an obvious benefit of using scripts and configuration management tools rather than making changes manually.


#### Best Practices

##### **Use Definition Files**
The cornerstone practice of infrastructure as code is the use of definition files. A definition specifies infrastructure elements and how they should be configured. The definition file is used as input for a tool that carries out the work to provision and/or configure instances of those elements.

The infrastructure element could be a server, a configuration item of a server, such as a user account, network configuration, such as a load balancer rule, or many other things. Different tools have different terms for this: for example, playbooks (Ansible), recipes (Chef), or manifests (Puppet). The term “configuration definition file” is used in this document as a generic term for these.

Definition files are managed as text files. They may use a standard format such as JSON, YAML, or XML. Or they may define their own domain-specific language (DSL)

##### **Self-Documented Systems and Processes**
With infrastructure as code, the steps to carry out a process are captured in the scripts, definition files, and tools that actually implement the process. Only a minimum of added documentation is needed to inform users of its use. The documentation that does exist should be kept close to the code it documents, to make sure it’s available when changes are required.

##### **Version All the Things**
The version control system (VCS) is a core part of infrastructure that is managed as code and should be used at all times. The VCS is the source of truth for the desired state of infrastructure. Changes to infrastructure are driven by changes committed to the VCS.

##### **Continuously Test Systems and Processes**
Effective automated testing is one of the most important practices that infrastructure teams can borrow from software development. Automated testing is a core practice of high-performing development teams. They implement tests along with their code and run them continuously, typically dozens of times a day as they make incremental changes to their code base.