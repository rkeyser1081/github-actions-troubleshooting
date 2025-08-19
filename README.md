# GitHub Actions Troubleshooting Challenge

<img src="https://img.ifunny.co/images/350fbba1526b08f0176f86dd945a9362ff8385f680b0cb32c29209958912ebc7_1.jpg" width="400">

**Goal:** Fork a repo that’s intentionally broken and make its GitHub Actions workflow run **green** (no errors).

## What you’ll do
1. Fork the starter repo.
2. Trigger the workflow and see it **fail** (or not run).
3. Find and fix **each issue** until the workflow passes.

## How to Fork a Repository
1. Click **Fork** in the top-right of this repo.
0. Choose your account and finalize the fork.
0. In **your fork**, go to `Settings → Actions` and ensure Actions are **enabled** (usually enabled by default).

## Your mission:
- Get the workflow file working.
- Make the **test pass**.

## Verify your progress
- Go to the **Actions** tab in your fork.
- If nothing ran, push a small change (edit README) to `main` or click `Run workflow` if available.
- You’re done when the latest run is green.

## Hints (click to expand)

<details>
  <summary>Hint 1: Why isn’t any workflow running?</summary>

  Workflows only execute if the file is in the exact path GitHub expects.

  <details>
    <summary>Solution</summary>

Move the file from:
```

.github/flowworks/microservice.yml

```
to:
```

.github/workflows/microservice.yml

````
Commit the change on **main**, then check the **Actions** tab again.
  </details>
</details>

<details>
  <summary>Hint 2: The first step in the job fails immediately.</summary>

  The checkout step references a non-existent action version.

  <details>
    <summary>Solution</summary>

Open `.github/workflows/microservice.yml` and fix:
```yaml
- name: Checkout code
  uses: actions/checkout@v4
````

(Replace `@vfour` or other wrong value with `@v4`.)

  </details>
</details>

<details>
  <summary>Hint 3: “Tests are failing in pytest.”</summary>

There’s a single dummy test that fails by design.

  <details>
    <summary>Solution</summary>

Edit `tests/test_example.py` to make the assertion pass:

```python
def test_dummy():
    assert 1 == 1
```

Commit and push. Re-check the **Actions** run; it should be green now.

  </details>
</details>

---

## Expected end state

* Workflow file lives at `.github/workflows/microservice.yml`.
* `actions/checkout` uses a valid version (`@v4`).
* The test in `tests/test_example.py` passes.
* Latest run in the **Actions** tab shows **Passed** ✅
