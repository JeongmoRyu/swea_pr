# swea palindrome1 1215


![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bd30c793-7030-4741-82a6-beeb0af330fc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230315%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230315T000834Z&X-Amz-Expires=86400&X-Amz-Signature=94cbdcca99a3767358798cc12119e7ba00e3220b4014022d0229cf6185de5159&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```
4
CBBCBAAB
CCCBABCB
CAAAACAB
BACCCCAC
AABCBBAC
ACAACABC
BCCBAABC
ABBBCCAA
4
BCBBCACA
BCAAACAC
ABACBCCB
AACBCBCA
ACACBAAA
ACCACCCB
AACAAABA
CACCABCB
3
BABBBACB
ABCAACCB
CCACBCBA
CACACBCA
CCABACCB
CCBAAAAA
BBACBACA
CBCCBABC
4
ACBBCCCA
CCBCBACB
ACBCABAA
BABCCAAA
ACCCCCBB
AABBCCBC
CCABBACA
CAACBCCC
7
AAACACAB
CCABCCCC
CABCAAAA
BBBCBBBA
ABCCACCC
ABACBCBB
CBABACAB
BBBBBABB
3
ABCBCBCA
ABCBCCCB
ABACCCCA
BBABBBAC
BBACBCCC
AAACACCA
BABCCCBC
ACCBCBCA
7
CACBCCBA
CBCCBCCA
CCBCBCAB
BBCCABAA
CACCBCCC
BCCACCBB
CBCCCBBC
CBACBCBC
5
BCBABCBA
CBBABABC
BCACBAAA
BBABACAB
BCBCCBAC
CBBCBBBB
CBBAACAB
ACCBCBCC
3
BBBBCCAA
BCBBCACC
BBCAAAAB
ABABBABB
BACAAABA
ABACCBCA
ACCAABCB
BACCACBA
5
BCCCACCB
CABCACAB
BAACCCAC
BBABBABC
CCABABCA
CABABACC
CBACACAB
CBCCCBAB

```

</br>

- solve

```python
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = [str(input()) for _ in range(8)]

    result = None
    result = ''
    count = 0
    # 가로일때
    for i in range(8):
        word_r = arr[i]
        num = 0
        word_list = []
        for a in range(8-N+1):
            word_list.append(word_r[a: a + N])
        for b in range(len(word_list)):
            if word_list[b] == word_list[b][::-1]:
                num += 1

        count = count + num

    for i in range(8):
        word_d = ''
        num_d = 0
        word_list_down = []
        for j in range(8):
            word_d += arr[j][i]
        for a in range(8-N+1):
            word_list_down.append(word_d[a: a + N])
        for b in range(len(word_list_down)):
            if word_list_down[b] == word_list_down[b][::-1]:
                num_d += 1
        count = count + num_d

    print(f'#{test_case} {count}')
```

</br>

- 다른 풀이

```python
import sys
sys.stdin = open("input.txt")

def is_palindrome(word):
    return word == word[::-1]

def solve(word, sub_len):
    count = 0
    for idx in range(len(word) - sub_len + 1):
        if is_palindrome(word[idx:idx + sub_len]):
            count += 1
    return count

for test_case in range(1, 11):
    word_len = int(input())
    size = 8

    col =[]
    row =['']*size
    for _ in range(size):
        word = input()
        col.append(word)
        for i in range(size):
            row[i] += word[i]

    # col과 row가 들어 있는 단어들 중 길이 word_len인 회문의 갯수
    result = 0
    for word in col:
        result += solve(word, word_len)

    for word in row:
        result += solve(word, word_len)

    print(f'#{test_case} {result}')

```