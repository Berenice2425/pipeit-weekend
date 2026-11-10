# PipeIt Weekend: my CI/CD pipeline

![pipeline](https://github.com/berenice2425/pipeit-weekend/actions/workflows/pipeline.yml/badge.svg) 

<img width="104" height="94" alt="{94314FDB-1CEF-4917-8F71-B8FF74432D40}" src="https://github.com/user-attachments/assets/c18c278d-5174-4acc-8140-4bbbb6daa0e9" />

**Live site:**  https://Berenice2425.github.io/pipeit-weekend/

A CI/CD pipeline I built with GitHub Actions during PipeIt Weekend by SKILL.SCH. 
Every change I push is tested, a web page is built by **my own custom GitHub Action**, and the result is published to GitHub Pages automatically. It also rebuilds itself every morning on a schedule. 

## How it works
``` push to main / daily schedule / Run workflow button | v test -> bash tests/check.sh (fails the pipeline if something is wrong) | v build -> my action: .github/actions/build-card (makes site/index.html) | v deploy -> GitHub Pages (the live site above) ```


<img width="888" height="336" alt="{44CEF8E1-1721-48C4-B14B-1FF910EE66B4}" src="https://github.com/user-attachments/assets/4438c54c-5721-44cb-af40-f1f57b513934" />


## What is in this repo 
| File | What it does |
|------|--------------| 
| `.github/workflows/hello.yml` | My first workflow: prints a message on every push |
| `.github/workflows/ci.yml` | Runs my test on every push and pull request | 
| `.github/workflows/pipeline.yml` | Test, build with my action, deploy to GitHub Pages | 
| `.github/actions/build-card/action.yml` | My custom action: builds the status page |
| `tests/check.sh` | My test: checks this README has a title | 



<img width="913" height="385" alt="{BB8EB166-42B6-46EC-9C8F-DA8A65265573}" src="https://github.com/user-attachments/assets/51d06837-5483-40eb-87e3-30f6b3bd543f" />


## My custom action `build-card` is a composite action.
It takes two inputs, `name` (required) and `message` (optional), writes `site/index.html` with the run number, commit and time, and adds a summary to the run page. 

```yaml - uses: ./.github/actions/build-card with: name: Your Name message: Built automatically by my own GitHub Action ``` 


## What I learned 
- Workflows live in `.github/workflows` and run on triggers: push, pull_request, schedule and workflow_dispatch.
- `needs:` makes jobs run in order, so a failing test stops a broken site going live.
- How to write and reuse my own action with inputs and outputs.
- How to read a red run's log and fix it. ## What I would add next
- [ ] Run the checks on pull requests only and protect the main branch
- [ ] Add a second test
- [ ] Publish my action so other repos can use it

 ## About 
 Built by Berenice during [PipeIt Weekend](https://skill-sch.com/pipeit) by SKILL.SCH.

<img width="359" height="330" alt="{094B25C2-AC25-4BD2-9636-1DC2CC5E845A}" src="https://github.com/user-attachments/assets/3fdf4e5e-ff69-4f60-b1c8-caedbe1af4f3" />
