# iac-flux-keda
Flux Configuration for Keda

## Developer Guide
This flux configuration will be created by the [Core LSCSDE Helm Chart](../../helm/lscsde-flux/), which in turn is called by the [Core LSCSDE Flux configuration](../lscsde/)

When the main branch of this repository is created it will trigger a github action which will:
* Calculate a semver version number
* Create a release branch with the semver version
* Update the submodules on the main repository
* Update the keda_branch value on the core [lscsde flux configuration](../lscsde)

This will in turn trigger github actions that will propagate those changes up the chain