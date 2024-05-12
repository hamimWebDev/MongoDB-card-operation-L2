### Mission-2

---

#### Module-5

```
db.test.find({ gender: "Female", age: { $in: [18, 20, 22, 24, 26, 28, 30] } }, { age: 1, gender: 1 }).sort({ age: 1 })

---

db.test.find(
    {
        gender: "Female",
        age: { $nin: [18, 20, 22, 24, 26, 28, 30] },
        interests: { $in: ["Gaming", "Cooking"] }
    },
    { age: 1, gender: 1, interests: 1 })
    .sort({ age: 1 })

---

db.test.find({ age: { $ne: 17, $lt: 30 } }, { age: 1 })

---

db.test.find({
    $and: [
        { age: { $ne: 17 } },
        { age: { $lte: 30 } }
    ]
})
    .project({ age: 1 }).sort({ age: 1 })

---

db.test.find({
    $or: [
        { interests: "Travelling" },
        { interests: "Cooking" },
    ]
})
    .project({ interests: 1 }).sort({ age: 1 })

---

db.test.find({
    $and: [
        { "skills.name": "JAVASCRIPT" },
        { "skills.level": "Expert" },

    ]
})
    .project({ skills: 1 }).sort({ age: 1 })

---

db.test.find({
    $or: [
        { "skills.name": "JAVASCRIPT" },
        { "skills.level": "Expert" },

    ]
})
    .project({ skills: 1 }).sort({ age: 1 })

---

db.test.find({ "skills.name": { $in: ["JAVASCRIPT", "PYTHON"] } })
    .project({ skills: 1 }).sort({ age: 1 })

---

db.test.find({ phone: { $exists: true } })

---

db.test.find({ age: { $type: "string" } })

---

db.test.find(
    { skills: { $elemMatch: { name: "JAVASCRIPT", level: "Expert" } } },
)
    .project({ skills: 1 }).sort({ age: 1 })

---

db.test.find({ friends: { $size: 0} }).project({ friends: 1 })

---

db.test.find({ "interests.2": "Cooking" }).project({ interests: 1 })

---

db.test.find({ interests: { $all: ["Gardening", "Gaming", "Cooking"] } }).project({ interests: 1 })

---

db.test.find({
    skills: {
        $elemMatch: {
            "name": "JAVASCRIPT",
            "level": "Expert",
        }
    }
}).project({ skills: 1 })

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $set: {
        age: 80
    }
})

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $addToSet: {
        interests: "Hacking"
    }
})

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $addToSet: {
        interests: { $each: ["Hacking", "gardening"] }
    }
})

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $push: {
        interests: { $each: ["Hacking", "gardening"] }
    }
})

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $pop: { interests: 1 }
}
)

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $pull: { friends: ["Fahim Ahammed Firoz", "Rasel Ahmed"] }
}
)

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $pullAll: { friends: ["Fahim Ahammed Firoz", "Rasel Ahmed"] }
}
)

---

db.test.updateOne({ _id: ObjectId("6406ad65fc13ae5a400000c4") }, {
    $set: {
        "address.country": "Bangladesh",
        education: "Js and Ts"
    }

}
)

---

db.test.updateOne({ _id: ObjectId("6406ad63fc13ae5a40000066"), "education.major": "History" }, {
    $set: {
        "education.$.major":"Socal work"
    }

}
)

---

db.test.updateOne({ _id: ObjectId("6406ad63fc13ae5a40000066") }, {
    $inc: {
        age: 6
    }

}
)

---

db.test.deleteOne({ _id: ObjectId("6406ad63fc13ae5a40000066") })

---

db.createCollection({"post"})

---

db.createCollection("post")

```
