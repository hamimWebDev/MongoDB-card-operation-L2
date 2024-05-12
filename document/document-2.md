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



```
