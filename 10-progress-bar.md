# Commit 10: feat: add delivery progress bar

**Replace** **src/components/ShipmentDetail.jsx** with:

```jsx
import StatusBadge from "./StatusBadge.jsx";
import { STATUSES } from "../data.js";

export default function ShipmentDetail({ shipment }) {
  const steps = STATUSES.filter((s) => s.key !== "exception");
  const progressIdx = steps.findIndex((s) => s.key === shipment.status);

  return (
    <div className="detail">
      <div className="row">
        <h2>{shipment.id}</h2>
        <StatusBadge status={shipment.status} />
      </div>
      <p className="meta">{shipment.courier} · {shipment.weightKg} kg</p>
      <p>
        <strong>{shipment.sender}</strong> → <strong>{shipment.recipient}</strong>
        <br />
        {shipment.origin} → {shipment.destination}
      </p>

      {shipment.status !== "exception" && (
        <div className="progress">
          {steps.map((s, i) => (
            <div key={s.key} className={`step ${i <= progressIdx ? "done" : ""}`}>
              <span className="dot" />
              <span className="step-label">{s.label}</span>
            </div>
          ))}
        </div>
      )}
    </div>
  );
}
```

**Append** to `src/styles.css`:

```css
.progress { display: flex; margin: 20px 0 4px; }
.step { flex: 1; display: flex; flex-direction: column; align-items: center; position: relative; text-align: center; }
.step::before { content: ""; position: absolute; top: 6px; left: -50%; width: 100%; height: 3px; background: var(--border); }
.step:first-child::before { display: none; }
.step.done::before { background: var(--primary); }
.dot { width: 15px; height: 15px; border-radius: 50%; background: var(--border); z-index: 1; }
.step.done .dot { background: var(--primary); }
.step-label { font-size: .7rem; margin-top: 6px; color: var(--muted); }
```

Commit:

```bash
git add src/components/ShipmentDetail.jsx src/styles.css
git commit -m "feat: add delivery progress bar"
```
