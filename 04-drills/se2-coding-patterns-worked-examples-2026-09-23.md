# SE II Coding Patterns — Worked C# Examples

Learn the recognition cue and correctness invariant, not code by rote. State the contract and complexity before coding. Examples use C#.

## 1. Two Sum — hash map

**Problem:** return indices of two distinct values whose sum is target. Assume exactly one answer.

**Baseline:** inspect every pair, O(n²) time and O(1) extra space.

**Invariant:** before processing index i, the map contains values at earlier indices only. If the complement exists, that pair is valid and uses distinct indices.

```csharp
public static int[] TwoSum(int[] nums, int target)
{
    var seen = new Dictionary<int, int>();

    for (var i = 0; i < nums.Length; i++)
    {
        var complement = target - nums[i];
        if (seen.TryGetValue(complement, out var previousIndex))
            return new[] { previousIndex, i };

        // Lookup first so an element cannot pair with itself.
        seen[nums[i]] = i;
    }

    throw new ArgumentException("No valid pair exists.");
}
```

**Complexity:** expected O(n) time, O(n) space. Hash lookup is expected constant time, not a universal worst-case guarantee.

**Tests:** [2,7], target 9; [3,3], target 6; negative values; no answer according to the API contract.

**Common bug:** inserting before lookup can reuse the same index when target is twice that element.

## 2. Minimum Size Subarray Sum — sliding window

**Problem:** for positive integers, return the minimum length of a contiguous subarray with sum at least target; return 0 if none exists.

**Baseline:** inspect all start/end ranges, O(n²).

**Invariant:** window [left,right] contains exactly the elements represented by sum. Since values are positive, extending right cannot lower the sum; when the sum reaches target, removing left can only shrink it. This monotonicity justifies the window. The logic fails for arbitrary negative values.

```csharp
public static int MinSubArrayLen(int target, int[] nums)
{
    var left = 0;
    long sum = 0;
    var best = int.MaxValue;

    for (var right = 0; right < nums.Length; right++)
    {
        sum += nums[right];

        while (sum >= target)
        {
            best = Math.Min(best, right - left + 1);
            sum -= nums[left];
            left++;
        }
    }

    return best == int.MaxValue ? 0 : best;
}
```

**Complexity:** O(n) time; each pointer advances at most n times. O(1) extra space.

**Tests:** one element meets target; all items needed; no valid window; empty input; large values requiring a wider sum.

**Constraint change:** if negatives are allowed, sliding-window monotonicity is gone; use a suitable prefix-sum/ordered data structure method.

## 3. Number of Islands — grid BFS

**Problem:** count 4-directionally connected groups of land ('1'). State whether input mutation is allowed. This version marks visited cells by mutating the grid.

**Invariant:** each land cell is enqueued and processed at most once. Mark it when enqueued so neighboring cells cannot add it repeatedly. A traversal from one unvisited land cell discovers one connected component.

```csharp
public static int CountIslands(char[][] grid)
{
    if (grid.Length == 0) return 0;

    var rows = grid.Length;
    var cols = grid[0].Length;
    var islands = 0;
    var queue = new Queue<(int Row, int Col)>();
    var directions = new (int Dr, int Dc)[]
    {
        (1, 0), (-1, 0), (0, 1), (0, -1)
    };

    for (var r = 0; r < rows; r++)
    {
        for (var c = 0; c < cols; c++)
        {
            if (grid[r][c] != '1') continue;

            islands++;
            grid[r][c] = '0';
            queue.Enqueue((r, c));

            while (queue.Count > 0)
            {
                var (cr, cc) = queue.Dequeue();

                foreach (var (dr, dc) in directions)
                {
                    var nr = cr + dr;
                    var nc = cc + dc;
                    if (nr < 0 || nr >= rows || nc < 0 || nc >= cols ||
                        grid[nr][nc] != '1')
                        continue;

                    grid[nr][nc] = '0';
                    queue.Enqueue((nr, nc));
                }
            }
        }
    }

    return islands;
}
```

**Complexity:** O(rows × cols) time; O(rows × cols) worst-case queue space. Each cell is visited once and checks a constant number of neighbors.

**Tests:** empty grid; all water; one land cell; one component; diagonal-only land cells (separate under 4-directional adjacency). Validate rectangular dimensions or handle ragged rows explicitly.

## Interview execution checklist

- Clarify contract and mutation/return convention.
- State baseline before optimizing.
- Name the invariant in plain language.
- Trace a representative and a boundary example.
- Use compile-ready code and test it aloud.
- Give complexity and its assumptions.
- State a constraint change that invalidates or alters the approach.
- Close with a correctness/complexity summary.
