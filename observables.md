# Observables

<details>
<summary>What is the difference between the map, switchMap, and mergeMap operators?</summary>

All of these pipe operators are designed to modify the result of the pipe or the input of the next pipe operator in 
different ways.

The `map()` operator is much like `Array.prototype.map()` that allows you to map an emitted item into something else. 
`switchMap()` and `mergeMap` in contrast should return a new observable for each item that is emitted. These will 
replace the input observable. The differ in the following way: When the input observable emits a new item,
`switchMap()` will unsubscribe and discard (and therefore cancel) a previously mapped observable and replace it with the new one returned by
the function passed to `switchMap()`, `mergeMap()` in contrast will subscribe to the observable returned by the function 
passed to it, and emit new items from this new observable while continuing to emit items from all previous observables.

In short:

* `map()` synchronously replaces the data emmited
* `switchMap()` replaces the observable by using a new observable source, __discarting__ all of its previous `switchMap()` results
* `mergeMap()` replaces the observable by using a new observable source, __keeping__ all of its previous `mergeMap()` results

__Examples__:

```typescript
let itemData = {};
let savedItems = observable.pipe(
    map((data: number) => data.id), // next items in pipe receive the id
    switchMap((id: number): Observable<object> => http.get("/data/id")),
    // next items receive an object (the one that is emitted by the observable from http.get()
    // When a new data item is emitted, this is cancelled and replaced by the new http.get() result
    mergeMap((object): Observable<boolean> => http.put("/data/id/item", itemData)),
    // Subscribers will now receive the boolean result from each put request
);
```

> __Tipp:__ The functions passed to `switchMap()`/`mergeMap()` can also return a Promise or Promise-Like (Thenable) 
> which will automatically be converted into an observable.  

</details>

<details>
<summary>Can I collect results from multiple observable in a pipe (like simultanious XHR responses)?</summary>

Yes, this can be done with `forkJoin()`. Fork join will subscribe to all observables passed to it and emit an result 
array when all of these observables are completed:

```typescript
http.get('/some/resource')
    .pipe(
        switchMap(result => joinFork(
            of(result), // Keep the emitted result
            // Collect additional info simultaniously:
            http.get(`/some/resource/${result.id}/comments`), 
            http.get(`/some/resource/${result.id}/authors`),
        )),
        map(allResults => {
            // Put it all together in a single object
            const [result, comments, authors] = allResults;
            
            return {
                ...result,
                comments,
                authors
            };
        })
    )
```

As you can see, this is much like `Promise.all(...).then()`

</details>

---
