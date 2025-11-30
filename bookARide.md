import '/auth/firebase_auth/auth_util.dart';
import '/backend/backend.dart';
import '/flutter_flow/flutter_flow_calendar.dart';
import '/flutter_flow/flutter_flow_drop_down.dart';
import '/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import '/flutter_flow/flutter_flow_widgets.dart';
import '/flutter_flow/form_field_controller.dart';
import '/profile/componetes/appbar/appbar_widget.dart';
import 'dart:ui';
import '/index.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:provider/provider.dart';

import 'book_a_ride_model.dart';
export 'book_a_ride_model.dart';

/// Create a book ride page with ride details, seat selector, booking form
/// with name and phone fields, and price breakdown
class BookARideWidget extends StatefulWidget {
  const BookARideWidget({super.key});

  static String routeName = 'BookARide';
  static String routePath = '/bookARide';

  @override
  State<BookARideWidget> createState() => _BookARideWidgetState();
}

class _BookARideWidgetState extends State<BookARideWidget> {
  late BookARideModel _model;

  final scaffoldKey = GlobalKey<ScaffoldState>();

  @override
  void initState() {
    super.initState();
    _model = createModel(context, () => BookARideModel());

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
        backgroundColor: FlutterFlowTheme.of(context).info,
        body: SafeArea(
          top: true,
          child: Column(
            mainAxisSize: MainAxisSize.max,
            children: [
              Padding(
                padding: EdgeInsetsDirectional.fromSTEB(0, 30, 350, 0),
                child: InkWell(
                  splashColor: Colors.transparent,
                  focusColor: Colors.transparent,
                  hoverColor: Colors.transparent,
                  highlightColor: Colors.transparent,
                  onTap: () async {
                    context.pushNamed(NavbarWidget.routeName);
                  },
                  child: Icon(
                    Icons.arrow_back,
                    color: FlutterFlowTheme.of(context).primaryText,
                    size: 30,
                  ),
                ),
              ),
              Padding(
                padding: EdgeInsetsDirectional.fromSTEB(10, 0, 0, 0),
                child: wrapWithModel(
                  model: _model.appbarModel,
                  updateCallback: () => safeSetState(() {}),
                  child: AppbarWidget(
                    title: FFLocalizations.of(context).getText(
                      '9nxz4qua' /* Book a ride
 */
                      ,
                    ),
                  ),
                ),
              ),
              Form(
                key: _model.formKey,
                autovalidateMode: AutovalidateMode.disabled,
                child: Padding(
                  padding: EdgeInsets.all(4),
                  child: SingleChildScrollView(
                    child: Column(
                      mainAxisSize: MainAxisSize.max,
                      mainAxisAlignment: MainAxisAlignment.end,
                      children: [
                        FlutterFlowCalendar(
                          color: FlutterFlowTheme.of(context).home,
                          iconColor: FlutterFlowTheme.of(context).home,
                          weekFormat: false,
                          weekStartsMonday: false,
                          rowHeight: 48,
                          onChange: (DateTimeRange? newSelectedDate) {
                            safeSetState(() =>
                                _model.calendarSelectedDay = newSelectedDate);
                          },
                          titleStyle:
                              FlutterFlowTheme.of(context).titleLarge.override(
                                    font: GoogleFonts.readexPro(
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .titleLarge
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .titleLarge
                                          .fontStyle,
                                    ),
                                    letterSpacing: 0.0,
                                    fontWeight: FlutterFlowTheme.of(context)
                                        .titleLarge
                                        .fontWeight,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .titleLarge
                                        .fontStyle,
                                  ),
                          dayOfWeekStyle:
                              FlutterFlowTheme.of(context).bodyLarge.override(
                                    font: GoogleFonts.inter(
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyLarge
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyLarge
                                          .fontStyle,
                                    ),
                                    letterSpacing: 0.0,
                                    fontWeight: FlutterFlowTheme.of(context)
                                        .bodyLarge
                                        .fontWeight,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .bodyLarge
                                        .fontStyle,
                                  ),
                          dateStyle:
                              FlutterFlowTheme.of(context).bodyMedium.override(
                                    font: GoogleFonts.inter(
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                    letterSpacing: 0.0,
                                    fontWeight: FlutterFlowTheme.of(context)
                                        .bodyMedium
                                        .fontWeight,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .bodyMedium
                                        .fontStyle,
                                  ),
                          selectedDateStyle:
                              FlutterFlowTheme.of(context).titleSmall.override(
                                    font: GoogleFonts.inter(
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontStyle,
                                    ),
                                    letterSpacing: 0.0,
                                    fontWeight: FlutterFlowTheme.of(context)
                                        .titleSmall
                                        .fontWeight,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .titleSmall
                                        .fontStyle,
                                  ),
                          inactiveDateStyle:
                              FlutterFlowTheme.of(context).labelMedium.override(
                                    font: GoogleFonts.inter(
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .labelMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .labelMedium
                                          .fontStyle,
                                    ),
                                    letterSpacing: 0.0,
                                    fontWeight: FlutterFlowTheme.of(context)
                                        .labelMedium
                                        .fontWeight,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .labelMedium
                                        .fontStyle,
                                  ),
                          locale: FFLocalizations.of(context).languageCode,
                        ),
                        Padding(
                          padding: EdgeInsets.all(12),
                          child: Row(
                            mainAxisSize: MainAxisSize.max,
                            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                            children: [
                              FlutterFlowDropDown<String>(
                                controller:
                                    _model.dropDownHourValueController ??=
                                        FormFieldController<String>(null),
                                options: [
                                  FFLocalizations.of(context).getText(
                                    'tso3ko3g' /* 0 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'r7u9pvg7' /* 1 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '2srnhtuv' /* 2 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'ef2wwoq0' /* 3 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'zp0wq6yp' /* 4 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'x4brcv67' /* 5 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '0904sglx' /* 6 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '78qvjq88' /* 7 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '17l8qgwk' /* 8 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'ben8edzg' /* 9 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '48dddpib' /* 10 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '1govm72s' /* 11 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'zshgxi8d' /* 12 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '7y60cbvh' /* 13 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'r372mf6s' /* 14 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'lv9gv9e4' /* 15 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '6bkqiqwm' /* 16 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'jcmq5pzk' /* 17 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '3hr7a8qy' /* 18 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'ros0grjx' /* 19 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '3nd16a8b' /* 20 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '00hm9avm' /* 21 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '4erit7q8' /* 22 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '1dowbhpt' /* 23 */,
                                  )
                                ],
                                onChanged: (val) => safeSetState(
                                    () => _model.dropDownHourValue = val),
                                width: 150,
                                height: 30,
                                textStyle: FlutterFlowTheme.of(context)
                                    .bodyMedium
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontStyle,
                                      ),
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                hintText: FFLocalizations.of(context).getText(
                                  'pz660isy' /* Hour */,
                                ),
                                icon: Icon(
                                  Icons.keyboard_arrow_down_rounded,
                                  color: FlutterFlowTheme.of(context)
                                      .secondaryText,
                                  size: 24,
                                ),
                                fillColor: FlutterFlowTheme.of(context)
                                    .secondaryBackground,
                                elevation: 2,
                                borderColor: FlutterFlowTheme.of(context).home,
                                borderWidth: 0,
                                borderRadius: 5,
                                margin: EdgeInsetsDirectional.fromSTEB(
                                    12, 0, 12, 0),
                                hidesUnderline: true,
                                isOverButton: false,
                                isSearchable: false,
                                isMultiSelect: false,
                              ),
                              FlutterFlowDropDown<String>(
                                controller:
                                    _model.dropDownminValueController ??=
                                        FormFieldController<String>(null),
                                options: [
                                  FFLocalizations.of(context).getText(
                                    '4pkli949' /* 0 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'syolispf' /* 15 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'kd84py38' /* 30 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '0ak6al04' /* 45 */,
                                  )
                                ],
                                onChanged: (val) => safeSetState(
                                    () => _model.dropDownminValue = val),
                                width: 150,
                                height: 30,
                                textStyle: FlutterFlowTheme.of(context)
                                    .bodyMedium
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontStyle,
                                      ),
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                hintText: FFLocalizations.of(context).getText(
                                  'c7lqgzc7' /* Min */,
                                ),
                                icon: Icon(
                                  Icons.keyboard_arrow_down_rounded,
                                  color: FlutterFlowTheme.of(context)
                                      .secondaryText,
                                  size: 24,
                                ),
                                fillColor: FlutterFlowTheme.of(context)
                                    .secondaryBackground,
                                elevation: 2,
                                borderColor: FlutterFlowTheme.of(context).home,
                                borderWidth: 0,
                                borderRadius: 5,
                                margin: EdgeInsetsDirectional.fromSTEB(
                                    12, 0, 12, 0),
                                hidesUnderline: true,
                                isOverButton: false,
                                isSearchable: false,
                                isMultiSelect: false,
                              ),
                            ],
                          ),
                        ),
                        Padding(
                          padding: EdgeInsets.all(6),
                          child: Row(
                            mainAxisSize: MainAxisSize.max,
                            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                            children: [
                              FlutterFlowDropDown<String>(
                                controller:
                                    _model.dropDownFromValueController ??=
                                        FormFieldController<String>(null),
                                options: [
                                  FFLocalizations.of(context).getText(
                                    'uqskqxkg' /* GATE 1 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '4by5gmkb' /* GATE 2 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'dktivr96' /* GATE 3 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'gep9hvf9' /* GATE 4 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'alar2gjn' /* GATE 5 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'wfc8gj9q' /* GATE 6 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'et9lnqfh' /* GATE 7 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'hpw8ys3b' /* GATE 8 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'z2ijny3n' /* LIBRARY */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'tl32iyda' /* CLINIC */,
                                  )
                                ],
                                onChanged: (val) => safeSetState(
                                    () => _model.dropDownFromValue = val),
                                width: 120,
                                height: 40,
                                textStyle: FlutterFlowTheme.of(context)
                                    .bodyMedium
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontStyle,
                                      ),
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                hintText: FFLocalizations.of(context).getText(
                                  '34jsx0wn' /* From */,
                                ),
                                icon: Icon(
                                  Icons.keyboard_arrow_down_rounded,
                                  color: FlutterFlowTheme.of(context)
                                      .secondaryText,
                                  size: 24,
                                ),
                                fillColor: FlutterFlowTheme.of(context)
                                    .secondaryBackground,
                                elevation: 2,
                                borderColor: FlutterFlowTheme.of(context).home,
                                borderWidth: 0,
                                borderRadius: 8,
                                margin: EdgeInsetsDirectional.fromSTEB(
                                    12, 0, 12, 0),
                                hidesUnderline: true,
                                isOverButton: false,
                                isSearchable: false,
                                isMultiSelect: false,
                              ),
                              FlutterFlowDropDown<String>(
                                controller: _model.dropDowntoValueController ??=
                                    FormFieldController<String>(null),
                                options: [
                                  FFLocalizations.of(context).getText(
                                    'ec5g2h58' /* GATE 1 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'usoxtysx' /* GATE 2 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'f4sw07di' /* GATE 3 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'md83vmhr' /* GATE 4 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '5ax2mf5t' /* GATE 5 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'txh8dno9' /* GATE 6 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'r2cb6i1u' /* GATE 7 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'umunu8o0' /* GATE 8 */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    'ieqg5fup' /* LIBRARY */,
                                  ),
                                  FFLocalizations.of(context).getText(
                                    '3o00cnyi' /* CLINIC */,
                                  )
                                ],
                                onChanged: (val) => safeSetState(
                                    () => _model.dropDowntoValue = val),
                                width: 120,
                                height: 40,
                                textStyle: FlutterFlowTheme.of(context)
                                    .bodyMedium
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .bodyMedium
                                            .fontStyle,
                                      ),
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                hintText: FFLocalizations.of(context).getText(
                                  '21gbxsxi' /* To */,
                                ),
                                icon: Icon(
                                  Icons.keyboard_arrow_down_rounded,
                                  color: FlutterFlowTheme.of(context)
                                      .secondaryText,
                                  size: 24,
                                ),
                                fillColor: FlutterFlowTheme.of(context)
                                    .secondaryBackground,
                                elevation: 2,
                                borderColor: FlutterFlowTheme.of(context).home,
                                borderWidth: 0,
                                borderRadius: 8,
                                margin: EdgeInsetsDirectional.fromSTEB(
                                    12, 0, 12, 0),
                                hidesUnderline: true,
                                isOverButton: false,
                                isSearchable: false,
                                isMultiSelect: false,
                              ),
                            ],
                          ),
                        ),
                        Row(
                          mainAxisSize: MainAxisSize.max,
                          mainAxisAlignment: MainAxisAlignment.spaceAround,
                          children: [
                            FFButtonWidget(
                              onPressed: () async {
                                await RidesRecord.collection
                                    .doc()
                                    .set(createRidesRecordData(
                                      date: dateTimeFormat(
                                        "d/M/y",
                                        _model.calendarSelectedDay?.start,
                                        locale: FFLocalizations.of(context)
                                            .languageCode,
                                      ),
                                      time: _model.dropDownHourValue,
                                      pickup: _model.dropDownFromValue,
                                      dropoff: _model.dropDowntoValue,
                                      minute: _model.dropDownminValue,
                                      email: FFAppState().email,
                                      plan: 5,
                                    ));

                                safeSetState(() {});

                                context
                                    .pushNamed(PaymentMethodWidget.routeName);
                              },
                              text: FFLocalizations.of(context).getText(
                                'e1l4x549' /* 5 SAR/H */,
                              ),
                              options: FFButtonOptions(
                                width: MediaQuery.sizeOf(context).width * 0.3,
                                height: 40,
                                padding: EdgeInsetsDirectional.fromSTEB(
                                    16, 0, 16, 0),
                                iconPadding:
                                    EdgeInsetsDirectional.fromSTEB(0, 0, 0, 0),
                                color: FlutterFlowTheme.of(context).home,
                                textStyle: FlutterFlowTheme.of(context)
                                    .titleSmall
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontStyle,
                                      ),
                                      color: Colors.white,
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontStyle,
                                    ),
                                elevation: 0,
                                borderRadius: BorderRadius.circular(8),
                              ),
                            ),
                            FFButtonWidget(
                              onPressed: () async {
                                await RidesRecord.collection
                                    .doc()
                                    .set(createRidesRecordData(
                                      pickup: _model.dropDownFromValue,
                                      dropoff: _model.dropDowntoValue,
                                      date: _model.calendarSelectedDay?.start
                                          ?.toString(),
                                      time: _model.dropDownHourValue,
                                      minute: _model.dropDownminValue,
                                      email: FFAppState().email,
                                      plan: 10,
                                    ));

                                safeSetState(() {});

                                context
                                    .pushNamed(PaymentMethodWidget.routeName);
                              },
                              text: FFLocalizations.of(context).getText(
                                'h2d22idk' /* 10 SAR/H */,
                              ),
                              options: FFButtonOptions(
                                width: MediaQuery.sizeOf(context).width * 0.3,
                                height: 40,
                                padding: EdgeInsetsDirectional.fromSTEB(
                                    16, 0, 16, 0),
                                iconPadding:
                                    EdgeInsetsDirectional.fromSTEB(0, 0, 0, 0),
                                color: FlutterFlowTheme.of(context).home,
                                textStyle: FlutterFlowTheme.of(context)
                                    .titleSmall
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontStyle,
                                      ),
                                      color: Colors.white,
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontStyle,
                                    ),
                                elevation: 0,
                                borderRadius: BorderRadius.circular(8),
                              ),
                            ),
                            FFButtonWidget(
                              onPressed: () async {
                                await RidesRecord.collection
                                    .doc()
                                    .set(createRidesRecordData(
                                      pickup: _model.dropDownFromValue,
                                      dropoff: _model.dropDowntoValue,
                                      date: _model.calendarSelectedDay?.start
                                          ?.toString(),
                                      time: _model.dropDownHourValue,
                                      minute: _model.dropDownminValue,
                                      email: FFAppState().email,
                                      plan: 15,
                                    ));

                                context
                                    .pushNamed(PaymentMethodWidget.routeName);
                              },
                              text: FFLocalizations.of(context).getText(
                                'hde9oeid' /* 15 SAR/H */,
                              ),
                              options: FFButtonOptions(
                                width: MediaQuery.sizeOf(context).width * 0.3,
                                height: 40,
                                padding: EdgeInsetsDirectional.fromSTEB(
                                    16, 0, 16, 0),
                                iconPadding:
                                    EdgeInsetsDirectional.fromSTEB(0, 0, 0, 0),
                                color: FlutterFlowTheme.of(context).home,
                                textStyle: FlutterFlowTheme.of(context)
                                    .titleSmall
                                    .override(
                                      font: GoogleFonts.inter(
                                        fontWeight: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontWeight,
                                        fontStyle: FlutterFlowTheme.of(context)
                                            .titleSmall
                                            .fontStyle,
                                      ),
                                      color: Colors.white,
                                      letterSpacing: 0.0,
                                      fontWeight: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontWeight,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .titleSmall
                                          .fontStyle,
                                    ),
                                elevation: 0,
                                borderRadius: BorderRadius.circular(8),
                              ),
                            ),
                          ],
                        ),
                        Row(
                          mainAxisSize: MainAxisSize.max,
                          mainAxisAlignment: MainAxisAlignment.spaceAround,
                          children: [
                            ClipRRect(
                              borderRadius: BorderRadius.circular(8),
                              child: Image.asset(
                                'assets/images/sar5.webp',
                                width: 90,
                                height: 60,
                                fit: BoxFit.cover,
                              ),
                            ),
                            ClipRRect(
                              borderRadius: BorderRadius.circular(8),
                              child: Image.asset(
                                'assets/images/images.jpg',
                                width: 80,
                                height: 60,
                                fit: BoxFit.cover,
                              ),
                            ),
                            ClipRRect(
                              borderRadius: BorderRadius.circular(8),
                              child: Image.asset(
                                'assets/images/34076789.png',
                                width: 80,
                                height: 60,
                                fit: BoxFit.cover,
                              ),
                            ),
                          ],
                        ),
                        Row(
                          mainAxisSize: MainAxisSize.max,
                          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                          children: <Widget>[].divide(SizedBox(width: 37)),
                        ),
                        Row(
                          mainAxisSize: MainAxisSize.max,
                          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                          children: [
                            Text(
                              FFLocalizations.of(context).getText(
                                'd8yuuwku' /* Pick Your Ride */,
                              ),
                              style: FlutterFlowTheme.of(context)
                                  .bodyMedium
                                  .override(
                                    font: GoogleFonts.inter(
                                      fontWeight: FontWeight.w600,
                                      fontStyle: FlutterFlowTheme.of(context)
                                          .bodyMedium
                                          .fontStyle,
                                    ),
                                    color: FlutterFlowTheme.of(context).home,
                                    fontSize: 25,
                                    letterSpacing: 0.0,
                                    fontWeight: FontWeight.w600,
                                    fontStyle: FlutterFlowTheme.of(context)
                                        .bodyMedium
                                        .fontStyle,
                                  ),
                            ),
                          ],
                        ),
                      ].divide(SizedBox(height: 7)),
                    ),
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
