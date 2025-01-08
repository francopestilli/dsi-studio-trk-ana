# dsi-studio-trk-ana

This repository contains a script designed for the analysis of tractography data using [DSI Studio](http://dsi-studio.labsolver.org/). The script computes a range of tract properties, leveraging the computational capabilities of Singularity and Brainlife.io.

## Features
This app computes detailed tract properties, including:
- **Length**
- **Span**
- **Volume**
- **Diameter**
- **Surface Area**
- **Curl**
- **Elongation**
- **Irregularity**

The results are exported as structured statistics for further analysis.

### Author

    Gabriele Amorosino (gabriele.amorosino@utexas.edu)

## Usage

### Running on Brainlife.io

You can run the `dsi-studio-trk-ana` app on the Brainlife.io platform via the web user interface (UI) or using the Brainlife CLI. With both methods, inputs and outputs are managed on the Brainlife.io platform, and computations are performed using its cloud computing resources.

#### On Brainlife.io via UI

1. Navigate to the Brainlife.io platform and locate the `dsi-studio-trk-ana` app.
2. Click the "Execute" tab and specify the required dataset inputs.

#### On Brainlife.io using CLI

1. Install the Brainlife CLI on your UNIX/Linux-based system by following the instructions at [Brainlife CLI Installation](https://brainlife.io/docs/cli/install/).
2. Log in to the Brainlife CLI using your Brainlife.io credentials:
   ```bash
   bl login
   ```
3. Run the app using the following command:
   ```bash
   bl app run --id <app_id> --project <project_id> --input src:<src_object_id> --input track:<tt_object_id>
   ```
   The output will be stored in the specified project identified by `<project_id>`.

### Running Locally (on your machine)

Follow these steps to run the script locally on your machine:

1. Clone the repository:
   ```bash
   git clone https://github.com/gamorosino/dsi-studio-trk-ana.git
   cd dsi-studio-trk-ana
   ```

2. Create a `config.json` file in the repository directory, specifying the required input paths. Example:
   ```json
   {
       "src": "/path/to/source.src.gz.sz",
       "tt": "/path/to/tract.tt.gz"
   }
   ```

3. Run the script:
   ```bash
   ./main
   ```

   The script will:
   - Use DSI Studio via a Singularity container to analyze the tract file.
   - Export computed statistics to `stat/tractmeasure.tsv`.

#### Requirements
- **Singularity**: Ensure Singularity is installed and accessible.



## Outputs
- **Statistics**: The results of the analysis will be stored in `stat/tractmeasure.tsv`.

## Citation
If you use this app in your research, please cite the following:

- DSI Studio function:
  - Yeh, F. C. (2020). Shape analysis of the human association pathways. *Neuroimage, 223*, 117329. [doi:10.1016/j.neuroimage.2020.117329](https://doi.org/10.1016/j.neuroimage.2020.117329)

- Brainlife.io:
  - Hayashi, Soichi, et al. "brainlife.io: a decentralized and open-source cloud platform to support neuroscience research." *Nature methods, 21*(5), 809-813. (2024). [https://doi.org/10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)

