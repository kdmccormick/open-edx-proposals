
OEP-57: Cores and Extensions
############################

.. list-table::
   :widths: 25 75

   * - OEP
     - :doc:`OEP-57 <oep-0057-cores-and-extensions.rst`_
   * - Title
     - Cores and Extensions
   * - Last Modified
     - 2022-08-??
   * - Authors
     - Kyle McCormick <kyle@tcril.org>
   * - Arbiter
     - TBD <tbd@openedx.org>
   * - Status
     - Draft
   * - Type
     - Architecture
   * - Created
     - 2022-08-??
   * - Review Period
     - 2022-??-?? - 2022-??-??
   * - Resolution
     - TBD
   * - References
     - TBD

Abstract
********

.. to do


Motivation
**********

The Open edX project is comprised of nearly two hundred repositories that, together, contain millions of lines of code.
Each repository increases the effort required to maintain the project and the cognitive load required to understand the project.

.. to do


Specification
*************

We define several terms to help us organize and make decisions abut Open edX repositories.
Firstly, we define two *Product Offerings*. Then, we define four axes upon which we will
classify all Open edX repositories:

* *ring*
* *layer*, and
* *support level*.


Product Offerings
=================

The Open edX Product Working Group (PWG) shall create and maintain two product specifications:
the *Core Product Offering* and the *Extended Product Offering*.
The PWG may document these specifications in any format, provided that:

* they are always easy-to-find and publicly visible,
* they are reviewed and updated at least every six months, and
* a public revision history is maintained.

Core Product Offering
---------------------

This is an articulation of which features should come fully supported by the community Open edX installation *without any additional configuration steps*. In other words, it is the desired "out-of-the-box" Open edX experience. Ensuring the support, maintenance, security, and quality of these features is of highest priority to the Open edX community.

Extended Product Offering
-------------------------

This is an articulation of which features should come supported by the community Open edX installation *without installing any additional software*, although configuration (overriding settings, toggling Waffle flags, etc.) may be necessary. By definition, this is a superset of the Core Product Offering. Ensuring the support, maintenance, security, and quality of these features is important, although secondary to ensuring so for the features in the Core Product Offering.


Repository Rings
================

Based on the Product Offering specifications,
we designate five *rings* of Open edX repositories:

1. **Clerical** repositories exist solely to help manage the Open edX project itself.
   For example, they may contain process documentation,
   hold code for project administration tools,
   or serve as a task-tracking repository.
   However, they may *not* contain code or documentation intended for *users* of
   Open edX, whether that be operators, educators, or otherwise.

2. **Kernel** repositories are necessary and sufficient to run a functioning
   instance of the Open edX LMS. In other words, the Kernel is the minimal set of
   repositories upon which Open edX depends. We recognize that it is ideal
   to minimize the size of this tier over time.
   (At the time of writing, this includes edx-platform
   and every Open edX repository upon which edx-platform has a hard dependency,
   of which they are currently very many.)

3. **Bundled** repositories, together with the kernel repositories,
   are necessary and sufficient to support the Core Product Offering.
   In other words, bundled repositories are part of the core product, but are
   not strictly necessary in order to run the LMS. For example, several
   XBlocks may be core to the Open edX product but may not be requirements of the LMS;
   they would be considered bundled repositories.

4. **Supplemental** repositories, together with the kernel and bundled repositories,
   are necessary and sufficient to support the Extended Product Offering.
   In other words, supplemental repositories are part of the extended product
   but not the core product. For example, a micro-service that operators could optionally
   enable in the Open edX community release would be considered a supplemental repository.

5. **External** repositories describe all remaining repositories related to Open edX.
   They are neither used in the Extended Product Offering nor for clerical purposes.
   There are an unbounded number of repositories in this ring.


Repository Layers
=================

Depending on how a repository is used, we release it to the community in
one of two different ways:

* **Top-layer** repositories are the entry points for software that deploys and runs Open edX. These include:

  * backend services,
  * frontend applications,
  * optional plugins that are *not* listed as explicit requirements by other repositories,
  * tools that are *not* invoked by other repositories, and
  * top-level documentation projects.

* **Lower-layer** repositories are referenced and used by primary repositories,
  either by numerical version or by git hash. These include:

  * libraries that are listed as explicit requirements by other repositories,
  * tools that are loaded and used by other repositories, and
  * documentation that is included into another documentation project.

Note that a repository's layer is just a tactical technical distinction;
it does not indicate the repository's importance, support level, or anything else qualitative.
For example, an optional component may be defined in a top-layer micro-service repository,
whereas a core architectural framework might be defined in a lower-layer library repository.



Repository Support Levels
=========================

.. todo table

We designate seven support levels for repositories powering the Extended Product Offering
(that is: kernel, bundled and supplemental repositories):

.. list-table::
   :header-rows: 1

   * - Support Level
     - Open edX Release
     - Production Readiness
     - Forwards Compatibility
     - Documention Level
     - Continuing Development
     - Community Support
   * - **Pre-Alpha**
     - ❌ Not in release
     - ❌ Not production ready
     - ❌ Frequent breaking changes
     - ❌ Sparsely documented
     - ✔️  Actively developed
     - ❌ No support
   * - **Alpha**
     - ✔️  In release
     - ⚠️  Production-ready for early adoptors (issues expected)
     - ❌ Frequent breaking changes
     - ⚠️  Partially documented
     - ✔️  Actively developed
     - ⚠️  Low-priority support
   * - **Beta**
     - ✔️  In release
     - ⚠️  Production-ready (issues anticipated)
     - ⚠️  Breaking changes expected, but communciated
     - ⚠️  Mostly documented
     - ⚠️  May be actively developed
     - ✔️  Supported
   * - **Stable**
     - ✔️  In release
     - ✔️  Production-ready
     - ✔️  Breaking changes minimized & communicated 
     - ✔️  Documented
     - ⚠️  May be actively developed
     - ✔️  Supported
   * - **Sustained**
     - ✔️  In release
     - ✔️  Production-ready
     - ⚠️  Breaking changes minimized & communicated. Potential future deprecation candidate
     - ✔️  Documented
     - ❌ Not actively developed
     - ✔️  Supported
   * - **Deprecated**
     - ✔️  In release
     - ⚠️  Production-ready, but migration encouraged
     - ❌ Upcoming removal expected
     - ⚠️  Possibly documented
     - ❌ Not actively developed
     - ❌ Not supported

.. 1. **Alpha** repositories are available for production trial by early adopters,
..    but instability should be anticipated and significant breaking changes should
..    be expected between releases. Documentation will provided when possible, but
..    due to the repository's frequent change rate, may not be comprehensive.
..    Support may be provided by maintainers but is not guaranteed.
.. 2. **Beta** repositories are ready for production use,
..    Documentation should be mostly complete.
..    Maintainers should provide support.
.. 3. **Stable** repositories are ideal for production use.
..    Complete documentation should be available and maintainers should provide support.
..    Breaking changes should be be minimized and notified with
..    adequate lead time between releases.


.. _openedx GitHub organization: https://github.com/openedx

.. to do

Rationale
*********

.. The rationale adds to the specification by describing the events or
.. requirements that led to the proposal, what influenced the design, and why
.. particular design decisions were made. The rationale could provide evidence
.. of consensus within the community and discuss important objections or
.. concerns raised during discussion. It could identify any related work,
.. for example, how the feature is supported in other systems.

Backward Compatibility
**********************

.. This statement identifies whether the proposed change is backward compatible.
.. An OEP that introduces backward incompatibilities must describe the
.. incompatibilities, with their severity and an explanation of how you propose to
.. address these incompatibilities.

Reference Implementation
************************

.. The reference implementation must be completed before any OEP is given "Final"
.. status, but it need not be completed before the OEP is "Accepted". While there is
.. merit to the approach of reaching consensus on the specification and rationale
.. before writing code, the principle of "rough consensus and running code" is
.. still useful when it comes to resolving many discussions.

Rejected Alternatives
*********************

.. This statement describes any alternative designs or implementations that were
.. considered and rejected, and why they were not chosen.

Change History
**************

2022-08-??
==========

* Document created
* `Pull request #XXX <https://github.com/openedx/open-edx-proposals/pull/XXX>`_
