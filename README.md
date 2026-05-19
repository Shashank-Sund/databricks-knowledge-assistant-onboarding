# Databricks Knowledge Assistant Onboarding

Reference notebooks for setting up document ingestion and Knowledge Assistant chatbots on Databricks.

## Notebooks

| Notebook | Description |
|---|---|
| [`01-sharepoint-connection-setup.ipynb`](01-sharepoint-connection-setup.ipynb) | End-to-end setup for ingesting documents from Microsoft SharePoint into Unity Catalog as a Delta table, ready for downstream consumption by Knowledge Assistant, AI/BI, or custom apps. |

## How to use

These notebooks are intended as reference implementations. Import the `.ipynb` files directly into a Databricks workspace, then update the placeholders (catalog name, schema name, SharePoint URLs, connection name, etc.) to match your environment.

To import a notebook into Databricks:

1. In the Databricks left sidebar, click **Workspace**.
2. Navigate to the folder where you want the notebook to live.
3. Click **+ Add** > **Import**.
4. Choose **File**, upload the `.ipynb` from this repo, click **Import**.

## Prerequisites

- Databricks workspace with Unity Catalog enabled and serverless compute available.
- For HIPAA workloads, the workspace must have the Enhanced Security and Compliance add-on (Compliance Security Profile).
- Microsoft Entra ID admin access to register an application and grant API permissions.
- SharePoint admin access to grant per-site application permissions.

## License

Apache 2.0
