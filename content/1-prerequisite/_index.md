+++
title = "Prerequiste"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

+ This Lab is part of the Landing Zone Lab.
+ At the beginning, we will need to create the AWS Organization with 4 Organizational Units under them for specific logical grouping. Create specific AWS accounts for Security, Shared Services, Logging and Application accounts and map them under appropriate OU’s.

![Lab Diagram](../../../images/1/1.png?width=60pc)

+ Next, we customized the secure multi-account environment with the following:
	* **Logging account**: Centralized location for Amazon VPC Flow Logs, CloudTrail logs, Config logs
	* **Security account**: AWS Config aggregator, Amazon GuardDuty master, and alerts.
	* **Network account /Shared Services account**: Shared virtual private cloud (VPC) for remote connectivity to other accounts. Primary AWS Direct Connect setup with an AWS Transit Gateway setup to communicate with VPCs from other accounts.
	* **Business Unit accounts**: Analytics-Prod, and Analytics-non-prod accounts.
