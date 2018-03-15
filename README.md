# leetcode-learn
1. 题目描述
Evaluate the value of an arithmetic expression in Reverse Polish Notation.
Valid operators are+,-,*,/. Each operand may be an integer or another expression.
Some examples:
  ["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
  ["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6

Code:
class Solution {
public:
    int evalRPN(vector<string> &tokens) {
        stack<int> datas;
        for(int i=0; i<tokens.size();i++){
            if(tokens[i]!="+"&&tokens[i]!="-"&&tokens[i]!="*"&&tokens[i]!="/"){
                int num = std::stoi(tokens[i]);
                datas.push(num);
            }
            else if(tokens[i]=="+"){
                if(datas.size()<2) return (0);
                int a = datas.top();datas.pop();
                int b = datas.top();datas.pop();
                int c = a + b;
                datas.push(c);
            }
            else if(tokens[i]=="-"){
                if(datas.size()<2) return (0);
                int a = datas.top();datas.pop();
                int b = datas.top();datas.pop();
                int c = b - a;
                datas.push(c);
            }
            else if(tokens[i]=="*"){
                if(datas.size()<2) return (0);
                int a = datas.top();datas.pop();
                int b = datas.top();datas.pop();
                int c = b * a;
                datas.push(c);
            }
            else if(tokens[i]=="/"){
                if(datas.size()<2) return (0);
                int a = datas.top();datas.pop();
                int b = datas.top();datas.pop();
                int c = b / a;
                datas.push(c);
            }
        }
        if(datas.size()==1)
            return datas.top();
        else
            return (0);
    }
};
