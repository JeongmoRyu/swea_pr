# swea palindrome2 1216

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/da025323-a02e-4043-98a3-ae03ce9f9889/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230315%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230315T001115Z&X-Amz-Expires=86400&X-Amz-Signature=fccd220833df73697994ed457aad30090a127e94d386376b0b80148c194f555d&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

</br>

- input
```
1
CCBBCBAABCCCBABCBCAAAACABBACCCCACAABCBBACACAACABCBCCB...
ACBAAAACCACCCBAACAAABACACCABCBCBABBBACBABCAACCBCCACBC...
CCCACCBCBACBACBCABAABABCCAAAACCCCCBBAABBCCBCCCABBACAC...
CABACBCBBCBABACABBBBBBABBCABCBCBCAABCBCCCBABACCCCABBA...
BCCBCCACCBCBCABBBCCABAACACCBCCCBCCACCBBCBCCCBBCCBACBC...
BBBBCBBAACABACCBCBCCABBBBCCAABCBBCACCBBCAAAABABABBABB...
ABBAACCCACBBABBABCCCABABCACABABACCCBACACABCBCCCBABCCC...
ABBBBAABCAACCBACBBAACACABCABACBAABCAABBCCCCCCACBCCCCA...
ACCACABABBACBBAACCBBACBBCCACCACCABCCBABABBBACBACBAABC...
BABACACCABCAACBAABCCACCACBCCAABBCBAABABAACAAAAAACCCBC..
...

```

</br>

- solve

```python
import sys
sys.stdin = open('input.txt', 'r')

def is_palindrome(word):
    return word == word[::-1]

# word는 100글자짜리 단어
# max_size 여태까지 찾았던 최대값
def solve(word, max_size, size):
    # 현재 100자 중 word_len 글자짜리 회문이 있는지 검사
    for word_len in range(100, 0, -1):
        # 만약 word_len이 내가 아는 최대보다 작거나 같으면 (탈출조건)
        if word_len == max_size:
            break
        for idx in range(size - word_len + 1):
            if is_palindrome(word[idx:idx + word_len]):
                if word_len > max_size:
                    return word_len

    return max_size

for test_case in range(1, 11):
    input()
    size = 100
    words = [input() for _ in range(size)]

    words_ver = []
    for i in range(size):
        tmp = ''
        for j in range(size):
            tmp += words[j][i]
        words_ver.append(tmp)

    result = 0
    for word in words:
        result = solve(word, result, size)
        # 현재 최대, 후보 최대 검증
    for word in words_ver:
        # 세로도 마찬가지로 진행
        result = solve(word, result, size)

    print(f'#{test_case} {result}')

```