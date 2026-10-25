# XL Lora Trainer 2 mod
 [![GitHub](https://raw.githubusercontent.com/ViTa-Plane/Lora-Trainer-Colab/main/assets/github.svg)](https://github.com/ViTa-Plane/Lora-Trainer-Colab) [![Open in Colab](https://raw.githubusercontent.com/ViTa-Plane/Lora-Trainer-Colab/main/assets/colab-badge.svg)](https://colab.research.google.com/github/ViTa-Plane/Lora-Trainer-Colab/blob/main/Lora_Trainer_XL_2_mod.ipynb)

 A modification of Hollowstrawberry's [Lora Trainer XL](https://colab.research.google.com/github/hollowstrawberry/kohya-colab/blob/main/Lora_Trainer_XL.ipynb) with save state and resume patch.<p> Now you can recover after Google Colab disconnect , or push your LoRa training beyond 5h30m limit of the free colab tier.</p>

How to use this workflow:
  1. First-time training:
     - Run `Unzip dataset` and `custom_dataset (optional)` cells , then setup your `LoRa Trainer` cell and run it when ready. It won't find any states, so it will start fresh from Step 0, but it will secretly turn on your save_state settings.

  2. Resume after a disconnect:
     - Reconect to the runtime, run `custom_dataset (optional)` cell.
     - Don't change anything else in the trainer setup.
     - run the `LoRa Trainer` cell.
     - The patched script will instantly find your last saved checkpoint from Google Drive and inject the `--resume command`.

To extend your training, leave your dataset folders and repeat counts exactly as they were, run `custom_dataset (optional)` cell to set the dataset, and adjust these parameters before running `LoRa Trainer` cell:

  1. Increase Max Train Epochs: Change this to your new total target.

	 <i>Example: If your original run stopped at 10 epochs, and you want to train for 5 more epochs, set your new Max Train Epochs to 15.</i>

  2. Increase Max Train Steps (If used): If you explicitly set a maximum step count instead of using epochs, you must increase that number by your desired amount.

	    <i> Example: If your original run completed 2,000 steps, and you want 1,000 more, change Max Train Steps to 3000.</i>

The resumed state training is equal to one long continuous training , in contrast of 'continue from LoRa file' method in the original Hollowstrawberry's notebook.
