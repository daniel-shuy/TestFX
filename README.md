TestFX
======

TestFX is an easy-to-use library for testing [JavaFX](http://www.oracle.com/us/technologies/java/fx/overview/index.html). TestFX provides:

 - A fluent and clean API for interacting with, and verifying the behavior of, JavaFX applications.
 - Hamcrest Matchers for JavaFX.
 - Screenshots of failed tests.
 - Supports JavaFX 2 and JavaFX 8.


### Usage Example

```java
class DesktopTest extends GuiTest
{
  public Parent getRootNode()
  {
    return new Desktop()
  }

  @Test
  public void shouldBeAbleToDragFileToTrashCan()
  {
    // GIVEN
    rightClick( "#desktop" ).move( "New" ).click( "Text Document" ).
                             type( "myTextfile.txt" ).push( ENTER );
  
    // WHEN
    drag( ".file" ).to( "#trash-can" );
    
    // THEN
    assertThat( "#desktop", contains( 0, ".file" ) );
  }
}
```


### Getting Started
To start using TestFX, simply add the following elements to your pom.xml file:
```XML
<dependency>
    <groupId>org.loadui</groupId>
    <artifactId>testFx</artifactId>
    <version>3.0.0</version>
</dependency>
```

After that, head over to [the documentation][7].

You might also be interested in these conference sessions featuring TestFX: [JavaZone](http://jz13.java.no/presentation.html?id=89b56833) and [JavaOne][8].

### Motivation
The motivation for creating TestFX was that the existing library for testing JavaFX, [Jemmy][1], was
too verbose and unwieldy. We wanted more behavior driven tests with easy-to-read code that our tester could follow and modify on her own.
Today, TestFX is used in all of the about 100 automated GUI tests in LoadUI ([source code][9], [video][10]).

[Comparison with Jemmy][4]

### Mailing list
Head over to [testfx-discuss@googlegroups.com](https://groups.google.com/d/forum/testfx-discuss) for discussions, questions and announcements. 

### Credits
TestFX was initially created by @dainnilsson and @minisu as a part of [LoadUI][2] in 2012. Today, it is being extended
and maintained by the [LoadUI team][5].

[1]: https://jemmy.java.net/              "Jemmy website"
[2]: https://github.com/SmartBear/loadui  "LoadUI project at Github"
[3]: http://www.oracle.com/technetwork/java/javafx/overview/index.html "JavaFX website"
[4]: https://github.com/SmartBear/TestFX/wiki/Comparison-with-Jemmy "Comparison with Jemmy"
[5]: https://github.com/SmartBear/loadui/graphs/contributors "Contributors of LoadUI"
[6]: https://github.com/guigarage/MarvinFX "MarvinFX's project page on Github"
[7]: https://github.com/SmartBear/TestFX/wiki/Documentation "Documentation"
[8]: https://oracleus.activeevents.com/2013/connect/sessionDetail.ww?SESSION_ID=2670 "Ten Man-Years of JavaFX: Real-World Project Experiences [CON2670]"
[9]: https://github.com/SmartBear/loadui/tree/master/loadui-project/loadui-fx-interface/src/test/java/com/eviware/loadui/ui/fx "GUI tests in LoadUI"
[10]: http://youtu.be/fgD8fBn1cYw "Video of the LoadUI TestFX test suite"

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/c241040fcacf2493960ad0a2a2e5cec2 "githalytics.com")](http://githalytics.com/SmartBear/TestFX)
