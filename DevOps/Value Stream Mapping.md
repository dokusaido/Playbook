## Value Stream Mapping

**Value stream** is the process including all steps a team follows to get changes and feature implementations into production thus delivering business value.

**Values Stream Mapping (VSM)** is the process of aligning the entire team around an agreed understanding of the steps, processes, timings and constraints in a Value Stream, thus helping the team to identify, agree and prioritize improvement steps.

**VSM** focuses the DevOps work on improvements which achieve the largest business value, thus helping organizations create blueprints in support of Lean transformations.

A Value Stream describes the process used to create and deliver goods and services. While a Value Stream Map is a pictorial representation of a value stream, using a standard set of symbols, of an end to end process including lead and activity times for all steps in the process.

A VSM will enable us to see the end to end flow of software from idea to delivery including branches, feedback loops and queues in our process.

- Processing time - Actual time spent working.
- Waste time - Handoffs, queues and incomplete or incorrect processing time.
- Total Duration = Processing Time + Waste Time

We use it to identify and eliminate waste, waste is any non value add activities in the value stream including handoffs, rework, manual activities, wait times etc.

The time it takes for a feature to be delivered includes both the actual time someone works on it and the time the feature spends waiting for someone to work on it.

- **Lead Time (LT)** the time it takes a work item to leave the previous step to when it leaves the current step. LT includes both the time during which value is being added to the the work item, processing time and idle time when no work is being done on the item.
- **Processing Time (PT)** is the time in the step when a work item is being productively processed.
- The percent of **Complete/Accurate (C/A%)** work items received in the current step from the previous step.

Capturing these metrics in the current state VSM will help the team understand the areas jeopardizing fast flow, short lead times and reliable outcomes, and thus guide the team toward identifying the desired improvements.

Eliminate non value activities in the current state VSM. Increase the percent complete and accurate (C/A):
- How can we improve the PT for each activity?
- How do we reduce, or even eliminate the non-productive time in the LT for each activity?
- What are the boundaries between the activities and why do they exist?
- What contributes to the LT for each activity including handoffs, queues, and organizational rules & procedures?
- Who performs each activity, including their roles?
- What tools are used by people performing each activity?
- Are there opportunities for automation and/or integration to help improve efficiency of the activities?
- How can we shift activities left to provide faster feedback?
- What other DevOps principles, practices or tools could be applied to improve the end- to-end LT?

The desired state VSM may have more challenging targets for each of the three key metrics - %C/A, LT, and PT per activity. These targets may need to be implemented over a couple of sprints.