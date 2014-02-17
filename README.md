Bugzilla on OpenShift
=====================

``Bugzilla`` is server software designed to help you manage software development.

More information can be found at http://www.bugzilla.org

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a PERL application with a PostgreSQL cartridge.

    rhc app create bugzilla perl-5.10 postgresql-9.2

Add this upstream Bugzilla quickstart repo

    git remote add upstream -m master https://github.com/worldline/openshift-bugzilla.git
    git pull -s recursive -X theirs upstream master

Push the repo upstream to OpenShift

    git push

Head to your application at:

    http://bugzilla-$yourdomain.rhcloud.com

Default Credentials
-------------------
<table>
<tr><td>Default Admin Username</td><td>admin@admin.com</td></tr>
<tr><td>Default Admin Password</td><td>bugzilla</td></tr>
</table>

To give your new bugzilla site a web address of its own, add your desired alias:

    rhc app add-alias -a bugzilla --alias "$whatever.$mydomain.com"

Then add a cname entry in your domain's dns configuration pointing your alias to $whatever-$yourdomain.rhcloud.com.

