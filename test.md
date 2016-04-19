pwcrepos
========

#Description

This module takes a hash of repos and enables them on the managed server. It also
enables a cron job to run a package update on a set schedule.

#Module Requirements

This module relies on the puppetlabs/apt and puppetlabs/stdlib repos.

#Example usage

Implementing through the console:

When implementing this in the console, create a classification group for each separate
server group, type, or environment in order to separate configurations. Then attach this
class to the classification group and update the following variables based on the os type
being managed:

- $aptrepos
```javascript
{ "wily-main": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Main", "repos": "wily main restricted" }, "wily-updates-main": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily-Updates Main", "repos": "wily-updates main restricted" }, "wily-universe": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Universe", "repos": "wily universe" }, "wily-updates-universe": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily-Updates Universe", "repos": "wily-updates universe" }, "wily-multiverse": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Multiverse", "repos": "wily multiverse" }, "wily-updates-multiverse": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily-Updates Multiverse", "repos": "wily-updates multiverse" }, "wily-backports": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Backports", "repos": "wily-backports main restricted universe multiverse" }, "wily-security-main": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Security Main", "repos": "wily-security main restricted" }, "wily-security-universe": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Security Universe", "repos": "wily-security universe" }, "wily-security-multiverse": { "location": "http://tdavdc3.nam.pwcinternal.com/apt/", "comment": "Wily Security Multiverse", "repos": "wily-security multiverse" }}
```
- $centosrepos
- $redhatrepos
```javascript
{
	"redhatrepos": [{
		"local_rhel-7-server-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-7-server-rpms/",
			"descr": "Local Redhat Server $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		},
		"local_rhel-7-server-eus-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-7-server-eus-rpms/",
			"descr": "Local Redhat Server eus $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		},
		"local_rhel-7-server-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-7-server-rpms/",
			"descr": "Local Redhat Server $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		},
		"local_rhel-7-server-extras-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-7-server-rpms/",
			"descr": "Local Redhat Server extras $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		},
		"local_rhel-ha-for-rhel-7-server-eus-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-7-server-rpms/",
			"descr": "Local Redhat Server HA for eus $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		},
		"local_rhel-rs-for-rhel-7-server-eus-rpms": {
			"baseurl": "http://tdavdc3.nam.pwcinternal.com/rpm/redhat/7/rhel-rs-for-rhel-7-server-eus-rpms/",
			"descr": "Local Redhat Server rs for eus $releasever - $basearch",
			"enabled": 1,
			"gpgcheck": 1,
			"sslverify": 0,
			"proxy": "_none_"
		}
	}]
}
```

If you are finding that you would like to set any defaults, you can use the following
variables:

        - $aptreposdefault
        - $centosreposdefault
        - $redhatreposdefault

Additionally, you should set the frequency that the cron job runs using the following
variables:

        - $cronminute
        - $cronhour
        - $cronmonthday
        - $cronmonth
        - $crondayofweek
