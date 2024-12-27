# Software Engineering at Google

https://arxiv.org/ftp/arxiv/papers/1702/1702.01715.pdf

We catalog and describe Google’s key software engineering practices.

The Source Repository:

* Most of Google’s code is stored in a single unified source-code repository, and is accessible to all engineers.

* Almost all development occurs at the “head” of the repository, not on branches.

* Automated systems run tests frequently.

* Code trees have owners, and any changes to code in the tree must be approved by an owner.

The Build System:

* Individual build steps must be “hermetic”: they depend only on their declared inputs.

* Individual build steps are deterministic, thus results are cacheable “in the cloud”, and rebuilds are fast.

* Each subtree can have presubmit checks.

Code Review:

* Google has built excellent web-based code review tools.​

* All changes to the main source code repository MUST be reviewed by at least one other engineer.

* Code review discussions for each project are automatically copied to a project mailing list.

* There is an “experimental” section of the repository where the normal code review requirements are not enforced.

* Engineers are encouraged to keep each individual change small.

* Larger challenges are preferably broken into smaller changes that can easily be reviewed in one go.

Testing:

* Unit testing is strongly encouraged and widely practiced.

* Integration testing and regression testing are also widely practiced.

* Presubmit Checks can be automatically enforced as part of the code review and commit process.

* Load testing prior to deployment is also de rigueur at Google.

* Google has automated tools for measuring test coverage.

Bug tracking:

* We track bugs, feature requests, customer issues, and processes (such as releases or clean-up efforts).
