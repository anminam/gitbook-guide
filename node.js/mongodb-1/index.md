---
description: MongoDB Index
---

# INDEX

##  설명

###  인덱스란?

DB의 검색을 빠르게 하기위해 미리 데이터의 순서를 정리해두는 과정

###  인덱스 사용시 주의할점

*  인덱스를 사용하면 쿼리 수행 시간이 단축됨
* 모든 쓰기\(읽기, 갱신, 삭제\) 작업은 인덱스 때문에 오래걸림
* 데이터가 변경될때마다 문서 자체는 물론 몽고디비에서 모든 인덱스를 갱신함
* 몽고디비는 컬랙션당 최대 64개까지 인덱스를 가지도록 제한됨
* 일반적으로 컬렉션당 2~3개의 인덱스를 가지고있는게 좋다
* 몽고디비의 인덱스는 전형적인 관계형 데이터베이스의 인덱스와 거의 흡사하게 작동함
* 새로운 인덱스를 구축하려면 오랜시간이 걸리고 자원을 많이 잡아먹음
* 몽고디비는 인덱스 구축이 완료될 때까지 DB의 모든 읽기 쓰기를 중단하면서 인덱스 구축하게됨
* background 옵션을 사용하면 인덱스를 구축하면서 다른 작업이 가능하기는 하지만 효율성이 떨어지고 느



##  인덱스 확인

```text
db.users.getIndexes();
```

## 인덱스 생성

```text
// 오름차순
> db.users.ensureIndex({"name":})
> db.users.getIndexes();
[
	{
		"v" : 2,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "app.users"
	},
	{
		"v" : 2,
		"key" : {
			"name" : -1
		},
		"name" : "name_-1",
		"ns" : "app.users"
	}
]
// 내림차
> db.users.ensureIndex({"name":-1})
```

###  백그라운드 옵션

인덱스 자체를 백그라운드로 설정 함으로서 인덱스때문에 

```text
> db.users.ensureIndex({"name":1},{unique:true})

// 중복되면 삭제
> db.users.ensureIndex({"name":1},{unique:true, dropDups:true})

```

##   인덱스 삭제

###  하나만 삭

```text
> db.users.dropIndex({name:-1})
> db.users.getIndexes();
[
	{
		"v" : 2,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "app.users"
	}
]
```

###  모두삭제

기본인덱스를 제외한 모든 인덱스 삭 

```text
> db.users.dropIndexes()
```

##   속도테스트

 아래와같이 더미 컬랙션을 생성해서 1,000,000 만개의 데이터를 만들어 보자

```text
// 몇분 걸릴정도로 오래걸린다
> 
for (i = 0; i < 1000000; i++) {
    db.users6.insert({
        "i":i,
        "username":"user"+(i+1),
        "age":Math.floor(Math.random()*120),
        "created":new Date()
    })
}
```

###   일반적인 찾기

```text
> db.users6.find({username:"user1000"})
{ "_id" : ObjectId("5ea67ca7122f97b1da3a7b59"), "i" : 999, "username" : "user1000", "age" : 72, "created" : ISODate("2020-04-27T06:33:11.040Z") }
```

```text
> db.users6.find({username:"user1000"}).explain()
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "app.users6",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"username" : {
				"$eq" : "user1000"
			}
		},
		"queryHash" : "379E82C5",
		"planCacheKey" : "379E82C5",
		"winningPlan" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"username" : {
					"$eq" : "user1000"
				}
			},
			"direction" : "forward"
		},
		"rejectedPlans" : [ ]
	},
	"serverInfo" : {
		"host" : "anhunmin-ui-iMac.local",
		"port" : 27017,
		"version" : "4.2.5",
		"gitVersion" : "2261279b51ea13df08ae708ff278f0679c59dc32"
	},
	"ok" : 1
}

```

```text
// 인덱스 지
> db.users6.ensureIndex({username:1})

```

### 

