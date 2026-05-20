# Databricks Knowledge Assistant Onboarding

Reference notebooks for setting up document ingestion and Knowledge Assistant chatbots on Databricks.

## Notebooks

| Notebook | Description |
|---|---|
| [`01-sharepoint-connection-setup.ipynb`](01-sharepoint-connection-setup.ipynb) | End-to-end setup for ingesting documents from Microsoft SharePoint into Unity Catalog as a Delta table. Covers Microsoft Entra ID app registration with `Sites.Selected` scoping, per-site grants via Graph Explorer, Unity Catalog connection creation, and a Delta landing table. |
| [`02-document-processing-for-knowledge-assistant.ipynb`](02-document-processing-for-knowledge-assistant.ipynb) | Reference patterns for processing landed documents into a Knowledge Assistant-ready corpus. Each section is a self-contained worked example: relevance filtering with `ai_classify` / `ai_query`, exact and semantic deduplication with `ai_similarity`, human-in-the-loop staging, parsing with `ai_parse_document`, section-grouped chunking, metadata extraction with `ai_extract`, and Knowledge Assistant configuration. All functions used are GA and HIPAA-eligible. |
| [`03-embed-knowledge-assistant-in-teams.ipynb`](03-embed-knowledge-assistant-in-teams.ipynb) | Production-ready path for embedding a deployed Knowledge Assistant in Microsoft Teams. Deploys a thin Streamlit-based Databricks App as a polished, branded chat surface with streaming responses, hidden Databricks chrome, and service-principal-based auth so end users do not need individual Databricks accounts. Then adds the App as a Website tab in Teams. |
| [`04-sharepoint-pages-ingestion.ipynb`](04-sharepoint-pages-ingestion.ipynb) | Pulls content from SharePoint web pages (`.aspx` pages with their web parts) into a Unity Catalog Delta table via the Microsoft Graph API. The Databricks SharePoint connector only handles document library files, so this notebook is the workaround for getting page content (announcements, news, embedded text) into the Knowledge Assistant's indexed corpus. Reuses the Entra ID app from notebook 01. |
| [`05-embed-knowledge-assistant-in-sharepoint.ipynb`](05-embed-knowledge-assistant-in-sharepoint.ipynb) | Step-by-step for embedding the Databricks App built in notebook 03 directly into a SharePoint page using SharePoint's Embed web part. Users see the page's at-a-glance content alongside the chatbot, without leaving the page. Includes detailed troubleshooting for iframe blocking, the most common embedding issue, with concrete fixes. |

## How to use

These notebooks are intended as reference implementations. Import the `.ipynb` files directly into a Databricks workspace, then update the placeholders to match your environment.

To import a notebook into Databricks:

1. In the Databricks left sidebar, click **Workspace**.
2. Navigate to the folder where you want the notebook to live.
3. Click **+ Add** > **Import**.
4. Choose **File**, upload the `.ipynb` from this repo, click **Import**.

The notebooks are designed to be used independently. A common end-to-end path is:

1. Notebook **01** to land SharePoint document library files in Unity Catalog.
2. Notebook **04** to land SharePoint page content in Unity Catalog (so the chatbot can answer questions about pages, not just documents).
3. Optionally notebook **02** for custom processing when default Knowledge Assistant chunking is not enough.
4. Notebook **03** to put the deployed Knowledge Assistant in front of end users via Microsoft Teams.
5. Notebook **05** to also embed the chatbot in the SharePoint page so users can ask questions without leaving the page.

## Prerequisites

- Databricks workspace with Unity Catalog enabled and serverless compute available.
- For HIPAA workloads, the workspace must have the Enhanced Security and Compliance add-on (Compliance Security Profile).
- Microsoft Entra ID admin access to register an application and grant API permissions (notebooks 01 and 04).
- SharePoint admin access to grant per-site application permissions (notebooks 01 and 04) and to edit SharePoint pages (notebook 05).
- Microsoft Teams workspace permissions to add tabs to channels (notebook 03).

## License

Apache 2.0
