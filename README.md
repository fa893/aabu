<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>حساب زاوية ميل اللوح الشمسي</title>
  <style>
    body { font-family: Arial; direction: rtl; margin: 30px; background: #f7f7f7; }
    .container { background: white; padding: 20px; border-radius: 10px; max-width: 400px; margin: auto; box-shadow: 0 0 10px rgba(0,0,0,0.1);}
    label, select, input, button { display: block; width: 100%; margin-bottom: 15px; font-size: 16px; }
    button { background-color: #4CAF50; color: white; border: none; padding: 10px; cursor: pointer; }
    #result { font-weight: bold; color: #1a237e; margin-top: 20px; text-align: center; }
  </style>
</head>
<body>
  <div class="container">
    <h2>حساب زاوية ميل اللوح الشمسي</h2>
    <label for="latitude">خط العرض (°):</label>
    <input type="number" id="latitude" step="0.01" placeholder="مثال: 32.0 للأردن">

    <label for="season">اختر الفصل:</label>
    <select id="season">
      <option value="winter">الشتاء</option>
      <option value="summer">الصيف</option>
      <option value="spring_fall">الربيع / الخريف</option>
    </select>

    <button onclick="calculateTilt()">احسب الزاوية</button>
    <div id="result"></div>
  </div>

  <script>
    function calculateTilt() {
      const lat = parseFloat(document.getElementById("latitude").value);
      const season = document.getElementById("season").value;
      let tilt;

      if (isNaN(lat)) {
        document.getElementById("result").innerText = "يرجى إدخال خط عرض صالح.";
        return;
      }

      // طريقة تقريبية مشهورة
      if (season === "winter") {
        tilt = lat + 15;
      } else if (season === "summer") {
        tilt = lat - 15;
      } else {
        tilt = lat;
      }

      document.getElementById("result").innerText = `الزاوية الموصى بها للميل هي: ${tilt.toFixed(2)}°`;
    }
  </script>
</body>
</html>
