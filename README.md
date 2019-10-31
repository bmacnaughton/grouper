
Grouper - a simple utility to group sorted items as they are added.

I created this in order to group runs of tests that either passed, failed, or skipped. Grouper makes
it easier to report ranges of tests succinctly.

This is a basic implementation that creates the groups but doesn't provide retrieval mechanisms nor does
it abstract the individual group from the Grouper implementation. It will come.

Basic usage:

```js
// make a grouper
const grouper = new Grouper();

//
// testResults look like:
// {status, testNum, details}
// status can be pass, fail, skip
//
testResults.forEach(result => {
  // add each result using status as the key to group by
  grouper.addItem(result, result.status);
})

// display the groups
grouper.groups.forEach(g => {
  console.log(`test status ${g.key} (${g.count}) range ${g.first.testNum} to ${g.last.testNum}`);
})

```
