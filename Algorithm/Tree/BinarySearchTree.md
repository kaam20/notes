* 线索化二叉树
* 中序遍历线索化，则左孩子指向前驱，右孩子指向后继
牛客：BM30 二叉搜索树与双向链表
不新建节点的做法

```
public class Solution {        
    TreeNode pre = null;
    TreeNode root = null;
    public TreeNode Convert(TreeNode pRootOfTree) {
        if(pRootOfTree == null) return null;//遍历到叶子结点，进行
        Convert(pRootOfTree.left);
        if(root == null) root = pRootOfTree;//初始化链表的头结点
        //当前节点的前驱节点不为0，则进行双向链表的构建
        if(pre != null)
        {
            pRootOfTree.left = pre;
            pre.right = pRootOfTree;
        }
        //更新前驱为当前节点，进行后续子树的递归遍历
        pre = pRootOfTree;
        Convert(pRootOfTree.right);
        return root;//头结点
    }
}
```
