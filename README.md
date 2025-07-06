# Spectral Unmixing

A notebook to correct spectral bleedthrough in images obtained from the Odyssey M imaging system. The default values correct spectral overlap between mScarlet3 (520 channel) and EGFP (488 channel).

<a href="https://colab.research.google.com/github/lariferg/spectral_unmixing/blob/main/spectral_unmixing.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

### Instructions

1.  **Open in Colab** using the button above.

2.  **Edit bleedthrough values.** In the first code cell, change `RG` and `GR` to your experimentally measured values.
    ```python
    RG = 0.00942703 # Red-into-Green
    GR = 0.11317624 # Green-into-Red
    ```

3.  **Update file paths.** Upload your images to the Colab session (drag-and-drop into the file pane on the left) and update the file paths in the fourth code cell.
    ```python
    image_green, filename_green = load_tif_keep_name('/content/your_green_image.TIF')
    image_red, filename_red = load_tif_keep_name('/content/your_red_image.TIF')
    ```

4.  **Run all cells.** The corrected images will be saved in your Colab session files with an `_unmixed.TIF` suffix. Download them before the session ends.

### Citation

This method was used for image analysis in:

> Lim, T. K. Y., et al. (2025). "Cap-independent co-expression of dsRNA-sensing and NF-κB pathway inhibitors enables tunable self-amplifying RNA expression with reduced immunotoxicity." *bioRxiv*, 2024.09.24.614636. doi: [10.1101/2024.09.24.614636](https://doi.org/10.1101/2024.09.24.614636).
