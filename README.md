# Spectral Unmixing for Odyssey M

This repository contains a colab notebook to correct spectral bleed-through (crosstalk) in multi-channel fluorescence well scan images using linear unmixing. This code was developed for images acquired on an Odyssey M imaging system but can be adapted for other systems.

The default values in the notebook are configured to correct spectral overlap between mScarlet3 (detected in the 520 nm channel) and EGFP (detected in the 488 nm channel), as described in our publication.

<a href="https://colab.research.google.com/github/lariferg/spectral_unmixing/blob/main/spectral_unmixing.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

### Instructions
Before you can unmix your experimental images, you must calculate the bleed-through coefficients using single-color control samples.

1. **Acquire Control Scans.** Scan wells containing samples expressing only EGFP and samples expressing only mScarlet3. Capture images in both the 488 nm and 520 nm channels for each control.

2. **Calculate Bleed-through.** Use the control scans to measure the percentage of EGFP signal that appears in the 520 nm channel, and the percentage of mScarlet3 signal that appears in the 488 nm channel.

3. **Update the notebook** Open the `spectral_unmixing.ipynb` notebook and update the spillover values with your calculated coefficients. The default values are set based on our experiments:  
   EGFP bleed-through into 520 channel: **11.32%**  
   mScarlet3 bleed-through into 488 channel: **0.94%**

4.  **Update file paths.** Upload your images to the Colab session (drag-and-drop into the file pane on the left) and update the file paths in the fourth code cell.
    ```python
    image_green, filename_green = load_tif_keep_name('/content/your_green_image.TIF')
    image_red, filename_red = load_tif_keep_name('/content/your_red_image.TIF')
    ```

5.  **Run all cells.** The corrected images will be saved in your Colab session files with an `_unmixed.TIF` suffix. Download them before the session ends.

### Citation

This method was used for image analysis in:

> Tony KY Lim, Anne Ritoux, Luke W Paine, Larissa Ferguson, Tawab Abdul, Laura J Grundy, Ewan St. John Smith (2025) Cap-independent co-expression of dsRNA-sensing and NF-κB pathway inhibitors enables tunable self-amplifying RNA expression with reduced immunotoxicity. eLife 14:RP105978
https://doi.org/10.7554/eLife.105978
