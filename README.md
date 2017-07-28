# simple-logging
One file simple logging utility. Fledged console logging without dependency.

# How to use:
Just copy file content, add your package name and private modifier, you're good to go.

### Basic usage:
```scala
class MyClass extends SimpleLogging{
  trace(...)
  debug(...)
  info(...) //default logging level.
  warn(...)
  error(...)
}
```

### Change logging level:
1. override loggerLevel
```scala
class MyClass extends SimpleLogging{
  override val loggerLevel = SimpleLogging.Trace
}
```

2. provide property file: `simple-logger.properties` in `resources` dir.
```properties
com.github.cuzfrog.scmd = info
com.github.cuzfrog.scmd.runtime = debug
com.github.cuzfrog.scmd.runtime.SomeObject$ = trace
```

### AOP logging:
A scalameta annotation is shipped for control single AOP method:
```scala
@IgnoreLogging
abstract override def addValidation[T](name: String, func: (T) => Unit): Unit = {
  debug(s"Add validation for arg:$name, func:$func")
  super.addValidation(name, func)
}
```
Aop Code example: [portal](https://github.com/cuzfrog/scala-points/blob/master/README.md#11aop-in-scala)

`@IgnoreLogging` depends on [ScalaMeta](http://scalameta.org/) at compile time.