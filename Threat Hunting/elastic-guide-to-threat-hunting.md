# Intro
Threat hunting is not about scanning an environment with IOCs, it is about setting a hypothesis and verify it in an environment.

# Chapter 1
## Page 1
Most security tools are passive, they trigger on prescribed events.
Threat hunting is an active process that seeks evidence of malicious activites.
## Page 2
IOCs search should be automated, human analysts should focus on understanding the environment and perform tasks that can only be performed by humans
The goal of threat hunting is to reduce dwell time (finding threats early).
## Page 3
The hunt team should have these skills:
* Adversary tradecraft: methods used by attackers
* Incident response: techniques and tools for analyzing and scoping attacks, malware and exploits
* Thread detection: techniques and tools for identifying attacks and tools used by attackers
* Threat Intelligence: collect, analyze, curate, disseminate intelligence to help team take actions
* IT operations: applications, networks, architecture of the systems used by the organization
* Communication: communicate effectivley with other stakeholders and teams

The hunt team should have people who can fulfil these roles:
 * Incident Manager: technical person who understands business risk
 * Response analyst: can analyze data from multiple sources
 * Malware analyst: can analyze and write decoders for malware
 * Operations Staff: people who know about systems and network administration and other IT functions
 
 SOC focus on IOCs, hunt team focus on uncovering the behaviours and attacker's techniques, they develop new detections for SOC
 
 Threat hunt team should automate the IOCs lookups.
 ## Page 5
 Threat hunt team should research TTPs, initial access (tactic), spear phishing (technique)
 
 Artifacts and indicators of attacker behaviour:
 * Filesystem data and metadata
 * Network metadata (Netflow and dns)
 * Application data and metadata (webserver logs)
 * User and authentication records
 * Process names and meta data
 * Registry paths and metadata

 ## Page 6
 Locard's exchange principle: Every contact leaves a trace
 Tradecraft: Techniques and procedures of espionage
 Most adversaries take the following steps:
 * Access victim's environment
 * create a C2 server
 * obtain and leverage additional privileges
 * conduct reconnaissance
 * Identify data and system of interest
 * Access systems
 * Collect/destroy data
 * Exfiltrate data or achieve objective
 
 ## Page 7
 Characteristics of successful intrustions:
 * Combine multiple, discrete techniques
 * Occur over relatively compressed time periods
 * Include both benign and malicious executables
 * Acquire and leverage some type of privileged access
 * Involve one or more endpoints
 * Change the content of the filesystem on endpoints
 
 ## Page 8
 Use frequency to judge events, malicious events tend to be scarce.
 * Ex: unkown binary on 2% of the machines (malicious)
 Low prevalence is more suspicious
 The intrusion we care about the most are happening right now.
 
 ## Page9
 Patterns can discover malware contacting C2 every x mins, or bruteforce attempts.
 Anomalies: deviations from the standard behavior
 * Unusual data volumes and frequencies
 * Deviation from the standard configuration
 * Departures from convetion
 * Unusual parent-child process relationships
 
 other places to hunt for anomalies:
 * Run and RunOnce keys
 * Windows services
 * Image file execution options
 * Application debuggers
 * Registered COM servers
 * Loaded drivers
 
 ## Page 10
 Build environmental awarness: learn what is normal to identify suspicious behavior
 * How do sys admins interact with servers, from where ?
 * which accounts are members of privileged groups
 * what remote execution tools are used
 * what user agent strings are common
 * where are sensitive data stored, and how users access it
 * what are typical levels of lateral movment
 * what network connections exist with thrid parties
 
 # Chapter2: structuring hunts
 ## Page13
 Dont look only for threats related to your industry, threat groups can change targeting.
 MITRE ATT&CK is threat agnostic.
 
 Structuring a hunt:
 * Propose a hypothesis: ex: bad actors are using mofcomp.exe to modify WMI CIMv2 database
 * Identify evidence to prove hypothesis: identify the forms of evidence that can approve or disapprove the hypothesis .
    * ex: collect process execution auditing (EID 4688 or sysmon EID 1)
 * Develop analytics: describe how the evidence can be reduced, grouped and analyzed to reach a conclusion. Use 3rd part to reduce amount of data that needs to be analyzed.
 * Automate: automate collection of events, data reduction, matching keywords 
 * Document: document during the course of the hunt.
 * Reporting: final report should include:
  * The metrics of the hunt
  * The root cause of any detected compromise
  * scope of affected machines, applications and accounts
  * description of the techniques detected
  * IOCs to be used for detecting similar attacks
  * Lessons learned and areas of increasing visibility
  * Recommendations for changes to the organization's security controls
  * A description for new analytics for detection and alerting
  # Page 16
  Transitioning to Incident response: At some point, the hunt team must declare an incident and assign a priority to it.
  
  measuring your hunt: can measure using time spent to collect the data, human hours required to analyze the data, number of findings
  # Page 18
  Was the hypothesis confirmed?: Use hypothesis that are not too generic, so that it is easy to evaluate the hypothesis
  un
  How effective was the hunt?: can be measured by the number of incidents uncovered and their severities :
    * number of vulns discovered and recommendations provided
    * Incidents discovered, grouped by threat category
    * compromised systems discovered
    * Days of dwell time for each incident
    * New attacker tactics uncovered
  Hunts without findings are good for creating baselines for future hunts.
  
  How effective was the team: can be measured using the following:
    * New sources of evidence integrated into hunt processes
    * New methods of data reduction and improvments in searching technologies
    * Reductions in false positives of incidents
    * Hunts esclated into investigations
    * investigations results in blocking ongoing attacks
    * Vulnerabilites fixed as a result of hunt report
  
  # Chapter 3
