// Automatic FlutterFlow imports
import '/backend/backend.dart';import '/backend/schema/structs/index.dart';
import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import 'index.dart'; // Imports other custom widgets
import '/flutter_flow/custom_functions.dart'; // Imports custom functions
import 'package:flutter/material.dart';
// Begin custom widget code
// DO NOT REMOVE OR MODIFY THE CODE ABOVE!

import 'package:readmore/readmore.dart';

class Readmore extends StatefulWidget {
  const Readmore({
    super.key,
    this.width,
    this.height,
  });

  final double? width;
  final double? height;

  @override
  State<Readmore> createState() => _ReadmoreState();
}

class _ReadmoreState extends State<Readmore> {
  @override
  Widget build(BuildContext context) {
    return ReadMoreText(
      'This toyota fortuner legender model isnt a world apart from the standard version, and yet gets a more premium looking face and more features on the inside. Sure, the price of this new top-spec trim has shot up and isnt available with a 4x4 set-up. .',
      style: TextStyle(
          fontFamily: 'Satoshi',
          color: FlutterFlowTheme.of(context).primaryText,
          fontSize: 16,
          fontWeight: FontWeight.w400),
      trimMode: TrimMode.Line,
      trimLines: 2,
      colorClickableText: Color(0xffE75434),
      trimCollapsedText: 'Read more..',
      trimExpandedText: 'Show less',
      lessStyle: TextStyle(
          fontSize: 16,
          fontWeight: FontWeight.w400,
          color: FlutterFlowTheme.of(context).primary),
      moreStyle: TextStyle(
          fontSize: 16,
          fontWeight: FontWeight.w500,
          color: FlutterFlowTheme.of(context).primary),
    );
  }
}
