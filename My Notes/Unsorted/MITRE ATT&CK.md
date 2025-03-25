---
tags:
  - mitre
  - cybersecurity
date: 2025-03-21
---
# MITRE ATT&CK
A common language for Tactics, Techniques, and Procedures
- TTPs are at the *top* of the **Pyramid of Pain**...

![](../../assets/images/Pasted%20image%2020250321150749.png)

> [!tip]+ Links & Sources
> - [Putting MITRE ATT&CK™ into Action with What You Have, Where You Are](https://www.youtube.com/watch?v=bkfwMADar0M) - Katie Nickels (YouTube)

## ATT&CK Matrix Hierarchy

- At the top of the matrix: **Tactics**
	- As of March 2025, there are 14 Tactics in the Enterprise Matrix
- Below each Tactic: **Techniques**
- Under each Technique: **Procedures** → Specific implementations of a particular technique. The *procedures* performed to implement them.

## ATT&CK Use Cases

![](../../assets/images/Pasted%20image%2020250321152913.png)

### How can I *actually use* it?

- Detection
	- Lvl 1
		- Look at others' behavioral analytics and choose a few to implement
			- Adapt/tune them to your environment
			- CAR repo, Endgame EQL Analytics Library, Threat Hunter Playbook, Sigma, Atomic Threat Coverage → all of these things map to ATT&CK
	- Lvl 2
		- Look at what techniques you may be able to detect based on data you're already collecting
			- Host-based + network-based
			- If you've got a lot of logs, there might be TTPs associated with their contents unbenknownst to you
		- Choose *one* data source and write your own analytics.
			- MITRE has a python library to help you pull the data sources from ATT&CK → [https://github.com/mitre-attack/mitreattack-python](https://github.com/mitre-attack/mitreattack-python)
	- Lvl 3
		- Assess your detection coverage across ATT&CK
			- Consider starting with one tactic and expanding from there.
				- Remember you'll never get to 100% / perfect coverage

- Assessment and Engineering

- Threat Intelligence
	- Inform your defenders...
	- Compare behaviors...
	- Communicate in a common language...
	- Hey, we know that X group is using Y tactic... can we do something about that?
	- Map your own threat intel to ATT&CK
		- Current threat data
		- Incident response data
		- Real-time alerts
		- Historic reporting
	- Prioritize frequently-used techniques
		- Remember any ATT&CK-mapped data has biases...
		- You're prioritizing *known* adversary behavior over the unknown...
	- Use and share your intel!

- Adversary Emulation
	- There are many red teaming tools...
	- Use ATT&CK to mature what your red team is doing...
		- Choose a different technique each week
		- Discuss how you'd use different procedures to perform behavior
		- Bring in your threat intel analysts to talk about how adversaries are using it
		- Communicate with your blue team in a common language
	- Have the red team start emulating ATT&CK techniques themselves
		- Adversary Emulation Field Manuals are available to assist in this process

### Blue Team Questions

- How effective are my defenses?
- Do I have a chance at detecting APT\[X]
- Is the data I'm collecting useful?
- Do I have overlapping tool coverage?
- Will this new product help my org's defenses?