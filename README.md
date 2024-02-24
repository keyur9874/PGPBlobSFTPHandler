# PGPBlobSFTPHandler
----
# Azure Function for Processing PGP Files

This project contains an Azure Function designed to periodically check an Azure Blob Storage container for PGP encrypted files, decrypt them using a key stored in Azure Key Vault, manipulate the file contents, and then upload the result to an SFTP server.

## Features

- Timer-triggered Azure Function that runs every 5 minutes.
- Integration with Azure Blob Storage to retrieve PGP files.
- Utilizes Azure Key Vault for secure key management.
- Manipulates CSV files by combining columns and renaming headers.
- Uploads processed files to an SFTP server.
- Cleans up processed and original files from Blob Storage.

## Prerequisites

- Azure subscription.
- Azure Storage Account with a Blob Container named `File`.
- Azure Function App.
- Azure Key Vault with stored decryption key.
- SFTP server access (host, username, password).
- Permissions set for Azure Function to access Blob Storage and Key Vault.

## Setup and Deployment

### 1. Azure Resources Setup

Ensure that you have the Azure Blob Storage, Azure Key Vault, and Azure Function App created as per the instructions in the Azure portal.

### 2. Configuring Azure Key Vault

Store your PGP decryption key and SFTP credentials in Azure Key Vault. Ensure the Azure Function has an access policy granting permission to read these secrets.

### 3. Developing the Azure Function

Clone this repository to your local machine. Implement the logic for the Azure Function as described in the project guidelines. Make sure to install necessary NuGet packages for Azure Storage, Azure Key Vault, PGP decryption, and SFTP communication.

### 4. Local Testing

Before deploying, you can test the function locally using Azure Storage Emulator and a local file with a `.pgp` extension in the monitored container. Ensure your local.settings.json file contains the necessary configurations for Azure Storage and Key Vault.

### 5. Deployment

Deploy the function to Azure using Visual Studio, VS Code, or the Azure CLI. Ensure that all necessary environment variables and application settings are configured in the Azure Function App settings.

## Usage

Once deployed, the Azure Function will automatically execute every 5 minutes. It will check the specified Blob Storage container for any `.pgp` files, decrypt them, manipulate the file contents, upload them to the configured SFTP server, and clean up the storage.

## Monitoring and Logs

Monitor the function execution and logs through the Azure portal under your Function App's "Monitor" section. This can help diagnose any issues or confirm successful execution.

## Contributing

Contributions to this project are welcome. Please fork the repository and submit a pull request with your changes.
