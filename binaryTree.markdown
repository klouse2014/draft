
```cpp
struct binaryNode
{
    string data;
    binaryNode *left;
    binaryNode *right;
    binaryNode(string value = ""){
        data = value;
        left = NULL;
        right = NULL;
    }
};
```

## 生成二叉树
### 前序输入创建二叉树
```cpp
void createBinaryTree(binaryNode* &root)
{
    string temp;
    getline(cin, temp);
    if(temp.empty())
        return;
    if(root == NULL)
        root = new binaryNode(temp);
    createBinaryTree(root->left);
    createBinaryTree(root->right);
}
```

## 二叉树遍历
### 递归方式
**前序、中序、后序实现方式相同**  
```cpp
void preOrderRecur(binaryNode *root)
{
    if(root == NULL)
        return;
    cout << root->data << " ";
    preOrderRecur(root->left);
    preOrderRecur(root->right);
}
```
### 迭代方式
**前序遍历**  
```cpp
void preOrderIter(binaryNode *root)
{
    if(root == NULL)
        return;
    stack<binaryNode *> stk;
    stk.push(root);
    while(!stk.empty())
    {
        binaryNode *tmp = stk.top();
        stk.pop();
        cout << tmp->data << " ";
        if(tmp->right != NULL)
            stk.push(tmp->right);
        if(tmp->left != NULL)
            stk.push(tmp->left);
    }
    cout<<endl;
}
```
**中序遍历**  
```cpp
void InOrderIter(binaryNode *root)
{
    if(root == NULL)
        return;
    stack<binaryNode *> stk;
    binaryNode *p = root;
    while(!stk.empty() || p != NULL)
    {
        while(p != NULL)
        {
            stk.push(p);
            p = p->left;
        }
        if(!stk.empty())
        {
            p = stk.top();
            stk.pop();
            cout<< p->data << " ";
            p = p->right;
        }
    }
    cout<<endl;
}
```

