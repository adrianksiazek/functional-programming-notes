# Functional programming

# High order functions

Higher-order functions (HOF / higher-order functions) is a function that takes as an argument another function (or returns a function). The biggest advantage of HOFs is that they can be used multiple times and can be combined (composed) with first-order functions (first-order functions).

```js
const songs = [
  { name: "Carry on Wayward Son", duration: 322, released: 1976 },
  { name: "Back in Black", duration: 231, released: 1980 },
  { name: "Cold as Ice", duration: 201, released: 1977 },
  { name: "Eye of the tiger", duration: 246, released: 1982 },
];

function getLongest(songs) {
  let result = songs[0];
  for (let i = 1, { length } = songs; i < length; i++) {
    if (result.duration < songs[i].duration) result = songs[i];
  }
  return result;
}

const longestSong = getLongest(songs);
longestSong;

function getShortest(songs) {
  let result = songs[0];
  for (let i = 1, { length } = songs; i < length; i++) {
    if (result.duration > songs[i].duration) result = songs[i];
  }
  return result;
}

const shortestSong = getShortest(songs);
shortestSong;

const reduce = (reducer, initial, arr) => {
  let result = initial;
  for (let i = 0, { length } = arr; i < length; i++) {
    result = reducer(result, arr[i]) ? result : arr[i];
  }
  return result;
};

const filter = (reducer, arr) => reduce(reducer, [], arr);
const shortestReducer = (prev, next) => (prev.duration < next.duration ? prev : next);
const shortest = songs.reduce(shortestReducer, songs);
```

# Pure functions

Pure Functions (PF / Pure Functions) are functions which for arguments of the same value always return the same result, without causing Side Effects. Such functions are also said to be idempotent (eng. Idempotent), memoizable (eng. Memoizable) and are characterized by the so-called Referentail Transparency - that is, the fact that their body can be replaced by an expected value.

```js
let totalPlayed = 20280;
const totalPlayingTime = (totalTime, sessionTime) => (totalTime += sessionTime);

totalPlayed = totalPlayingTime(totalPlayed, 210); // 20490
totalPlayed = totalPlayingTime(totalPlayed, 210); // 20700
totalPlayed; // 20700

const totalPlayed = 20280;
const totalPlayingTime = (totalTime, sessionTime) => (totalTime += sessionTime);

totalPlayingTime(totalPlayed, 210); //20490
totalPlayingTime(totalPlayed, 210); //20490
totalPlayed; // 20280
```
