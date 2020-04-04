# Git

## 명령어

###  연결

```text
$ git remote add origin [깃주소]
```

### 받아오기 - clone

```text
$ git clone [깃주소]
```

### 브랜치

#### 목록보기

```javascript
// 로컬
$ git branch -a

// 원격
$ git branch -r
```

####  선택하기

```javascript
// 로
$ git checkout [브랜치이름]
// 원격
$ git checkout -t remotePath/branchName
```

####  만들기

```javascript
$ git branch 브랜치이름
```



