<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>مغامرة الطفو - Archimedes Quest</title>
<style>
  body { font-family: Arial, sans-serif; text-align: center; background: #e0f7fa; }
  h1 { color: #006064; }
  button { margin: 10px; padding: 10px 20px; font-size: 16px; }
  #result { font-size: 20px; margin-top: 20px; }
  #game-container { margin-top: 30px; display:none; }
  #welcome { margin-top: 50px; }
</style>
</head>
<body>

<div id="welcome">
  <h1>مغامرة الطفو 🌊</h1>
  <p>إعداد الطالبات: لين فهد - ليان سعود - بشاير عبدالله - الجوهره محمد</p>
  <p>معلمة المادة: حنان الجعيد</p>
  <button id="startBtn">ابدأ اللعبة</button>
</div>

<div id="game-container">
  <p>اختر جسم وسائل لتعرف إذا سيطفو أو يغرق!</p>
  <label>اختر الجسم:</label>
  <select id="object-select">
    <option value="خشب">خشب (الكتلة: 2, الحجم: 5)</option>
    <option value="حجر">حجر (الكتلة: 10, الحجم: 2)</option>
    <option value="بلاستيك">بلاستيك (الكتلة: 1, الحجم: 3)</option>
    <option value="حديد">حديد (الكتلة: 15, الحجم: 2)</option>
  </select>
  <br><br>
  <label>اختر السائل:</label>
  <select id="liquid-select">
    <option value="ماء">ماء (الكثافة: 1)</option>
    <option value="ماء مالح">ماء مالح (الكثافة: 1.2)</option>
    <option value="زيت">زيت (الكثافة: 0.9)</option>
  </select>
  <br><br>
  <button onclick="checkBuoyancy()">اختبر الطفو</button>
  <div id="result"></div>
</div>

<script>
document.getElementById("startBtn").onclick = function() {
  document.getElementById("welcome").style.display = "none";
  document.getElementById("game-container").style.display = "block";
};

function checkBuoyancy() {
  const obj = document.getElementById("object-select").value;
  const liquid = document.getElementById("liquid-select").value;

  let mass, volume, liquidDensity;

  // خصائص الأجسام
  if (obj === "خشب") { mass = 2; volume = 5; }
  else if (obj === "حجر") { mass = 10; volume = 2; }
  else if (obj === "بلاستيك") { mass = 1; volume = 3; }
  else if (obj === "حديد") { mass = 15; volume = 2; }

  // كثافة السوائل
  if (liquid === "ماء") { liquidDensity = 1; }
  else if (liquid === "ماء مالح") { liquidDensity = 1.2; }
  else if (liquid === "زيت") { liquidDensity = 0.9; }

  const g = 9.8; // عجلة الجاذبية
  const buoyantForce = liquidDensity * g * volume;
  const weight = mass * g;

  const resultDiv = document.getElementById("result");
  if (buoyantForce >= weight) {
    resultDiv.innerHTML = `🎉 الجسم يطفو! قوة الطفو = ${buoyantForce.toFixed(2)} > الوزن = ${weight.toFixed(2)}`;
  } else {
    resultDiv.innerHTML = `💧 الجسم يغرق! قوة الطفو = ${buoyantForce.toFixed(2)} < الوزن = ${weight.toFixed(2)}`;
  }
}
</script>
</body>
</html>
