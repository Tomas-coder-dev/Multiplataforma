# Multiplataforma
import 'package:flutter/material.dart';

void main() {
  runApp(const MiCalculadora());
}

class MiCalculadora extends StatefulWidget {
  const MiCalculadora({Key? key}) : super(key: key);

  @override
  _MiCalculadoraState createState() => _MiCalculadoraState();
}

class _MiCalculadoraState extends State<MiCalculadora> {
  int _clickCounter = 0;

  void _buttonPressed(String buttonText) {
    setState(() {
      _clickCounter++;
    });
  }

  Widget buildButton(String text, Color color, Color textColor, {int flex = 1}) {
    return Expanded(
      flex: flex,
      child: Container(
        margin: const EdgeInsets.all(6),
        decoration: BoxDecoration(
          color: color,
          borderRadius: BorderRadius.circular(50),
        ),
        child: Material(
          color: Colors.transparent,
          child: InkWell(
            borderRadius: BorderRadius.circular(50),
            onTap: () => _buttonPressed(text),
            child: Center(
              child: Text(
                text,
                style: TextStyle(
                  fontSize: 36,
                  color: textColor,
                  fontWeight: FontWeight.bold,
                ),
              ),
            ),
          ),
        ),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: SafeArea(
        child: Scaffold(
          backgroundColor: Colors.black,
          body: Column(
            children: [
              Expanded(
                flex: 1,
                child: Container(
                  width: double.infinity,
                  color: Colors.grey[900],
                  alignment: Alignment.center,
                  child: Text(
                    'Clicks: $_clickCounter',
                    style: const TextStyle(
                      fontSize: 48,
                      color: Colors.white,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
              ),
              Expanded(
                flex: 2,
                child: Container(
                  padding: const EdgeInsets.all(10),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.end,
                    children: [
                      Expanded(
                        child: Row(
                          children: [
                            buildButton('AC', Colors.pink[400]!, Colors.white),
                            buildButton('+/-', Colors.cyan[400]!, Colors.white),
                            buildButton('%', Colors.tealAccent[400]!, Colors.white),
                            buildButton('÷', Colors.orange[400]!, Colors.white),
                          ],
                        ),
                      ),
                      const SizedBox(height: 8),
                      Expanded(
                        child: Row(
                          children: [
                            buildButton('7', Colors.indigo[400]!, Colors.white),
                            buildButton('8', Colors.blue[400]!, Colors.white),
                            buildButton('9', Colors.lightBlue[400]!, Colors.white),
                            buildButton('×', Colors.orange[400]!, Colors.white),
                          ],
                        ),
                      ),
                      const SizedBox(height: 8),
                      Expanded(
                        child: Row(
                          children: [
                            buildButton('4', Colors.green[400]!, Colors.white),
                            buildButton('5', Colors.lightGreen[400]!, Colors.white),
                            buildButton('6', Colors.lime[400]!, Colors.white),
                            buildButton('-', Colors.orange[400]!, Colors.white),
                          ],
                        ),
                      ),
                      const SizedBox(height: 8),
                      Expanded(
                        child: Row(
                          children: [
                            buildButton('1', Colors.yellow[600]!, Colors.black),
                            buildButton('2', Colors.amber[400]!, Colors.black),
                            buildButton('3', Colors.orange[400]!, Colors.white),
                            buildButton('+', Colors.orange[400]!, Colors.white),
                          ],
                        ),
                      ),
                      const SizedBox(height: 8),
                      Expanded(
                        child: Row(
                          children: [
                            buildButton('0', Colors.red[400]!, Colors.white, flex: 2),
                            buildButton('.', Colors.purple[400]!, Colors.white),
                            buildButton('=', Colors.deepOrange[400]!, Colors.white),
                          ],
                        ),
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
