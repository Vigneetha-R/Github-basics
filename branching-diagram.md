
# 🌳 Git Branching Visualization

```mermaid
gitGraph
   commit id: "Commit 1"
   commit id: "Commit 2"
   commit id: "Commit 3"
   branch feature
   checkout feature
   commit id: "Feature Commit 1"
   commit id: "Feature Commit 2"
   checkout main
   commit id: "Commit 4"
   branch hotfix
   checkout hotfix
   commit id: "Hotfix Commit"
   checkout main
   merge hotfix id: "Merge Hotfix"
   merge feature id: "Final Merge"
