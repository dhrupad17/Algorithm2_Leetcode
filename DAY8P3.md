# All Paths From Source to Target
---
- ## Question:
> Given a directed acyclic graph (DAG) of n nodes labeled from 0 to n - 1, find all possible paths from node 0 to node n - 1 and return them in any order.
> 
> The graph is given as follows: graph[i] is a list of all nodes you can visit from node i (i.e., there is a directed edge from node i to node graph[i][j]).
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2020/09/28/all_1.jpg)
> Input: graph = [[1,2],[3],[3],[]]
> 
> Output: [[0,1,3],[0,2,3]]
> 
> Explanation: There are two paths: 0 -> 1 -> 3 and 0 -> 2 -> 3.
---
- ## Solution:
**Code :**
```java
class Solution {
    List<List<Integer>> res = new ArrayList<>();
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        findPaths(graph, 0, new ArrayList<Integer>());
        return res;
    }
    private void findPaths(int[][] graph, int i, List<Integer> list) {
        int n = graph.length;
        list.add(i);
        if (i == n - 1) {
            res.add(list);
        }
        for (int j = 0; j < graph[i].length; j++) {
            findPaths(graph, graph[i][j], new ArrayList<>(list));
        }
    }
}
