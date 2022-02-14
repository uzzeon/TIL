

#  반복문 활용해서 구구단 만들어보기



```PYTHON
N = int(input())

# <FOR문 활용>
# for i in range(1, N+1):
#     for j in range(1, N+1):
#         print(f'{i}x{j} = {i*j}')

# <WHILE문 활용>
i = 1
while i <= N:
    j = 1
    while j <= N:
        print(f'{i}x{j} = {i*j}')
        j += 1
    print()
    i += 1
```

