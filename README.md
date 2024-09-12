# @mozart25/react-event-bus

A simple event bus for React and Next.js applications.

## Installation

```bash
npm install @mozart25/react-event-bus
```

Usage

In ComponentA

```javascript
import React from "react";
import eventBus from "@mozart25/react-event-bus";

const ComponentA = () => {
  const handleClick = () => {
    eventBus.emit("customEvent", "Hello from ComponentA");
  };

  return <button onClick={handleClick}>Send Event</button>;
};

export default ComponentA;
```

In ComponentB

```javascript
import React, { useEffect, useState } from "react";
import eventBus from "@mozart25/react-event-bus";

const ComponentB = () => {
  const [message, setMessage] = useState("");

  useEffect(() => {
    const handleEvent = (data) => {
      setMessage(data);
    };

    eventBus.on("customEvent", handleEvent);

    return () => {
      eventBus.off("customEvent", handleEvent);
    };
  }, []);

  return <div>Received Message: {message}</div>;
};

export default ComponentB;
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue if you have any suggestions or improvements.

## License

This project is licensed under the MIT License.
