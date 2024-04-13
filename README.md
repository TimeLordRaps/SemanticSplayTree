# SemanticSplayTree
It's a splay tree that means something.

# Process when retrieving or adding a node:
1. Semantic Retrieval from Vector DB

    a. Retrieve the D (Absolute tree depth) most similar nodes from the VDB to the query node.
   
    b. Filter these nodes for only nodes below the query node
3. Standard Splaying with Semantic Marking
   
    a. Splay the query node to the root
   
    b. Along the way mark each parent node based on its semantic similarity to the query node.
5. Splay Marked nodes above initial query depth
   
    a. 1 by 1 splay the appropriate closest in similarities to the query node in a depth wise way, where the most similar node should sit at highest at depth 1 and so on until depth d where the d - 1 ranked parent node is placed in the worst case.
7. Splay nodes below initial query depth
   
    a. For nodes identified in Section 1, assign new depths starting from at worst d+1 based on their ranking of similarity.

# Current idea for deletion of nodes:
1. Mark current root as comparison node.
2. Splay deletion node to root.
3. Delete root.
4. Find most similar node in left tree splay to left tree root.
5. Attach right tree to new left tree root as right tree.
