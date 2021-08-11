# gestures_goto
Building a simple chat interface with basic
flutter widgets

# Initialiazation and #UI

```dart
class Chat_interface extends StatefulWidget {
  @override
  _Chat_interfaceState createState() => _Chat_interfaceState();
}

class _Chat_interfaceState extends State<Chat_interface> {
  final _textController = TextEditingController();
  final List<ChatFeature> _message = [];
  final FocusNode _focusNode = new FocusNode();

  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
        appBar: AppBar(
          title: Text("Chat app"),
        ),
        body: Column(
          children: [
            Expanded(
              child: ListView.builder(
                itemBuilder: (context,  s ) => _message[s],
                padding: EdgeInsets.all(8.0),
                //reverse: ,
                itemCount: _message.length,

              ),
            ),
            Divider(
              height: 1.5,
            ),
            Container(
              decoration: BoxDecoration(
                color: Colors.grey,
              ),
              child: hello(),
            )
          ],
        )

    );
  }

  void onSubm(String yo) {
    _textController.clear();
    ChatFeature message = ChatFeature(
      text: yo,
    );

    setState(() {
      _message.insert(0, message);
    });
    _focusNode.requestFocus();
  }

  @override
  Widget hello() {
    return Container(
      margin: EdgeInsets.symmetric(horizontal: 8.0),
      child: Row(
        // NEW
        children: [
          // NEW
          Flexible(
            // NEW
            child: TextField(
              controller: _textController,
              onSubmitted: onSubm,
              focusNode: _focusNode,
              decoration:
              InputDecoration.collapsed(hintText: 'Send a message'),

            ),
          ),
          Container(
            margin: EdgeInsets.symmetric(horizontal: 4.0),
            child: IconTheme(
              data: IconThemeData(color: Colors.black) ,
              child: IconButton(

                icon: Icon(Icons.send),
                onPressed: () => _textController.text,
              ),
            ),
          )
          // NEW
        ], // NEW
      ),
    );
  }
}

class ChatFeature extends StatelessWidget {

  final String _name = "hello";
  final String text;



  ChatFeature({this.text});




  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Container(
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Container(
            margin: const EdgeInsets.only(right: 16.0),
            child: CircleAvatar(child: Text(_name[0])),
          ),
          Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(_name, style: Theme
                  .of(context)
                  .textTheme
                  .headline4),
              Container(
                margin: EdgeInsets.only(top: 5.0),
                child: Text(text),
              ),
            ],
          ),
        ],
      ),
    );
  }
}
```

`


A new Flutter application.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
