# flutter-widgets

StatefulBuilder class
A platonic widget that both has state and calls a closure to obtain its child widget.
The StateSetter function passed to the builder is used to invoke a rebuild instead of a typical State's State.setState.
Since the builder is re-invoked when the StateSetter is called, any variables that represents state should be kept outside the builder function.
Link: https://api.flutter.dev/flutter/widgets/StatefulBuilder-class.html

await showDialog<void>(
  context: context,
  builder: (BuildContext context) {
    int? selectedRadio = 0;
    return AlertDialog(
      content: StatefulBuilder(
        builder: (BuildContext context, StateSetter setState) {
          return Column(
            mainAxisSize: MainAxisSize.min,
            children: List<Widget>.generate(4, (int index) {
              return Radio<int>(
                value: index,
                groupValue: selectedRadio,
                onChanged: (int? value) {
                  setState(() => selectedRadio = value);
                },
              );
            }),
          );
        },
      ),
    );
  },
);



ScaffoldMessenger class Null safety
Manages SnackBars and MaterialBanners for descendant Scaffolds.
https://api.flutter.dev/flutter/material/ScaffoldMessenger-class.html

  ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(
            content: Text('A SnackBar has been shown.'),
          ),
        );























Badges(Package)


dependencies:
  badges: ^2.0.2


Badge(
      badgeContent: Text('3'),
      child: Icon(Icons.settings),
    )
Link: https://pub.dev/packages/badges#basic-usage


Baseline class
https://api.flutter.dev/flutter/widgets/Baseline-class.html
A widget that positions its child according to the child's baseline.

Baseline(
baseline: 100,
baselineType: TextBaseline.alphabetic,
child: MyText(),
)

Freezed
code generator for data-classes/unions/pattern-matching/cloning.

https://pub.dev/packages/freezed










TabPageSelector

https://dartpad.dev/?null_safety=true&id=afc693da482659e918d46a21c5e80ae4
https://api.flutter.dev/flutter/material/TabPageSelector-class.html

Displays a row of small circular indicators, one per tab.
The selected tab's indicator is highlighted. Often used in conjunction with a TabBarView.
If a TabController is not provided, then there must be a DefaultTabController ancestor.

class MyHomePage extends StatefulWidget {
  final String title;




  const MyHomePage({
    Key? key,
    required this.title,
  }) : super(key: key);

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> with SingleTickerProviderStateMixin {
  final int _numDots = 3;
  late final TabController _controller;
  
  @override
  void initState() {
    super.initState();
    _controller = TabController(length: _numDots, vsync: this);
  }

  void _incrementCounter() {
    setState(() {
      (_controller.index == _numDots - 1) ? _controller.index = 0 : _controller.index++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('You are on index: ${_controller.index}'),
            TabPageSelector(controller: _controller),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
    );
  }
}



font_awesome_flutter(Package)
The Font Awesome Icon pack available as set of Flutter Icons.
https://pub.dev/packages/font_awesome_flutter



import 'package:font_awesome_flutter/font_awesome_flutter.dart';

class MyWidget extends StatelessWidget {
  Widget build(BuildContext context) {
    return IconButton(
      // Use the FaIcon Widget + FontAwesomeIcons class for the IconData
      icon: FaIcon(FontAwesomeIcons.gamepad), 
      onPressed: () { print("Pressed"); }
     );
  }
}


sensors_plus(Package)
https://pub.dev/packages/sensors_plus
To use this plugin, add sensors_plus as a dependency in your pubspec.yaml file.
This will expose four classes of sensor events through four different streams.
AccelerometerEvents describe the velocity of the device, including the effects of gravity. Put simply, you can use accelerometer readings to tell if the device is moving in a particular direction.
UserAccelerometerEvents also describe the velocity of the device, but don't include gravity. They can also be thought of as just the user's affect on the device.
GyroscopeEvents describe the rotation of the device.
MagnetometerEvents describe the ambient magnetic field surrounding the device. A compass is an example usage of this data.
import 'package:sensors_plus/sensors_plus.dart';

accelerometerEvents.listen((AccelerometerEvent event) {
  print(event);
});
// [AccelerometerEvent (x: 0.0, y: 9.8, z: 0.0)]
userAccelerometerEvents.listen((UserAccelerometerEvent event) {
  print(event);
});
// [UserAccelerometerEvent (x: 0.0, y: 0.0, z: 0.0)]
gyroscopeEvents.listen((GyroscopeEvent event) {
  print(event);
});
// [GyroscopeEvent (x: 0.0, y: 0.0, z: 0.0)]
magnetometerEvents.listen((MagnetometerEvent event) {
  print(event);
});
// [MagnetometerEvent (x: -23.6, y: 6.2, z: -34.9)]


MouseRegion class
A widget that tracks the movement of mice.
MouseRegion is used when it is needed to compare the list of objects that a mouse pointer is hovering over between this frame and the last frame. This means entering events, exiting events, and mouse cursors.
MouseRegion(
        onEnter: _incrementEnter,
        onHover: _updateLocation,
        onExit: _incrementExit,
        child: Container(
          color: Colors.lightBlueAccent,
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              const Text(
                  'You have entered or exited this box this many times:'),
              Text(
                '$_enterCounter Entries\n$_exitCounter Exits',
                style: Theme.of(context).textTheme.headline4,
              ),
              Text(
                'The cursor is here: (${x.toStringAsFixed(2)}, ${y.toStringAsFixed(2)})',
              ),
            ],
          ),
        ), ),
animated_text_kit
A flutter package which contains a collection of some cool and awesome text animations.

https://pub.dev/packages/animated_text_kit

AnimatedTextKit(
  animatedTexts: [
    TypewriterAnimatedText(
      'Hello world!',
      textStyle: const TextStyle(
        fontSize: 32.0,
        fontWeight: FontWeight.bold,
      ),
      speed: const Duration(milliseconds: 2000),
    ),
  ],
  
  totalRepeatCount: 4,
  pause: const Duration(milliseconds: 1000),
  displayFullTextOnTap: true,
  stopPauseOnTap: true,
)

FlutterLogo
FlutterLogo widget is as simple as it sounds, it is just the flutter logo in the form of an icon. This widget also comes built-in with flutter SDK. This widget can found its use as a placeholder for an image or icon.
FlutterLogo(
              size: 300,
              textColor: Colors.blue,
              style: FlutterLogoStyle.stacked,
            ),
Scrollbar class
A Material Design scrollbar.
To add a scrollbar to a ScrollView, wrap the scroll view widget in a Scrollbar widget.
https://api.flutter.dev/flutter/material/Scrollbar-class.html
Scrollbar(
                isAlwaysShown: true,
                controller: _firstController,
                child: ListView.builder(
                    controller: _firstController,
                    itemCount: 100,
                    itemBuilder: (BuildContext context, int index) {
                      return Padding(
                        padding: const EdgeInsets.all(8.0),
                        child: Text('Scrollable 1 : Index $index'),
                      );
                    }),
              )


ExpansionPanel 
The ExpansionPanel widget will expand when tapped on to show more information, for those times when the details don’t justify an entirely separate view.

http://goo.gle/expansionpanel
  ExpansionPanel(
                body: ListTile(
                    subtitle: Text(
                        "... amet, consectetur adipiscing elit. Nullam ultricies porta rutrum. Vivamus id ultrices velit. Sed tellus lorem, egestas ac magna non, fringilla sagittis erat. Interdum et malesuada fames ac ante ipsum primis in faucibus. Fusce tempor mi et eleifend fermentum. Sed quis molestie nunc.")),
                headerBuilder: (_, isExpanded) {
                  return Center(
                    child: Text("Lorem ipsum dolor sit ..."),
                  );
                },
                isExpanded: _isExpanded[i],
              )


RotatedBox class
A widget that rotates its child by a integral number of quarter turns.

const RotatedBox(
  quarterTurns: 3,
  child: Text('Hello World!'),
)

https://www.youtube.com/watch?v=BFE6_UglLfQ&list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG&index=27

https://api.flutter.dev/flutter/widgets/RotatedBox-class.html




flutter_slidable (Package)
Slidable(
  // Specify a key if the Slidable is dismissible.
  key: const ValueKey(0),

  // The start action pane is the one at the left or the top side.
  startActionPane: ActionPane(
    // A motion is a widget used to control how the pane animates.
    motion: const ScrollMotion(),

    // A pane can dismiss the Slidable.
    dismissible: DismissiblePane(onDismissed: () {}),

    // All actions are defined in the children parameter.
    children: const [
      // A SlidableAction can have an icon and/or a label.
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFFFE4A49),
        foregroundColor: Colors.white,
        icon: Icons.delete,
        label: 'Delete',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF21B7CA),
        foregroundColor: Colors.white,
        icon: Icons.share,
        label: 'Share',
      ),
    ],
  ),

  // The end action pane is the one at the right or the bottom side.
  endActionPane: const ActionPane(
    motion: ScrollMotion(),
    children: [
      SlidableAction(
        // An action can be bigger than the others.
        flex: 2,
        onPressed: doNothing,
        backgroundColor: Color(0xFF7BC043),
        foregroundColor: Colors.white,
        icon: Icons.archive,
        label: 'Archive',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF0392CF),
        foregroundColor: Colors.white,
        icon: Icons.save,
        label: 'Save',
      ),
    ],
  ),

  // The child of the Slidable is what the user sees when the
  // component is not dragged.
  child: const ListTile(title: Text('Slide me')),
),



https://pub.dev/packages/flutter_slidable

Draggable

A widget that can be dragged from to a DragTarget.


import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  static const String _title = 'Flutter Code Sample';

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: _title,
      home: Scaffold(
        appBar: AppBar(title: const Text(_title)),
        body: const MyStatefulWidget(),
      ),
    );
  }
}

class MyStatefulWidget extends StatefulWidget {
  const MyStatefulWidget({Key? key}) : super(key: key);

  @override
  State<MyStatefulWidget> createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int acceptedData = 0;

  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: <Widget>[
        Draggable<int>(
          // Data is the value this Draggable stores.
          data: 10,
          feedback: Container(
            color: Colors.deepOrange,
            height: 100,
            width: 100,
            child: const Icon(Icons.directions_run),
          ),
          childWhenDragging: Container(
            height: 100.0,
            width: 100.0,
            color: Colors.pinkAccent,
            child: const Center(
              child: Text('Child When Dragging'),
            ),
          ),
          child: Container(
            height: 100.0,
            width: 100.0,
            color: Colors.lightGreenAccent,
            child: const Center(
              child: Text('Draggable'),
            ),
          ),
        ),
        DragTarget<int>(
          builder: (
            BuildContext context,
            List<dynamic> accepted,
            List<dynamic> rejected,
          ) {
            return Container(
              height: 100.0,
              width: 100.0,
              color: Colors.cyan,
              child: Center(
                child: Text('Value is updated to: $acceptedData'),
              ),
            );
          },
          onAccept: (int data) {
            setState(() {
              acceptedData += data;
            });
          },
        ),
      ],
    );
  }
}




ShaderMask
A widget that applies a mask generated by a Shader to its child.

ShaderMask(
  shaderCallback: (Rect bounds) {
    return RadialGradient(
      center: Alignment.topLeft,
      radius: 1.0,
      colors: <Color>[Colors.yellow, Colors.deepOrange.shade900],
      tileMode: TileMode.mirror,
    ).createShader(bounds);
  },
  child: const Text('I’m burning the memories'),
)
AboutDialog
An about box. This is a dialog box with the application's icon, name, version number, and copyright, plus a button to show licenses for software used by the application.

















Tool tip

Wrap your icons and images with Tooltips to attach Tooltip messages that improve accessibility and provide more context.

Tooltip(
message: “Dash”,
height: 24,
verticalOffset: 48,
child: Container(
child:
Text(“ hello”)
))

Some material widgets comes with the tooltip included:
IconButton(
icon: ….,
tooltip: “Message”
)

 

Dismissible
A widget that can be dismissed by dragging in the indicated direction.

import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  static const String _title = 'Flutter Code Sample';

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: _title,
      home: Scaffold(
        appBar: AppBar(title: const Text(_title)),
        body: const MyStatefulWidget(),
      ),
    );
  }
}

class MyStatefulWidget extends StatefulWidget {
  const MyStatefulWidget({Key? key}) : super(key: key);

  @override
  State<MyStatefulWidget> createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  List<int> items = List<int>.generate(100, (int index) => index);

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      itemCount: items.length,
      padding: const EdgeInsets.symmetric(vertical: 16),
      itemBuilder: (BuildContext context, int index) {
        return Dismissible(
          background: Container(
            color: Colors.green,
          ),
          key: ValueKey<int>(items[index]),
          onDismissed: (DismissDirection direction) {
            setState(() {
              items.removeAt(index);
            });
          },
          child: ListTile(
            title: Text(
              'Item ${items[index]}',
            ),
          ),
        );
      },
    );
  }
}


