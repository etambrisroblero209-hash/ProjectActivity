#ProjectActivity

Task 1: 
```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

struct Player {
    string first_name;
    string last_name;
    string team;
};

vector<string> findCommonPlayers(
    vector<Player>& basketball,
    vector<Player>& football
) {
    unordered_set<string> names;
    vector<string> result;

    
    for (const Player& p : basketball) {
        names.insert(p.first_name + " " + p.last_name);
    }

    
    for (const Player& p : football) {
        string fullName = p.first_name + " " + p.last_name;
        if (names.count(fullName)) {
            result.push_back(fullName);
        }
    }

    return result;
}

int main() {
    vector<Player> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
    };

    vector<Player> football_players = {
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };

    vector<string> common = findCommonPlayers(basketball_players, football_players);

    for (const string& name : common) {
        cout << name << endl;
    }

    return 0;
} 

output: Jill Huang
        Wanda Vakulskas

Task 2: 
Formula used: N * (N + 1) / 2

#include <iostream>
#include <vector>
using namespace std;

int findMissingNumber(vector<int>& arr) {
    int n = arr.size();     
    int expectedSum = n * (n + 1) / 2;
    int actualSum = 0;

    for (int num : arr) {
        actualSum += num;
    }

    return expectedSum - actualSum;
}

int main() {
    vector<int> nums1 = {2, 3, 0, 6, 1, 5};
    vector<int> nums2 = {8, 2, 3, 9, 4, 7, 5, 0, 6};

    cout << findMissingNumber(nums1) << endl; // 4
    cout << findMissingNumber(nums2) << endl; // 1

    return 0;
}

Task 3: 

#include <iostream>
#include <vector>
using namespace std;

int maxProfit(vector<int>& prices) {
    int minPrice = prices[0];
    int maxProfit = 0;

    for (int i = 1; i < prices.size(); i++) {
        if (prices[i] < minPrice) {
            minPrice = prices[i];
        } else {
            int profit = prices[i] - minPrice;
            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }
    }

    return maxProfit;
}

int main() {
    vector<int> prices = {10, 7, 5, 8, 11, 2, 6};

    cout << maxProfit(prices) << endl; // 6

    return 0;
}

Task 4: 

#include <iostream>
#include <vector>
using namespace std;

int highestProductOfTwo(vector<int>& nums) {
    int max1 = INT_MIN, max2 = INT_MIN;
    int min1 = INT_MAX, min2 = INT_MAX;

    for (int n : nums) {
        
        if (n > max1) {
            max2 = max1;
            max1 = n;
        } else if (n > max2) {
            max2 = n;
        }

        
        if (n < min1) {
            min2 = min1;
            min1 = n;
        } else if (n < min2) {
            min2 = n;
        }
    }

    return max(max1 * max2, min1 * min2);
}

int main() {
    vector<int> nums = {5, -10, -6, 9, 4};

    cout << highestProductOfTwo(nums) << endl; // 60

    return 0;
}

Task 5: 
#include <iostream>
#include <vector>
using namespace std;

void sortTemperatures(vector<double>& temps) {
    
    vector<int> count(21, 0);

    
    for (double t : temps) {
        int index = (int)(t * 10) - 970;
        count[index]++;
    }

    
    int i = 0;
    for (int j = 0; j < 21; j++) {
        while (count[j] > 0) {
            temps[i++] = (j + 970) / 10.0;
            count[j]--;
        }
    }
}

int main() {
    vector<double> temps = {
        98.6, 98.0, 97.1, 99.0, 98.9,
        97.8, 98.5, 98.2, 98.0, 97.1
    };

    sortTemperatures(temps);

    for (double t : temps) {
        cout << t << " ";
    }

    return 0;
}

Task 6: 
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

int longestConsecutive(vector<int>& nums) {
    unordered_set<int> s(nums.begin(), nums.end());
    int longest = 0;

    for (int num : nums) {
        
        if (s.count(num - 1) == 0) {
            int currentNum = num;
            int length = 1;

            while (s.count(currentNum + 1)) {
                currentNum++;
                length++;
            }

            longest = max(longest, length);
        }
    }

    return longest;
}

int main() {
    vector<int> nums1 = {10, 5, 12, 3, 55, 30, 4, 11, 2};
    vector<int> nums2 = {19, 13, 15, 12, 18, 14, 17, 11};

    cout << longestConsecutive(nums1) << endl; 
    cout << longestConsecutive(nums2) << endl; 

    return 0;
}


'''cpp
video: https://youtu.be/HjynH29D1NE
