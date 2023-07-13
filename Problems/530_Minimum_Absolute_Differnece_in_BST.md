# Description
Given the root of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two different nodes in the tree.

# Thought
* 因為是二元搜尋樹，使用中序遍歷可以得到由小到大排列的值
* 從得到的陣列中，計算相鄰兩數的差求最小值

# Code:
```cpp
class Solution
{
public:
    void trvl(TreeNode* root, vector<int>& treeVal){
        if(!root)
            return;
        trvl(root->left, treeVal);
        treeVal.push_back(root->val);
        trvl(root->right, treeVal);
    }

    int getMinimumDifference(TreeNode* root){
        vector<int> treeVal;
        trvl(root, treeVal);
        
        int minDiff = INT_MAX;
        for(int i = 1; i < trvl.size(); i++){
            minDiff = min(minDiff, treeVal[i] - treeVal[i - 1]);
        }

        return minDiff;
    }
}
