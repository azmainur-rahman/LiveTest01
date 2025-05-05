import 'dart:convert';
void main()
{
  List students = [
    {"name": "Alice", "scores": [85, 90, 78]},
    {"name": "Bob", "scores": [88, 76, 95]},
    {"name": "Charlie", "scores": [90, 92, 85]}
  ];
    Map<String, double> averageScores = {};
    for (var student in students)
    {
    String name = student['name'];
    List<int> scores = student['scores'];
    int sum = scores.reduce((a, b) => a + b);
    double average = sum / scores.length;
    double roundedAverage = double.parse(average.toStringAsFixed(2));
    averageScores[name] = roundedAverage;
   }
  var sortedEntries = averageScores.entries.toList()
    ..sort((a, b) => b.value.compareTo(a.value));
  Map<String, double> sortedScores = Map.fromEntries(sortedEntries);
  JsonEncoder encoder = JsonEncoder.withIndent('  ');
  print(encoder.convert(sortedScores));
}
