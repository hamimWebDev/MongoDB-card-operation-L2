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

// group operation

db.test.aggregate([
    {
        $group: {
            _id: null,
            totalSalary: {
                $sum: "$salary"
            },
            maxSalary: { $max: "$salary" },
            minSalary: { $min: "$salary" },
            avgSalary: { $avg: "$salary" }

        }
    },
    {
        $project: {
            totalSalary: 1,
            maxSalary: 1,
            minimumSalary: "$minSalary",
            avgSalary: 1,
            minMaxDiff: {$subtract: ["$maxSalary","$minSalary"]}
        }
    }
])

// group-with-$unwind

db.test.aggregate([
    { $unwind: "$friends" },
    { $group: { _id: "$friends", count: { $sum: 1 } } }
])

db.test.aggregate([
    { $unwind: "$interests" },
    { $group: { _id: "$age", interestsPerAge: { $push: "$interests" } } }
])

// use-bucket-sort-limit

db.test.aggregate([
    {
        $bucket: {    //bucket
            groupBy: "$age",
            boundaries: [20, 40, 60, 80],
            default: "GT:80",
            output: {
                "count": { $sum: 1 },
                "PersonName": { $push: "$$ROOT" }
            }

        }
    },
    //sort
    { $sort: { count: -1 } },
    //limit
    { $limit: 4 },
    //project
    { $project: { count: 1 } }
])

// use facet multiple pipeline

db.test.aggregate([
    {
        $facet: {
            "friendsCount": [
                { $unwind: "$friends" },
                { $group: { _id: "$friends", count: { $sum: 1 } } }
            ],
            "educationCount": [
                { $unwind: "$education" },
                { $group: { _id: "$education", count: { $sum: 1 } } }
            ],
            "skillsCount": [
                { $unwind: "$skills" },
                { $group: { _id: "$skills", count: { $sum: 1 } } }
            ]


        }
    }
])

// use lookup

db.orders.aggregate([

    {
        $lookup: {
            from: "test",
            localField: "userId",
            foreignField: "_id",
            as: "user"
        }
    }
])

```
