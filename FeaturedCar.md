import '/backend/schema/structs/index.dart';
import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import '/flutter_flow/flutter_flow_widgets.dart';
import '/profile/componetes/appbar/appbar_widget.dart';
import '/profile/componetes/car_componet/car_componet_widget.dart';
import 'dart:ui';
import '/flutter_flow/custom_functions.dart' as functions;
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:provider/provider.dart';

import 'featured_car_copy_model.dart';
export 'featured_car_copy_model.dart';

class FeaturedCarCopyWidget extends StatefulWidget {
  const FeaturedCarCopyWidget({super.key});

  static String routeName = 'FeaturedCarCopy';
  static String routePath = '/featuredCarCopy';

  @override
  State<FeaturedCarCopyWidget> createState() => _FeaturedCarCopyWidgetState();
}

class _FeaturedCarCopyWidgetState extends State<FeaturedCarCopyWidget> {
  late FeaturedCarCopyModel _model;

  final scaffoldKey = GlobalKey<ScaffoldState>();

  @override
  void initState() {
    super.initState();
    _model = createModel(context, () => FeaturedCarCopyModel());

    WidgetsBinding.instance.addPostFrameCallback((_) => safeSetState(() {}));
  }

  @override
  void dispose() {
    _model.dispose();

    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    context.watch<FFAppState>();

    return GestureDetector(
      onTap: () {
        FocusScope.of(context).unfocus();
        FocusManager.instance.primaryFocus?.unfocus();
      },
      child: Scaffold(
        key: scaffoldKey,
        backgroundColor: FlutterFlowTheme.of(context).secondaryBackground,
        body: SafeArea(
          top: true,
          child: Column(
            mainAxisSize: MainAxisSize.max,
            children: [
              wrapWithModel(
                model: _model.appbarModel,
                updateCallback: () => safeSetState(() {}),
                child: AppbarWidget(
                  title: FFLocalizations.of(context).getText(
                    'rz62o8in' /* Featured car */,
                  ),
                ),
              ),
              Expanded(
                child: ListView(
                  padding: EdgeInsets.fromLTRB(
                    0,
                    16,
                    0,
                    16,
                  ),
                  shrinkWrap: true,
                  scrollDirection: Axis.vertical,
                  children: [
                    Padding(
                      padding: EdgeInsetsDirectional.fromSTEB(16, 0, 16, 0),
                      child: Builder(
                        builder: (context) {
                          final featuredcar = functions
                                  .filterdata('Featured car',
                                      FFAppState().carList.toList())
                                  ?.toList() ??
                              [];

                          return Wrap(
                            spacing: 16,
                            runSpacing: 16,
                            alignment: WrapAlignment.start,
                            crossAxisAlignment: WrapCrossAlignment.start,
                            direction: Axis.horizontal,
                            runAlignment: WrapAlignment.start,
                            verticalDirection: VerticalDirection.down,
                            clipBehavior: Clip.none,
                            children: List.generate(featuredcar.length,
                                (featuredcarIndex) {
                              final featuredcarItem =
                                  featuredcar[featuredcarIndex];
                              return wrapWithModel(
                                model: _model.carComponetModels.getModel(
                                  featuredcarIndex.toString(),
                                  featuredcarIndex,
                                ),
                                updateCallback: () => safeSetState(() {}),
                                child: CarComponetWidget(
                                  key: Key(
                                    'Keykdo_${featuredcarIndex.toString()}',
                                  ),
                                  hight: 219.0,
                                  data: featuredcarItem,
                                ),
                              );
                            }),
                          );
                        },
                      ),
                    ),
                  ],
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
