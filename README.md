Environment of MEC_53614 (*Artificial intelligence for solids and structures*, École polytechnique).

The dependencies are listed once, in `environment.yml`; only the way the course library `LIB53614` is installed differs:

| Case | Install | `LIB53614` |
|---|---|---|
| Students: Docker image (JupyterHub), Binder, local conda | the image built by the workflow, or `conda env create -f environment.yml` | from GitHub (pip line of `environment.yml`) |
| Students: Colab | uncomment the `!pip install git+https://github.com/mgenet/LIB53614.git` line of the notebook's first code cell (numpy, scipy, matplotlib and scikit-learn are preinstalled on Colab) | from GitHub |
| Teacher (development) | `conda env create -f environment.yml -n MEC53614-2026-dev`, `conda activate MEC53614-2026-dev`, then `pip install -e ../LIB53614` | the local clone, in editable mode: it replaces the GitHub version, and changes are visible immediately (with `%autoreload 2` in the notebooks) |

* In every case, the exercise zips (`NOTEBOOKS-Subjects/En.zip`) also contain a copy of `LIB53614`, which takes precedence when a notebook is run from its unzipped folder.
* `environment.yml` is always the current session's environment (repo2docker/Binder use it); previous sessions are tagged (e.g., `env-2026`).
* The GitHub Actions workflow (`.github/workflows/build_docker.yml`, same as in N-DEG-paper-demos) builds the Docker image with `jupyterhub/repo2docker-action`, pushes it to the GitHub Container Registry, as `ghcr.io/<actor>/<repository>` (lowercase), tagged `latest` and with the commit SHA, and checks that the main packages and `LIB53614` import. The package is private on its first push: make it public once (package settings, "Change visibility") so that the JupyterHub or students can pull it without credentials.
