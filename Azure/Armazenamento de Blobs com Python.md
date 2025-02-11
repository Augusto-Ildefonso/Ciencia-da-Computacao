Primeiramente, serão necessárias as seguintes bibliotecas `azure-storage-blob` e `azure-identity`. Para instala-las execute:
```
$ pip install azure-storage-blob azure-identity
```
Além delas também são necessárias as bibliotecas `os` e `uuid`. Uma vez que foram instaladas, podemos importar as seguintes classes delas:
~~~python
from azure.identity import DefautAzureCredential
from azure.storage.blob import BlobServiceClient, BlobClient, ContainerClient
~~~
As classes lidam com os seguintes recursos:
- **BlobServiceClient**: permite manipular os recursos do Armazenamento do Azure e os contêineres do blob
- **ContainerClient**: permite manipular os contêineres do Armazenamento do Azure e seus blobs
- **BlobClient**: permite manipular os blobs do Armazenamento do Azure

>Link do artigo: [clique aqui](https://learn.microsoft.com/pt-br/azure/storage/blobs/storage-quickstart-blobs-python?tabs=managed-identity%2Croles-azure-portal%2Csign-in-azure-cli&pivots=blob-storage-quickstart-scratch)