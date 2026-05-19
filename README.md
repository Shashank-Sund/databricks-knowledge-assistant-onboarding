# Databricks Knowledge Assistant Onboarding

Reference notebooks for setting up document ingestion and Knowledge Assistant chatbots on Databricks.

## Notebooks

| Notebook | Description |
|---|---|
| [`01-sharepoint-connection-setup.ipynb`](01-sharepoint-connection-setup.ipynb) | End-to-end setup for ingesting documents from Microsoft SharePoint into Unity Catalog as a Delta table, ready for downstream consumption by Knowledge Assistant, AI/BI, or custom apps. Covers Microsoft Entra ID app registration with `Sites.Selected` scoping, per-site grants via Graph Explorer, Unity Catalog connection creation, and a Delta landing table. |
| [`02-document-processing-for-knowledge-assistant.ipynb`](02-document-processing-for-knowledge-assistant.ipynb) | Reference patterns for processing landed documents into a Knowledge Assistant-ready corpus. Each section is a self-contained worked example: relevance filtering with `ai_classify` / `ai_query`, exact + semantic deduplication with `ai_similarity`, human-in-the-loop staging, parsing with `ai_parse_document`, section-grouped chunking, metadata extraction with `ai_extract`, and Knowledge Assistant configuration. All functions used are GA and HIPAA-eligible. |

## How to use

These notebooks are intended as reference implementations. Import the `.ipynb` files directly into a Databricks workspace, then update the placeholders (catalog name, schema name, SharePoint URLs, connection name, etc.) to match your environment.

To import a notebook into Databricks:

1. In the Databricks left sidebar, click **Workspace**.
2. Navigate to the folder where you want the notebook to live.
3. Click **+ Add** > **Import**.
4. Choose **File**, upload the `.ipynb` from this repo, click **Import**.

The notebooks are designed to be used independently. You can run only the SharePoint setup (notebook 01) and rely on Knowledge Assistant's default chunking, OR add the processing pipeline (notebook 02) when you need finer control over chunking, deduplication, or metadata-filtered retrieval.

## Prerequisites

- Databricks workspace with Unity Catalog enabled and serverless compute available.
- For HIPAA workloads, the workspace must have the Enhanced Security and Compliance add-on (Compliance Security Profile).
- Microsoft Entra ID admin access to register an application and grant API permissions (notebook 01).
- SharePoint admin access to grant per-site application permissions (notebook 01).

## License

Apache 2.0
