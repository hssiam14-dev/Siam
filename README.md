# BD Loan Hub 
Instant loan in 5 munite 
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Loan Real — A REAL LOAN</title>
  <style>
    body{font-family:system-ui,Segoe UI,Arial;max-width:900px;margin:30px auto;padding:20px}
    .real-banner{background:#ffecec;color:#900;padding:10px;border-radius:6px;margin-bottom:20px;font-weight:700}
    .card{border:1px solid #eee;padding:18px;border-radius:8px;box-shadow:0 6px 18px rgba(0,0,0,0.03)}
    label{display:block;margin-top:10px}
    input[type="number"]{width:160px;padding:8px;margin-top:6px}
    button{margin-top:12px;padding:10px 14px;border-radius:6px;border:0;cursor:pointer}
    .result{margin-top:12px;font-weight:700}
    small{color:#666}
  </style>
</head>
<body>
  <div class="Real-banner">REAL — A REAL LOAN SERVICE. This page is for learning/portfolio only.  enter real personal or financial details.</div>

  <h1>Loan Calculator — Real (BDT)</h1>
  <div class="card">
    <p><small>Enter loan amount and term to see estimated monthly payment. This is a simple illustrative calculator — not an offer.</small></p>

    <label>Loan amount (BDT)
      <input id="amount" type="number" min="1000" step="1000" value="10000">
    </label>

    <label>Term (months)
      <input id="months" type="number" min="1" max="60" value="12">
    </label>

    <label>Annual interest rate (%) (example)
      <input id="rate" type="number" step="0.1" value="18">
    </label>

    <button id="calc">Calculate Payment</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calcPayment(P, annualRate, nMonths){
      if(annualRate <= 0) return (P / nMonths);
      let r = annualRate / 100 / 12;
      let payment = (P * r) / (1 - Math.pow(1 + r, -nMonths));
      return payment;
    }

    document.getElementById('calc').addEventListener('click', ()=> {
      let P = parseFloat(document.getElementById('amount').value) || 0;
      let n = parseInt(document.getElementById('months').value) || 1;
      let rate = parseFloat(document.getElementById('rate').value) || 0;
      if(P <= 0 || n <= 0){ document.getElementById('result').textContent = 'Enter valid values.'; return; }
      let pay = calcPayment(P, rate, n);
      document.getElementById('result').innerHTML = 
        'Estimated monthly payment: <strong>' + pay.toFixed(2) + ' BDT</strong><br>' +
        '<small>This is a demonstration only — not a loan approval or offer.</small>';
    });
  </script>
</body>
</html>
