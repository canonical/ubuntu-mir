||<tablestyle="float:right; font-size: 0.9em; width:30%; background:#F1F1ED; background-repeat: no-repeat; background-position:  98% 0.5ex; margin: 0 0 1em 1em; padding: 0.5em;"><<TableOfContents>>||

== Introduction ==

Packages in Ubuntu main (and restricted) are officially maintained, supported and recommended by the Ubuntu project. Security updates are provided for them as necessary by Canonical, and Canonical's standard support services apply to these packages.

Therefore, special consideration is necessary before adding new packages to these components.
The [[https://launchpad.net/~ubuntu-mir|Ubuntu MIR Team]] reviews packages for promotion from universe to main.

That is the ''Main Inclusion Review'' => MIR

=== Process states ===

This is supposed to be an overview of MIR bug status (as there was enough confusion in the past).
Especially to make clear who's turn it is to act next on a MIR bug.

|| 1. New/Confirmed (unassigned)|| Bug is new for the MIR team to dispatch it to a MIR Team member||
|| 2. New/Confirmed (assigned)|| on the TODO list of the assigned MIR team member||
|| 3. New/Confirmed (assigned to Security)|| on the TODO list of the Security Team||
|| 4. In Progress (any)|| MIR team ack (and if needed Security Team ack) done, but now needs the Dependency/Seed change to happen to pull it into Main||
|| 5. Fix Committed (any)|| All of the above done, waiting for an AA to promote the packages||
|| 6. Fix Released (any)|| Case resolved by an AA||
|| 7. Incomplete (any)|| Questions/Requests were raised for the bug reporter to resolve/clarify||
|| 8. Won't Fix (any)|| Final Nack or given up by the bug reporter||
|| 9. Invalid (any)|| No Feedback for a while when in incomplete status||

{{{
          Answered       +-7----------+     No feedback        +-9-------+
      +------------------+ Incomplete +------------------------> Invalid |
      |   old assign can | any        <--------------------+   | any     |
      |   be kept as-is  +-----^------+                    |   +---------+
      |                        |    question               |
      |                        |                           |
+-1---v-------+  Triage  +-2---+----+ Security needed  +-3-+------------------+
|  New/Conf   +--------->+ New/Conf +----------------->+ New/Conf             |
| unassigned  |          | assigned |                  | assigned to Security |
+-------------+          +-+--+--+--+                  +-+--+--+--------------+
                           |  |  |    +-8-----------+    |  |  |
                           |  |  +----> Won't Fix   <----+  |  |
                           |  |   Nack| any         | Nack  |  |
                           |  |       +-------------+       |  |
                           |  |                             |  |
                           |  |       +-4-----------+       |  |
                           |  +-------> In Progress <-------+  |
                           |    Ack   | any         |  Ack     |
                           |          +-------------+          |
                           |             |Change that pulls    |
                           |             |into Main            |
+-6------------+           |         +-5-v-----------+         |
| Fix Released |           +---------> Fix Committed <---------+
| any          <---------------------+ any           |
+--------------+  AA promotes        +---------------+
}}}

Note1: Since many people set things to confirmed once they are sure it "exists" all too often bugs get set to confirmed. Since confirmed does not have any meaning for our process we will handle new<->confirmed as if the'y be the same.

Note2: All other combinations are undefined and should be fixed up to one of the defined states

== Exceptions ==

=== Font Packages ===

Fonts packages given that fonts are just data, there's no way for them to trip any of the problems that would cause us to not want to support it. Therefore not all of the process has to be followed for these.
Unfortunately there were cases where src:font-* packages contained way more than just a font - due to that either the MIR Team (if a MIR bug was filed) or the Ubuntu-Archive team (on promoting it) has to do a spot check that neither the source nor the created binary packages violate these assumptions.

The only limitation is that the package needs a valid team subscriber before being promoted by an archive admin - just in case anything might come up later.
The MIR Team should try to clarify that with the Team that owns the depending package to own the font as well (read: without the overhead of a full MIR process).

== Filing a MIR bug ==

The steps of the MIR process require a reporter (the one who wants a package promoted) a MIR team member (who does the review) and potentially a Security team member (for an extra review).

The MIR-bug reporter is expected to:

 1. Thoroughly go through [[#Main_Inclusion_requirements|Ubuntu Main Inclusion Requirements]], check that the package meets all the points there. If this package has nontrivial problems, it is not eligible for main inclusion, and needs to be fixed first.
  1. Write down issues that violate the requirements and list them in the MIR bug
  1. Write down all positive checks that you did as well (not only the issues)
 1. File a bug report about the package, titled "[MIR] sourcepackagename".
  1. Include the rationale and description of the violations of [[#Main_Inclusion_requirements|Ubuntu Main Inclusion Requirements]], and a confirmation that you checked the requirements carefully.
 1. Subscribe `ubuntu-mir` to the bug report (do not assign it to anyone!), so that it appears in the [[https://bugs.launchpad.net/ubuntu/?field.searchtext=&orderby=-date_last_updated&field.status%3Alist=NEW&assignee_option=none&field.assignee=&field.subscriber=ubuntu-mir|MIR bug list]].
 1. The [[https://launchpad.net/~ubuntu-mir|MIR team]] reviews the reports, and sets acceptable ones to ''In Progress'' or ''Fix Committed''. They might also delegate portions of the review to other teams, by assigning it to them; common cases are getting a thorough security review from the [[https://launchpad.net/~ubuntu-security|security team]] (please see [[SecurityTeam/Auditing|SecurityTeam/Auditing]] for details on requesting an audit and the [[https://trello.com/b/HvFhIQpv/security-team|security team trello board]] (private board; Reviews lane) for prioritized list of MIR security reviews), or getting a sign-off from particular team leads about maintenance commitments.
  1. In the case where an MIR needs a security review, a normal MIR review will happen by a member of the MIR team and the security review by a member of the security team. Among these team members, whoever does the last review shall adjust the bug status accordingly. For instance, if MIR team says ok then security says ok, the security team member should mark the bug as Fix Committed (see above for other statuses).
  1. In case the MIR Team (or later other reviewers) identify tasks that need to be done the bug is set to "incomplete" to reflect that is back on the reporter to drive that forward before more progress can be made. Common Examples are "please add an automated test" or "this needs the new version"
1. The submitter should then take responsibility for adding the package to the seeds as per SeedManagement or adding a dependency to it from another package that already is in `main`. The package will not be moved to main automatically, but will show up in the [[http://people.ubuntu.com/~ubuntu-archive/component-mismatches.txt|component-mismatches]] list, or if the dependency is only in proposed, the [[http://people.canonical.com/~ubuntu-archive/component-mismatches-proposed.txt|component-mismatches-proposed]] list.
 1. Archive administrators will review the component-mismatches output, and for each package waiting to move into `main`, look for a corresponding [[https://bugs.launchpad.net/~ubuntu-mir/+subscribedbugs|bug]].
 1. The archive administrators will promote approved packages to `main` if some other package or the seeds want it (see [[http://people.ubuntu.com/~ubuntu-archive/component-mismatches.txt|component-mismatches output]]) and the package in question has an owning team subscribed to it.

Notes:

 * MIR bugs should always be named for SOURCE packages, not binary packages
 * New binary packages from existing source packages, where the source package is already in main, do not require MIR bugs.
 * If a new source package contains only code which is already in main (e.g. the result of a source package split or rename, or source packages with a version in the name), it may not need a full review. Submitting a MIR bug with an explanation (but without the full template) or updating/extending on the existing old MIR bug and re-opening it by setting it to "NEW" is sufficient.


=== MIR bug report template ===
Use this template for the MIR bug report.
See below at [[#Main_Inclusion_requirements|Ubuntu Main Inclusion Requirements]] for the details to add in those sections.

{{{
[Availability]

[Rationale]

[Security]

[Quality assurance]

[UI standards]

[Dependencies]

[Standards compliance]

[Maintenance]

[Background information]
}}}

=== Main Inclusion requirements  ===

The package must fulfill the following requirements:

 0. ''Availability:'' The package must already be in the Ubuntu universe, and must build for the architectures it is designed to work on.
 0. ''Rationale:'' There must be a certain level of demand for the package, for example:
  * The package is useful for a large part of our user base.
  * The package is a new runtime dependency of a package that we already support (build-dependencies can stay in universe).
  * The package helps meet a specific Blueprint/Roadmap goal.
  * The package replaces another package we currently support and promises higher quality and/or better features, so that we can drop the old package from the supported set.
 0. ''Security:'' The security history and the current state of security issues in the package must allow us to support the package for at least 9 months (60 for LTS support) without exposing its users to an inappropriate level of security risks. This requires checking of several things:
  * Check how many vulnerabilities the package had in the past and how they were handled by upstream and the Debian/Ubuntu package:
   * http://cve.mitre.org/cve/search_cve_list.html: Search in the National Vulnerability Database using the package as a keyword
   * check OSS security mailing list (feed 'site:www.openwall.com/lists/oss-security <pkgname>' into search engine)
   * Ubuntu CVE Tracker
    * http://people.ubuntu.com/~ubuntu-security/cve/main.html
    * http://people.ubuntu.com/~ubuntu-security/cve/universe.html
    * http://people.ubuntu.com/~ubuntu-security/cve/partner.html
  * Check for security relevant binaries. If any are present, this requires a more in-depth security review.
   * Executables which have the `suid` or `sgid` bit set.
   * Executables in `/sbin`, `/usr/sbin`.
   * Packages which install services / daemons (`/etc/init.d/*`, `/etc/init/*`, `/lib/systemd/system/*`)
   * Packages which open privileged ports (ports < 1024).
   * Add-ons and plugins to security-sensitive software (filters, scanners, UI skins, etc)
 0. ''Quality assurance:''
  * After installing the package it must be possible to make it working with a reasonable effort of configuration and documentation reading.
  * The package must not ask debconf questions higher than medium if it is going to be installed by default. The debconf questions must have reasonable defaults.
  * There are no long-term outstanding bugs which affect the usability of the program to a major degree. To support a package, we must be reasonably convinced that upstream supports and cares for the package.
  * The status of important bugs in [[http://bugs.debian.org|Debian's]], [[https://bugs.launchpad.net/ubuntu|Ubuntu's]], and upstream's bug tracking systems must be evaluated. Important bugs must be pointed out and discussed in the MIR report.
  * The package is maintained well in Debian/Ubuntu (check out the Debian PTS)
  * The package should not deal with exotic hardware which we cannot support.
  * The package must include a non-trivial test suite, and if there is no obvious reason why it cannot work during build (e.g. it needs root privileges or network access), it should be run during package build, and a failing test suite should fail the build. The package should, but is not required to, also contain non-trivial autopkgtest(s).
   * If no build tests nor autopkgtests are included, and/or if the package requires specific hardware to perform testing, the subscribed team must provide a written test plan in a comment to the MIR bug, and commit to running that test either at each upload of the package or at least once each release cycle. In the comment to the MIR bug, please link to the codebase of these tests (scripts or doc of manual steps) and attach a full log of these test runs. This is meant to assess their validity (e.g. not just superficial)
  * The package uses a debian/watch file whenever possible. In cases where this is not possible (e.g. native packages), the package should either provide a debian/README.source file or a debian/watch file (with comments only) providing clear instructions on how to generate the source tar file.
  * It is often useful to run `lintian --pedantic` on the package to spot the most common packaging issues in advance
  * The package should not rely on obsolete or about to be demoted packages. That currently includes package dependencies on Python2 (without providing Python3 packages), and packages depending on GTK2.
 0. ''UI standards:'' (generally only for user-facing applications)
  * End-user applications must be internationalized (translatable), using the standard intltool/gettext build and runtime system and produce a proper PO template during build.
  * End-user applications must ship a standard conformant desktop file.
 0. ''Dependencies:''
  * All binary dependencies (including `Recommends:`) must be satisfiable in main (i. e. the preferred alternative must be in main). If not, these dependencies need a separate MIR report (this can be a separate bug or another task on the main MIR bug)
 0. ''Standards compliance:'' The package should meet the [[https://refspecs.linuxfoundation.org/fhs.shtml|FHS]] and [[http://www.debian.org/doc/debian-policy/|Debian Policy]] standards. Major violations should be documented and justified. Also, the source packaging should be reasonably easy to understand and maintain.
 0. ''Maintenance:'' The package must have an acceptable level of maintenance corresponding to its complexity:
  * All packages must have a designated "owning" team, regardless of complexity, which is set as a package bug contact. This is not a requirement for the MIR team ACK, but for the package to be promoted by an archive admin. Still, it is strongly suggested to subscribe, as the owning team will get a preview of the to-be-expected incoming bugs later on (once they are responsible).
  * Simple packages (e.g. language bindings, simple Perl modules, small command-line programs, etc.) might not need very much maintenance effort, and if they are maintained well in Debian we can just keep them synced
  * More complex packages will usually need a developer or team of developers paying attention to their bugs, whether that be in Ubuntu or elsewhere (often Debian). Packages that deliver major new headline features in Ubuntu need to have commitment from Ubuntu developers willing to spend substantial time on them.
 0. ''Background information:''
  * The package descriptions should explain the general purpose and context of the package. Additional explanations/justifications should be done in the MIR report.
  * If the package was renamed recently, or has a different upstream name, this needs to be explained in the MIR report.

== Reviewing a bug ==

This section is a guideline for the [[https://launchpad.net/~ubuntu-mir|MIR Team]].
The primary decision a reviewer is making is '''"Will this package be well maintained in main?"'''

The following guidelines are just ways to help you answer to that question.

 1. Duplication
  * One easy way to avoid the burden of maintaining the package is to not use it in the first place!  If a package is pulling in some random jpeg parsing library that needs a MIR, maybe it makes more sense to patch the package to just use libjpeg instead.  Keep an eye out for duplicated functionality in main, since that makes bug fixing and security reviewing that much harder.

 1. Embedded sources and static linking
  * Embedding a library source increases the maintenance burden of a package since that source needs to be maintained separately from the source in the Ubuntu archive. If a source embeds another package, in general the embedded package should not be used and the packaging should be modified to use the Ubuntu archive version. When this is not possible, the security team must agree to using the embedded source.

  * Similarly, when a binary from one source package statically links to libraries from another source package from the archive, when those libraries are updated the statically linked binaries must be rebuilt with the updated libraries to receive the fix, which increases the maintenance burden. For this reason, static linking in archive builds is discouraged unless static linking is required for the package in question to function correctly (e.g. an integrity scanner).

  * Golang
   * golang 1.4 packages and earlier could only statically compile their binaries. golang 1.5 in Ubuntu 16.10 introduced `-buildmode=shared` to build shared libraries and `-linkshared` to dynamically link against shared libraries. In general, statically compiled binaries are not suitable for the Ubuntu archive because they increase the maintenance burden significantly. As such, from Ubuntu 16.10 through 17.04, golang packages packages in main were expected to be built with shared libraries.

   * Evaluating cost/benefits while considering the ABI instability of golang libraries during this period, the MIR team decided for 17.10 and later to allow static builds of golang packages in main, so long as the number of these packages remains low and they follow the guidelines below (under "Packaging red flags/If it's a statically compiled golang package").

   * Specifically, in 17.10 and later, golang applications in main are expected:
    1. to build using `golang-*-dev` packages from the Ubuntu archive with `Built-Using` in debian/control. This requirement ensures that the security team is able to track security issues for all affected static binary packages
    2. not to build any vendored (i.e. embedded) code in the source package whose binaries appear in the archive (e.g. test code is ok) without clear justification from the requesting team and approval from the security team. This requirement ensures that the security team is able to track security issues for all affected source packages.
    3. only build against approved vendored sources (when applicable) and not build against newly added vendored code in subsequent Ubuntu uploads without approval from the security team. This requirement ensures that the security team is able to track security issues for all affected source packages.

   * The intended outcomes from the above requirements are for packages in main to standardize on particular versions of `golang-*-dev` packages (when possible) with the requesting team adjusting their packaging as necessary, all teams responsible for golang packages coordinating on transitions and the requesting team occasionally creating new `golang-*-dev` packages as agreed to in the MIR bug (upstreaming to Debian whenever possible). 

   * As a practical matter, golang source packages in main are not required to remove embedded code copies.

   * When it is infeasible to comply with this policy, the justification, discussion and approval should all be clearly represented in the bug.

   * Responsibilities once promoted to main (17.10+)
    * the security team will track CVEs for all golang packages in main
    * the security team will provide updates to main for all `golang-*-dev` packages
    * the security team will provide updates to main for golang applications whose non-vendored source code is affected as per normal procedures (including e.g., sponsoring/coordinating uploads from teams/upstream projects, etc)
    * the security team will perform no-change-rebuilds for all packages Built-Using `golang-*-dev` packages it has provided, and coordinate testing with the owning teams responsible for the rebuilt packages
    * for packages that build using any `golang-*-dev` packages:
     * the owning team must state their commitment to test no-change-rebuilds triggered by a dependent library/compiler and to fix any issues found for the lifetime of the release (including ESM when included)
     * the owning team must provide timely testing of no-change-rebuilds from the security team, fixing the rebuilt package as necessary
    * for packages that build with approved vendored code:
     * the owning team must state their commitment to provide updates to the security team for any affected vendored code for the lifetime of the release (including ESM when included)
     * the security team will alert the owning team of issues that may affect their vendored code
     * the owning team will provide timely, high quality updates for the security team to sponsor to fix issues in the affected vendored code

 1. Security
  * Determine if the package may have security implications (has a history of CVEs, runs a daemon as root, uses webkit^1,2^, uses lib*v8 directly, parses data formats, opens a port, processes arbitrary web content, uses centralized online accounts, integrates arbitrary javascript into the desktop, deals with system authentication (e.g. pam), etc).  Err on the side of caution.
  * If the package is security sensitive, you should review as much as you can and then assign to the ubuntu-security team. The bug will then be added to the [[https://trello.com/b/HvFhIQpv/security-team|security team trello board]] (private board; Reviews lane) in the prioritized list of MIR security reviews.

 1. Common blockers

  * Does it FTBFS currently?
  * Does it have a test suite?  Make sure it's being run and will fail the build upon error.
  * Does it have a team bug subscriber? (This is not a blocker for a MIR team ACK, but needs to be provided before the package can be promoted by an AA)
  * Is the code translatable (if end user visible)?
  * If it's a Python package, does it use dh_python?
  * If it's a Python package going on the desktop CD, will it pull in Python 2?

 1. Packaging red flags

  * Does Ubuntu carry a delta?
   * If it's a library, does it either have a symbols file or use an empty argument to dh_makeshlibs -V?  (pass such a patch on to Debian, but don't block on it).  Note that for C++, see [[DailyRelease/FAQ]] for a method to demangle C++ symbols files.
   * Does it have a watch file? (If relevant, e.g. non-native)
   * Is its update history slow or sporadic?
   * Is the current release packaged?
   * Will entering main make it harder for the people currently keeping it up to date?  (i.e. are they only MOTUs?)
   * Lintian warnings
   * Is debian/rules a mess?  Ideally it uses dh7 and overrides to make it as tiny as possible.
   * Does debian/control use `Built-Using`. This may indicate static linking which should be discouraged (excepting golang, see below)
   * If it's a statically compiled golang package:
    * Does the package use dh-golang (if not, suggest dh-make-golang to create the package)?
    * Does debian/control use `Built-Using: ${misc:Built-Using}` for each non'-dev' binary package (importantly, golang-*-dev packages only ship source files so don't need Built-Using)? 
    * Does the package follow [[http://pkg-go.alioth.debian.org/packaging.html|Debian Go packaging guidelines]]?
   * If a package shall be promoted it should NOT be on the lto-disabled list, but the fix, or the work-around should be directly in the package to enforce maintainer awareness and make it more visible to anyone looking at the package - see https://wiki.ubuntu.com/ToolChain/LTO.

 1. Upstream red flags

  * Errors/warnings during the build
  * Incautious use of malloc/sprintf
  * Uses of sudo, gksu, pkexec, or LD_LIBRARY_PATH (its OK to be used in tests)
  * User nobody is strictly for NFS's use and must not be used by any running processes on the system.
  * Use of setuid needs very careful design (prefer systemd to set those for services)
  * Important bugs (crashers, etc) in Debian or Ubuntu
  * Dependency on webkit, qtwebkit, seed or libgoa-*
  * Embedded source copies (this happens frequently with Go upstreams)
  * If this is a scope for the Unity Dash, does it [[http://mhall119.com/2012/12/adding-privacy-setting-support-to-your-unity-lens/|honor the privacy settings]]?

=== MIR review template ===

MIR members should use this template for the MIR review.

It helps to not miss any of the details mentioned above by processing them line by line.
In a perfect world with a perfect package one would only remove ''TODO:'' prefixes and be done.
In reality check them one by one and in case you can't just remove the ''TODO:'' prefix add an explanation as needed.

By default statements are in the ''OK'' section, issues that need to be addressed should go to the ''Problem:'' sections (and the summary at the top).

{{{
[Summary]
TODO: WRITE - The essence of the review result from the MIR POV
TODO: MIR team ACK
TODO: MIR team NACK
TODO: This does need a security review, so I'll assign ubuntu-security
TODO: List of specific binary packages to be promoted to main: <TODO>

Notes:
TODO: - add todos, issues or special cases to discuss
Required TODOs:
TODO - TBD
Recommended TODOs:
TODO: - The package has a team bug subscriber
TODO - TBD

[Duplication]
TODO: There is no other package in main providing the same functionality.

[Dependencies]
OK:
TODO - no other Dependencies to MIR due to this
TODO   (use tools: check-mir, seeded-in-ubuntu, reverse-depends)
TODO - no -dev/-debug/-doc packages that need exclusion

TODO: Problems:

[Embedded sources and static linking]
OK:
TODO: - no embedded source present
TODO: - no static linking

TODO: Problems:

[Security]
OK:
TODO: - history of CVEs does not look concerning
TODO: - does not run a daemon as root
TODO: - does not use webkit1,2
TODO: - does not use lib*v8 directly
TODO: - does not parse data formats
TODO: - does not open a port
TODO: - does not process arbitrary web content
TODO: - does not use centralized online accounts
TODO: - does not integrate arbitrary javascript into the desktop
TODO: - does not deal with system authentication (eg, pam), etc)

TODO: Problems:

[Common blockers]
OK:
TODO: - does not FTBFS currently
TODO: - does have a test suite that runs at build time
TODO:   - test suite fails will fail the build upon error.
TODO: - does have a non-trivial test suite that runs as autopkgtest
TODO: - if special HW does prevent build/autopkgtest is there a test plan, code, log provided?
TODO: - no translation present, but none needed for this case (user visible)?
TODO: - not a python/go package, no extra constraints to consider in that regard
TODO: - no new python2 dependency
TODO: - Python package that is using dh_python
TODO: - Go package that uses dh-golang

TODO: Problems:

[Packaging red flags]
OK:
TODO: - Ubuntu does not carry a delta
TODO: - Ubuntu does carry a delta, but it is reasonable and maintenance under control
TODO: - symbols tracking is in place
TODO: - symbols tracking not applicable for this kind of code.
TODO: - d/watch is present and looks ok (if needed, e.g. non-native)
TODO: - Upstream update history is (good/slow/sporadic)
TODO: - Debian/Ubuntu update history is (good/slow/sporadic)
TODO: - the current release is packaged
TODO: - promoting this does not seem to cause issues for MOTUs that so far
TODO:   maintained the package
TODO: - no massive Lintian warnings
TODO: - d/rules is rather clean
TODO: - Does not have Built-Using
TODO: - Go Package that follows the Debian Go packaging guidelines
TODO:   (see https://go-team.pages.debian.net/packaging.html)
TODO: - is not on the lto-disabled list
TODO:   (fix, or the work-around should be directly in the package,
TODO:    see https://launchpad.net/ubuntu/+source/lto-disabled-list/+publishinghistory)

TODO: Problems:

[Upstream red flags]
OK:
TODO: - no Errors/warnings during the build
TODO: - no incautious use of malloc/sprintf (as far as I can check it)
TODO: - no use of sudo, gksu, pkexec, or LD_LIBRARY_PATH (usage is OK inside tests)
TODO: - no use of user nobody
TODO: - no use of setuid
TODO: - no important open bugs (crashers, etc) in Debian or Ubuntu
TODO: - no dependency on webkit, qtwebkit, seed or libgoa-*
TODO: - not part of the UI for extra checks

TODO: Problems:
}}}


== MIR Team weekly status meeting ==

The MIR Team holds weekly meetings on Tuesdays, at 4.30 PM CET, in #ubuntu-meeting.

If you're chairing the meeting, you can the following meetingology template:

{{{
#startmeeting Weekly Main Inclusion Requests status

Use the #action command to note something for someone to do (optional)

#topic Review of previous action items

#topic current component mismatches
#link https://people.canonical.com/~ubuntu-archive/component-mismatches-proposed.svg
#link https://people.canonical.com/~ubuntu-archive/component-mismatches.svg

#topic New MIRs

#link https://bugs.launchpad.net/ubuntu/?field.searchtext=&orderby=-date_last_updated&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&assignee_option=none&field.assignee=&field.subscriber=ubuntu-mir

#topic Incomplete bugs / questions

#link https://bugs.launchpad.net/ubuntu/?field.searchtext=&orderby=-date_last_updated&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.subscriber=ubuntu-mir

#topic Any other business?

#endmeeting
}}}

The meeting is meant to help to facilitate

 * a fair share of work for each of us
 * a timely response to reporters of MIR requests
 * detection and discussion of any current or complex cases

Due to the nature of this process there are times when this is very
busy and the meeting is strongly needed.
But there are other times (e.g. at the beginning of a new release)
where not a lot is happening.
In such "idle" phases the leader of the meeting can pre-check the
links we usually check together and skip steps of the agenda quoting
that a pre-check has not shown anything worth to discuss.

From there we can then go rather directly to "Any other business?"
which serves as a catch all for all attendees.
By that we can make the meeting more efficient in those times, instead
of filing a monologue-log every week.

== MIR related helpers ==

=== Tools ===

 * `check-mir` can be run from a checked out source and tell you which dependencies are in universe.
 * `seeded-in-ubuntu PACKAGE` can tell you whether and how a given PACKAGE is seeded
 * `reverse-depends` can tell you reverse source or binary depends, per component
 * The [[http://people.canonical.com/~ubuntu-archive/component-mismatches.svg|component mismatch map]]

=== Making Life Easier for Archive Team Members ===

To help prevent promotion of packages that cause component mismatches, we can do two things:

 1. Run `check-mir` and make sure that all dependencies have a MIR.  We don't want to be surprised by a dependency after a package is promoted.
 1. List all distinct binary packages that should be promoted.  Often a source package will have binary packages that aren't actually needed in main.  Things like `-doc`, `-autopilot` or `-dbgsym`.  These can stay in universe, and it is a kindness to list only the packages we need for the archive team member that does the promotion. 
 1. Recommend the owning team to add their corresponding team bug subscriber during the MIR process.

=== Bug Lists ===

 * [[https://bugs.launchpad.net/~ubuntu-mir|All MIR bugs]]
 * [[https://bugs.launchpad.net/~ubuntu-mir/+bugs?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE|All open MIR bugs]]
 * [[https://bugs.launchpad.net/ubuntu/?field.searchtext=&orderby=-date_last_updated&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&assignee_option=none&field.assignee=&field.subscriber=ubuntu-mir|All open unclaimed MIR bugs]]
 * [[https://bugs.launchpad.net/ubuntu/?field.searchtext=&orderby=-importance&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=ubuntu-mir&field.structural_subscriber=&field.component-empty-marker=1&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1|All incomplete MIR bugs]]
 * [[https://bugs.launchpad.net/%7Eubuntu-mir/+bugs?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=choose&field.assignee=ubuntu-security&field.bug_reporter=&field.bug_commenter=&field.subscriber=ubuntu-mir&field.structural_subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on|All MIR bugs where the security team is assigned]]

