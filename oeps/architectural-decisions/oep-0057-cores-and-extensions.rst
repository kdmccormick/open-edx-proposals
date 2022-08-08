
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

We designate four classes of Open edX repositories:

1. logistical repositories,
2. kernel repositories,
3. bundled extension repositories,
4. official extension repositories, and
5. unofficial extension repositories.

We mandate that:

* The `openedx GitHub organization` shall contain precisely classes 1-4.
* All code in the `openedx GitHub organization` is subject the decisions made in OEPs.
* The Open edX Named Release shall include classes 2-4.
* The *Core Product Offering*, as defined by the Product Working Group, shall be supported by the code in classes 2-3.
* The *Exteneded Product Offering*, as defined by the Product Working Group, shall be supported by the code in classes 2-4.

.. _openedx GitHub organization: https://github.com/openedx


Motivation
**********

The Open edX project is comprised of nearly two hundred repositories that, together, contain millions of lines of code.
Each repository increases the effort required to maintain the project and the cognitive load required to understand the project.


Specification
*************

.. The specification describes the technical details of the Architecture, Best
.. Practice or Process proposed by the OEP. If the proposal includes a new API,
.. specify its syntax and semantics.

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
