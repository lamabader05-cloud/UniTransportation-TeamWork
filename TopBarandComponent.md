import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import '/flutter_flow/flutter_flow_widgets.dart';
import 'dart:ui';
import '/custom_code/widgets/index.dart' as custom_widgets;
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:provider/provider.dart';

import 'top_barand_componet_model.dart';
export 'top_barand_componet_model.dart';

class TopBarandComponetWidget extends StatefulWidget {
  const TopBarandComponetWidget({
    super.key,
    required this.name,
    required this.img,
  });

  final String? name;
  final String? img;

  @override
  State<TopBarandComponetWidget> createState() =>
      _TopBarandComponetWidgetState();
}

class _TopBarandComponetWidgetState extends State<TopBarandComponetWidget> {
  late TopBarandComponetModel _model;

  @override
  void setState(VoidCallback callback) {
    super.setState(callback);
    _model.onUpdate();
  }

  @override
  void initState() {
    super.initState();
    _model = createModel(context, () => TopBarandComponetModel());

    WidgetsBinding.instance.addPostFrameCallback((_) => safeSetState(() {}));
  }

  @override
  void dispose() {
    _model.maybeDispose();

    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Container(
      width: () {
        if (MediaQuery.sizeOf(context).width < 810.0) {
          return ((MediaQuery.sizeOf(context).width - 80) * 1 / 4);
        } else if ((MediaQuery.sizeOf(context).width >= 810.0) &&
            (MediaQuery.sizeOf(context).width <= 1280.0)) {
          return ((MediaQuery.sizeOf(context).width - 144) * 1 / 8);
        } else if (MediaQuery.sizeOf(context).width < 1280.0) {
          return ((MediaQuery.sizeOf(context).width - 208) * 1 / 12);
        } else {
          return ((MediaQuery.sizeOf(context).width - 208) * 1 / 12);
        }
      }(),
      height: 91,
      decoration: BoxDecoration(
        color: FlutterFlowTheme.of(context).primaryBackground,
        boxShadow: [
          BoxShadow(
            blurRadius: 16,
            color: Color(0x14000000),
            offset: Offset(
              0,
              4,
            ),
            spreadRadius: 0,
          )
        ],
        borderRadius: BorderRadius.circular(12),
        border: Border.all(
          color: FlutterFlowTheme.of(context).secondaryBackground,
        ),
      ),
      child: Padding(
        padding: EdgeInsetsDirectional.fromSTEB(0, 15, 0, 15),
        child: Column(
          mainAxisSize: MainAxisSize.max,
          mainAxisAlignment: MainAxisAlignment.start,
          children: [
            Container(
              decoration: BoxDecoration(),
              child: custom_widgets.Image1(
                width: 34,
                height: 34,
                imagepath: widget!.img!,
              ),
            ),
            Text(
              valueOrDefault<String>(
                widget!.name,
                '0',
              ),
              textAlign: TextAlign.center,
              maxLines: 2,
              style: FlutterFlowTheme.of(context).bodyMedium.override(
                    font: GoogleFonts.inter(
                      fontWeight:
                          FlutterFlowTheme.of(context).bodyMedium.fontWeight,
                      fontStyle:
                          FlutterFlowTheme.of(context).bodyMedium.fontStyle,
                    ),
                    fontSize: 13,
                    letterSpacing: 0.0,
                    fontWeight:
                        FlutterFlowTheme.of(context).bodyMedium.fontWeight,
                    fontStyle:
                        FlutterFlowTheme.of(context).bodyMedium.fontStyle,
                    lineHeight: 1.2,
                  ),
            ),
          ].divide(SizedBox(height: 8)),
        ),
      ),
    );
  }
}
