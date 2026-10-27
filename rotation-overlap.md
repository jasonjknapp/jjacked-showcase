# Rotation overlap

This pure function measures the shared muscle load between a candidate and the exercise just completed. The surrounding planner uses this as a ranking penalty; the function is shown in its original app context.

```swift
    public static func overlap(candidate: [String: Double], worked: [String: Double]) -> Double {
        guard !candidate.isEmpty, !worked.isEmpty else { return 0 }
        var total = 0.0
        for muscle in worked.keys.sorted() {
            guard let load = worked[muscle], load >= overlapFocusThreshold,
                  let shared = candidate[muscle], shared > 0 else { continue }
            total += min(shared, load)
        }
        return total
    }
```
