
# IBANalyze: Simplifying IBAN Extraction from Images

IBANalyze is a powerful .NET 9 tool designed to automate the process of extracting and validating IBANs (International Bank Account Numbers) from images. By combining OCR (Optical Character Recognition), regex, and validation algorithms, it simplifies what was once a tedious and error-prone task.

---

## Table of Contents

1. [Features](#features)
2. [Supported Countries](#supported-countries)
3. [Tesseract Supported Languages](#tesseract-supported-languages)
4. [Installation](#installation)
5. [Usage](#usage)
   - [1. Configure the IBAN Extractor](#1-configure-the-iban-extractor)
   - [2. Extract IBANs](#2-extract-ibans)
6. [Testing](#testing)
7. [Contributing](#contributing)
8. [License](#license)
9. [About the Project](#about-the-project)
10. [Acknowledgments](#acknowledgments)

---

## Features

- **OCR-Based IBAN Extraction**: Automatically extracts IBANs from images using Tesseract OCR.
- **Error Correction**: Fixes common OCR mistakes, such as confusing "O" with "0".
- **IBAN Validation**: Validates extracted IBANs using country-specific rules and checksum calculations.
- **Simple Configuration**: Use a builder pattern to configure OCR settings and image paths effortlessly.
- **Extensive Unit Tests**: Over 90% test coverage ensures reliability and robustness.
- **.NET 9 Support**: Built with the latest .NET 9 features for enhanced performance and maintainability.

---

## Supported Countries

IBANalyze supports IBAN validation for the following countries:

- Turkey (TR)
- France (FR)
- Italy (IT)
- Spain (ES)
- Germany (DE)
- Netherlands (NL)
- Switzerland (CH)
- Belgium (BE)
- Austria (AT)
- United Kingdom (GB)

Additional countries can be added easily by extending the validation rules.

---


## Tesseract Supported Languages

This project supports English, Turkish, Italian, and German by default. If you want to use a different language, you must download the corresponding `.traineddata` file from the list below.

| **Lang Code** | **Language** | **Trained Data** |
|---------------|--------------|------------------|
| eng           | English      | [eng.traineddata](https://github.com/tesseract-ocr/tessdata/raw/4.00/eng.traineddata) |
| tur           | Turkish      | [tur.traineddata](https://github.com/tesseract-ocr/tessdata/raw/4.00/tur.traineddata) |
| ita           | Italian      | [ita.traineddata](https://github.com/tesseract-ocr/tessdata/raw/4.00/ita.traineddata) |
| deu           | German       | [deu.traineddata](https://github.com/tesseract-ocr/tessdata/raw/4.00/deu.traineddata) |

For a complete list of supported languages and trained data, visit the [Tesseract tessdata repository](https://github.com/tesseract-ocr/tessdata).

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/sametkayikci/IBANalyze.git
   cd IBANalyze
   ```

2. Ensure you have the following installed:
   - .NET 9 or higher
   - Tesseract OCR with the required `tessdata` files.

3. Restore dependencies and build the project:
   ```bash
   dotnet restore
   dotnet build
   ```

4. Run the tests:
   ```bash
   dotnet test
   ```

---

## Usage

### 1. Configure the IBAN Extractor

Set up the extractor using the builder pattern:

```csharp
var extractor = new IbanalyzeBuilder()
    .SetTessDataPath("./tessdata")
    .SetLanguage("eng+tur")
    .AddImages("invoice1.jpg", "invoice2.jpg")
    .RemoveSpaces(true)
    .Build();
```

### 2. Extract IBANs

Use the extractor to process the images and retrieve validated IBANs:

```csharp
var ibans = extractor.ExtractValidIbans();

foreach (var iban in ibans)
{
    Console.WriteLine($"Extracted IBAN: {iban}");
}
```

---

## Testing

IBANalyze includes a comprehensive suite of unit tests to ensure accuracy and robustness. Tests cover:

- Valid and invalid IBANs.
- Handling edge cases like null, empty, or excessively long IBANs.
- Correcting common OCR errors.

Run the tests with:
```bash
dotnet test
```

---

## Contributing

We welcome contributions! To contribute:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes and push:
   ```bash
   git commit -m "Add feature-name"
   git push origin feature-name
   ```
4. Submit a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## About the Project

IBANalyze was created to address a common pain point in financial workflows: extracting and validating IBANs from imperfect image data. By automating this process, IBANalyze saves time, reduces errors, and streamlines financial data processing.

For more information, visit the [GitHub repository](https://github.com/sametkayikci/IBANalyze).

---

## Acknowledgments

Special thanks to the open-source contributors and the Tesseract OCR community for providing the foundation for this project.

---

Happy coding! 🎉
