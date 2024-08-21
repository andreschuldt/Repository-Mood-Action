![Repository Mood](mood/mood.png)

# Repository-Mood-Action

This Project contains the GitHub Actions workflow to generate a repository mood image into the repository, which represents the current state of the project.

This image shows a house which design is dependend on certain project metadata. Lines of code will determine the overall size and number of contributors will increase the number of living creatures surrounding it. The number of vulnerabilities inside of the project determines the state the house is in. A high vulnerability to dependency ration results in a chaotic or even destroyed house.


# Integrating into a project
  
  1. Allow GitHub Actions: Settings > Actions > Actions permissions > check "Allow all actions and reusable workflows"
  2. Enabling workflow write permissions: Settings > Actions > General > Workflow permissions > check "Read and write permissions".
  3. Creating repository Secrets: Settings > Secrets and Variables > Actions > click "New repository Secret" and enter the values for the secrets ```RUNPOD_ENDPOINT``` and ```RUNPOD_TOKEN``` accordingly.
  4. Create a new directory called ```mood``` inside of the project's root. This is where the image will be located once finished generating.
  5. Reference the mood image inside of the README.md with ```![Repository Mood](mood/mood.png)``` at the desired location.
  6. Finally, create a ```.github/workflows/use-rmig.yml``` file that calls this project's action inside your project:
```
Name: Use RMIG Workflow

on:
  workflow_dispatch:

jobs:
  call-rmig-workflow:
    uses: andreschuldt/Repository-Mood-Action/.github/workflows/rmig.yml@main
    with:
      ref: ${{ github.ref }}
    secrets:
      runpod_token: ${{ secrets.RUNPOD_TOKEN }}
      runpod_endpoint: ${{ secrets.RUNPOD_ENDPOINT }}
      github_accesstoken: ${{ secrets.GITHUB_TOKEN }}
```
# Changing workflow trigger

instead of triggering the rmig manually in the actions menu of the repository with
```
on:
  workflow_dispatch:
```
you can call it automatically via push on a desired branch like

```
on:
  push:
    branches:
      - main
      - master
      - develop
```




