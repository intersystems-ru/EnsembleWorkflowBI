# EnsembleWorkflowBI
DeepSee Cube and sample dashboards for Ensemble Workflow.

## Installation

1. Import latest release or all XMLs (except from `Locale` folder) into any Ensemble enabled namespace.
2. Compile: `Do $system.OBJ.Compile("Workflow.Cube")`
3. Build cube: `Do ##class(%DeepSee.Utils).%BuildCube("WORKFLOW")`
4. (Optional) For localization call: `Do ##class(%MessageDictionary).ImportDir(dir)` where dir is a path to `Locale` folder.

## Development

Development is done via [Cache-Tort-Git](https://github.com/intersystems-ru/cache-tort-git).

## Localization development

Execute in a terminal to regenerate basic localization:

```
Kill ^CacheMsg("WORKFLOW") 
ZWrite ^CacheMsg("WORKFLOW")
Set $mvv(58)="en"
Set dir = "C:\temp\EnsembleWorkflowBI\Locale"
Do $system.OBJ.Compile("Workflow.Cube")
Do ##class(%MessageDictionary).ExportDomainList(dir _ "WORKFLOW_en.xml","WORKFLOW", "en")
Do ##class(%MessageDictionary).ExportDomainList(dir _ "WORKFLOW_ru.xml","WORKFLOW", "ru")
Do ##class(%MessageDictionary).ImportDir(dir)
```
