### [1002. Find Common Characters](https://leetcode.com/problems/find-common-characters/)

```
func commonChars(words []string) []string {
    res := make([]int, 26)

    for i := range res {
        res[i] = math.MaxInt32
    }

    for _, s := range words {
        tmpCount := make([]int, 26)
        for _, c := range s {
            tmpCount[c - 'a']++
        }

        for i := range res {
            res[i] = min(res[i], tmpCount[i])
        }
    }

    var resArray []string
    for i := range res {
        for res[i] != 0 {
            resArray = append(resArray, string('a' + i))
            res[i]--
        }
    }

    return resArray
}
```
