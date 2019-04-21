## 基本知識

[建立 linked list 觀念](https://www.youtube.com/watch?v=dmezFFv522I)

### 時間與空間複雜度

```
search => O(n)
insert head => O(1) 
delete => O(n)
```

### 反轉

```
1 => 2 => 3
反轉

3 => 2 => 1
var temp = current.next;
current.next = pre;
pre = current;
current = temp;

round1:
pre = null;
temp = 2;
current.next = null;
pre = 1;
current = 2;
```

### merge

補充題:

[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        
        ListNode* dummy = new ListNode(-1);
        ListNode* temp = dummy;
        
        while(l1 && l2){
            
            if(l1->val < l2->val){
                temp->next = l1;
                l1 = l1->next;
            }else{
                temp->next = l2;
                l2 = l2->next;
            }
            temp = temp->next;
        }
        
        if(l1) temp->next = l1;
        if(l2) temp->next = l2;
        
        return dummy->next;
    }
};
```