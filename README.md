<h1 align="center">Add flat channel</h1>

<p align="center">
  Add a flat channel to a mne/raw file. This helps add a missing channel before concatenation.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.856"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.856-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-see_LICENSE-lightgrey.svg" alt="License"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Add a flat channel to a mne/raw file. This helps add a missing channel before concatenation.**

Creates a zero-valued channel with the given name and type at the recording's sampling rate, appends it to the raw MEG/EEG data with raw.add_channels, and saves the result with an HTML report listing the channels. Use it to add a missing stimulus or placeholder channel so that recordings can be concatenated or share the same channel layout. The new channel contains no signal.

| | |
|---|---|
| **Inputs** | `neuro/meeg/mne/raw` |
| **Outputs** | `neuro/meeg/mne/raw` |
| **Container** | `brainlifemeeg/mne:1.12.1` |
| **Resources** | 1 CPUs · 10 GB memory · 2 h walltime |
| **Run it** | [doi.org/10.25663/brainlife.app.856](https://doi.org/10.25663/brainlife.app.856) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `raw0` | `neuro/meeg/mne/raw` | yes | Continuous MEG/EEG recording in MNE raw .fif format. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `out_dir` | `neuro/meeg/mne/raw` | Raw data (raw.fif) with the added flat channel. |

<details>
<summary><b>Parameters</b> (2)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `ch_name` | string |  | Name of the channel to add. |
| `ch_type` | string |  | Type of the channel to add. |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.856](https://doi.org/10.25663/brainlife.app.856), choose `neuro/meeg/mne/raw` from your project, set the parameters and press **Execute**. The results are saved to your project as `neuro/meeg/mne/raw`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlifemeeg/mne:1.12.1`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "raw": "/path/to/raw0/raw",
       "ch_name": "",
       "ch_type": ""
   }
   ```

3. Run `./main`.

## Configuration Parameters

| key | type | default | description |
|---|---|---|---|
| `ch_name` | string | required | Name for the new flat channel (e.g. `"STI 014"`). |
| `ch_type` | string | required | Type of the new channel, passed to `mne.create_info()` (e.g. `stim`, `misc`, `eeg`, `meg`). |

## Local Testing

```bash
# Edit config.json with your own input file and channel name/type, then run:
python3 main.py
```

## Technical Details

- **Execution**: Python with MNE-Python and the shared `brainlife_utils` library
- **Data format**: MNE `.fif` format (compatible with all downstream Brainlife.io apps)
- **Channel addition**: Uses `mne.create_info()` and `raw.add_channels()` for consistent channel handling
- **Report generation**: Automatic HTML report with channel visualization

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- Add flat channel. brainlife.io App. [doi:10.25663/brainlife.app.856](https://doi.org/10.25663/brainlife.app.856)
- Gramfort et al. MEG and EEG data analysis with MNE-Python. *Frontiers in Neuroscience* 7 (2013). [doi:10.3389/fnins.2013.00267](https://doi.org/10.3389/fnins.2013.00267)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

- [Kami Salibayeva](https://github.com/KSalibay) (Indiana University)
- [Maximilien Chaumon](https://github.com/dnacombo), Paris Brain Institute

## Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io, which runs this App, is publicly funded by Wellcome, the U.S. National Institutes of Health and the U.S. National Science Foundation; acknowledging that support helps keep it running.</sub>

## License

See [LICENSE](LICENSE).
