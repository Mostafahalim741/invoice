<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>فاتورة إلكترونية</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <style>
    body {
      font-family: 'Tahoma', sans-serif;
      margin: 40px;
      background: #f9f9f9;
    }
    .container {
      background: #fff;
      padding: 30px;
      border: 1px solid #ccc;
      max-width: 800px;
      margin: auto;
    }
    input, button {
      font-size: 1rem;
      margin: 5px 0;
      padding: 5px;
      width: 100%;
    }
    label {
      font-weight: bold;
    }
    .row {
      display: flex;
      gap: 20px;
    }
    .row > div {
      flex: 1;
    }
    hr {
      margin: 20px 0;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>مؤسسة الخليج الذهبي</h2>
    <h3>فاتورة نقدية</h3>
    <div class="row">
      <div>
        <label>رقم الفاتورة:</label>
        <input type="text" id="invoiceNumber" value="1001" />
      </div>
      <div>
        <label>التاريخ:</label>
        <input type="date" id="invoiceDate" />
      </div>
    </div>
    <label>اسم العميل:</label>
    <input type="text" id="customerName" />
    <hr />
    <label>الخدمة:</label>
    <input type="text" id="service" value="فك مكيفات" />
    <div class="row">
      <div>
        <label>الكمية:</label>
        <input type="number" id="quantity" value="1" />
      </div>
      <div>
        <label>سعر الوحدة (ر.س):</label>
        <input type="number" id="unitPrice" value="300" />
      </div>
    </div>
    <label>نسبة الضريبة %:</label>
    <input type="number" id="vat" value="5" />
    <button id="generateBtn">إنشاء الفاتورة PDF</button>
  </div>

  <script>
    window.addEventListener('load', async () => {
      const { jsPDF } = window.jspdf;

      document.getElementById('generateBtn').addEventListener('click', () => {
        const doc = new jsPDF();

        const invoiceNumber = document.getElementById('invoiceNumber').value;
        const invoiceDate = document.getElementById('invoiceDate').value;
        const customerName = document.getElementById('customerName').value;
        const service = document.getElementById('service').value;
        const quantity = parseFloat(document.getElementById('quantity').value);
        const unitPrice = parseFloat(document.getElementById('unitPrice').value);
        const vatPercent = parseFloat(document.getElementById('vat').value);

        const subtotal = quantity * unitPrice;
        const vatAmount = subtotal * vatPercent / 100;
        const total = subtotal + vatAmount;

        doc.setFont('Helvetica');
        doc.setFontSize(16);
        doc.text(\"مؤسسة الخليج الذهبي\", 105, 20, { align: \"center\" });
        doc.setFontSize(12);
        doc.text(`فاتورة رقم: ${invoiceNumber}`, 20, 40);
        doc.text(`التاريخ: ${invoiceDate}`, 20, 48);
        doc.text(`اسم العميل: ${customerName}`, 20, 56);

        doc.text(\"الخدمة: \" + service, 20, 70);
        doc.text(`الكمية: ${quantity}`, 20, 78);
        doc.text(`سعر الوحدة: ${unitPrice.toFixed(2)} ر.س`, 20, 86);
        doc.text(`الإجمالي بدون الضريبة: ${subtotal.toFixed(2)} ر.س`, 20, 94);
        doc.text(`ضريبة (${vatPercent}%): ${vatAmount.toFixed(2)} ر.س`, 20, 102);
        doc.text(`الإجمالي شامل الضريبة: ${total.toFixed(2)} ر.س`, 20, 110);

        doc.text(\"شكراً لتعاملك معنا. نتطلع لخدمتك مرة أخرى!\", 105, 140, { align: \"center\" });

        doc.save(`فاتورة-${invoiceNumber}.pdf`);
      });
    });
  </script>
</body>
</html>
