
# Model Training Optimizer

This module is designed to help users determine the optimal range of learning rates and batch sizes for training a deep learning model. By using a small sample of training data, the module provides an estimate of the best starting points for these hyperparameters, enabling more efficient training when scaling up to the full dataset.

### Image Considerations

The type of images you should use for training depends on the architecture of the model being employed. For example, in this module, the pre-trained ResNet-18 model is utilized, which has been trained on the ImageNet dataset. This means the images you use should generally match the characteristics of ImageNet images:

- **Image Size**: The model expects images of size 224x224 pixels. If your images are larger or smaller, they should be resized accordingly.
- **Color Images**: ResNet-18 is designed to work with RGB color images, so your images should be in color rather than grayscale.
- **Content**: The images should be representative of the task you are trying to solve. For example, if you're trying to classify different types of animals, your training data should include a variety of images with clear examples of each animal class.
- **Data Diversity**: Ensure that your dataset includes a diverse set of images, capturing different angles, lighting conditions, and variations in the subject matter. This helps the model generalize better to unseen data.

If you are using a different model architecture or pre-trained weights, similar considerations should be applied based on the model’s requirements. Always refer to the model's documentation for specific input requirements.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Command-Line Arguments](#command-line-arguments)
  - [Example Usage](#example-usage)
- [Required Data Directory Structure](#required-data-directory-structure)
- [File Descriptions](#file-descriptions)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Automatic Hyperparameter Tuning**: Automatically tests different combinations of learning rates and batch sizes to find the optimal settings.
- **Flexible Configuration**: Easily configurable via command-line arguments.
- **Comprehensive Reporting**: Provides detailed reports on the best model, including accuracy, batch size, and learning rate.
- **Customizable Data Directory Structure**: Supports custom directory structures for training and validation data.

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/wise_elm/model-training-optimizer.git
   ```

2. **Navigate to the project directory**:
   ```bash
   cd model-training-optimizer
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   Ensure that you have Python 3.6+ installed.

## Usage

### Command-Line Arguments

- `--data-path`: Path to the directory containing the training and validation data. Default is `image-data` in the script's directory.
- `--model-output-path`: Directory where the trained model will be saved. Default is `models` in the script's directory.
- `--batch-size`: Batch size for training. Default is `32`.
- `--learning-rate`: Learning rate for training. Default is `0.001`.
- `--epochs`: Number of epochs to train the model. Default is `10`.
- `--verbose`: Enable detailed logging during training and validation.
- `--info`: Print the module's docstring and exit.

### Example Usage

```bash
python model_optimizer.py --data-path /path/to/data --batch-size 32 --learning-rate 0.001 --epochs 10 --verbose
```

This command will train and validate models using the specified data, testing different combinations of batch sizes and learning rates, and print detailed output to the console.

## Required Data Directory Structure

The provided data directory must follow this structure for the module to function correctly:

```
data/
├── train/
│   ├── desired/
│   │   ├── <image1>  # Images classified as "desired" for training
│   │   └── ...
│   └── not_desired/
│       ├── <image2>  # Images classified as "not desired" for training
│       └── ...
└── validation/
    ├── desired/
    │   ├── <image3>  # Images classified as "desired" for validation
    │   └── ...
    └── not_desired/
        ├── <image4>  # Images classified as "not desired" for validation
        └── ...
```

- `train/desired/`: Directory containing images for training that are classified as "desired".
- `train/not_desired/`: Directory containing images for training that are classified as "not desired".
- `validation/desired/`: Directory containing images for validation that are classified as "desired".
- `validation/not_desired/`: Directory containing images for validation that are classified as "not desired".

Ensure that each directory contains the appropriate images for training and validation. The module expects this structure to correctly load and process the datasets.

## File Descriptions

- **`model_optimizer.py`**: The main script that performs model training optimization by testing different combinations of hyperparameters.
- **`requirements.txt`**: Lists the Python packages required to run the script.
- **`README.md`**: Provides an overview of the module, its usage, and other relevant information.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/YourFeature`)
3. Commit your Changes (`git commit -m 'Add some YourFeature'`)
4. Push to the Branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact

For any inquiries or issues, please contact:

Graham Steeds  
Email: steeds.g@gmail.com  
GitHub: [github.com/wise-elm](https://github.com/wise-elm)
