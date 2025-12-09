# MACHINE_LEARNING
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Regression & KNN — README</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--muted:#94a3b8;--accent:#60a5fa;--glass:rgba(255,255,255,0.03)}
    body{font-family:Inter,system-ui,Segoe UI,Roboto,Helvetica,Arial,sans-serif;background:linear-gradient(180deg,#071129 0%, #071726 100%);color:#e6eef8;margin:0;padding:36px}
    .container{max-width:900px;margin:0 auto}
    header{display:flex;align-items:center;gap:16px;margin-bottom:20px}
    h1{font-size:28px;margin:0}
    p.lead{color:var(--muted);margin:6px 0 18px}
    .card{background:var(--card);padding:20px;border-radius:12px;box-shadow:0 6px 18px rgba(2,6,23,.6);margin-bottom:18px}
    h2{margin-top:0}
    pre{background:var(--glass);padding:12px;border-radius:8px;overflow:auto;color:#cfe9ff}
    code{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,"Liberation Mono","Courier New",monospace}
    ul{color:var(--muted)}
    .grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    footer{color:var(--muted);font-size:13px;margin-top:10px}
    @media(max-width:700px){.grid{grid-template-columns:1fr}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div>
        <h1>Regression & KNN — Quick README</h1>
        <p class="lead">Simple reference: Simple Linear, Multiple Linear, Polynomial Regression, and KNN Classification (with examples).</p>
      </div>
    </header>

    <section class="card">
      <h2>1. Simple Linear Regression</h2>
      <p>Predict a continuous target <code>y</code> from one feature <code>x</code> using a line: <code>y = b0 + b1 * x</code>.</p>
      <ul>
        <li>Assumes linear relationship between <code>x</code> and <code>y</code>.</li>
        <li>Common metrics: <code>MSE</code>, <code>RMSE</code>, <code>R²</code>.</li>
      </ul>
      <h3>Example (scikit-learn)</h3>
      <pre><code>from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train.reshape(-1,1), y_train)
pred = model.predict(X_test.reshape(-1,1))</code></pre>
    </section>

    <section class="card">
      <h2>2. Multiple Linear Regression</h2>
      <p>Predict <code>y</code> from multiple features: <code>y = b0 + b1*x1 + b2*x2 + ... + bn*xn</code>.</p>
      <ul>
        <li>Works with many features; check multicollinearity (<code>VIF</code>).</li>
        <li>Use regularization (Ridge, Lasso) to avoid overfitting.</li>
      </ul>
      <h3>Example (scikit-learn)</h3>
      <pre><code>from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
pred = model.predict(X_test)</code></pre>
    </section>

    <section class="card">
      <h2>3. Polynomial Regression</h2>
      <p>Extend linear models to capture non-linear relationships by generating polynomial features.</p>
      <h3>How it works</h3>
      <ul>
        <li>Transform input with polynomial terms (x, x², x³...).</li>
        <li>Fit a linear model on transformed features.</li>
      </ul>
      <h3>Example (scikit-learn)</h3>
      <pre><code>from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression

poly = PolynomialFeatures(degree=2, include_bias=False)
X_poly = poly.fit_transform(X.reshape(-1,1))
model = LinearRegression()
model.fit(X_poly, y)
# To predict: transform new X the same way
</code></pre>
    </section>

    <section class="card">
      <h2>
