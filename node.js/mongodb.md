# MongoDB

## 명령어

###  조회

```bash
// db 조회
show dbs;

// 컬랙션 조회
show callections;
```

### javascript 명령

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

### save 명령

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

### find 명령

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

###  수정

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







{% embed url="https://poiemaweb.com/mongoose" %}



