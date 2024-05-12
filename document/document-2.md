### Mission-2

---

#### Module-5

```
// aggregate-match

db.test.aggregate([
    { $match: { gender: 'Male', age: { $lte: 30 } } },
    { $project: { name: 1, age: 1, gender: 1 } }
])



```
