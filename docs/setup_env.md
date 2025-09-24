# Setup `uv` and Install Dependencies

This section will guide you through setting up your development environment with [`uv`](https://github.com/astral-sh/uv), a modern Python package and project manager that serves as a faster and more reliable alternative to `pip` and `venv`.  

Unlike `pip`, `uv` integrates environment management and dependency resolution, which makes it easier to work with projects that have complex requirements.

---

### 1. Clone the Repository
Before starting, ensure you have [`git`](https://git-scm.com/) installed and configured on your system.  
Clone the project repository locally:

```bash
git clone <repository-url>
cd <repository-name>
```

### 2. Install uv and Set Up the Virtual Environment

First, install uv using pip:

```bash
pip install uv
```

Next, use uv to install the required Python version for this project.
Here we’ll use Python 3.12:

```bash
uv python install 3.12
```

Now create a virtual environment using the installed Python version:

```bash
uv venv --python=3.12
```

Finally, activate the environment:

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

With the environment active, install the project dependencies.

Synchronize all requirements defined in the project’s configuration (e.g., pyproject.toml or requirements.txt):

```bash
uv sync
```

Install `gymnasium-robotics` manually to avoid known versioning conflicts with mujoco-py:

```bash
uv pip install "gymnasium-robotics[mujoco-py]==1.4"
```

`gymnasium-robotics` is a collection of simulated robotics environments built on top of the Gymnasium API and maintained by the [Farama Foundation](https://farama.org/). Its key features include: 

+ Simulated robotic tasks: Includes tasks like reaching, pushing, sliding, and pick-and-place, using robot arms such as the “Fetch” arm, or dexterous hands. 

+ Multi-goal environments: The environments often have goal-based structure: observations include “current state,” “desired goal,” and “achieved goal.” This setup allows use of techniques like Hindsight Experience Replay. 

+ Physics engine: Uses MuJoCo (or its maintained python bindings) for physics simulation. 

+ Flexible and research-friendly: Environments are configurable, support rendering, resetting, termination, etc., following Gymnasium conventions. They allow both experimentation and benchmarking. 

Install the project itself in editable mode, so changes to the source code are reflected without reinstallation:

```bash
uv pip install -e .
```

✅ After completing these steps, your environment will be ready with all necessary dependencies installed and configured.