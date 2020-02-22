Leetcode15.三数之和

给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。
注意：答案中不可以包含重复的三元组。
例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
满足要求的三元组集合为：
[
[-1, 0, 1],
[-1, -1, 2]
]

class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        for (int i = 0; i < nums.length - 2; i++) {
            int j = i + 1;
            int k = nums.length - 1;
            while (j < k) {
                while (j < k && nums[i] + nums[j] + nums[k] < 0) {
                    j++;
                }
                if (j >= k) {
                    break;
                }
                if (nums[i] + nums[j] + nums[k] == 0) {
                    List<Integer> e = new ArrayList<>();
                    e.add(nums[i]);
                    e.add(nums[j]);
                    e.add(nums[k]);
                    result.add(e);
                    while (j < k && nums[j] == nums[j + 1]) {
                        j++;
                    }
                    j++;
                }

                while (j < k && nums[i] + nums[j] + nums[k] > 0) {
                    k--;
                }
                if (j >= k) {
                    break;
                }
                if (nums[i] + nums[j] + nums[k] == 0) {
                    List<Integer> e = new ArrayList<>();
                    e.add(nums[i]);
                    e.add(nums[j]);
                    e.add(nums[k]);
                    result.add(e);
                    while (j < k && nums[k] == nums[k - 1]) {
                        k--;
                    }
                    k--;
                }
            }
            while (i < nums.length - 2 && nums[i] == nums[i + 1]) {
                i++;
            }
        }
        return result;
    }
}
