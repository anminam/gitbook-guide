# 명령어

## 명령어

###  show - 조회

```bash
// db 조회
show dbs;

// 컬랙션 조회
show callections;
```

### javascript - js 사용

```bash
> a = 10
> a * 10
```

```bash
for(i=0; i < 10; i++) {
    print('hello')
}
```

```bash
> var a = {age:30}
> var n = {name: 'anminam', age: 30}
> var person = {name: 'anminam', languages:['eng','kor']
```

### save - 저장

```bash
> db.users.save({name: 'anminam'})
> db.users.find()

{ "_id" : ObjectId("5ea295e95e5354125adbe2bd"), "name" : "anminam" }

```

```bash
> for(i = 0;i < 10; i++){db.users.save({name: 'anminam', age:i})}
> db.users.find()
{ "_id" : ObjectId("5ea296ef5e5354125adbe304"), "name" : "anminam", "age" : 0 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe305"), "name" : "anminam", "age" : 1 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe306"), "name" : "anminam", "age" : 2 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe307"), "name" : "anminam", "age" : 3 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe308"), "name" : "anminam", "age" : 4 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe309"), "name" : "anminam", "age" : 5 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30a"), "name" : "anminam", "age" : 6 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30b"), "name" : "anminam", "age" : 7 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30c"), "name" : "anminam", "age" : 8 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30d"), "name" : "anminam", "age" : 9 }
```

### find - 찾기

```bash
// 일반 찾
> db.users.find({age:1})
{ "_id" : ObjectId("5ea296ef5e5354125adbe305"), "name" : "anminam", "age" : 1 }

// $gt 이상
> db.users.find({age:{'$gt':4}})
{ "_id" : ObjectId("5ea296ef5e5354125adbe309"), "name" : "anminam", "age" : 5 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30a"), "name" : "anminam", "age" : 6 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30b"), "name" : "anminam", "age" : 7 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30c"), "name" : "anminam", "age" : 8 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30d"), "name" : "anminam", "age" : 9 }

// AND
> db.users.find({age:{$gte:4, $lte:8}})
{ "_id" : ObjectId("5ea296ef5e5354125adbe308"), "name" : "anminam", "age" : 4 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe309"), "name" : "anminam", "age" : 5 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30a"), "name" : "anminam", "age" : 6 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30b"), "name" : "anminam", "age" : 7 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30c"), "name" : "anminam", "age" : 8 }

// OR
> db.users.find({$or:[{age:{$lte:2}},{age:{$gte:8}}]})
{ "_id" : ObjectId("5ea296ef5e5354125adbe304"), "name" : "anminam", "age" : 0 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe305"), "name" : "anminam", "age" : 1 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe306"), "name" : "anminam", "age" : 2 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30c"), "name" : "anminam", "age" : 8 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30d"), "name" : "anminam", "age" : 9 }

// $in 안에있는 $in 뒤에는 배열
> db.users.find({age:{$in:[4,1,3]}})
{ "_id" : ObjectId("5ea296ef5e5354125adbe305"), "name" : "anminam", "age" : 1 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe307"), "name" : "anminam", "age" : 3 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe308"), "name" : "anminam", "age" : 4 }

// 존재 여부 확인
> db.users.find({age:{$exists:true}})
{ "_id" : ObjectId("5ea296ef5e5354125adbe304"), "name" : "anminam", "age" : 0 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe305"), "name" : "anminam", "age" : 1 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe306"), "name" : "anminam", "age" : 2 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe307"), "name" : "anminam", "age" : 3 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe308"), "name" : "anminam", "age" : 4 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe309"), "name" : "anminam", "age" : 5 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30a"), "name" : "anminam", "age" : 6 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30b"), "name" : "anminam", "age" : 7 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30c"), "name" : "anminam", "age" : 8 }
{ "_id" : ObjectId("5ea296ef5e5354125adbe30d"), "name" : "anminam", "age" : 9 }

// 반환 필드 선택
> db.users.find({},{age:1,_id:0})
{ "age" : 0 }
{ "age" : 1 }
{ "age" : 2 }
{ "age" : 3 }
{ "age" : 4 }
{ "age" : 5 }
{ "age" : 6 }
{ "age" : 7 }
{ "age" : 8 }
{ "age" : 9 }

```

###  update - 수정

```bash
// 수정하기위해 데이터 추가

> db.users2.save({name:'anminam', languages:['python','javasciprt']})
> db.users2.save({name:'mini', languages:['html','css']})
```

```bash
// update
> db.users2.update({name:'anminam'},{name:'minam',languages:['c']})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c" ] }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html", "css" ] }
```

```bash
// $set
// 일부만 추가
> db.users2.update({name:'minam'},{$set:{'age':10}})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c" ], "age" : 10 }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html", "css" ] }

// 일부만 변경 - 그냥 없데이트랑 똑같나??
> db.users2.update({name:'minam'},{$set:{'languages':['c++']}})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c++" ], "age" : 10 }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html", "css" ] }
```

```bash
// $unset
// age 값 20을 넣었는데도 잘 지워지네...

> db.users2.update({name:'minam'},{$unset:{age:20}})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c++" ] }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html", "css" ] }
```

```bash
// $pull
// 배열 값 삭제
> db.users2.update({name:'mini'},{$pull:{languages:'css'}})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c++" ] }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html" ] }
```

```bash
// $push
// 배열 값 추가
> db.users2.update({name:'mini'},{$push:{languages:'aaaaaaa'}})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c++" ] }
{ "_id" : ObjectId("5ea29b835e5354125adbe313"), "name" : "mini", "languages" : [ "html", "aaaaaaa" ] }
```

### remove - 삭제

```bash
// remove
> db.users2.remove({name:'mini'})
> db.users2.find()
{ "_id" : ObjectId("5ea29b825e5354125adbe312"), "name" : "minam", "languages" : [ "c++" ] }
```

```bash
// 전체 삭제
> db.users.remove({})
```

### drop - 컬랙션 삭제

```bash
> db.users2.drop()
true
> db.users2.find()
// 아무것도 안나옴 😭
```

## CRUD

### Create

* db.users.save\({name:'anminam'}\)

### read

* db.users.find\(\)

### update

* db.users.update\({name:'anminam'}, {name: 'mini', age: 10}\)

### delete

* db.users.remove\({name: 'anminam'}\)



## ex

1.  컬렉션 하나를 생성
2. 100 명의 Document 만들기

```bash
{name: name0, pos:0}
{name: name1, pos:1}
.
.
{name: name99, pos:99}


```

3. 조회

```bash
5 <= pos < 25 or 80 < pos < 87
```

```bash
> db.users.find({pos:{$gte:5,$lt:25}})
{ "_id" : ObjectId("5ea2a2145e5354125adbe319"), "name" : "name5", "pos" : 5 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31a"), "name" : "name6", "pos" : 6 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31b"), "name" : "name7", "pos" : 7 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31c"), "name" : "name8", "pos" : 8 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31d"), "name" : "name9", "pos" : 9 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31e"), "name" : "name10", "pos" : 10 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31f"), "name" : "name11", "pos" : 11 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe320"), "name" : "name12", "pos" : 12 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe321"), "name" : "name13", "pos" : 13 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe322"), "name" : "name14", "pos" : 14 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe323"), "name" : "name15", "pos" : 15 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe324"), "name" : "name16", "pos" : 16 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe325"), "name" : "name17", "pos" : 17 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe326"), "name" : "name18", "pos" : 18 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe327"), "name" : "name19", "pos" : 19 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe328"), "name" : "name20", "pos" : 20 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe329"), "name" : "name21", "pos" : 21 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32a"), "name" : "name22", "pos" : 22 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32b"), "name" : "name23", "pos" : 23 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32c"), "name" : "name24", "pos" : 24 }
> 

```

```bash
> db.users.find({$or:[{pos:{$gte:5,$lt:25}}, {pos:{$gt:80, $lt:87}}]})
{ "_id" : ObjectId("5ea2a2145e5354125adbe319"), "name" : "name5", "pos" : 5 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31a"), "name" : "name6", "pos" : 6 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31b"), "name" : "name7", "pos" : 7 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31c"), "name" : "name8", "pos" : 8 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31d"), "name" : "name9", "pos" : 9 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31e"), "name" : "name10", "pos" : 10 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe31f"), "name" : "name11", "pos" : 11 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe320"), "name" : "name12", "pos" : 12 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe321"), "name" : "name13", "pos" : 13 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe322"), "name" : "name14", "pos" : 14 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe323"), "name" : "name15", "pos" : 15 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe324"), "name" : "name16", "pos" : 16 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe325"), "name" : "name17", "pos" : 17 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe326"), "name" : "name18", "pos" : 18 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe327"), "name" : "name19", "pos" : 19 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe328"), "name" : "name20", "pos" : 20 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe329"), "name" : "name21", "pos" : 21 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32a"), "name" : "name22", "pos" : 22 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32b"), "name" : "name23", "pos" : 23 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe32c"), "name" : "name24", "pos" : 24 }
Type "it" for more
> it
{ "_id" : ObjectId("5ea2a2145e5354125adbe365"), "name" : "name81", "pos" : 81 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe366"), "name" : "name82", "pos" : 82 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe367"), "name" : "name83", "pos" : 83 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe368"), "name" : "name84", "pos" : 84 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe369"), "name" : "name85", "pos" : 85 }
{ "_id" : ObjectId("5ea2a2145e5354125adbe36a"), "name" : "name86", "pos" : 86 }
> 
```









{% embed url="https://poiemaweb.com/mongoose" %}



