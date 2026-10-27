# Settings change undo

This method restores a previous setting only when the current value still matches the value being undone. It records the outcome so a later edit is not silently overwritten. Types and storage helpers belong to the full app.

```swift
    @MainActor
    @discardableResult
    public func undo(entryId: String, target: SettingsPatchTarget, now: Date = Date()) -> Bool? {
        var all = entries()
        guard let i = all.firstIndex(where: { $0.id == entryId }), all[i].canUndo else { return nil }
        let c = all[i].change
        let inverse = SettingsChange(key: c.key, muscle: c.muscle, from: c.to, to: c.from)
        guard SettingsPatchPlanner.evaluate(inverse, target: target).outcome == .apply,
              target.write(key: c.key, muscle: c.muscle, value: c.from) else {
            all[i].reason = "not undone: value changed since"
            save(all)
            return false
        }
        target.batchDidWrite()
        all[i].status = .undone
        all[i].undoneAt = now
        all[i].reason = nil
        save(all)
        return true
    }
```
