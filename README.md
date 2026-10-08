# Dự đoán giá đóng cửa cổ phiếu bằng RNN, LSTM và GRU

Notebook Chương 4 môn Phát triển hệ thống thông minh. Bài toán dự đoán giá `close` của phiên kế tiếp từ 60 phiên giao dịch trước đó, dùng dữ liệu OHLCV của một mã cổ phiếu.

## Nội dung

- [`chapter4_stock_price_prediction.ipynb`](chapter4_stock_price_prediction.ipynb): EDA, chia train/validation/test theo thời gian, chuẩn hóa trên train, huấn luyện và so sánh SimpleRNN/LSTM/GRU bằng PyTorch.
- [`data/all_stocks_5yr.csv`](data/all_stocks_5yr.csv): dữ liệu [S&P 500 Stock Data trên Kaggle](https://www.kaggle.com/datasets/camnugent/sandp500), được tải và lưu kèm để notebook chạy ngay.
- [`requirements_stock.txt`](requirements_stock.txt): các thư viện cần cài.
- `artifacts/`: trọng số GRU và hai scaler tạo bởi lần chạy mẫu với `AAPL`.

## Chạy notebook

```powershell
python -m pip install -r requirements_stock.txt
jupyter notebook chapter4_stock_price_prediction.ipynb
```

Chạy các ô từ trên xuống dưới. Đổi `STOCK_SYMBOL = "AAPL"` ở ô cấu hình sang `MSFT`, `GOOGL` hoặc `AMZN`, rồi chọn **Restart & Run All** để huấn luyện lại cho mã khác. Mô hình và scaler trong `artifacts/` thuộc lần chạy `AAPL`; lần chạy mã khác sẽ ghi đè chúng.

## Kết quả mẫu

Với `AAPL`, tập dữ liệu có 1.259 phiên từ 08/02/2013 đến 07/02/2018. Lần chạy mẫu trên CPU cho RMSE test: SimpleRNN 8,581 USD, LSTM 6,676 USD, GRU 6,172 USD. Kết quả có thể thay đổi theo môi trường và phiên bản thư viện.

Dataset kết thúc năm 2018. Dự đoán phiên tiếp theo trong notebook là minh họa trên dữ liệu lịch sử, không phải giá hiện tại hay khuyến nghị đầu tư.
