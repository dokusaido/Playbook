## Buzzwords

#### Continous Integration?
Continuous integration is the process of automating the build and testing of code every time a team member commits changes to version control.

#### Continuous Deployment
Continuous deployment is a software release process that uses automated testing to validate if changes to a codebase are correct and stable for immediate autonomous deployment to a production environment.

#### Continuous Delivery
Continuous delivery sits between and requires manual interaction between the processes of integration and deployment.

#### Shift Left on Security
Usually a Continuous Integration w pipeline is represented by several stages starting from left to right. Hopefully you already have security checks a some point. [[Shift Left on Security]] means to run these security checks as early as possible. Fail fast and do not waste time to pass other stages if you can detect earlier that you have to rework your code.

The shift-left philosophy of DevSecOps implies that problems should be identified as soon as possible in the lifecycle. The picture below maps the ability to identify security problems to different activities throughout the lifecycle.

Shifting left means that weaknesses in the code can be found before they become exploitable vulnerabilities. During design, identifying risks in the architecture can help avoid exposing weak code to attackers, or at least minimize the severity if a potential attack. By finding gaps between the project plans and the customer needs, the product can be built correctly from the start, reducing the need to later change the design to decrease risks. Truly shifting left doesn’t mean just running tests as soon as writing the code starts – it means considering security as part of the requirements and design thinking process.

#### DevOps Kaizen
[[DevOps Kaizen]] is a process which uses DevOps tools, technologies and methodologies to continuously improve the flow of work through the E2E value stream to achieve better customer outcomes.

#### Value Stream Mapping
[[Value Stream Mapping]] is the process of aligning the entire team around an agreed understanding of the steps, processes, timings and constraints in a Value Stream, thus helping the team to identify, agree and prioritize improvement steps.

#### Improvement Themes
The output of the [[DevOps Kaizen]] events are the Improvement Themes. The improvement theme should be a living document accessible to all stakeholders. The core Kaizen team should review the improvement theme once or twice per week, updating the theme based on completed and new identified actions. A team can have many improvement themes active at any one time. The next steps agreed for each improvement theme should be used to create stories in the team's backlog.