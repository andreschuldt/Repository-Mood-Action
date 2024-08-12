# Repository-Mood-Action

This Project contains the GitHub Actions workflow to generate a repository mood image into the repository, which represents the current state of the project.
This image shows a house which design is dependend on certain project metadata. Lines of code will determine the overall size and number of contributors will increase the number of living creatures surrounding it. The number of vulnerabilities inside of the project determines the state the house is in. A high vulnerability to dependency ration results in a chaotic or even destroyed house.


# Integrating into a project

  1. Enabling workflow write permissions: Settings > Actions > General > Workflow permissions > check "read and write permissions"
  2. Creating repository Secrets: Settings > Secrets and Variables > Actions > click "New repository Secret" and enter the values for the secrets ```RUNPOD_ENDPOINT``` and ```RUNPOD_TOKEN``` accordingly.
  3. Create a new directory called ```mood``` inside of the project's root. This is where the image will be located once finished generating.
  4. Reference image inside if the README.md with ```![Repository Mood](mood/mood.png)``` at the desired location.
