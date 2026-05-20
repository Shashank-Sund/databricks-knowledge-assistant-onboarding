# Databricks Knowledge Assistant Onboarding

Reference notebooks for setting up document ingestion and Knowledge Assistant chatbots on Databricks.

## Notebooks

| Notebook | Description |
|---|---|
| [`01-sharepoint-connection-setup.ipynb`](01-sharepoint-connection-setup.ipynb) | End-to-end setup for ingesting documents from Microsoft SharePoint into Unity Catalog as a Delta table. Covers Microsoft Entra ID app registration with `Sites.Selected` scoping, per-site grants via Graph Explorer, Unity Catalog connection creation, and a Delta landing table. |
| [`02-document-processing-for-knowledge-assistant.ipynb`](02-document-processing-for-knowledge-assistant.ipynb) | Reference patterns for processing landed documents into a Knowledge Assistant-ready corpus. Each section is a self-contained worked example: relevance filtering with `ai_classify` / `ai_query`, exact and semantic deduplication with `ai_similarity`, human-in-the-loop staging, parsing with `ai_parse_document`, section-grouped chunking, metadata extraction with `ai_extract`, and Knowledge Assistant configuration. All functions used are GA and HIPAA-eligible. |
| [`03-embed-knowledge-assistant-in-teams.ipynb`](03-embed-knowledge-assistant-in-teams.ipynb) | Production-ready path for embedding a deployed Knowledge Assistant in Microsoft Teams. Deploys a thin Streamlit-based Databricks App as a polished, branded chat surface with streaming responses, hidden Databricks chrome, and service-principal-based auth so end users do not need individual Databricks accounts. Then adds the App as a Website tab in Teams. |

## How to use

These notebooks are intended as reference implementations. Import the `.ipynb` files directly into a Databricks workspace, then update the placeholders to match your environment.

To import a notebook into Databricks:

1. In the Databricks left sidebar, click **Workspace**.
2. Navigate to the folder where you want the notebook to live.
3. Click **+ Add** > **Import**.
4. Choose **File**, upload the `.ipynb` from this repo, click **Import**.

The notebooks are designed to be used independently. A common path is:

1. Notebook **01** to land SharePoint documents in Unity Catalog.
2. Optionally notebook **02** for custom processing when default Knowledge Assistant chunking is not enough.
3. Notebook **03** to put the deployed Knowledge Assistant in front of end users via Microsoft Teams.

## Prerequisites

- Databricks workspace with Unity Catalog enabled and serverless compute available.
- For HIPAA workloads, the workspace must have the Enhanced Security and Compliance add-on (Compliance Security Profile).
- Microsoft Entra ID admin access to register an application and grant API permissions (notebook 01).
- SharePoint admin access to grant per-site application permissions (notebook 01).
- Microsoft Teams workspace permissions to add tabs to channels (notebook 03).

## License

Apache 2.0
