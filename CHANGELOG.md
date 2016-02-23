Changelog
=========

This changelog mostly documents breaking changes and deprecations.
For a complete list of releases, see the [releases page][0].

[0]: https://github.com/treehouselabs/queue/releases


## v0.1.0

### Fixes
* The Doctrine serializer removed the identifier keys, which is a problem when
  using entities with composite identifiers.

### Changes
* Added Symfony3 support
* Added timestamp property to `Message`

### Breaking changes
* Implemented AMQP abstraction layer: all AMQP related classes have been moved.
  * If you're importing/extending classes from this library, you need to update
    their namespaces.
  * All references to the `\AMQP*` classes/constants need to be changed to
    their counterparts provided by this library. For instance: `AMQP_REQUEUE`
    becomes `QueueInterface::REQUEUE`.
* Renamed base exception from `QueueException` to `AmqpException`
* `Message` and `MessageProperties` class properties are now private instead of protected
* The Jms serializer has a changed constructor and now accepts a context rather
  than groups:

  **Before:**

  ```php
  public function __construct(BaseSerializer $serializer, array $groups = [], $format = 'json')
  ```

  **After:**

  ```php
  public function __construct(BaseSerializer $serializer, $format = 'json', SerializationContext $context = null)
  ```


## v0.0.1

First alpha release