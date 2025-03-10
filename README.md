# ScholarGraph

<div style="color:mediumblue;font-weight:800;font-size:48px; text-align:center">
Scholar-Graph
</div>
</br>
<div style="color:darkolivegreen;font-weight:800;font-size:32px; text-align:center">
    Building Agentic Apps: ArangoDB, NVIDIA cuGraph, and NetworkX Hackathon
</div>
<br>

<p align="center">
    <img src="https://arangodb.com/wp-content/uploads/2016/05/ArangoDB_logo_avocado_@1.png" style="height: 50px;">
    <img src="https://www.nvidia.com/content/dam/en-zz/Solutions/about-nvidia/logo-and-brand/02-nvidia-logo-color-grn-500x200-4c25-p@2x.png" style="height: 50px;">
    <img src="https://rapids.ai/images/RAPIDS-logo.png" style="height: 50px;">
    <img src="https://avatars.githubusercontent.com/u/388785?s=200&v=4" style="height: 50px;">
</p>



# Key Technologies Used

- **ArangoDB** - To Store Graph - Nodes and Edges
- **NVIDIA cuGraph** - To run NetworkX Algorithms efficiently, on-scale
- **NetworkX** - To model the graph and run Graph Algorithms
- **OpenAI gpt-4o-mini** - As LLM
- **Langchain & Langgraph** - As Agentic Framework to Build Deep Research Agentic App
- **nx-cugraph** - To run cuGraph with networkx
- **LangChain Structured Output** - To extract Topic Entities from unstructured data

**Agentic App** uses below Agents:

1. **Data Augmentation Agent** - leverages Wikipedia to extract information about various cities as a Graph. Uses LangChain WikipediaRetriever and LLM Graph Transformer
2. **Master ReAct Agent** - Which Plans which tools to call. The ability to plan and call below tools and pass results of one to another, allows it run below queries:

* **SIMPLE QUERIES** → Dynamic AQL (via LangChain)
* **COMPLEX QUERIES** → GPU-Accelerated Graph Analytics (via NetworkX/cuGraph)
* **HYBRID QUERY EXECUTION** → Combining AQL and cuGraph for Contextual Responses

Available Tools for Master ReAct Agent:

- **Text to AQL** - Converts Natural Language to ArangoDB AQL Query
- **Text to AQL to Text** - Converts Natural Language to ArangoDB AQL Query, run it and convert the results to a Natural Language Answer
- **Text to NetworkX Algorithm** - Converts Natural Language to NetworkX Algorithm, executes it and provides response in natural Language - With Robust Re-Try Mechanism
- **NetworkX Algorithm to AQL to Text** - Converts Natural Language to NetworkX Algorithm, executes it and then passes results to execute AQL Query and then provides response in natural Language


# Key Use Cases:

## Simple Queries - Use Cases Answerable by AQL Queries

- Find all papers written by a Author `Mina Aganagic`.
- List all topics associated with papers published in a journal - `Int.J.Mod.Phys. A7 (1992) 5661-5705`.
- Find authors who have written papers on topics - `String Theory` and `Quantum Theory`.
- Determine the number of papers published by author `Mina Aganagic` in Year 1996 .

## Complex Queries = GPU-Accelerated Graph Analytics (via NetworkX/cuGraph)

### Breadth-First Search (BFS)
- Find the shortest path between two authors - `Mina Aganagic` and `A. Giveon` based on co-authorship.
### Depth-First Search (DFS)
- Identify strongly connected components in the citation network.
### Centrality Measures (e.g., PageRank)
- Rank papers by their influence using PageRank.
### Community Detection Algorithms (e.g., Girvan-Newman)
- Detect communities of authors based on co-authorship patterns.
### Shortest Path Algorithms (e.g., Dijkstra’s)
- Find the shortest path between papers `9907178` and `9211097` in the citation network.

## Hybrid Query Execution - Combining AQL and cuGraph for Contextual Responses
### Centrality Measures (e.g., PageRank)
- Calculate the PageRank of Top 10 authors based on their papers’ citations.
### Community Detection Algorithms (e.g., Girvan-Newman)
- Identify communities of papers based on their topics and citations.
### Breadth-First Search (BFS)
- Find the shortest path between topics - `String Theory` and `Quantum Theory` based on papers.
### Network Clustering Coefficient
- Calculate the clustering coefficient of the author co-authorship network.


# Steps

Copy .enn.sample to .env and update it with OpenAI keys and ArangoDB credentials.
Then Open the Jupyter Notebook and follow the steps - They are self explainatory