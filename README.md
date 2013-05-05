Fork and Partial Rewrite
========================
This is my attemp to fork and partially rewrite the cis-puppet module into a format that I think would be easier to consume and maintain.

I have the following plans for the re-organization of this module:

- Separate out manifest into sections that correspond to the CIS Benchmark Theme
- Have a settings.pp type manifest where you can turn benchmark items on or off (maybe just in init.pp)
- Have classes with subclasses for each section (e.g. cis-puppet:filesystem:cramfs)
- Augeaus all config file operations so as to be compatible with existing Puppet infrastructure
- Move facts from disparate shell scripts into a Ruby file (facts as Ruby code)
- Choice of Level 1 or Level 2 enforcement
- Give facts names you can use to check your compliance ( e.g. cis_tmp_ownfilesystem: true )

The initial version of this module was a great start and a LOT of work.  My hope is to make some improvements upon it to make it even more useful.

-Dave


Overview
========
 
This module implements the Center for Internet Security (CIS) Security Configuration Benchmark for Red Hat Enterprise Linux 6 v.1.1.0 (avilable at http://benchmarks.cisecurity.org). Each scored control has been implemented as a class or a custom fact.

Installation
============

Please either:

- Clone git repo from https://github.com/arildjensen/cis-puppet
- Run "puppet module install arildjensen/cis" and install from PuppetForge (http://forge.puppetlabs.com/arildjensen/cis)

Use
===

The class cis::el6all will enforce all the controls. If you wish to deviate please look for the el6all.pp file and use that as a template. Note that some of the scored controls not able to be written in Puppet code have been implemented as custom facts using Facter. Controls labeled "not scored" by the benchmark are not included.

Note that there are two subclasses in the cis module, cis::linuxcontrols and cis::el6. The former implements the specific controls with a general name (such as cis::linuxcontrols::c0001), allowing for future re-use. The latter maps directly to a specific CIS control for RHEL6 (such as cis::el6::1_1_17 for control 1.1.17 in the benchmark).

Author
====

Written by Arild Jensen <ajensen@counter-attack.com> with source code repository at https://github.com/arildjensen/cis-puppet.


Release History
==========
0.1.0 - Initial release

