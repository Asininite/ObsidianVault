
Given the `head` of a singly linked list, return _the middle node of the linked list_.

If there are two middle nodes, return **the second middle** node.

### USE FAST AND SLOW POINTERS

```cpp
class Solution{
public:
	ListNode* middleNode(ListNode* head){
		ListNode* slow = head;
		ListNode* fast = head;
		
		while(fast != nullptr && fast->next != nullptr){
			slow = slow->next;
			fast = fast->next->next;
		}
		return slow;
	}
}
```