import '/backend/schema/structs/index.dart';
import '/flutter_flow/flutter_flow_animations.dart';
import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import '/flutter_flow/flutter_flow_widgets.dart';
import '/profile/componetes/appbar/appbar_widget.dart';
import '/profile/componetes/car_componet/car_componet_widget.dart';
import 'dart:math';
import 'dart:ui';
import '/flutter_flow/custom_functions.dart' as functions;
import 'package:flutter/material.dart';
import 'package:flutter/scheduler.dart';
import 'package:flutter_animate/flutter_animate.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:provider/provider.dart';

import 'more_from_seller_model.dart';
export 'more_from_seller_model.dart';

class MoreFromSellerWidget extends StatefulWidget {
  const MoreFromSellerWidget({super.key});

  static String routeName = 'MoreFromSeller';
  static String routePath = '/moreFromSeller';

  @override
  State<MoreFromSellerWidget> createState() => _MoreFromSellerWidgetState();
}

class _MoreFromSellerWidgetState extends State<MoreFromSellerWidget>
    with TickerProviderStateMixin {
  late MoreFromSellerModel _model;

  final scaffoldKey = GlobalKey<ScaffoldState>();

  final animationsMap = <String, AnimationInfo>{};

  @override
  void initState() {
    super.initState();
    _model = createModel(context, () => MoreFromSellerModel());

    animationsMap.addAll({
      'wrapOnPageLoadAnimation': AnimationInfo(
        trigger: AnimationTrigger.onPageLoad,
        effectsBuilder: () => [
          FadeEffect(
            curve: Curves.easeInOut,
            delay: 100.0.ms,
            duration: 600.0.ms,
            begin: 0.0,
            end: 1.0,
          ),
        ],
      ),
    });

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
                    's0yjbo92' /* More from seller  */,
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
                          final popularevcars = functions
                                  .filterdata('Popular ev cars',
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
                            children: List.generate(popularevcars.length,
                                (popularevcarsIndex) {
                              final popularevcarsItem =
                                  popularevcars[popularevcarsIndex];
                              return wrapWithModel(
                                model: _model.carComponetModels.getModel(
                                  popularevcarsIndex.toString(),
                                  popularevcarsIndex,
                                ),
                                updateCallback: () => safeSetState(() {}),
                                child: CarComponetWidget(
                                  key: Key(
                                    'Keyb5n_${popularevcarsIndex.toString()}',
                                  ),
                                  hight: 219.0,
                                  data: popularevcarsItem,
                                ),
                              );
                            }),
                          ).animateOnPageLoad(
                              animationsMap['wrapOnPageLoadAnimation']!);
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
