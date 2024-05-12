### Mission-2

---

#### Module-5

```
// aggregate-match

db.test.aggregate([
    { $match: { gender: 'Male', age: { $lte: 30 } } },
    { $project: { name: 1, age: 1, gender: 1 } }
])

// aggregate-Heros-out-collection

 db.test.aggregate([
     { $match: { gender: 'Male' } },
     { $addFields: { course: "level-2", eduTech: "programming Hero" } },
     {$out: "Heros"}
 ])

// aggregate-marge-ThisCollection

db.test.aggregate([
    { $match: { gender: 'Male' } },
    { $addFields: { course: "level-2", eduTech: "programming Hero" } },
    { $merge: "test" }
])

// aggregate-group-count-p.$name

db.test.aggregate([
    { $group: { _id: "$gender", count: { $sum: 1 }, personName: { $push: "$name" } } }
])

//aggregate-group-p.$$ROOT

db.test.aggregate([
    { $group: { _id: "$gender", count: { $sum: 1 }, person: { $push: "$$ROOT" } } },
    { $project: { count: 1, "person.name": 1, "person.email": 1, "person.phone": 1 } }
])

```
