Bignum API for Scala.js
================================
This is a Scala.js type-safe binding for [Bignum](https://www.npmjs.com/package/bignum)

An arbitrary-precision integer arithmetic using OpenSSL.

#### Build Requirements

* [ScalaJs.io v0.3.x](https://github.com/ldaniels528/scalajs.io)
* [SBT v0.13.13](http://www.scala-sbt.org/download.html)


#### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

#### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

#### Examples

Given the following values:

```scala
val v1 = "782910138827292261791972728324982"
val v2 = "182373273283402171237474774728373"
```

You can perform math functions via built-in methods:

```scala
val b = new BigNum(v1).add(500).sub(v2).div(8)
// b.toString == "75067108192986261319312244199638"
```

Alternatively, you can perform math functions via overloaded operators:

```scala
val b = (new BigNum(v1) + 500 - v2) / 8
// b.toString == "75067108192986261319312244199638"
```

Prime number detection:

```scala
for {
    n <- 0 to 100
    p = BigNum.pow(2, n) - 1 if p.probPrime(50)
} {
    val perfect = p.mul(BigNum.pow(2, n - 1))
    println(perfect.toString)
}
```

#### Artifacts and Resolvers

To add the Moment binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "md5" % "0.3.0.3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```
