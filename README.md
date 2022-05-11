# Artifacts for the EPIT paper submission

Please find our anonymized traces from [here](https://github.com/EpitPaper/main/releases/tag/ase2022).

Each filename is in `{tool_id}-{app_id}-{run_id}.7z`, where `tool_id` can be any of `monkey`, `ape`, and `wctester`, while `run_id` can be any of `b`, `pM`, and `pW`, corresponding to a baseline run, a machine-time constrained parallel run, and a wait-time constrained parallel run.

Each 7zip file contains several folders. If a folder's name contains a number (e.g., `monkey-quizlet-pMr2`), the folder corresponds to a partial run. If not (e.g., `monkey-quizlet-pM`), the folder contains information regarding the parallel run.
