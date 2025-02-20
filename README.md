# Demo instructions

Please follow below instructions to run the trestle functions / demos. 

1. Create a folder on your local machine where you want to setup trestle workspace and download sample files for the demo.

2. `cd` to the directory.
3. Please follow the instructions to [install compliance trestle](https://oscal-compass.github.io/compliance-trestle/latest/installation/) on your local machine.
4. After installing trestle again run `source venv.trestle/bin/activate`

## Importing an OSCAL json catalog into trestle workspace and validating it

Below steps demonstrate how to import an external OSCAL catalog JSON file into trestle workspace.

1. Download [NIST 800-53 catalog file](https://github.com/butler54/devconf-demo/blob/main/data/NIST_SP-800-53_rev5_catalog.json) to `data` folder
2. From trestle workspace directory run ` trestle import -f ../data/NIST_SP-800-53_rev5_catalog.json -o NIST_800-53_v5`
3. The catalog would be imported into `trestle-workspace/catalogs/NIST_800-53_v5/catalog.json`
4. To validate the imported model run `trestle validate -t catalog -n NIST_800-53_v5` 

## Creating OSCAL Component Definition from CIS benchmarks

Below steps demonstrate how to convert a CIS benchmark into OSCAL Component Definition JSON.

1. Download snippet of [RHEL 9 CIS benchmarks file](https://github.com/butler54/devconf-demo/blob/main/data/CIS_Red_Hat_Enterprise_Linux_9_Benchmark_v1.0.0.xlsx) to `data` folder.
2. Also download the [config file](https://github.com/butler54/devconf-demo/blob/main/data/CIS_Red_Hat_Enterprise_Linux_9_Benchmark_v1.0.0.config) containing command line configuration options for executing the command to `data` folder.
3. From trestle workspace directory run `trestle task cis-xlsx-to-oscal-cd -c ../data/CIS_Red_Hat_Enterprise_Linux_9_Benchmark_v1.0.0.config`
4. The component definition would be created into `trestle.workspace/component-definitions/RHEL9-1_0_0/component-definition.json`

## Converting RHEL9 xccdf results to OSCAL assessment results

OpenSCAP tool is used to execute CIS benchmarks compliance checks for RHEL9. It generates the check results in an xccdf XML format. This can be converted to OSCAL assessment results format using the below instructions.

1. Create an `xccdf` folder in `data` folder. Download sample [RHEL 9 results xml file]https://github.com/butler54/devconf-demo/blob/main/data/xccdf/cis_rhel9_scan.xml) to `data/xccdf` folder.
2. Also download the the [config file](https://github.com/butler54/devconf-demo/blob/main/data/cis_rhel9_scan.config) containing command line configuration options for executing the command to `data` folder.
3. From trestle workspace directory run `trestle task xccdf-result-to-oscal-ar -c ../data/cis_rhel9_scan.config`
4. The OSCAL assessment result would be created into `trestle.workspace/assessment-results/cis_rhel9_scan.oscal.json`

