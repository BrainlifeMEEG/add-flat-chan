# Add Flat Channel to MNE Raw Data

[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.856-blue.svg)](https://doi.org/10.25663/brainlife.app.856)

## Description

Adds an artificial flat (zero-valued) channel to an MNE raw `.fif` file, using `mne.create_info()` to build the new channel and `raw.add_channels()` to merge it into the recording. This is useful for:
- Adding a stimulus/trigger channel that was not originally recorded
- Standardizing channel layouts across datasets by adding placeholder channels
- Preparing data for analyses that require specific channel configurations

The app generates:
- An updated raw `.fif` file with the new flat channel added
- An HTML QC report with a raw data summary and the updated channel list
- A `product.json` summary for the Brainlife.io interface

## Inputs

- **`raw`** (`neuro/meeg/mne/raw`): continuous MNE raw data to which the flat channel will be added (required)

## Outputs

- **out_dir/raw.fif** (`neuro/meeg/mne/raw`): raw data with the new flat channel added
- **out_report/report.html**: QC report containing a raw data summary and the updated channel list
- **product.json**: metadata summarizing the added channel and raw info

## Configuration Parameters

| key | type | default | description |
|---|---|---|---|
| `ch_name` | string | required | Name for the new flat channel (e.g. `"STI 014"`). |
| `ch_type` | string | required | Type of the new channel, passed to `mne.create_info()` (e.g. `stim`, `misc`, `eeg`, `meg`). |

## Usage

### Running on Brainlife.io

1. Go to the [Add flat channel app page](https://brainlife.io/app/856) on Brainlife.io.
2. Select your project and the raw `.fif` file as input.
3. Set `ch_name` and `ch_type` for the channel to add.
4. Submit the process, then download `out_dir/raw.fif` and `out_report/report.html` once it completes.

### Local Testing

```bash
# Edit config.json with your own input file and channel name/type, then run:
python3 main.py
```

## Technical Details

- **Execution**: Python with MNE-Python and the shared `brainlife_utils` library
- **Data format**: MNE `.fif` format (compatible with all downstream Brainlife.io apps)
- **Channel addition**: Uses `mne.create_info()` and `raw.add_channels()` for consistent channel handling
- **Report generation**: Automatic HTML report with channel visualization

## Authors

- [Kami Salibayeva](https://github.com/KSalibay) (Indiana University)
- [Maximilien Chaumon](https://github.com/dnacombo), Paris Brain Institute

## Citations

We kindly ask that you cite the following articles when publishing papers and code using this app:

Hayashi, S., Caron, B.A., Heinsfeld, A.S. et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. Nat Methods 21, 809–813 (2024). https://doi.org/10.1038/s41592-024-02237-2

Gramfort, A. et al. MEG and EEG data analysis with MNE-Python. Front. Neurosci. 7, 267 (2013). https://doi.org/10.3389/fnins.2013.00267

## Funding Acknowledgement

brainlife.io is publicly funded and for the sustainability of the project we kindly ask that you acknowledge the following funding sources:

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://grantome.com/grant/NIH/R01-EB030896-01)

## License

Copyright (c) 2026 MEEG Brainlife team. Licensed under AGPL-3.0, see [license.txt](license.txt).
