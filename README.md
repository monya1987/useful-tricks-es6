# useful-tricks-es6
Do you realy need lodash in some cases ?
<hr>
Using spread to remove not useful keys ofm obj. (return new  obj)
<code>
  const a = {
        one: 1,
        two: 2,
        three: 3,
    };
  const {one, ...clean} = a;
  console.log(clean); // clean = {two: 2, three: 3}
</code>


<hr>
Remove object from array by property 
<code>
const initial = [ {id: 1, score: 1}, {id: 2, score: 2}, {id: 3, score: 4}]
const removeId = 3
const without3 = initial.filter(x => x.id !== removeId)
console.log(without3) // => [ { id: 1, score: 1  }, { id: 2, score: 2  }  ]
</code>

<hr>
Update an object in array by property
<code>
const initial = [ {id: 1, score: 1}, {id: 2, score: 2}, {id: 3, score: 4}]
const newValue = {id: 3, score: 3}
const updated = initial.map(x => x.id === newValue.id ? newValue : x)
console.log(updated) // => [ { id: 1, score: 1  }, { id: 2, score: 2  }, { id: 3, score: 3  }  ]
</code>

<hr>
Merge an array of objects
<code>
const data = [ {a: 1}, {b: 2}, {c: 3} ]
const merged = data.reduce((res, obj) => ({...res, ...obj}), {})
console.log(merged) // => { a: 1, b: 2, c: 3  }
</code>

<hr>
Merge an array of objects by property
<code>
const toMerge = [
  { id: 1, value: 'a', },
  { id: 2, value: 'b', },
  { id: 3, value: 'c' },
  { id: 1, score: 1 },
  { id: 2, score: '2' },
]
const mergedByProperty = toMerge.reduce((result, obj) => ({
  ...result,
  [obj.id]: {
    ...result[obj.id],
    ...obj
  }
}), {})
console.log(mergedByProperty) // =>
/*
 *{ '1': { id: 1, value: 'a', score: 1 },
 *  '2': { id: 2, value: 'b', score: '2' },
 *  '3': { id: 3, value: 'c' } }
 */
</code>

<hr>
Flatten an array of arrays
<code>
const arrayOfArray = [ [1, 2], [3, 4], [[5, 6]] ]
const flattened = arrayOfArray.reduce((res, a) => [...res, ...a], [] )
console.log(flattened) // => [1, 2, 3, 4, [5, 6]]
</code>

<hr>
From array pairs to key-value
<code>
const pairs = [['a', 1], ['b', 2], ['c', 3]]
const asObjects = pairs.reduce((res, [key, value]) => ({ ...res, [key]: value }), {})

// Or event smarter (thanks to @nomaed for pointing this one out)
const asObjects2 = { ...(new Map(pairs)) }

console.log(asObjects) // => { a: 1, b: 2, c: 3  }
</code>

<hr>
Subtract two sets
<code>
const s1 = [ 1, 2, 3, 4, 5 ]
const s2 = [ 2, 4 ]
const subtracted = s1.filter(x => s2.indexOf(x) < 0)
console.log(subtracted)
</code>



