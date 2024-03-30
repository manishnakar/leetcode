There are some spherical balloons taped onto a flat wall that represents the XY-plane. The balloons are represented as a 2D integer array points where points[i] = [xstart, xend] denotes a balloon whose horizontal diameter stretches between xstart and xend. You do not know the exact y-coordinates of the balloons.

Arrows can be shot up directly vertically (in the positive y-direction) from different points along the x-axis. A balloon with xstart and xend is burst by an arrow shot at x if xstart <= x <= xend. There is no limit to the number of arrows that can be shot. A shot arrow keeps traveling up infinitely, bursting any balloons in its path.

Given the array points, return the minimum number of arrows that must be shot to burst all balloons.

Here's the JavaScript code to solve the problem of finding the minimum number of arrows needed to burst all the balloons:

```javascript
/**
 * @param {number[][]} points
 * @return {number}
 */
var findMinArrowShots = function(points) {
    if (points.length === 0) {
        return 0;
    }
    
    // Sort the balloons by their end coordinates in ascending order
    points.sort((a, b) => a[1] - b[1]);
    
    let arrowCount = 1;
    let currentArrowPos = points[0][1];
    
    for (let i = 1; i < points.length; i++) {
        // If the current balloon starts after the current arrow position,
        // we need to shoot a new arrow
        if (points[i][0] > currentArrowPos) {
            arrowCount++;
            currentArrowPos = points[i][1];
        }
    }
    
    return arrowCount;
};
```

Explanation:

1. We first check if the `points` array is empty. If it is, we return 0 since no arrows need to be shot.

2. We sort the balloons based on their end coordinates in ascending order. This is because we want to shoot an arrow at the earliest end coordinate possible to burst as many balloons as possible.

3. We initialize `arrowCount` to 1, assuming we need at least one arrow to burst the first balloon. We also set `currentArrowPos` to the end coordinate of the first balloon.

4. We iterate through the balloons starting from the second balloon (index 1).

5. For each balloon, we check if its start coordinate is greater than the `currentArrowPos`. If it is, it means the current arrow cannot burst this balloon, so we need to shoot a new arrow. We increment the `arrowCount` and update the `currentArrowPos` to the end coordinate of the current balloon.

6. If the start coordinate of the current balloon is less than or equal to the `currentArrowPos`, it means the current arrow can burst this balloon as well, so we don't need to shoot a new arrow.

7. After iterating through all the balloons, we return the `arrowCount`, which represents the minimum number of arrows needed to burst all the balloons.

The time complexity of this solution is O(n log n) due to the sorting step, where n is the number of balloons. The space complexity is O(1) since we only use a constant amount of extra space.
