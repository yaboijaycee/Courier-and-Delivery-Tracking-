# Commit 09: feat: add ShipmentDetail with shipment info

Create **src/components/ShipmentDetail.jsx**:

```jsx
import StatusBadge from "./StatusBadge.jsx";

export default function ShipmentDetail({ shipment }) {
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
    </div>
  );
}
```

Commit:

```bash
git add src/components/ShipmentDetail.jsx
git commit -m "feat: add ShipmentDetail with shipment info"
```
