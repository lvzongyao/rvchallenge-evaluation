ACRV Robotic Vision Challenge 1 Evaluation Program
==================================================

Evaluation code for the ACRV Robotic Vision Challenge 1, see
https://competitions.codalab.org/competitions/19742

This is the code that will be used to evaluate all submissions.
For the starter kit, see:
https://github.com/jskinn/rvchallenge-starter-kit

Dependencies
------------

The code is written using Python 3.5, and requires the following additional modules, installed using pip:
- numpy
- scipy
- opencv

While not tested, it is also expected to work under python 2.7.

The docker image for all workers used to perform the evaluation can be found at
https://hub.docker.com/r/jskinn/rvchallenge-codalab-worker/

Structure
---------

This code is structured as a CodaLab scoring program.

The main method is contained in `evaluate.py`, which takes an input directory and output directory as command-line
arguments. The input directory must contain a submission in a folder called 'res', which is read by the submission
loader (`submission_loader.py`), and the ground truth information read by the ground truth loader (`gt_loader.py`).
The resulting intermediate objects are defined in `data_holders.py`,
and are passed to `pdq.py` to perform the evaluation.


Tests
-----

Unit tests are contained in the `tests` subdirectory.
Some of these tests (particularly the integration tests in `test_integration.py`)
will fail to run without access to the ground truth.


Probability-Based Detection Quality
-----------------------------------

The key metric used for this challenge is the probability-based detection quality (PDQ) measure
described in this paper: http://arxiv.org/abs/1811.10800, and explained in more detail on the competition page,
here:

https://competitions.codalab.org/competitions/20940#learn_the_details-evaluation

This metric is implemented in `pdq.py`
