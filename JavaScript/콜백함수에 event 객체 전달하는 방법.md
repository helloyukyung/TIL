# 콜백함수에 event 객체 전달하는 방법

```tsx
const handleChangeTimerSelect =
  (label: string) => (newValue: TimerOption | null) => {
    if (!newValue) return;
    setTime((prev) => {
      return { ...prev, [label]: newValue };
    });
  };

return (
  <TimerSelect
    onChange={handleChangeTimerSelect("hour")}
    // or
    onChange={handleChangeTimerSelect("hour")(newValue)}
  />
);
```
