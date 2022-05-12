# Artifacts for the EPIT paper submission

*Incomplete. Will be updated with more data and explanations!*

## Obtaining raw experimental data

Please find our anonymized data from [here](https://github.com/EpitPaper/main/releases/tag/ase2022). Please note that although we have tried our best to anonymize our data, it could still be possible to find the author(s)' identity by digging deep into the data.

## Organization of data

Each file corresponds to a parallel run, with filename in the format of `{tool_id}-{app_id}-{run_id}.7z`, where `tool_id` can be any of `monkey`, `ape`, and `wctester`, while `run_id` can be any of `b`, `pM`, and `pW`, corresponding to a baseline run, a machine-time constrained parallel run, and a wait-time constrained parallel run.

Each 7zip file contains several folders. If a folder's name contains a number (e.g., `monkey-quizlet-pMr2`), the folder corresponds to a partial run. If not (e.g., `monkey-quizlet-pM`), the folder contains meta information regarding the parallel run.

## Format of partial run data

The meanings of files are as follows (taken from [VET's repository](https://github.com/VET-UI-Testing/main) given that we re-used their infrastructure),

- `./{TIMESTAMP}.json` represents the full UI hierarchy of each screen in the trace. Within each file:
  - Each JSON object is a UI element. Child elements are stored as JSON arrays in the `ch` field.
  - The UI element that the tool acts on is marked with `is_source: true`. Note that it is possible to act without involving any UI element (e.g., pressing Back on the device).
  - `act_id` denotes Activity ID.
  - `ua_type` denotes what kind of action triggers TOLLER to record this step. The values have the following meanings:
    * 0: short click
    * 1: long click
    * 2: touch
    * 3: context click
    * 7: menu click
    * 100: back
  - `en`: whether the UI element is enabled.
  - `vclk`, `vlclk`, `vcclk`: class names of short click handlers, long click handlers, and context click handlers, respectively. If one field is not present for some object, the corresponding UI element does not respond to the corresponding event.
  - `bound`: UI element boundary.
  - `class`: Class name of the type of the UI element.
  - `ucls`: Unified class name, must be a super class of `android.view.View`, either starts with `android.widget.` or is `android.webkit.WebView`. Might not exist in some cases.
  - `id`: Resolved resource ID in strings if the UI element has one.
  - `idn`: Resource ID in numbers, `-1` if the UI element does not have an associated resource ID.
  - `hash`: Internal unique representation of the object supporting the corresponding UI element in the app's internal UI data structures.
- `./crash.log`: Logcat entries that capture the app's crash logs.
- `./tool.log`: logs produced by the testing tool.
- `./minitrace/cov-{TIMESTAMP}.log`: Coverage information produced by [MiniTrace](http://gutianxiao.com/ape/install-mini-tracing) throughout the test run.

## Format of parallel run meta data


