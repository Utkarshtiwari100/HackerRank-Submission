# HackerRank-Submission


1. Sales by Match

public static int sockMerchant(int n, List<Integer> socks) {
    Map<Integer, Integer> sockCounts = new HashMap<>();
     // Count the occurrences of each color in the ArrayList
     for (int sock : socks) {
     sockCounts.put(sock, sockCounts.getOrDefault(sock, 0) + 1);
     }
     int totalPairs = 0;
     for (int count : sockCounts.values()) {
     totalPairs += count / 2;
     }
     return totalPairs;

    }


2. Simple Array Sum

public static int simpleArraySum(List<Integer> ar) {
        int sum = 0;
        for(Integer ans : ar) sum += ans;
        return sum;

 }

3. Breaking the Records

public static List<Integer> breakingRecords(List<Integer> scores) {
        int max = scores.get(0);
        int min = scores.get(0);
        
        int countMax = 0;
        int countMin = 0;
        
        int n = scores.size();
         
        for(int i=1; i<n; i++) {
            int curr = scores.get(i);
            
            if(curr > max) {
                // update max
                max = curr;
                countMax++;
            }
            
            if (curr < min) {
                min = curr;
                countMin++;
            }
        }
        
        List<Integer> result = new ArrayList<>();
        result.add(countMax);
        result.add(countMin);
        return result;

    }

4. Number Line Jumps

public static String kangaroo(int x1, int v1, int x2, int v2) {
     if (v1 == v2) return "NO";

     int temp = (x2 - x1) / (v1 - v2);

    if (temp >= 0 && (x1 + v1 * temp) == (x2 + v2 * temp)) return "YES"; 
    return "NO";

    }

5. Staircase

public static void staircase(int n) {
        for(int row=1; row<=n; row++){
            for(int col=1; col<=n-row; col++){
                System.out.print(" ");            
            }
            for(int col=1; col<=row; col++) {
                System.out.print("#");
            }
        System.out.println();
        }
    }


6. Compare the Triplets

public static List<Integer> compareTriplets(List<Integer> a, List<Integer> b) {
        int alice=0;
        int bob=0;
        for(int i=0; i<a.size(); i++) {
            int ai = a.get(i);
            int bi = b.get(i);
            // case 1
            if(ai > bi) {
                alice++;
            }
            // case 2
            if (ai < bi) {
                bob++;
            }
            
            // case 3 - both have same number do nothing
        }
        
        List<Integer> result = new ArrayList<>();
        result.add(alice);
        result.add(bob);
        return result;
    }

7. Quicksort 1 - Partition

public static List<Integer> quickSort(List<Integer> arr) {
        if (arr == null || arr.size() <= 1) {
            return arr;
        }

        List<Integer> less = new ArrayList<>();
        List<Integer> equal = new ArrayList<>();
        List<Integer> greater = new ArrayList<>();

        int pivot = arr.get(arr.size() / 2);

        for (int num : arr) {
            if (num < pivot) {
                less.add(num);
            } else if (num > pivot) {
                greater.add(num);
            } else {
                equal.add(num);
            }
        }

        List<Integer> sorted = new ArrayList<>();
        sorted.addAll(quickSort(less));
        sorted.addAll(equal);
        sorted.addAll(quickSort(greater));

        return sorted;

    }
8. Between Two Sets

public static int getTotalX(List<Integer> a, List<Integer> b) {
        int minA = a.stream().mapToInt(Integer::intValue).max().orElse(0);
        int maxB = b.stream().mapToInt(Integer::intValue).min().orElse(Integer.MAX_VALUE);
        int count = 0;

        for (int num = minA; num <= maxB; num++) {
            final int finalNum = num; 
            boolean isFactorOfA = a.stream().allMatch(x -> finalNum % x == 0);
            boolean isFactorOfB = b.stream().allMatch(y -> y % finalNum == 0);
            
            if (isFactorOfA && isFactorOfB) count++;
        }
        return count;
    }

9. Super Reduced String

public static String superReducedString(String s) {
        StringBuilder sb = new StringBuilder(s);
        int i = 0;
        while (!sb.isEmpty() && i < sb.length()) {
            if (i+1 < sb.length() && sb.charAt(i) == sb.charAt(i+1)) {
                sb.deleteCharAt(i+1);
                sb.deleteCharAt(i);
                if (i > 0) {
                    i--;
                }
            }
            else {
                i++;
            }
        }
        if (sb.isEmpty()) {
            return "Empty String";
        }
        return sb.toString();

    }

10. Bill Division

public static void bonAppetit(List<Integer> bill, int k, int b) {
        Integer temp = bill.get(k);
    
        int sum=0;
        for(Integer val : bill) {
            sum += val;
        }
        sum -= temp;

        sum /= 2;

        if (b - sum > 0) {
            System.out.println(b-sum);
        } else {
            System.out.println("Bon Appetit");
        }

    }
11. A Very Big Sum in C++

long aVeryBigSum(vector<long> ar) {
    long res = 0;
    auto f = [&](long x) { 
        res+=x;
    };
    for_each(ar.begin(), ar.end(), f); 
    return res;
}

12. Plus Minus in C++

void plusMinus(vector<int> arr) {
    float length = arr.size();
    float positive= 0;
    float negative=0;
    float zero =0;
    
    for (int i = 0; i< length; i++) {
    if(arr[i] > 0){
        positive += 1;    
    }
    else if(arr[i] < 0){
        negative += 1;
    }
    else{
        zero += 1;
    }
    }
    
    cout <<fixed <<setprecision(6) <<(positive/length) << endl << (negative/length) 
    << endl << (zero/length) << endl;
    
    return;
}

13. Subarray Division in C++

int birthday(vector<int> s, int d, int m) {
        if (s.size() < m) { 
            return 0; 
        } else {
        int sum {};
        int count {};
        for (int i=0; i<=s.size()-m; i++) {
            if (sum == 0) {
                for (int j=0; j<m; j++) {
                    sum += s[j];
                }
            } else {
              sum -= s[i-1];  
              sum += s[i-1+m];  
            }
            
            if (sum == d) count++;
        }
        return count;
        }
}

14. Migratory Birds

int migratoryBirds(vector<int> arr) {
    int len=arr.size();
    vector<int> v(len,0);
    for(int i=0;i<len;i++){
        v[arr[i]-1]++;
    }
    int max=v[0];
    int index=0;
    for(int i=1;i<len;i++){
        if(v[i]>max) {max=v[i];
        index=i;}
    }
    return index+1;
}

15. Diagonal Difference

int diagonalDifference(vector<vector<int>> arr) {
    int leftDiff =0;
        int rightDiff=0;
        int n = arr.size();

    for (int i = 0; i<n; i++) {
        leftDiff += arr[i][i];
        rightDiff += arr[i][n -1 -i];
    }    

    return(abs(leftDiff-rightDiff));
}

16. Birthday Cake Candles in C++

int birthdayCakeCandles(vector<int> candles) {
       int n = candles.size();
       int count=0;
       sort(candles.begin(), candles.end());
       int tallest = candles[n-1];
       
       for(int i=0; i<n; i++)
        {
            if(candles[i] == tallest) count++;
        }
        return count;
}


17. Grading Students


vector<int> gradingStudents(vector<int> grades) {
    vector<int> result;
    for(int i = 0; i < grades.size(); i++){
        int mo = grades[i] % 5;
        if(mo < 3 || grades[i] < 38) result.push_back(grades[i]);
        else result.push_back(grades[i] - mo + 5);
    }
    return result;
}

18. Drawing Book

int pageCount(int n, int p) {
    int flip = p/2;  
    if(flip > n/4) flip = n/2 - flip; 
    return flip;
}


19. Divisible Sum Pairs
int divisibleSumPairs(int n, int k, vector<int> ar) {
    vector<int> ans(k, 0);
    int validPairs = 0;
    for (int i = 0; i < n; i++) {
        int remainder = ar[i] % k;
        int complement = (k - remainder) % k;
        validPairs += ans[complement];
        ans[remainder]++;
    }
    return validPairs;
}

20.  Mini-Max Sum

void miniMaxSum(vector<int> arr) {
int length = arr.size();
long long maxele = *max_element(arr.begin(), arr.end());// find the higest value element 
long long minele = *min_element(arr.begin(), arr.end());// find the lowest value element
long long totalsum = 0;

for (int i =0; i < length; i++){
    totalsum +=arr[i];
}

cout << (totalsum -maxele) << ' ' << (totalsum - minele);
}

21. Counting Valleys

int countingValleys(int steps, string path) {
    int res = 0, level = 0;
    for(char c : path){
        if(c == 'U'){
            level++;
            if(level == 0) res ++;
        }
        else level--;
    }
    return res;
}

22. Library Fine

int libraryFine(int d1, int m1, int y1, int d2, int m2, int y2) {
    int res = 0;
    if(y1<y2 || (y1 == y2 && m1<m2) || (y1 == y2 && m2 == m1 && d1<=d2)) return 0;
    if(y2 == y1){
        if(m1 == m2) return 15 * (d1 - d2);
        else return (m1 - m2) * 500;
    }
    else return 10000;
    return 0;
}

23. Time Conversion

string timeConversion(string s) {
    if(s[s.length()-2]=='A'){
            if(s[0]=='1'&&s[1]=='2'){
                s[0]='0';
                s[1]='0';
            }
        }
        else if(s[s.length()-2]=='P'){
            if(s[0]=='0'&&s[1]-'0'<=7){
                s[0]='1';
                s[1]=((s[1]-'0')+2)+'0';
            }
            else if(s[0]=='0'&&s[1]-'0'<=9){
                s[0]='2';
                s[1]=((s[1]-'0')-8)+'0';
            }
            else if(s[0]=='1'&&s[1]-'0'<2){
                s[0]='2';
                s[1]=((s[1]-'0')+2)+'0';
            }
        }
        return s.substr(0,8);

}

24. Caesar Cipher

string caesarCipher(string s, int cipher) {
    for(char &c:s) {
           if(isalpha(c)){
               char a = isupper(c)? 'A':'a';
               c = a + (c - a + cipher) % 26;
           }
       }
     return s;
}

25. Tower Breakers

int towerBreakers(int n, int m) {
    if(m == 1) return 2;
    return n % 2 == 1 ? 1 : 2;
}

26. Day of the Programmer

string dayOfProgrammer(int year) {
    string s;
    if(year>=1700 && year<=1917){
        if(year%4==0){//leap years
            s="12.09."+std::to_string(year);
        }
        else{
            s="13.09."+std::to_string(year);
        }
    }
    else if(year==1918){
        s="26.09."+std::to_string(year);
    }
    else if(year>=1919){
        if(year%400==0||(year%4==0&&year%100!=0)){//leap year
            s="12.09."+std::to_string(year);
        }
        else{
            s="13.09."+std::to_string(year);
        }
    }
    return s;
}

27. The Hurdle Race

int hurdleRace(int k, vector<int> height) {
     int mx = *max_element(height.begin(), height.end());
     return max(0, mx-k);
}

28. Strong Password

char getNature(char c){
    if(c >= '0' && c <='9') return 'n';
    if(c >= 'a' && c <= 'z') return 'l';
    if(c >= 'A' && c <= 'Z') return 'u';
    return 's';
}
int minimumNumber(int n, string password) {
    // Return the minimum number of characters to make the password strong
    map<char, int> mp;
    for(char c: password){
        mp[getNature(c)] = 1;
    }
    return max(4 - (int)mp.size(), 6 - n); 

}

29. Minimum Absolute Difference in an Array


int minimumAbsoluteDifference(vector<int> vec) {
    int n = vec.size();
    sort(vec.begin(), vec.end());
    int diff = abs(vec[0] - vec[1]);
    int sub;
    for(int i=0; i<(n-1); i++){
            sub = abs(vec[i] - vec[i+1]);
        if(sub < diff)
            diff = sub;
    }
    return diff;
}

30. Mars Exploration

int marsExploration(string s) {
    int result = 0;
    string base = "SOS";
    for(int i = 0; i < s.size(); i++) if(s[i] != base[i%3]) result++;
    return result;
}

31. Electronics Shop

int getMoneySpent(vector<int> keyboards, vector<int> drives, int b) {
    int maxPrice = 0;
    for (int i = 0; i < keyboards.size(); i++) {
        for(int j = 0; j < drives.size();j++){
            if(keyboards[i] + drives[j] >= maxPrice && keyboards[i] + drives[j] <= b){
                int temp = keyboards[i] + drives[j];
                if(temp > maxPrice){
                maxPrice = temp;
                }
            }
        }
    }
    if (maxPrice > 0) {
        return maxPrice;
    }else{
        return -1;
    }

}

32. CamelCase

int camelcase(string s) {
    int r = 1;
    for(int i = 0; i < s.size(); i++) {
        if(s[i] < 'a') r++;
    }
    return r;
}

33. Viral Advertising

int viralAdvertising(int n) {
     int ans = 0, shared = 5;
    for(int i = 1; i <= n; i++){
        ans += shared / 2;
        shared = (shared/2)*3;
    }
    return ans;
}

34. Jumping on the Clouds: Revisited

int jumpingOnClouds(vector<int> c, int k) {
    int position = 0, energie = 100;
        do{
            position = (position + k) % c.size();
            energie -= 1 + c[position] * 2;
        }while(position != 0);
        return energie;

}

35. Game of Stones

int dp[101][2];

int solve(int n, int p){
    if(n==1){
        return dp[1][p]=!p;
    }
    if(n>=2 && n<=6){
        return dp[n][p]=p;
    }
    if(dp[n][p]!=-1)return dp[n][p];

    int op1 = solve(n-5,!p);
    int op2 = solve(n-3,!p);
    int op3 = solve(n-2,!p);

    if(op1==p || op2==p || op3==p){
        return dp[n][p]=p;
    }
    return dp[n][p]=!p;
} 
string gameOfStones(int n) {
    for(int i=1;i<=n;i++){
        for(int j=0;j<2;j++) dp[i][j]=-1;
    } 
    int res = solve(n,1);
    if(res==1)return "First";
    return "Second";
}

36. Marc's Cakewalk

long marcsCakewalk(vector<int> calorie) {
    sort(calorie.begin(), calorie.end(), [](int l, int r){return l > r;});
        long ans = 0;
        for(int i = 0; i < calorie.size(); i++){
            ans += pow(2, i) * calorie[i];
        }
        return ans;
}

37. Cats and a Mouse

string catAndMouse(int x, int y, int z) {
 int a = abs(x-z), b = abs(y-z);
    if(a==b) return "Mouse C";
    if(a < b) return "Cat A";
    return "Cat B";
}

38. Save the Prisoner!

int saveThePrisoner(int n, int m, int s) {
 return (m - 1  + s - 1 ) % n + 1;
}

39. Beautiful Days at the Movies

int beautifulDays(int i, int j, int k) {
int ans = 0;
    for(int el = i; el <= j; el++){
        string s = to_string(el);
        reverse(s.begin(), s.end());
        if(abs(stoi(s) -el ) % k == 0) ans++;
    }
    return ans;
}

40. Sequence Equation

vector<int> permutationEquation(vector<int> p) {
 vector<int> indexes(p.size() + 1), result;
    for(int i = 1; i <= p.size(); i++) indexes[p[i-1]] = i;
    for(int i = 1; i <= p.size(); i++) result.push_back(indexes[indexes[i]]);
    return result;
}

41. Grid Challenge

string gridChallenge(vector<string> grid) {
for(int i = 0; i < grid.size(); i++) sort(grid[i].begin(), grid[i].end());
    for(int col = 0; col < grid.size(); col++){
       for(int row = 1; row < grid.size(); row++)
            if(grid[row][col] < grid[row-1][col]) return "NO";
    }
    return "YES";
}

42. Angry Professor

string angryProfessor(int k, vector<int> a) {
    int attendees = 0;
    for(int el: a) if(el <= 0) attendees++;
    return attendees >= k ? "NO":"YES";
}

43. Sherlock and Squares


int find_base(const pair<int,int> & range)
{
    int lo = 1;
    int hi = range.second;

    int mid;

    while(lo <= hi)
    {
        mid = lo + (hi - lo) / 2;

        if(mid >= range.first * 1.0 / mid) 
        {
            // in range
            if(mid <= range.second * 1.0 / mid) return mid;
            else hi = mid - 1; // bigger than range
        }
        else lo = mid + 1;   // small than range
    }

    // out of range
    return 0;
}


int squares(int a, int b) {
    // find square in [a,b]

    // base range : [1,b]

    // binary_search in [1,b] find a base or cant 
    int base = find_base({a,b});


    if(base == 0) return 0;

    int count = 1;
    int lo = base - 1;
    int hi = base + 1;

    for(;lo >=0;lo--)
    {
        if(a * 1.0 / lo <= lo && b * 1.0 / lo >= lo) count++;
        else break;
    }

    for(;hi <= b;hi++)
    {
        if(a * 1.0 / hi <= hi && b * 1.0 / hi >= hi) count++;
        else break;
    }

    return count;
}

44. Circular Array Rotation

vector<int> circularArrayRotation(vector<int> a, int k, vector<int> queries) {
    int x =a.size() - k %(a.size());
    int i = 0; for (int y : queries) queries[i++] = a[(y+x)%a.size()];
    return queries;
}

45. Big Sorting

vector<string> bigSorting(vector<string> unsorted) {
    sort(unsorted.begin(), unsorted.end(), [](string l, string r){
        if(l.size() == r.size()) return l < r;
        return l.size() < r.size();
    });
    return unsorted;
}

46. Equalize the Array


int equalizeArray(vector<int> arr) {
    sort(arr.begin(),arr.end());
    int count = 0, j = 0;
    for(int i = 1; i<arr.size(); i++){
        if(arr[j] != arr[i]){
            j++;
            count++;
        }
    }
    return count;
}

47. Minimum Distances

int minimumDistances(vector<int> a) {
 vector <int> x(100001, INT_MAX);
    int ret = INT_MAX;
    for (int i = 0; i < a.size(); ++i) {
        ret = min(ret, abs(i - x[a[i]]));
        x[a[i]] = i;
    }
    return ret > 1000 ? -1 : ret;
}

48. Separate the Numbers

void separateNumbers(string s) {
    int bl = 1;
    bool f = false;
    while(bl * 2 <= s.size()){
        string base = s.substr(0, bl);
        string newString = "";
        long baselong = atol(base.c_str());
        do{
            newString += to_string(baselong);
            baselong++;
        }while(newString.size() < s.size());
        if(newString == s) {cout << "YES " << base;f = true;break;}
        bl++;
    }
    if(!f) cout << "NO";
    cout << endl;
}

49. The Love-Letter Mystery

int theLoveLetterMystery(string s) {
    int ans = 0 , start = 0, end = s.size() - 1;
    while(start < end){
        ans += abs(s[start] - s[end]);
        start++; end--;
    }
    return ans;
}

50. Halloween Sale

int howManyGames(int p, int d, int m, int s) {
    // Return the number of games you can buy
    if( s < p) return 0;
    return howManyGames( max(m, p-d), d, m, s - p) + 1;
}

51. Maximum Perimeter Triangle

vector<int> maximumPerimeterTriangle(vector<int> sticks) {
sort(sticks.begin(), sticks.end());
    for(int i = sticks.size() - 1; i >= 2; i--){
        if(sticks[i] < sticks[i - 1] + sticks[i - 2]) return {sticks[i - 2], sticks[i -1], sticks[i] };
    }
    return {-1};
}

52. Alternating Characters

int alternatingCharacters(string s) {
    regex re("A{2,}|B{2,}");
    return s.size() - regex_replace(s, re, "*").size();
}

53. Pangrams

string pangrams(string s) {
    vector<int> c(26, 0);
    for(int i = 0; i < s.size(); i++){
        if(s[i] != ' ')
        c[tolower(s[i]) - 'a']++;
    }
    string r = "pangram";
    for(int i = 0; i < c.size(); i++){
        if(c[i] == 0){
            r = "not " + r;
            break;
        }
    }
    return r ;
}

54. Beautiful Binary String

int beautifulBinaryString(string b) {
    int ans = 0;
    for(int i = 0; i < b.size();){
        string sub = b.substr(i, 3);
        if(sub == "010") {
            ans++;
            i+=3;
        }else i++;
    }
    return ans;
}

55. Utopian Tree

int utopianTree(int n) {
    int height =1;
    for (int i = 1; i <= n; i++) {
        if(i%2!=0){
            height = height*2;
        }
        else{
            height = height+1;
        }
    }
    return height;
}

56. Beautiful Triplets

int beautifulTriplets(int d, vector<int> arr) {
    map<int, int> mp;
    int result = 0;
    for (int a : arr) {
        mp[a] += 1;
        result += mp[a-d]*mp[a-2*d];
    }
    return result;
}

57. Picking Numbers

int pickingNumbers(vector<int> a) {
    sort(a.begin() ,a.end());
    int prev_count=0;
    int count=1;
    int min=a[0];
    for(int i=1;i<a.size();i++)
    {
        
        if ((a[i]==min+1 ) || (a[i]==min))
            count++;
        else if(prev_count<=count)
           { prev_count=count;
            min=a[i];
            count=1;
           }
    }
    if(prev_count==0) 
        return count;
    return prev_count;
}

58. Repeated String

long f(string s) {
    return count(s.begin(), s.end(), 'a');
}

long repeatedString(string s, long n) {
     return (n / s.size()) * f(s) + f(s.substr(0, n % s.size()));
}

59. HackerRank in a String!

string hackerrankInString(string s) {
     string target ="hackerrank";
    int currentIndex = 0;    
    for(int i = 0; i < s.size(); i++){
        if(s[i] == target[currentIndex]){
            currentIndex++;
            if(currentIndex == target.size()) return "YES";
        }
    }
    return "NO";
}

60. Designer PDF Viewer

int designerPdfViewer(vector<int> h, string word) {
    int mx = 0;
    for(int el : word) if(h[el - 'a'] > mx) mx = h[el - 'a'];
    return mx * 1 * word.size();
}

61. Service Lane

vector<int> serviceLane(int n, vector<vector<int>> cases) {
    vector<int> result;
    for(auto cas: cases){
        int r = width[cas[0]];
        for(int i = cas[0]; i <= cas[1]; i++){
            r = min(r, width[i]);
        }
        result.push_back(r);
    }
    return result;
}

62. Service Lane

vector<int> serviceLane(int n, vector<vector<int>> cases) {
    vector<int> result;
    for(auto cas: cases){
        int r = width[cas[0]];
        for(int i = cas[0]; i <= cas[1]; i++){
            r = min(r, width[i]);
        }
        result.push_back(r);
    }
    return result;
}

63. Service Lane

vector<int> serviceLane(int n, vector<vector<int>> cases, vector<int> width) {
    vector<int> result;
    for(auto cas: cases){
        int r = width[cas[0]];
        for(int i = cas[0]; i <= cas[1]; i++){
            r = min(r, width[i]);
        }
        result.push_back(r);
    }
    return result;
}

64. Lonely Integer

int lonelyinteger(vector<int> a) {
    sort(a.begin() , a.end()) ;

    int num ;
    int len = a.size() ;
    if(len == 1 ){
        return a[0] ;
    }
    for(int i = 0 ; i < len -1 ; i+=2 ){

        if(a[i] != a[i+1] ){
            return a[i] ;
        }

    }
    return a[len-1] ;
}

65. Lonely Integer

int lonelyinteger(vector<int> a) {
    sort(a.begin() , a.end()) ;

    int num ;
    int len = a.size() ;
    if(len == 1 ){
        return a[0] ;
    }
    for(int i = 0 ; i < len -1 ; i+=2 ){

        if(a[i] != a[i+1] ){
            return a[i] ;
        }

    }
    return a[len-1] ;
}

66. Luck Balance

int luckBalance(int k, vector<vector<int>> contests) {
sort(contests.begin(), contests.end(), [](vector<int> l, vector<int>r){
        return l[0] > r[0];
    });
    int ans = 0, im = 0;
    for(int i = 0; i < contests.size(); i++){
        if(im < k || contests[i][1] == 0) ans += contests[i][0];
        else ans -= contests[i][0];
        if(contests[i][1] == 1) im++;
    }
    return ans;
}


67. Append and Delete

string appendAndDelete(string s, string t, int k) {
    if(k >= t.size() + s.size()) return "Yes";
    int same = min(t.size(), s.size());
    for(int i = 0; i< min(t.size(), s.size()); i++){
        if(s[i] != t[i]){
            same = i;
            break;
        }
    }
    k -= (s.size() - same);
    k -= (t.size() - same);
    return (k >= 0 && k%2 == 0)? "Yes":"No";
}

68. Misère Nim

string misereNim(vector<int> s) {
    int n =s.size();
    int xr = 0;
    int sum = 0;

    for(int i=0;i<n;i++){
        xr ^= s[i];
        sum += s[i];
    }

    if(n % 2 == 0){
        return n != sum && xr == 0 ? "Second" : "First";
    }else{
        return n == sum || xr == 0 ? "Second" : "First";
    }
}

69. Jumping on the Clouds

int jumpingOnClouds(vector<int> c) {
    int result = 0, index = 0;
    while(index < c.size() - 1){
        if(c[index + 2] == 1) index++;
        else index+=2;
        result++;
    }
    return result;
}

70. Gemstones

string getShortest(vector<string> arr) {
    string result = arr[0];
    for(int i = 1; i < arr.size(); i++){
        if(arr[i].size() < result.size()) result = arr[i];
    }
    return result;
}

int gemstones(vector<string> arr) {
    int result = 0;
    string shortest = getShortest(arr);
    set<char> liste(shortest.begin(), shortest.end());
    for(auto j = liste.begin(); j != liste.end(); j++){
        int cp = 0;
        for(int i = 0; i < arr.size(); i++){
            if(arr[i].find(*j) != string::npos) cp++;
        }
        if(cp == arr.size())result++;
    }
    return result;
}

71. Two Strings

string twoStrings(string s1, string s2) {
    map<char, int>mp;
    for(int i = 0; i < s1.size(); i++) mp[s1[i]] = 1;
    for(int i = 0; i < s2.size(); i++){
        if(mp[s2[i]]) return "YES";
    }
    return "NO";
}

72. Chocolate FeastChocolate Feast

int chocolateFeast(int n, int c, int m) {
    int result = 0, wrappers = 0;
    while( n >= c){
        result ++;
        wrappers ++;
        n -= c;
        if(wrappers == m){
            result ++;
            wrappers = 1;
        }
    }
    return result;
}

73. ACM ICPC Team

vector<int> acmTeam(vector<string> topic) {
    int h = 0, cp = 0;
    for(int i = 0; i < topic.size() - 1; i++){
        bitset<500> a = bitset<500>(topic[i]);
        for(int j = i + 1; j < topic.size(); j++){
         bitset<500> b = bitset<500>(topic[j]);
         bitset<500> c = a | b;
         int x = c.count();
         if( x > h){h = x; cp = 1;}
         else if( x == h) cp++;
        }
    }
    return {h, cp};
}

74. Taum and B'day

long taumBday(int b, int w, int bc, int wc, int z) {
    long bp = min(bc, wc + z);
    long wp = min(wc, bc + z);
    return bp * b + wp * w;
}

75. Funny String

 string r = s;
    reverse(r.begin(), r.end());
    for(int i = 1; i < s.size(); i++){
        if(abs(s[i]-s[i-1]) != abs(r[i]- r[i-1])) return "Not Funny";
    }
    return "Funny";

76. Sum vs XOR

long r = 1;
    for (; n; n >>= 1) if (0 == (n & 1)) r *= 2;
    return r;

77. String Construction

 set<char> se(s.begin(), s.end());
    return se.size();

78. Find Digits

int result = 0, original = n;
    while(n){
        int d = n % 10;
        if(d != 0 && original % d == 0) result ++;
        n /= 10;
    }
    return result;

79. Palindrome Index

bool caller(string& str)
{
    int len=str.size();
    for(int i=0;i<str.size()/2;i++)
    {
        if(str[i]!=str[len-i-1])
        return false;
    }
    return true;
}
int palindromeIndex(string s) {
    int len = s.size();
    for(int i=0;i<s.size()/2;i++)
    {
        if(s[i]!=s[len-i-1])
        {
            if(i+1<len)
            {
                string str=s.substr(i+1,len-i-(i+1));
                bool check=caller(str);
                if(check)
                return i;
                return len-i-1;
            }
        }
    }
    return -1;
}

80. Lisa's Workbook

int page = 1, chapter = 1, fe = 1, res = 0;
    while(chapter <= arr.size()){
        int le = min(fe + k - 1, arr[chapter-1]);
        if(fe <= page && page <= le) res++;
        fe = le + 1;
        if(fe > arr[chapter-1]) {
            chapter++;
            fe = 1;
        }
        page ++;
    }   
    return res;

81. Smart Number

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

bool is_smart_number(int num) {
    int val = (int) sqrt(num);
    if(num / val == 1)
        return true;
    return false;
}

int main() {
    
    int test_cases;
    cin >> test_cases;
    int num;
    for(int i = 0; i < test_cases; i++) {
        cin >> num;
        bool ans = is_smart_number(num);
        if(ans) {
            cout << "YES" << endl;
        }
        else cout << "NO" << endl;
    }
    return 0;
}



82. XOR Strings

string res = "";
for(int i = 0; i < s.size(); i++) {
    if(s[i] == t[i])
        res += '0';
    else
        res += '1';
}

return res;

83. Fair Rations


int res = 0;
    for(int i = 0; i < B.size() - 1; i++){
        if(B[i] % 2 == 1){
            B[i+1]++;
            res+=2;
        }
    }
    return B[B.size() - 1] % 2 == 0 ? to_string(res) : "NO";

84. Anagram

if(s.size() % 2 == 1) return -1;
    map<char, int> mp;
    int ans = 0;
    for(int i = 0; i < s.size() / 2; i++) mp[s[i]]++;
    for(int i = s.size() / 2; i < s.size(); i++){
        if(mp[s[i]] != 0) mp[s[i]]--;
        else ans++;
    }
    return ans;


85. Cut the sticks


 sort(arr.begin(), arr.end());
    vector<int>result(1, arr.size());
    for(int i = 1; i < arr.size(); i++){
      if(arr[i-1] != arr[i]) result.push_back(arr.size() - i);
    }
    return result;

86. Modified Kaprekar Numbers

int getSum(long a){
    long sq = a * a;
    int digit = (int)log10(a) + 1;
    int result = sq % (int)pow(10, digit);
    int rest = (int)log10(sq) + 1 - digit;
    if(rest > 0) result += stoi(to_string(sq).substr(0, rest));
    return result;
}
void kaprekarNumbers(int p, int q) {
    bool valid_range = false;
    for(int i = p; i <= q; i++){
        int s = getSum(i);
        if(s == i){
           cout << i << " ";
           valid_range = true; 
        }  
    }
    if(!valid_range) cout << "INVALID RANGE";
}

87. Sherlock and The Beast

 int three = ((3 - (n % 3)) % 3 ) * 5;
    if(three > n) cout << -1;
    else cout << string(n - three, '5') << string(three, '3');
    cout << endl;

88. Game of Thrones - IGame of Thrones - I
map<char, int> mp;
    for(int i = 0; i < s.size(); i++){
        if(mp[s[i]] == 1)  mp.erase(s[i]);
        else mp[s[i]]++;
    }
    if(mp.size() > 1) return "NO";
    return "YES";

89. Maximizing XOR

int maxres = 0;
    
    for (int i = l; i < r; i++)
    {
        for (int j = l; j <= r; j++)
            maxres = max(maxres, i ^ j);
    }
    return maxres;

90. Happy Ladybugs

vector<int> occ(26, 0);
    bool happy = true, underscore = false;
    b = "0"+b+"0";
    for(int i = 1; i < b.size()-1; i++){
        if(b[i] != '_' && b[i] != b[i-1] && b[i] != b[i+1]) happy = false;
        if(b[i] == '_') underscore = true;
        else occ[b[i] - 'A']++;
    }
    if(happy) return "YES";
    if(underscore && find(occ.begin(), occ.end(), 1) == occ.end()) return "YES";
    return "NO";

91. Counting Sort 1
vector<int> count(100, 0);
    for(int i = 0; i < arr.size(); i++) count[arr[i]]++;
    return count;

92. Priyanka and Toys

sort(w.begin(),w.end());
    int i = 0, sizew = w.size();
    int start = w[0], end = start + 4;
    int container = 1, items = 0;
    while(i < sizew){
        if (start <= w[i] && w[i] <= end){
            i++; items++;
        } else {
            if (items > 0){container++;}
            items = 0; start =  w[i]; end = start + 4;
        }
    }
    return container;

93. Cavity Map

for(int i = 1; i < grid.size() - 1; i++){
        for(int j = 1; j < grid[i].size()-1; j++){
            if(grid[i][j] > grid[i][j-1] && grid[i][j] > grid[i][j+1])
                if(grid[i][j] > grid[i-1][j] && grid[i][j] > grid[i+1][j])
                grid[i][j] = 'X'; 
        }
    }
    return grid;

94. Strange Counter

 long ini=3,time=0;
    while(time<t){
        time+=ini;
        ini*=2;
    }
    
    return time-t+1;

95. Insertion Sort - Part 1

void printArr(vector<int> arr){
    for(int i = 0; i < arr.size(); i++){cout << arr[i] << " ";}
    cout << endl;
}
void insertionSort1(int n, vector<int> arr) {
    int last = arr[arr.size()-1];
    for(int i = arr.size() - 1; i >= 0; i--){
        if(last < arr[i-1]) {
            arr[i] = arr[i-1];
            printArr(arr);
        }
        else{
            arr[i] = last;
            printArr(arr);
            break;
        }
    }
}

96. Making Anagrams

int makingAnagrams(string s1, string s2) {
    vector<int>fsc(26,0), ssc(26,0);
    int i, result = 0;
    for(i = 0; i < s1.size(); i++) fsc[s1[i] - 'a']++;
    for(i = 0; i < s2.size(); i++) ssc[s2[i] - 'a']++;
    for(i = 0; i < 26; i++) result += abs(fsc[i] - ssc[i]);
    return result;
}

97. Correctness and the Loop Invariant

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
void insertionSort2(int n, vector<int> arr) {
    for (int i = 1; i < n; i++) {
        int current = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > current) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = current;
    }
    for(int i = 0; i < n; i++) cout << arr[i] << " ";
        cout << endl;
}

int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */   
    int n;
    cin >> n;
    vector<int> vec(n);
    for(auto &i : vec) cin >> i;
    insertionSort2(n, vec);
    return 0;
}


98. Running Time of Algorithms

int i,j;
    int value;
    int result = 0;
    for(i=1;i<arr.size();i++)
    {
        value=arr[i];
        j=i-1;
        while(j>=0 && value<arr[j])
        {
            arr[j+1]=arr[j];
            j=j-1;
            result ++;
        }
        arr[j+1]=value;
    }
    return result;

99. Insertion Sort - Part 2

for (int i = 1; i < n; i++) {
        int current = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > current) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = current;
        for(int i = 0; i < n; i++) cout << arr[i] << " ";
        cout << endl;
    }

100. Intro to Tutorial Challenges

return distance(arr.begin(), find(arr.begin(), arr.end(), V));

101. Counting Sort 2

vector<int> countingSort(vector<int> arr) {
    vector<int> result, count(100, 0);
    for(int i = 0; i < arr.size(); i++) count[arr[i]]++;
    for(int i = 0; i < 100; i++) result.resize(result.size() + count[i], i);
    return result;
}

102. Manasa and Stones

vector<int> result;
    for(int i = min(a, b) * (n-1); i < max(a,b) * (n-1); i += abs(b - a)) result.push_back(i);
    result.push_back(max(a, b) * (n-1));
    return result;

103. Largest Permutation

 int N = arr.size();
    vector<int> position(N+1);
    for (int i=0; i < N; i++) position[arr[i]] = i;
    int I = 0;
    while (k > 0 and I < N) {
        if (arr[I] != N-I) {
            int temp = arr[I];
            swap(arr[I], arr[position[N-I]]);
            position[temp] = position[N-I];
            position[N-I] = I;
            k--;
        }
        I++;
    }
    return arr;

104. Mark and Toys

sort(prices.begin(), prices.end());
    int out = 0;
    int temp = 0;
    while (k>0) {
        out++;
        k-=prices[temp];
        temp++;
    }
    if(k<0) {
        out--;
    }
    return out;

105. Closest Numbers

sort(arr.begin(), arr.end());
    int diff = INT_MAX;
    vector<int> result;
    for(int i = 1; i < arr.size(); i++){
        if(arr[i] - arr[i-1] < diff){
            diff = arr[i] - arr[i-1];
            result = {arr[i-1], arr[i]};
        }
        else if(arr[i] - arr[i-1] == diff){
            result.insert(result.end(), {arr[i-1], arr[i]});
        }
    }
    return result;

106. Sherlock and Array

int ls = 0, rs = accumulate(arr.begin(), arr.end(), 0);
    for(int i = 0; i < arr.size(); i++){
        rs -= arr[i];
        if(i != 0) ls += arr[i-1];
        if(ls == rs) return "YES";
    }
    return "NO";

107. Flipping bits

 auto num = bitset<32>(n).to_string();
    transform(num.begin(), num.end(), num.begin(),
        [](char c) { return (c == '0' ? '1' : '0'); });
    return bitset<32>(num).to_ulong();

108. Jim and the Orders

vector<pair<int,int>> par;
    for (int i = 0; i < orders.size(); i++)
        par.push_back({orders[i][0] + orders[i][1],i+1});
    sort(par.begin(), par.end());
    vector<int>result;
    for(int i = 0; i < par.size(); i++)
        result.push_back(par[i].second);
    return result;      

109. Permuting Two Arrays

sort(A.begin() , A.end()) ;
sort(B.begin() , B.end() , greater<int>()) ;

int len = A.size() ;
for(int i = 0 ; i < len ; i++ ){
    if(A[i] + B[i] < k) {
        return "NO" ;
    }
}
return  "YES" ;

110. Missing Numbers

int n = arr.size(), m = brr.size();
    map<int, int> mp;
    vector<int> res;
    for(int val : brr) {
        mp[val]++;
    }
    for(int val : arr) {
        mp[val]--;
    }
    // check if any element is still left
    for(auto it : mp) {
        if(it.second > 0)
            res.push_back(it.first);
    }
    return res;

111. Forming a Magic Square

#include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);
vector<string> split(const string &);

/*
 * Complete the 'formingMagicSquare' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts 2D_INTEGER_ARRAY s as parameter.
 */
bool ismagic(vector<vector<int>> temp){
    int MagicNumber = 15; // sum(1-9) / 3 = 15
    for(int i=0;i<3;i++){
        int t1 = 0;
        int t2 = 0;
        for(int j=0;j<3;j++){
            t1 += temp[i][j];
            t2 += temp[j][i];
        }
        if(t1!=MagicNumber || t2!=MagicNumber) return false;
    }
    if(temp[0][0] + temp[1][1] + temp[2][2] != MagicNumber) return false;
    if(temp[2][0] + temp[1][1] + temp[0][2] != MagicNumber) return false;
    return true;
}
void gen(int ind, int mp[], vector<vector<int>>& temp, vector<vector<vector<int>>>& data){
    if(ind == 9){ 
        if(ismagic(temp)) data.push_back(temp);
        return ;
    }
    for(int i =0;i<9;i++){
        if(!mp[i]){
            mp[i]=1;
            int k = ind%3;
            int j = ind/3;
            temp[j][k] = i+1;
            gen(ind+1,mp,temp,data);
            temp[j][k] = 0;
            mp[i]=0;
        }
    }
}
int formingMagicSquare(vector<vector<int>> s) {
    vector<vector<vector<int>>> data;
    vector<vector<int>> temp(3,vector<int>(3,0));
    int mp[9] = {0};
    gen(0,mp,temp,data);
    int Mini = INT_MAX;
    int M = data.size();
    for (int m = 0;m < M;m++) {
        int t = 0;
        for(int i=0;i<3;i++){
            for(int j=0;j<3;j++){
                t += abs(data[m][i][j] - s[i][j]);
            }   
        }     
        Mini = min(Mini,t);
    }
    return Mini;
}

int main()
{
    ofstream fout(getenv("OUTPUT_PATH"));

    vector<vector<int>> s(3);

    for (int i = 0; i < 3; i++) {
        s[i].resize(3);

        string s_row_temp_temp;
        getline(cin, s_row_temp_temp);

        vector<string> s_row_temp = split(rtrim(s_row_temp_temp));

        for (int j = 0; j < 3; j++) {
            int s_row_item = stoi(s_row_temp[j]);

            s[i][j] = s_row_item;
        }
    }

    int result = formingMagicSquare(s);

    fout << result << "\n";

    fout.close();

    return 0;
}

string ltrim(const string &str) {
    string s(str);

    s.erase(
        s.begin(),
        find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );

    return s;
}

string rtrim(const string &str) {
    string s(str);

    s.erase(
        find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
        s.end()
    );

    return s;
}

vector<string> split(const string &str) {
    vector<string> tokens;

    string::size_type start = 0;
    string::size_type end = 0;

    while ((end = str.find(" ", start)) != string::npos) {
        tokens.push_back(str.substr(start, end - start));

        start = end + 1;
    }

    tokens.push_back(str.substr(start));

    return tokens;
}


112. Climbing the Leaderboard

inline int index(const vector<int> & a,int target)
{
    // big to small
    // binaray serach for the first bigger or equal than target

    int hi = a.size()-1;
    int lo = 0;

    while(lo <= hi)
    {
        int mid = lo + (hi - lo) / 2;

        if(a[mid] >= target)
        {
            lo = mid + 1;
        }

        else hi = mid - 1;
    }

    if(a[lo-1] == target) return lo;
    return lo + 1;
}
vector<int> climbingLeaderboard(vector<int> ranked, vector<int> player) {
    ranked.erase(std::unique(ranked.begin(), ranked.end()), ranked.end());

    vector<int> ret;

    // rank all 
    for(int i = 0;i < player.size();i++)
    {
        ret.push_back(index(ranked,player[i]));
    }
    
    return ret;
}

113. The Time in Words

// Map of hours
    std::map<int, string> hours {
        {1, "one"}, {2, "two"}, {3, "three"}, {4, "four"}, {5, "five"}, {6, "six"},
        {7, "seven"}, {8, "eight"}, {9, "nine"}, {10, "ten"}, {11, "eleven"}, {12, "twelve"}
    };

    // Map of minutes
    std::map<int, string> minutes {
        {0, "o' clock"}, {1, "one minute"}, {2, "two minutes"}, {3, "three minutes"}, {4, "four minutes"}, {5, "five minutes"},
        {6, "six minutes"}, {7, "seven minutes"}, {8, "eight minutes"}, {9, "nine minutes"}, {10, "ten minutes"}, {11, "eleven minutes"},
        {12, "twelve minutes"}, {13, "thirteen minutes"}, {14, "fourteen minutes"}, {15, "quarter"}, {16, "sixteen minutes"},
        {17, "seventeen minutes"}, {18, "eighteen minutes"}, {19, "nineteen minutes"}, {20, "twenty minutes"}, {21, "twenty one minutes"},
        {22, "twenty two minutes"}, {23, "twenty three minutes"}, {24, "twenty four minutes"}, {25, "twenty five minutes"},
        {26, "twenty six minutes"}, {27, "twenty seven minutes"}, {28, "twenty eight minutes"}, {29, "twenty nine minutes"},
        {30, "half"}
    };

    
    string indicator = " past ";
    if(m == 0) return hours[h] + " o' clock";
    if( m > 30){
        indicator = " to ";
        m = 60 - m;
        h += 1;
    }
    return minutes[m] + indicator + hours[h];

114. Organizing Containers of Balls

int n=container.size();
    set<int> row,column;
    for(int i=0;i<n;i++){
        int temp=0;
        int r=0;
        for(int j=0;j<n;j++){
            r+=container[i][j];
            temp+=container[j][i];
        }
        row.insert(r);
        column.insert(temp);
    }
    if(row==column){
        return "Possible";
    }
    else{
        return "Impossible";
    }

115. Encryption

 string str;
    for(char i:s)
    {
        if(i!=' ')
        {
            str+=i;
        }
    }
    int l=str.length();
    float r=sqrt(l);
    int row=floor(r);
    int column=ceil(r);
    if((row*column)<l)
    {
        for(int i=row+1;i<=l;i++)
        {
            if((column*i)>=l)
            {
                row=i;
                break;
            }
        }
    }
    string result;
    int i=0;
    while(i<column)
    {   
        string re;
        for(int j=i;j<l;j=j+column)
        {
            re+=str[j];
        }
        if(i>0)
        {
            result+=" ";
        }
        result=result+re;
        i++;
    }
    return result;

116. Sansa and XOR

unsigned int l = arr.size()   ;
    int result = 0;
    if(l%2 == 0) return 0;
    for(unsigned int i = 0; i<l; i+=2)
        result ^= arr[i];
    return result;

117. Recursive Digit Sum

int r = 0;
    for (char v : n) {
        r += (v - '0') * k;
        if (10 <= r) {
            r %= 9;
            if (0 == r) r = 9;
        }
    }
    return r;

118. The Grid Search

int rows_G = G.size();
    int cols_G = G[0].size();
    int rows_P = P.size();
    int cols_P = P[0].size();

    for (int i = 0; i <= rows_G - rows_P; i++) {
        for (int j = 0; j <= cols_G - cols_P; j++) {
            bool patternMatch = true;
            for (int k = 0; k < rows_P; k++) {
                for (int l = 0; l < cols_P; l++) {
                    if (G[i + k][j + l] != P[k][l]) {
                        patternMatch = false;
                        break;
                    }
                }
                if (!patternMatch) {
                    break;
                }
            }
            if (patternMatch) {
                return "YES";
            }
        }
    }

    return "NO";

119. Flipping the Matrix

const int n = matrix.size() / 2, sz1 = matrix.size() - 1;
    int sum = 0;
    for (int y = 0; y < n; ++y) for (int x = 0; x < n; ++x) {
        int m1 = max(matrix[y][x], matrix[sz1 - y][x]);
        int m2 = max(matrix[y][sz1 - x], matrix[sz1 - y][sz1 - x]);
        sum += max(m1, m2);
    }
    return sum;

120. Counter game

string counterGame(long n) {
    int count = 0;

    // Keep looping until n is not equal to 1
    while (n != 1) {
        // Check if n is a power of 2
        if ((n & (n - 1)) == 0) {
            n /= 2; // Divide by 2
        } else {
            // Find the largest power of 2 less than n
            long long nearestPowerOf2 = pow(2, floor(log2(n)));
            n -= nearestPowerOf2; // Reduce by the largest power of 2
        }
        count++;
    }

    // If the number of moves is even, Louise wins, otherwise Richard wins
    if (count % 2 == 0) {
        return "Richard";
    } else {
        return "Louise";
    }
}

121. Max Min

sort(arr.begin(), arr.end());
    int i = 0;
    auto minimum = INT64_MAX;
    while (i <= arr.size()-k){
        auto beginarr = arr.begin()+i;
        auto Min = min(beginarr,beginarr+k-1);
        auto Max = max(beginarr,beginarr+k-1);
        int Unfair = *Max - *Min;
        if (minimum > Unfair){ minimum = Unfair; }
        i++;
    }
    return minimum;

122. Greedy Florist

int getMinimumCost(int k, vector<int> c) {
 sort(c.rbegin(), c.rend());
    int sizearr = c.size();
    long long count = 0, i = 0, sum = 0;
    while(count < sizearr){
        if (count % k == 0 && count != 0){i++;}
        sum = sum + c[count]*(i+1);count++;
    }
    return sum;
}

123. Sherlock and the Valid String

vector<int>alpha(26,0);
    for(size_t i=0;i<s.length();i++){
        int c=s[i]-'a';
        alpha[c]++;
    }

    size_t i;
    bool removeOneTime=false;
    int prev=alpha[0];
    for(i=1;i<alpha.size();i++){
        if(alpha[i]!=0){
            if(alpha[i]!=prev && !removeOneTime) {
                removeOneTime=true;
                continue;
            }
            else if(alpha[i]!=prev && removeOneTime){
                return "NO";
            }
            prev=alpha[i];
        }
    }

    return "YES";

124. Gaming Array

 int count = 0, prev = 0;    
    for(auto &num : arr) {
        if(num > prev) {
            prev = num;
            count++;
        }
    }    
    return !(count % 2) ? "ANDY" : "BOB";




