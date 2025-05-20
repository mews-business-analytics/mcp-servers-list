# MCP Servers for Cursor: Enhancing the AI Coding Experience

This repository provides an overview of various Model-Command-Program (MCP) servers that can be used with [Cursor](https://cursor.sh/), an AI-first code editor. MCP servers extend Cursor's capabilities by allowing the AI to interact with external tools, services, and data sources, leading to a more powerful and context-aware coding assistant.

**Purpose of this Repository**: This collection is curated specifically for our business analytics team's most valuable MCP servers. It serves as a central knowledge base for the team to discover, understand, and leverage the best tools that enhance our analytics workflows. If you discover useful MCP servers that benefit your analytics work, please contribute by adding them here and letting the team know.

## What are MCP Servers?

In the context of Cursor, MCP servers act as bridges that connect the AI model to specialized tools and functionalities. Think of them as plugins or extensions that grant the AI new "senses" or "abilities." When you have an MCP server enabled, Cursor's AI can leverage the tools provided by that server to perform tasks it wouldn't be able to do on its own.

For example, an MCP server for a specific database can allow the AI to:

*   Execute SQL queries directly from your dbt project.
*   Fetch schema information.
*   Retrieve sample data to help you understand table structures.

Similarly, an MCP server for a version control system like GitHub can empower the AI to:

*   Read files from repositories.
*   Understand branch structures.
*   Create or review pull requests.

MCP servers enable a more interactive and productive coding experience by allowing the AI to directly engage with your development environment and workflows. You can often find MCP servers for popular developer tools, and the community is continuously building more.

Below is a list of some useful MCP servers, their purposes, and links to their sources or documentation.

> ⚠️ **Warning**: Enabling too many MCP server tools simultaneously can cause performance issues in Cursor. It's recommended to keep the total number of enabled tools under 40. Cursor will display a warning in the MCP settings when you exceed this limit.
>
> **Where to find MCP settings in Cursor**: Go to Preferences → Cursor Settings → MCP to view, add, enable, or disable MCP servers.

## Databricks MCP Server

> 🌟 **TEAM CRITICAL RESOURCE** 🌟  
> This MCP server is absolutely essential for everyone on the business analytics team. It's a complete game-changer for our data workflows and dramatically enhances our ability to analyze and create data solutions.

*   **Purpose**: Enables interaction with Databricks environments.
*   **GitHub Repository**: [mews-business-analytics/databricks-mcp-server](https://github.com/mews-business-analytics/databricks-mcp-server)
*   **Key Capabilities & Tools**:
    *   `execute_sql_query`: Run SQL queries directly against your Databricks cluster. This is incredibly useful for testing dbt models, exploring data, or quickly answering data-related questions without leaving your editor.
    *   `list_schemas`: List available schemas within a specified catalog.
    *   `list_tables`: List tables within a given schema.
    *   `describe_table`: Get the schema definition for a specific table.
    *   `get_view_definition`: Fetch the DDL (Data Definition Language) for a Databricks view. This is powerful for migrating existing views from Databricks into a dbt project, allowing you to version control and manage them as code.
    *   `list_views`: List all views in a specific catalog and schema.

This MCP server is particularly beneficial for teams using Databricks alongside dbt, as it streamlines workflows like:

*   Inspecting data while developing dbt models.
*   Migrating legacy views into a dbt-managed structure.
*   Quickly querying data for ad-hoc analysis during development.
*   Performing deep data analysis that identifies underlying trends and patterns, then enables interactive digging into these patterns to answer complex business questions.
*   Creating entirely new tables derived from existing Databricks or dbt sources without leaving your coding environment.
*   Building complete new data pipelines by leveraging Databricks table definitions and sample data as foundations.
*   Rapidly prototyping analytics solutions by combining on-the-fly queries with immediate visualization review.
*   Testing hypotheses about data relationships through iterative querying and refinement with AI guidance.
*   Optimizing existing query performance by analyzing execution plans and exploring alternative approaches.
*   Enabling cross-functional data exploration where team members can collaborate on the same datasets in real-time.
*   Documenting data lineage and dependencies through systematic schema examination and metadata collection.

## GitHub MCP Servers

The GitHub integration has been split into two separate MCP servers to provide better flexibility and performance. This separation allows you to enable only the functionality you need, reducing the total number of active tools.

### GitHub Repos MCP Server

*   **Purpose**: Manages repository-related operations and file interactions.
*   **Key Capabilities & Tools**:
    *   **Repository Management**: `create_repository`, `fork_repository`.
    *   **Branch Management**: `create_branch`, `list_branches`.
    *   **File Operations**: `create_or_update_file`, `get_file_contents`, `push_files`.
    *   **Commit Interaction**: `get_commit`, `list_commits`.
    *   **Search**: `search_code`, `search_repositories`.
    *   **User Information**: `get_me` (to get authenticated user details).

### GitHub PRs MCP Server

*   **Purpose**: Handles pull request-specific operations for code review workflows.
*   **Key Capabilities & Tools**:
    *   **Pull Request Management**: `create_pull_request`, `get_pull_request`, `list_pull_requests`, `merge_pull_request`, `update_pull_request`.
    *   **Review Operations**: `add_pull_request_review_comment`, `create_pull_request_review`, `get_pull_request_comments`, `get_pull_request_reviews`.
    *   **PR Utilities**: `get_pull_request_files`, `get_pull_request_status`, `update_pull_request_branch`.
    *   **User Information**: `get_me` (to get authenticated user details).

This split approach lets you selectively enable the GitHub functionality you actually use. For example, if you rarely work with pull requests directly from Cursor, you can disable the GitHub PRs MCP server while keeping the repos functionality active.

## Context7 MCP Server

*   **Purpose**: Provides up-to-date documentation for libraries and frameworks directly to the AI.
*   **Repository**: [upstash/context7](https://github.com/upstash/context7)
*   **Website**: [context7.com](https://context7.com/)
*   **Key Capabilities & Tools**:
    *   `resolve-library-id`: Resolves a general library name into a Context7-compatible library ID.
    *   `get-library-docs`: Fetches documentation for a library using a Context7-compatible library ID, with optional parameters to focus on specific topics or control the amount of documentation returned.

Context7 solves one of the most common issues with AI coding assistants: outdated or incorrect knowledge about libraries and frameworks. When working with a framework that has changed significantly since the AI's training data was cut off, Context7 can retrieve the most current documentation, allowing for accurate and up-to-date assistance.

### How Context7 Enhances AI Coding

Without Context7, LLMs rely on outdated or generic information about libraries, which leads to:
*   Outdated code examples based on old training data
*   Hallucinated APIs that don't actually exist
*   Generic answers for old package versions

With Context7 enabled, the AI can:
*   Access current documentation directly from the source
*   Generate code using the latest APIs and best practices
*   Understand breaking changes and deprecations
*   Provide version-specific guidance

### Using Context7 in Cursor

To use Context7, simply add the phrase "use context7" to your prompt when asking about a specific library or framework:

```
Create a basic Next.js project with app router. use context7
```

Or

```
Create a script to delete the rows where the city is "" given PostgreSQL credentials. use context7
```

Context7 is particularly valuable when:
*   Working with rapidly evolving libraries and frameworks
*   Learning a new technology
*   Needing version-specific implementation details
*   Confirming if a particular API or feature exists

## PBIXRay MCP Server

*   **Purpose**: Enables analysis of Power BI (.pbix) files with detailed model exploration and data inspection.
*   **Repository**: [jonaolden/pbixray-mcp-server](https://github.com/jonaolden/pbixray-mcp-server)
*   **Resource**: [Playbooks - PBIXRay MCP Server](https://playbooks.com/mcp/jonaolden-pbixray)
*   **Key Capabilities & Tools**:
    *   **Core**: `load_pbix_file` - Load a Power BI file for analysis.
    *   **Model Analysis**:
        *   `get_tables` - List all tables in the model.
        *   `get_metadata` - Get metadata about the Power BI configuration.
        *   `get_model_size` - Get the model size in bytes.
        *   `get_statistics` - Get statistics about the model.
        *   `get_model_summary` - Get a comprehensive summary of the model.
    *   **Query Language Access**:
        *   `get_power_query` - Display all M/Power Query code used for data transformation.
        *   `get_m_parameters` - Display all M Parameters values.
        *   `get_dax_tables` - View DAX calculated tables.
        *   `get_dax_measures` - Access DAX measures with filtering options.
        *   `get_dax_columns` - Access calculated column DAX expressions.
    *   **Data Structure Analysis**:
        *   `get_schema` - Get details about the data model schema and column types.
        *   `get_relationships` - Get the details about data model relationships.
        *   `get_table_contents` - Retrieve table contents with pagination and filtering.

### How PBIXRay Enhances Power BI Development

PBIXRay MCP Server provides deep insights into Power BI files, allowing developers to:

*   Understand complex data models without opening Power BI Desktop.
*   Analyze DAX measures for optimization opportunities.
*   Review relationships and dependencies in the model.
*   Extract and modify M queries and DAX expressions.
*   Generate new metrics or optimize existing ones with AI assistance.

The server works particularly well in conjunction with [Tabular Editor](https://tabulareditor.com/), a powerful tool for editing and managing tabular models. PBIXRay can help analyze a model, and the optimizations can be implemented using Tabular Editor.

### Typical Workflow

A typical workflow with PBIXRay might look like this:

1.  Load the Power BI file:
    ```
    load_pbix_file(file_path="/path/to/your/file.pbix")
    ```

2.  Get a model summary to understand the structure:
    ```
    get_model_summary()
    ```

3.  Explore specific aspects like DAX measures:
    ```
    get_dax_measures(table_name="Sales")
    ```

4.  Analyze and optimize with AI assistance, then implement changes using Tabular Editor.

## dbt MCP Server

*   **Purpose**: Provides dbt (data build tool) integration to work with your dbt projects directly within Cursor.
*   **Key Capabilities & Tools**:
    *   `mcp_dbt-mcp_build`: Run the dbt build command, which will run models, test tests, snapshot snapshots, and seed seeds in DAG order.
    *   `mcp_dbt-mcp_compile`: Generate executable SQL from source model, test, and analysis files.
    *   `mcp_dbt-mcp_docs`: Generate your project's documentation website.
    *   `mcp_dbt-mcp_list`: List the resources in your dbt project.
    *   `mcp_dbt-mcp_parse`: Parse and validate the contents of your dbt project.
    *   `mcp_dbt-mcp_run`: Execute compiled SQL model files against the current target database.
    *   `mcp_dbt-mcp_test`: Run data tests defined on models, sources, snapshots, and seeds.
    *   `mcp_dbt-mcp_show`: Execute an arbitrary SQL statement and return the results.

The dbt MCP server is invaluable for data engineers and analysts who use dbt for their data transformation pipelines. It allows the AI to understand your dbt project structure, execute dbt commands, and help you develop and debug your models without leaving your coding environment.

### How dbt MCP Enhances Data Workflows

With the dbt MCP server, you can:

*   Quickly validate models during development.
*   Troubleshoot failing tests with AI assistance.
*   Review the SQL generated by your dbt models.
*   Run ad-hoc queries to verify your transformations.
*   Generate documentation for your data models.

This server is particularly powerful when combined with the Databricks MCP server, creating a comprehensive environment for dbt development directly within Cursor.

## Contributing to This Repository

This repository aims to be a comprehensive resource for understanding and utilizing MCP servers with Cursor. If you're using an MCP server that isn't listed here, or if you've created one yourself, please consider contributing by:

1.  Opening a pull request with details about the server.
2.  Filing an issue with information about the server you'd like to see added.
3.  Sharing your experiences with different MCP servers to help others understand their real-world applications.

## Conclusion

MCP servers significantly enhance Cursor's capabilities by connecting the AI to specialized tools and data sources. By carefully selecting the MCP servers that align with your development workflow, you can create a powerful, context-aware AI coding environment that helps you work more efficiently.

Remember to be mindful of the number of tools you enable simultaneously to maintain optimal performance, and explore new MCP servers as they become available to continuously expand what you can accomplish with Cursor.

As this repository is maintained for our business analytics team, we encourage all team members to actively contribute to this collection. When you discover an MCP server that improves your analytics workflow or solves a specific challenge, please add it to this repository and share your experience with the team. This collaborative approach ensures we all benefit from the latest tools and best practices in our data work. 