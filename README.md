# 💻 Bài giải LeetCode bằng C++, Python, Javascript 

## Array (Easy)

### 🧠 Đề bài 1 
**TWO SUM**:  
```
Given an array of integers 'nums' and an integer 'target'  
Return -> *indices of the two numbers such that they add up to target*  
You may assume that each input would have exactly one solution, and you may not use the same element twice.
```
Dịch:
```
Cho 1 mảng số nguyên 'nums' và 1 số nguyên 'target'  
Trả về -> *Chỉ số của 2 phần tử trong mảng mà cộng lại bằng target*
Chỉ có 1 cặp duy nhất có tổng bằng target
```
### 🧩 Ý tưởng & Phân tích
- Cần tìm cặp số có tổng là target, vì đề bài nói là 'one solution, may not use the same element twice' nên
  không cần tính đến trường hợp trong mảng có phần tử giống nhau
- PP1: Duyệt chay
    - Duyệt từng phần tử trong mảng xem nó có thể cộng với số nào để bằng target
    - Độ phức tạp là O(n^2) 
    - > Ưu điểm: Là cách nghĩ ra đầu tiên  
      > Nhược điểm: Lâu, chậm 
- PP2: Dùng 2 con trỏ chạy từ 2 đầu của mảng
    - Phải sắp xếp trước khi duyệt
    - So tổng cặp đầu cuối với target, nếu lớn hơn target thì tăng đầu và ngược lại, nhỏ hơn target thì giảm cuối
    - Độ phức tạp là O(n logn)
    - > Ưu điểm: Hiệu quả hơn duyệt chay
      > Nhược điểm: + phải sắp xếp trước nên tốn thêm thời gian
                    + nếu phải in ra cả chỉ số từ mảng gốc thì không dùng được
- PP3: Dùng hashmap unordered_map<key,value>...
    - Lấy target trừ từng phần tử, nếu tìm thấy hiệu đó trong hashmap thì đó là cặp cần tìm
    - Nếu tìm không thấy hiệu đó thì lưu vào hashmap
    - Độ phức tạp là O(n) 
    - > Đây là cách tối ưu nhất 
### 🧑‍💻 Code C++
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map <int, int> seen;
        for (int i = 0; i < nums.size(); ++i) {
          int kq= nums[i];
          int tru = target - kq;
          auto it = seen.find(tru);
          if (it != seen.end()) {
              return {it->second, i};
          } else {
              seen[kq] = i;
        }
    }
    return {};
    }
};
```
### 🧑‍💻 Code Python
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}
        for i in range(len(nums)):
            tru = target - nums[i]
            if tru in seen:
                return [seen[tru], i]
            else:
                seen[nums[i]] = i
```

### 🧠 Đề bài 2
**REMOVE DUPLICATES FROM SORTED ARRAY**:  
```
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such
that each unique element appears only once. 
```
Dịch: 
```
Cho 1 mảng số nguyên 'nums' đã được sắp xếp tăng dần, loại bỏ các phần tử trùng lặp sao cho các
phần tử chỉ xuất hiện 1 lần duy nhất
```
### 🧩 Ý tưởng & Phân tích
- Cần tìm cặp số có tổng là target, vì đề bài nói là 'one solution, may not use the same element twice' nên
  không cần tính đến trường hợp trong mảng có phần tử giống nhau
- PP1: Duyệt chay
    - Duyệt từng phần tử trong mảng xem nó có thể cộng với số nào để bằng target
    - Độ phức tạp là O(n^2) 
    - > Ưu điểm: Là cách nghĩ ra đầu tiên  
      > Nhược điểm: Lâu, chậm 
- PP2: Dùng 2 con trỏ chạy từ 2 đầu của mảng
    - Phải sắp xếp trước khi duyệt
    - So tổng cặp đầu cuối với target, nếu lớn hơn target thì tăng đầu và ngược lại, nhỏ hơn target thì giảm cuối
    - Độ phức tạp là O(n logn)
    - > Ưu điểm: Hiệu quả hơn duyệt chay
      > Nhược điểm: + phải sắp xếp trước nên tốn thêm thời gian
                    + nếu phải in ra cả chỉ số từ mảng gốc thì không dùng được
- PP3: Dùng hashmap unordered_map<key,value>...
    - Lấy target trừ từng phần tử, nếu tìm thấy hiệu đó trong hashmap thì đó là cặp cần tìm
    - Nếu tìm không thấy hiệu đó thì lưu vào hashmap
    - Độ phức tạp là O(n) 
    - > Đây là cách tối ưu nhất 
### 🧑‍💻 Code C++
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int k = 1;
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[i] != nums[k - 1]) {
            if (k != i) {
                 nums[k] = nums[i];
            }
            k++;
        }
    }
    return k;

    }
};
```
