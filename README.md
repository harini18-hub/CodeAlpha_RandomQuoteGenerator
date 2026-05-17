# CodeAlpha_RandomQuoteGenerator

import 'dart:math';
import 'package:flutter/material.dart';

void main() {
  runApp(const QuoteApp());
}

class QuoteApp extends StatelessWidget {
  const QuoteApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Random Quote Generator',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const QuoteHomePage(),
    );
  }
}

class QuoteHomePage extends StatefulWidget {
  const QuoteHomePage({super.key});

  @override
  State<QuoteHomePage> createState() => _QuoteHomePageState();
}

class _QuoteHomePageState extends State<QuoteHomePage> {

  List<Map<String, String>> quotes = [
    {
      "quote": "Believe in yourself.",
      "author": "Harini"
    },
    {
      "quote": "Dream big and dare to fail.",
      "author": "Norman Vaughan"
    },
    {
      "quote": "Never give up.",
      "author": "Unknown"
    },
    {
      "quote": "Success is not final.",
      "author": "Winston Churchill"
    },
    {
      "quote": "Stay positive and happy.",
      "author": "Roy Bennett"
    },
  ];

  String currentQuote = "Click the button to generate a quote";
  String currentAuthor = "";

  void generateQuote() {
    final random = Random();
    int index = random.nextInt(quotes.length);

    setState(() {
      currentQuote = quotes[index]["quote"]!;
      currentAuthor = quotes[index]["author"]!;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(

      appBar: AppBar(
        title: const Text("Random Quote Generator"),
        centerTitle: true,
      ),

      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(20),

          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [

              Text(
                currentQuote,
                textAlign: TextAlign.center,
                style: const TextStyle(
                  fontSize: 24,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 15),

              Text(
                currentAuthor,
                style: const TextStyle(
                  fontSize: 18,
                  color: Colors.grey,
                ),
              ),

              const SizedBox(height: 40),

              ElevatedButton(
                onPressed: generateQuote,

                child: const Text(
                  "New Quote",
                  style: TextStyle(fontSize: 18),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}