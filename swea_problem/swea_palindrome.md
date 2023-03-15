# swea palindrome 4861

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/03ed9b9c-0511-4bd8-b92f-78d0b2ba0fd1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230315%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230315T000411Z&X-Amz-Expires=86400&X-Amz-Signature=2f848f8489321e19750ea7fe7ef31c2931904d5205dcaba2e9f433944ae4f8ac&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```python
3
10 10
GOFFAKWFSM
OYECRSLDLQ
UJAJQVSYYC
JAEZNNZEAJ
WJAKCGSGCF
QKUDGATDQL
OKGPFPYRKQ
TDCXBMQTIO
UNADRPNETZ
ZATWDEKDQF
10 10
WPMACSIBIK
STWASDCOBQ
AMOUENCSOG
XTIIGBLRCZ
WXVSWXYYVU
CJVAHRZZEM
NDIEBIIMTX
UOOGPQCBIW
OWWATKUEUY
FTMERSSANL
20 13
ECFQBKSYBBOSZQSFBXKI
VBOAIDLYEXYMNGLLIOPP
AIZMTVJBZAWSJEIGAKWB
CABLQKMRFNBINNZSOGNT
NQLMHYUMBOCSZWIOBINM
QJZQPSOMNQELBPLVXNRN
RHMDWPBHDAMWROUFTPYH
FNERUGIFZNLJSSATGFHF
TUIAXPMHFKDLQLNYQBPW
OPIRADJURRDLTDKZGOGA
JHYXHBQTLMMHOOOHMMLT
XXCNJGTXXKUCVOUYNXZR
RMWTQQFHZUIGCJBASNOX
CVODFKWMJSGMFTCSLLWO
EJISQCXLNQHEIXXZSGKG
KGVFJLNNBTVXJLFXPOZA
YUNDJDSSOPRVSLLHGKGZ
OZVTWRYWRFIAIPEYRFFG
ERAPUWPSHHKSWCTBAPXR
FIKQJTQDYLGMMWMEGRUZ
```

</br>

- solve

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, M = map(int, input().split())

    voca = [str(input()) for _ in range(N)]

    # 가로에서 회문을 만들어준다.
    for i in range(N):
        for j in range(N-M+1):
            num = 0
            ans = []
            # 정답 리스트를 만든다.
            while num < M:
                ans.append(voca[i][j + num])
                num += 1

            if ans == ans[::-1]:
                # 역순의 글자들을 만든다.
                result = ans
    # 세로에서 회문을 찾아준다.
    for i in range(N-M+1):
        for j in range(N):
            num = 0
            ans = []
            # 정답 리스트를 만든다.
            while num < M:
                ans.append(voca[i+num][j])
                num += 1

            if ans == ans[::-1]:
                # 역순의 글자들을 만든다.
                result = ans
    # finish = ''.join(result.split())
    answer = ''
    for a in range(M):
        answer += result[a]
    # #1 J A E Z N N Z E A J
    # #2 M W O I V V I O W M
    # #3 T L M M H O O O H M M L T
    # 로 정답이 나와서 붙여주는 줘서 답을 구할 수 있다.
    print(f'#{test_case}', answer)

```

- 다른 풀이

```python
import sys
sys.stdin = open('sample_input.txt')

def contains_palindrome(word, palindrome_len):
    idx = 0
    # 0부터 M-1까지
    # while은
    # word에 사용할 인덱스 끝값이
    # word의 최대 인덱스값
    # 보다 작을 동안
    while idx + palindrome_len - 1 < len(word):
        target = word[idx:idx + palindrome_len]
        # substring
        if target == target[::-1]:
            return target
        idx += 1
    return False
    # 회문이 없을시

T = int(input())

for test_case in range(1, T +1):
    N, M = map(int, input().split())
    arr = [input() for _ in range(N)]

    result = None
    result = ''
    # 가로 줄 확인
    for i in range(N):
        # i 행 가로 단어
        word_horizontal = arr[i]
        result = contains_palindrome(word_horizontal, M)
        if result:
            break
        # i 열 세로 단어
        word_vertical = ''
        for j in range(N):
            word_vertical += arr[j][i]
        result = contains_palindrome(word_vertical, M)
        if result:
            break
    # 세로 줄 확인

    print(f'#{test_case} {result}')
```