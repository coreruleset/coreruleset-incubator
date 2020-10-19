# OWASP ModSecurity Core Rule Set - Incubator

## Purpose

This is a CRS side project with non-blocking rules in beta quality. The idea
is to allow people to use these rules in production and to provide
feedback so we can adjust them or include them at the right paranoia
level in the real releases.

Rules in the Incubator are non-blocking. They are meant to do no harm, but they are still beta.

## Rules organization

There is a rules folder and in the rules folder, the rules get their own rules file.
Strict siblings (if any) are kept together with the filename pointing to the
first rule.

Rule range: 9M prefix. E.g. 9920470 is the incubator rule for 920470.

Rules are tagged with `"CRS_incubator"` in addition to `"OWASP_CRS"`.

Please note that ModSec2 does regex matching on the tags. So if
we do `OWASP_CRS_incubator`, then `RemoveRuleByTag "OWASP_CRS"`
would also remove one of these rules. This is probably not
intended, So we need to keep the tags separate.

When people are using the rules, they are invited to submit reports about the
alerts that the kindergarden rules produce. The reports are meant to be submitted
as github issue via a predefined issue templates.

## Reporting about your experiences with these rules

Please submit all reports as issues. We will prepare a template for that.

A report issue should contain the following infos:
* rule id
* brief description of traffic (e.g. "API for machine agents", "Wiki for DB admins", ...)
* Amount of traffic (Ideally http requests per day)
* Number of false positives for this rule (mean absolute number per day, or some other measurement)
* Performance observations
* Remarks

One report should be submitted per rule, with the exception of
strict siblings that should be reported together with the report
of the first rule in a group as a single report.

Performance observations are hard to standartize. Ideally, this would be a
script. In ModSec2, we have `PERF_RULES` and other helpers, in ModSec3, this
option does not exist and we are a bit at a loss.

So for the time being, we keep the "performance observations" open.
When we have more experience with the new repo and this really remains
a problem, we can invest more time into it.

## Process to promote rules from incubator to the main CRS

There are no clear rules so far as to when rules are considered sufficiently
mature to be promoted. We need to gain experience, discuss things
together and then with the time, we might get a clear policy.

