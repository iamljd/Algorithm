648. 单词替换   //中等
------
    
    在英语中，我们有一个叫做 词根(root)的概念，它可以跟着其他一些词组成另一个较长的单词——我们称这个词为 继承词(successor)。
    
    例如，词根an，跟随着单词 other(其他)，可以形成新的单词 another(另一个)。

    现在，给定一个由许多词根组成的词典和一个句子。你需要将句子中的所有继承词用词根替换掉。如果继承词有许多可以形成它的词根，则用最短的词根替换它。

    你需要输出替换之后的句子。

    示例 1：

    输入：dictionary = ["cat","bat","rat"], sentence = "the cattle was rattled by the battery"
    输出："the cat was rat by the bat"
    
    示例 2：

    输入：dictionary = ["a","b","c"], sentence = "aadsfasf absbs bbab cadsfafs"
    输出："a a b c"
    
    示例 3：

    输入：dictionary = ["a", "aa", "aaa", "aaaa"], sentence = "a aa a aaaa aaa aaa aaa aaaaaa bbb baba ababa"
    输出："a a a a a a a a bbb baba a"
    
    示例 4：

    输入：dictionary = ["catt","cat","bat","rat"], sentence = "the cattle was rattled by the battery"
    输出："the cat was rat by the bat"
    
    示例 5：

    输入：dictionary = ["ac","ab"], sentence = "it is abnormal that this solution is accepted"
    输出："it is ab that this solution is ac"
 
    提示：

    1 <= dictionary.length <= 1000
    1 <= dictionary[i].length <= 100
    dictionary[i] 仅由小写字母组成。
    1 <= sentence.length <= 10^6
    sentence 仅由小写字母和空格组成。
    sentence 中单词的总量在范围 [1, 1000] 内。
    sentence 中每个单词的长度在范围 [1, 1000] 内。
    sentence 中单词之间由一个空格隔开。
    sentence 没有前导或尾随空格。

链接:https://leetcode-cn.com/problems/replace-words/

Code:
```cpp
class Trie
{
    private:
        bool isWord;
        Trie *child[26];
    public:
        Trie()
        {
            isWord=false;
            for(int i=0;i<26;i++) child[i]=nullptr;
        }
        void insert(string word)
        {
            Trie *t=this;
            for(auto c:word)
            {
                if(!t->child[c-'a']) t->child[c-'a']=new Trie();
                t=t->child[c-'a'];
            }
            t->isWord=true;
        }
        int search(string word)
        {
            Trie *t=this;
            int minlen=0;
            for(auto c:word)
            {
                if(t->child[c-'a'])
                {
                    if(t->child[c-'a']->isWord) { return minlen+1; break; }
                    else
                    {
                        t=t->child[c-'a'];
                        minlen++;
                    }
                }
                else { return 0;break; }
            }
            return 0;   //缺少此行会显示与return int的匹配错误
        }
};
class Solution
{
    public:
        string replaceWords(vector<string>& dict, string sentence)
        {
            Trie *root=new Trie();
            for(auto s:dict) root->insert(s);
            string res;
            int i=0,j=0;
            int len=sentence.size();
            while(i<len&&j<len)
            {
                while(j<len&&sentence[j]!=' ') j++;
                string temp=sentence.substr(i,j-i);
                int k=root->search(temp);
                if(k==0) res+=temp;
                else     res+=sentence.substr(i,k);
                res+=" ";
                i=j+1;
                j=i;
            }
            if(!res.empty()) res.pop_back();   //去除最后一个char
            return res;
        }
};
```
#####
思路分析
* 字典树解法，快于哈希解法
#####
* 执行用时：64 ms, 在所有 C++ 提交中击败了92.68%的用户
* 内存消耗：49.5 MB, 在所有 C++ 提交中击败了52.54%的用户
* 2020/11/17 22:56
