<h1 align="center">
	<img
		alt="spark"
		src="https://i.imgur.com/ykHn9vx.png">
</h1>

# WindPvP build

This fork builds spark-minestom for the WindPvP servers, against the Minestom version they run. The jar bundles
spark-common and its libraries (relocated under `me.lucko.spark.lib`), so using it needs nothing but Minestom:

```xml
<repository>
    <id>windpvp-spark</id>
    <url>https://raw.githubusercontent.com/WindPvP/spark/maven/</url>
</repository>

<dependency>
    <groupId>ga.windpvp</groupId>
    <artifactId>spark-minestom</artifactId>
    <version>1.10.165-1</version>
</dependency>
```

To release, change `releaseVersion` in `spark-minestom/gradle.properties` (for example to `1.10.165-2`) and push. The
`Minestom` workflow builds every push and commits each version that is not published yet to the `maven` branch, which
is the repository above. Published versions are never overwritten.

# Spark for Minestom
```kts
repositories {
    maven("https://repo.hypera.dev/snapshots/") // spark-minestom
    maven("https://repo.lucko.me/") // spark-common
    maven("https://oss.sonatype.org/content/repositories/snapshots/") // spark-common's dependencies
}

dependencies {
    implementation("dev.lu15:spark-minestom:1.10-SNAPSHOT")
}
```
```java
Path directory = Path.of("spark");
SparkMinestom spark = SparkMinestom.builder(directory)
        .commands(true) // enables registration of Spark commands
        .permissionHandler((sender, permission) -> true) // allows all command senders to execute all commands
        .enable();
```

# spark-extra-platforms

This repository contains implementations of [spark](https://github.com/lucko/spark) for additional platforms.

These releases do not receive the same level of support as the main spark plugins/mods. They are provided as-is, and may be out of date or contain bugs. If you run into problems, please open an issue on GitHub and/or raise a pull request to fix!

#### Useful Links
* [**Website**](https://spark.lucko.me/) - browse the project homepage
* [**Documentation**](https://spark.lucko.me/docs) - read documentation and usage guides
* [**Downloads**](https://ci.lucko.me/job/spark-extra-platforms/) - latest plugin/mod downloads

## License

spark is free & open source. It is released under the terms of the GNU GPLv3 license. Please see [`LICENSE.txt`](LICENSE.txt) for more information. 
