// Prim's algorithm to find minimum spanning tree for undirected connected weighted graph


#include<bits/stdc++.h>
using namespace std;

class Graph
{
public:
    int vertices;
    list<pair<int,int>> *adjlist;

    Graph(int v)
    {
        vertices=v;
        adjlist = new list<pair<int,int>>[v];
    }

    void addEdge(int u,int v,int w)
    {
      adjlist[u].push_back(make_pair(v,w));
      adjlist[v].push_back(make_pair(u,w));
    }
    int findMinimumVertex(int *weight,bool *visited,int v)
    {
        int min_vertex=-1;
        for(int i=0;i<v;i++)
        {
            if(!visited[i] && (min_vertex==-1 || weight[i]<weight[min_vertex]))
            {
                min_vertex = i;
            }
        }
        return min_vertex;
    }
    void primsAlgorithm()
    {
        bool *visited = new bool[vertices]; // mapping for vertices that are visited
        int *weight = new int[vertices];
        int *parent = new int[vertices];
        for(int i=0;i<vertices;i++)
        {
            visited[i]=false;
            weight[i]=INT_MAX;
        }

        weight[0]=0;
        parent[0]=-1;
        for(int i=0;i<vertices;i++)
        {


            //finding minimum vertex from the mapping i.e. vertex having minimum weight in current mapping
            int min_vertex = findMinimumVertex(weight,visited,vertices);
            visited[min_vertex]=true;
            for(auto neighbor :adjlist[min_vertex])
            {
                // if weight for a vertex in our mapping is greater than the weight at a particular edge or not
                if(!visited[neighbor.first] && neighbor.second<weight[neighbor.first])
                {

                    weight[neighbor.first]=neighbor.second;
                    parent[neighbor.first]=min_vertex;
                }
            }
        }
        for(int i=0;i<vertices;i++)
        {
            cout<<i<<" -- "<<parent[i]<<" weight "<<weight[i]<<"\n";
        }
    }
};


int main()
{
    int v,e;
    cin>>v>>e;
    Graph g(v);
    for(int i=0;i<e;i++)
    {
        int u,v,w;
        cin>>u>>v>>w;
        g.addEdge(u,v,w);
    }
    g.primsAlgorithm();
    return 0;
}

/********************************** Sample test Case **********************************/

/*
7 8
0 3 4
0 1 6
1 2 5
3 2 7
3 4 2
4 5 4
5 6 1
4 6 3
*/
