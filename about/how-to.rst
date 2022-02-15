About Artifact Expressions
================================

How to Use This Guide
~~~~~~~~~~~~~~~~~~~~

The CIS Artifact Expressions documentation is a guide for creating Artifacts during benchmark customization. The documentation is organized by family and broken down by Artifact Types.
This guide will walk you through forking a benchmark and adding a custom recommendation in Workbench using this documentation.

Creating a Recommendation
=========================

1. Navigate to the benchmark you would like to use.

2. In order to make changes to a published benchmark, you must first fork it. Click the ‘Fork’ button.

.. image:: ArtifactExpressions/images/forkBenchmark.png
  :width: 700
  :alt: Alternative text

3. Fill out the required fields.

.. image:: ArtifactExpressions/images/forkFields.png
  :width: 700
  :alt: Alternative text

.. image:: ArtifactExpressions/images/forkContinued.png
  :width: 700
  :alt: Alternative text

4. When you’re finished, click ‘Submit’.

.. image:: ArtifactExpressions/images/submitFork.png
  :width: 700
  :alt: Alternative text

5. The left pane lists all of the ‘Sections’ of the benchmark. Each recommendation is nested in a particular Section. Use these sections to determine where to place your recommendation. In this example, we are going to create a recommendation that prohibits a user from using the same password more than once. Therefore, we are going to place it in the System Access, Authentication and Authorization > Password Management section.

.. image:: ArtifactExpressions/images/leftPane.png
  :width: 700
  :alt: Alternative text

6. Click ‘Password Management’.

.. image:: ArtifactExpressions/images/passwordMenuItem.png
  :width: 700
  :alt: Alternative text

7. Scroll down until you see ‘Recommendations’.

.. image:: ArtifactExpressions/images/passwordManagementPage.png
  :width: 700
  :alt: Alternative text

.. image:: ArtifactExpressions/images/passwordRecommendations.png
  :width: 700
  :alt: Alternative text

8. Click ‘Add New’.

.. image:: ArtifactExpressions/images/addNewRec.png
  :width: 700
  :alt: Alternative text

9. Click ‘+Artifact’.

.. image:: ArtifactExpressions/images/addArtifact.png
  :width: 700
  :alt: Alternative text

10. Choose the artifact type you wish to use from the dropdown menu.

.. image:: ArtifactExpressions/images/artifactDrop.png
  :width: 700
  :alt: Alternative text

11. Choose the test type you wish to use. If the artifact type is linked to only one test type, you have only one test type to choose from.

.. image:: ArtifactExpressions/images/testTypeDrop.png
  :width: 700
  :alt: Alternative text

12. Fill in the required fields. Make sure you set ‘Assessment Status’ to ‘Automated’. NOTE: If you would like this Recommendation to be excluded from the CIS-CAT Assessor Tool, set ‘Assessment Status’ to ‘Manual’.

.. image:: ArtifactExpressions/images/assessmentStatus.png
  :width: 700
  :alt: Alternative text

13. Next, you must add an Artifact Equation. The purpose of the Artifact Equation is twofold: 1) To determine the All Pass All Fail result of the Recommendation in the CIS-CAT Assessor 2) To tell Workbench how multiple artifacts should be evaluated (together?). The artifact equation is a logical statement consisting of AND, OR, and a number. The number references the artifact. This number can be found in the top left corner of the artifact. See the image below.

.. image:: ArtifactExpressions/images/artifactNumber.png
  :width: 700
  :alt: Alternative text

In this case, our artifact equation is simply ‘1’. AND(1) would also be acceptable.

.. image:: ArtifactExpressions/images/artifactEquation.png
  :width: 700
  :alt: Alternative text

If you wanted to add another artifact (and have it evaluated with the first artifact) to the export, the equation would be AND(1,2). If you would like the two artifacts to be evaluated separately, the equation would be OR(1,2). NOTE: Be careful when constructing the artifact equation. An incorrect or incomplete artifact equation will cause the benchmark export to fail. Some common examples of an incorrect or incomplete artifact equation include missing a parenthesis or referencing an artifact that does not exist in the recommendation (for example, AND(1,3) would fail if there were only two artifacts in the recommendation).

.. image:: ArtifactExpressions/images/secondArtifactEquation.png
  :width: 700
  :alt: Alternative text

14. When you’re finished, click ‘Submit’.

.. image:: ArtifactExpressions/images/submitRec.png
  :width: 700
  :alt: Alternative text

15. Your recommendation is now included in the benchmark.

.. image:: ArtifactExpressions/images/mustUseUniqueSection.png
  :width: 700
  :alt: Alternative text

16. Scroll down to view the artifact(s)' details at a glance.

.. image:: ArtifactExpressions/images/mustArtifactButton.png
  :width: 700
  :alt: Alternative text

.. image:: ArtifactExpressions/images/artifactDetailsGlance.png
  :width: 700
  :alt: Alternative text





