# sugarcoat-labs

**sugarcoat-labs** publishes modular, production-grade Java software components designed around clean architectural boundaries, minimal dependencies, and strict behavioral guarantees.

---

## Persistence Engines

The Persistence Engines suite provides unified abstractions for event sourcing (`EventStreamEngine`) and mutable key-value state storage (`StateStoreEngine`). At the heart of the suite is the leading `core` module, which defines all behavioral contracts and provides a baseline implementation written entirely in pure Java (JDK). Downstream modules—such as the Amazon DynamoDB implementation, as well as other possible implementations for MySQL, PostgreSQL, or MongoDB, etc. — strictly adhere to these core contracts. As a result, they offer identical behavioral and concurrency guarantees, making the underlying storage engines completely swappable. 

### [`persistence-engines-core`](https://github.com/sugarcoat-labs/persistence-engines-core)
The leading Java 24 module defining all persistence contracts, concurrency exceptions, and fluent pipeline entry points with zero external compile dependencies. It provides a thread-safe, pure-JDK in-memory realization alongside an exportable Technology Compatibility Kit (`test-jar`) that defines and verifies monotonic sequence ordering, global idempotency, and virtual-thread safety across storage implementations.

### [`persistence-engines-dynamodb`](https://github.com/sugarcoat-labs/persistence-engines-dynamodb)
The Amazon DynamoDB realization of `persistence-engines-core`. This module directly imports the persistence interfaces and the portable Technology Compatibility Kit (`test-jar`) from `core`, implementing single-table storage with `TransactWriteItems` and a zero-framework `DynamoDbCodec<T>` for custom payload serialization, verified against `amazon/dynamodb-local`.

## Support & Sponsorship
If you find this project helpful or use it in your work, please consider supporting its ongoing development. Your sponsorship helps maintain existing features, build new tools, and keep these open-source projects moving forward.

[💖 Sponsor @x-artifactory on GitHub](https://github.com/sponsors/x-artifactory)
