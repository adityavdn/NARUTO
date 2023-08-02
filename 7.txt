#include <iostream>
#include <vector>
#include <list>
using namespace std;

class Graph {
	int V;
	vector<list<int>> adj;
public:
	Graph(int V) : V(V), adj(V) {}
	void addEdge(int v, int w) { adj[v].push_back(w); }
	void BFS(int s) {
		vector<bool> visited(V, false);
		list<int> queue = {s};
		visited[s] = true;
		while (!queue.empty()) {
			s = queue.front(); cout << s << " "; queue.pop_front();
			for (int adjacent : adj[s]) {
				if (!visited[adjacent]) {
					visited[adjacent] = true;
					queue.push_back(adjacent);
				}
			}
		}
	}
};

int main() {
	Graph g(4);
	g.addEdge(0, 1); g.addEdge(0, 2); g.addEdge(1, 2); g.addEdge(2, 0); g.addEdge(2, 3); g.addEdge(3, 3);
	cout << "Following is Breadth First Traversal (starting from vertex 2)\n";
	g.BFS(2);
	return 0;
}
