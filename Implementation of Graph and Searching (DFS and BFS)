#include <iostream>
#include <vector>
#include <queue>
#include <chrono>

using namespace std;
using namespace std::chrono;

class Graph {
private:
    int V;
    vector<vector<int>> adj;

public:
    // Constructor
    Graph(int vertices) {
        V = vertices;
        adj.resize(V);
    }

    // Add edge
    void addEdge(int u, int v) {
        adj[u].push_back(v);
        adj[v].push_back(u);   // Undirected graph
    }

    // DFS Utility function
    void DFSUtil(int v, vector<bool>& visited) {
        visited[v] = true;
        cout << v << " ";

        for (int neighbor : adj[v]) {
            if (!visited[neighbor]) {
                DFSUtil(neighbor, visited);
            }
        }
    }

    // DFS
    void DFS(int start) {
        vector<bool> visited(V, false);
        DFSUtil(start, visited);
    }

    // BFS
    void BFS(int start) {
        vector<bool> visited(V, false);
        queue<int> q;

        visited[start] = true;
        q.push(start);

        while (!q.empty()) {
            int node = q.front();
            q.pop();

            cout << node << " ";

            for (int neighbor : adj[node]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.push(neighbor);
                }
            }
        }
    }
};

int main() {
    int V, E;

    // Number of vertices
    cout << "Enter number of vertices: ";
    cin >> V;

    Graph g(V);

    // Number of edges
    cout << "Enter number of edges: ";
    cin >> E;

    // Enter edges
    cout << "Enter edges (u v):" << endl;

    for (int i = 0; i < E; i++) {
        int u, v;
        cin >> u >> v;

        g.addEdge(u, v);
    }

    // Starting vertex
    int start;
    cout << "Enter starting vertex: ";
    cin >> start;

    // DFS Time Analysis
    auto startDFS = high_resolution_clock::now();

    cout << "\nDFS Traversal: ";
    g.DFS(start);

    auto endDFS = high_resolution_clock::now();

    auto dfsTime =
        duration_cast<nanoseconds>(endDFS - startDFS);

    // BFS Time Analysis
    auto startBFS = high_resolution_clock::now();

    cout << "\n\nBFS Traversal: ";
    g.BFS(start);

    auto endBFS = high_resolution_clock::now();

    auto bfsTime =
        duration_cast<nanoseconds>(endBFS - startBFS);

    // Display execution time
    cout << "\n\nExecution Time:" << endl;
    cout << "DFS: " << dfsTime.count() << " ns" << endl;
    cout << "BFS: " << bfsTime.count() << " ns" << endl;

    return 0;
}
