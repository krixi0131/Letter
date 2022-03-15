# Letter
Patrick has just finished writing a message to his sweetheart Stacey when he noticed that the message didn't look fancy. Patrick was nervous while writing the message, so some of the letters there were lowercase and some of them were uppercase.

Patrick believes that a message is fancy if any uppercase letter stands to the left of any lowercase one. In other words, this rule describes the strings where first go zero or more uppercase letters, and then — zero or more lowercase letters.

To make the message fancy, Patrick can erase some letter and add the same letter in the same place in the opposite case (that is, he can replace an uppercase letter with the lowercase one and vice versa). Patrick got interested in the following question: what minimum number of actions do we need to make a message fancy? Changing a letter's case in the message counts as one action. Patrick cannot perform any other actions.

Input
The only line of the input contains a non-empty string consisting of uppercase and lowercase letters. The string's length does not exceed 105.

Output
Print a single number — the least number of actions needed to make the message fancy.
```python
a=str(input())
ma=10**5
pre,suf=[0]*len(a),[0]*len(a)
n=len(a)
for i in range(len(a)):
    if i==0:
        if ord(a[0])>96:
            pre[i]=1
        else:
            pre[i]=0
        continue
    if ord(a[i])>96:
        pre[i]=pre[i-1]+1
    else:
        pre[i]=pre[i-1]
for i in range(len(a)-1,-1,-1):
    if i==n-1:
        if ord(a[n-1])>96:
            suf[i]=0
        else:
            suf[i]=1
        continue
    if ord(a[i])<96:
        suf[i]=suf[i+1]+1
    else:
        suf[i]=suf[i+1]    
for i in range(len(a)-1):
    if pre[i]+suf[i+1]<ma:
        ma=pre[i]+suf[i+1]
ans=0
for hi in range(len(a)):
    if ord(a[hi])<97:
        ans+=1
ma=min(ans,ma)
ans=0
for ii in range(len(a)):
    if ord(a[ii])>96:
        ans+=1
ma=min(ans,ma)
print(ma)
```
