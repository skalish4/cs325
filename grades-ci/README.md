# CS 325 Quiz — Test Cases, Docker, CI

Part A test cases: [Part_A_Test_Cases.md](Part_A_Test_Cases.md). The Word document is in the submission ZIP.

Part B uses the five tests supplied in the quiz. The code is exactly the assignment's grading example. We add pytest-cov for the HTML coverage requirement.

## Local setup (Windows PowerShell)

```powershell
cd grades-ci
py -m pip install -r requirements.txt
py -m pytest -v
py -m pytest --cov=grades --cov-report=html:htmlcov
```

Open `htmlcov/index.html` in a browser.

## Docker

With Docker Desktop installed and running, from grades-ci:

```powershell
docker build -t grades-test:v1 .
docker run --rm grades-test:v1
```

## Docker Hub — still required for full assignment

Create a **public** Docker Hub repo named `grades-test`. Then (replace YOUR_DOCKERHUB_USERNAME):

```powershell
docker login
docker tag grades-test:v1 YOUR_DOCKERHUB_USERNAME/grades-test:v1
docker push YOUR_DOCKERHUB_USERNAME/grades-test:v1
```

In the GitHub repository Settings > Secrets and variables > Actions > Variables, add `DOCKERHUB_USERNAME` with your Docker Hub username. The workflow's `test-from-dockerhub` job will then run inside your published image. Until that variable exists, the job is intentionally skipped; the `local-tests-and-docker` job still validates code and builds/runs Docker.

## GitHub Actions

Open [Actions](https://github.com/skalish4/cs325/actions/workflows/grades-ci.yml). This workflow tests the five examples, uploads the HTML coverage report as the `html-coverage` artifact, and builds/runs the Docker image. Once Docker Hub is configured as above, a second job pulls the Docker Hub image.

To demonstrate CI detecting a bug, change `if score >= 90:` to `if score > 90:`, commit and push. Confirm **red**, then restore the condition and push again to confirm **green**. This is a demonstration of an intentional regression, not a bug to leave unfixed.

## Evidence to submit

1. Completed Part A form (Word file from ZIP, with any actual run results).
2. GitHub repository URL and screenshots of green/red/green Actions jobs.
3. Public Docker Hub image URL.
4. HTML coverage artifact from Actions or the bundled local htmlcov ZIP.

**Important:** The Project 1 acceptance tests are proposed, not executed: the matching app was not supplied. Docker Hub publishing requires access to your Docker Hub account.
