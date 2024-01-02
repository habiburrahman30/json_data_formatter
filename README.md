
## Description

This document is Flutter List to Map and Map to List 🥰.

## Convert json to list

```bash
final data = res.data['data']
            .map((json) => Post.fromJson(json as Map<String, dynamic>))
            .toList()
            .cast<Post>() as List<Post>;
```
## Convert json to map
```bash
final data = Post.fromJson(res.data['data']);
```
## Convert list to map
```bash
final data = services.map((e) => e.toJson()).toList();
```

## List<Uint8List> and DateTime Json Serializable
```
import 'dart:typed_data';

import 'package:hive/hive.dart';
import 'package:json_annotation/json_annotation.dart';

part 'offline_shout.g.dart';

@JsonSerializable()
@HiveType(typeId: 30)
class OfflineShoutModel {
  @HiveField(0)
  @JsonKey(fromJson: dateTimeFromJson, toJson: dateTimeToJson)
  DateTime? reportedAt;
  @HiveField(1)
  @JsonKey(fromJson: convertJsonToUint8ListList, toJson: convertUint8ListListToJson)
  List<Uint8List>? files;

  OfflineShoutModel({
    this.files,
    this.reportedAt,

  });

  factory OfflineShoutModel.fromJson(Map<String, dynamic> json) => _$OfflineShoutModelFromJson(json);
  Map<String, dynamic> toJson() => _$OfflineShoutModelToJson(this);
}

List<List<int>>? convertUint8ListListToJson(List<Uint8List>? list) {
  return list?.map((Uint8List item) => item.toList()).toList();
}

List<Uint8List>? convertJsonToUint8ListList(List<dynamic>? jsonList) {
  return jsonList?.map((list) => Uint8List.fromList(List<int>.from(list))).toList();
}

String? dateTimeToJson(DateTime? dateTime) => dateTime?.toIso8601String(); // Convert DateTime to String

DateTime? dateTimeFromJson(String? json) => json != null ? DateTime.tryParse(json) : null; // Convert String to DateTime

// class Uint8ListConverter implements JsonConverter<List<int>, Uint8List> {
//   const Uint8ListConverter();

//   @override
//   ;

//   @override
//   List<int> toJson(Uint8List object) => object.toList();
// }
```
