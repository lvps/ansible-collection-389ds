# Contributing

Role implementation changes should be made in the upstream role repository. This repository integrates released role revisions and owns collection metadata, packaging, documentation, and integration validation.

Before opening a pull request:

1. Run `git submodule update --init --recursive`.
2. Create and activate a virtual environment, then install the dependencies:

	python3 -m venv .venv
	. .venv/bin/activate
	python -m pip install --upgrade pip
	python -m pip install -r requirements.txt

3. Run the lint and collection build commands used by CI. If a command is not found, confirm that `.venv/bin` is active rather than installing tools system-wide.
4. Confirm that the submodule pointers reference released upstream tags.

Collection releases are created from a GitHub release whose tag matches the version in `galaxy.yml`.