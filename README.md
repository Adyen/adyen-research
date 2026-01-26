# adyen-research

This repository serves as a centralized hub for Adyen's internal research materials, providing the academic and professional research community with the resources necessary to understand, replicate, and build upon our findings in Software Engineering research. 

The repository contains **experimentation replication packages**, including anonymized datasets (when possible), analysis scripts, and detailed methodological documentation. It bridges the gap between industrial practice and academic research by sharing the empirical evidence gathered from Adyen's unique ecosystem. Researchers can use this material to validate new theories on developer experience and more. 

## Contributing

We strongly encourage you to contribute to our repository. Find out more in our [contribution guidelines](https://github.com/Adyen/.github/blob/master/CONTRIBUTING.md).

## Requirements

Requirements depend on the specific replication package, but generally include:

* **Docker**: Recommended for ensuring a consistent environment for running analysis scripts and reproduction models.
* **Python 3.10+**: For standalone statistical analysis and data processing scripts.
* **Standard Data Science Stack**: Libraries such as `pandas`, `numpy`, and `scipy` for processing the provided CSV and JSON data exports.

## Installation

1. **Clone the repository:**
   
```bash
git clone https://github.com/Adyen/adyen-research.git
```

2. **Navigate to a specific research study directory:**
```bash
cd ase26
```


3. **Install study-specific dependencies:**
```bash
pip install -r requirements.txt
```

## Usage

Each subdirectory represents a unique research initiative. 


## Support

If you have a feature request, or spotted a bug or a technical problem, create a GitHub issue. For other questions, contact our Support Team via [Customer Area](https://ca-live.adyen.com/ca/ca/contactUs/support.shtml) or via email: support@adyen.com

## License

MIT license. For more information, see the LICENSE file.
