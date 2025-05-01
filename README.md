# cloud_native_hw4
此專案為一個前後端分離的應用系統，包含：

- **Backend**：Python Flask API，位於 `backend/` 資料夾。
- **Frontend**：基於 Vite + React + Tailwind 的網頁介面，位於 `frontend/` 資料夾。

## Docker Build 打包應用程式
進入根目錄，執行：
```
docker build -t peixuan911/2025cloud:backend ./backend
docker build -t peixuan911/2025cloud:frontend ./frontend
```
## 執行容器（Docker Run）
Backend：
```
docker run -d -p 8000:8000 peixuan911/2025cloud:backend
```
Frontend:
```
docker run -d -p 5173:5173 peixuan911/2025cloud:frontend
```

## 測試
進入：http://localhost:8000
進入：http://localhost:5173
即可看到 Hello 等字