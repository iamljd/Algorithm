208. 实现 Trie (前缀树)   //中等
------
    实现一个 Trie (前缀树)，包含 insert, search, 和 startsWith 这三个操作。

    示例:

    Trie trie = new Trie();
    trie.insert("apple");
    trie.search("apple");   // 返回 true
    trie.search("app");     // 返回 false
    trie.startsWith("app"); // 返回 true
    trie.insert("app");   
    trie.search("app");     // 返回 true
    
    说明:

    你可以假设所有的输入都是由小写字母 a-z 构成的。
    保证所有输入均为非空字符串。
链接:https://leetcode-cn.com/problems/implement-trie-prefix-tree/
Code:
```cpp
class Trie 
{
    Trie *child[26];
    bool isWord;
public:
    /** Initialize your data structure here. */
    Trie() 
    {
        for(int i=0;i<26;i++)
        {
            child[i]=nullptr;
        }
        isWord=false;
    }
    
    /** Inserts a word into the trie. */
    void insert(string word) 
    {
        Trie *t=this;
        for(auto c:word)
        {
            if(!t->child[c-'a']) { t->child[c-'a']=new Trie(); }
            t=t->child[c-'a'];
        }
        t->isWord=true;
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) 
    {
        Trie *t=this;
        for(auto c:word)
        {
            if(!t->child[c-'a']) { return false; break; }
            t=t->child[c-'a'];
        }
        return t->isWord;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) 
    {
        Trie *t=this;
        for(auto c:prefix)
        {
            if(!t->child[c-'a']) { return false; break; }
            t=t->child[c-'a'];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
#####
思路分析
* class类中用this指针
#####
用时
* 执行用时：104 ms, 在所有 C++ 提交中击败了84.33%的用户
* 内存消耗：43.1 MB, 在所有 C++ 提交中击败了24.52%的用户
* 2020/11/17   9:55
