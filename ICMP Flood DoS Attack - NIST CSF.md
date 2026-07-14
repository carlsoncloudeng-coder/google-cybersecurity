# Incident Report Analysis: ICMP Flood DoS Attack (NIST CSF)

A firewall with no ICMP rate limit sat between a small multimedia company and the internet. Someone found it, flooded the network with ping packets for two hours, and every internal service went dark. Nobody's data was touched. Nobody logged into anything they shouldn't have. The whole incident came down to one traffic type nobody had bothered to control.

This project walks that incident through the five functions of the NIST Cybersecurity Framework: Identify, Protect, Detect, Respond, Recover. It's coursework from Google's Cybersecurity Certificate, built around a case study, but I treated it the way I'd treat a real postmortem: figure out what broke, decide what changes actually prevent a repeat, and write it down so the next person doesn't have to relearn the same lesson.

## The scenario

A denial-of-service attack against an internal network. The attacker sent a flood of ICMP echo requests through a firewall that had no rule limiting that traffic. Network services stopped responding to legitimate requests for about two hours. The response team blocked incoming ICMP, took non-critical services offline to reduce load, and brought critical services back up. A follow-up investigation traced the root cause to the unconfigured firewall rule.

## Working through the framework

**Identify.** Name the attack correctly before doing anything else: an ICMP flood, a specific kind of DoS attack, not a breach and not malware. The affected system was availability itself, not data. The entry point was a firewall gap, not a phished credential. Getting this distinction right changes everything downstream, since a breach calls for credential resets and customer notification, and an availability attack calls for rate limiting and traffic filtering instead.

**Protect.** Four things get built or changed here: a firewall rule that caps ICMP packet rate, source IP verification to catch spoofed addresses, a documented change-management process so a rule this permissive doesn't slip through unnoticed again, and a recurring audit schedule for firewall configurations. The unconfigured rule wasn't a one-time mistake. It was a gap in the review process, so the fix has to be a process fix, not just a config fix.

**Detect.** Monitoring software that knows what normal traffic looks like, so a spike stands out instead of blending in. An IDS/IPS tuned to flag ICMP traffic on packet rate and source pattern. Regular log review instead of log review that only happens after something already broke. The goal is catching the next flood at minute five, not hour two.

**Respond.** Block the traffic at the firewall. Take down only what has to come down, keep critical services running if at all possible. Pull logs and monitoring data to reconstruct what happened and when. Fix the root cause, not just the symptom, meaning the firewall rule gets rewritten, not just the ICMP traffic gets blocked temporarily. Tell the people who need to know.

**Recover.** Confirm critical services are actually stable, not just back online. Check that nothing was corrupted during the outage, since an availability attack can still cause collateral damage if a service crashes mid-transaction. Restore whatever got taken offline. Run a post-incident review to confirm the new firewall rule and monitoring tools are doing what they're supposed to, because a fix nobody verifies is just a hope.

## Deliverable

[`Incident-report-analysis-completed.docx`](./Incident-report-analysis-completed.docx) contains the full write-up in the standard incident report template used throughout the course, with a summary and all five NIST functions filled in against this scenario.

## What this exercise actually taught me

The interesting part of this case isn't the ICMP flood. Ping floods are old news. The interesting part is that a two-hour outage traced back to one unset firewall rule, and no amount of good detection tooling would have caught that gap beforehand, because detection tools watch traffic, not configuration. That's an audit problem. Catching it means someone has to periodically ask "what is this firewall actually configured to allow," not just "is anything weird happening on the wire right now." Identify and Protect do different jobs, and this incident is a decent reminder of why both matter.
