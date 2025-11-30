// Automatic FlutterFlow imports
import '/backend/backend.dart';import '/backend/schema/structs/index.dart';
import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import 'index.dart'; // Imports other custom widgets
import '/flutter_flow/custom_functions.dart'; // Imports custom functions
import 'package:flutter/material.dart';
// Begin custom widget code
// DO NOT REMOVE OR MODIFY THE CODE ABOVE!

class Image1 extends StatefulWidget {
  const Image1({
    super.key,
    this.width,
    this.height,
    required this.imagepath,
  });

  final double? width;
  final double? height;
  final String imagepath;

  @override
  State<Image1> createState() => _Image1State();
}

class _Image1State extends State<Image1> {
  @override
  Widget build(BuildContext context) {
    return ClipRRect(
      borderRadius: BorderRadius.only(
        topLeft: Radius.circular(12),
        topRight: Radius.circular(12),
        bottomLeft: Radius.circular(12),
        bottomRight: Radius.circular(12),
      ),
      child: Image.asset(
        'assets/images/${widget.imagepath}',
        width: widget.width,
        height: widget.height,
        fit: BoxFit.contain,
      ),
    );
  }
}
