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

## 說明：自動化產生 Container Image 的邏輯
專案的 Docker 映像檔建構與推送是透過 GitHub Actions 自動完成的。以下是整體邏輯流程圖：

自動化建構流程：
1. Git Push to Main：當開發人員將代碼推送到 main 分支時，會觸發 GitHub Actions 工作流。
2. GitHub Actions Workflow Run：這會觸發工作流，並且根據 Dockerfile 分別為 frontend 和 backend 構建容器映像檔。
3. Build Docker Image：在 backend 和 frontend 目錄下，GitHub Actions 使用對應的 Dockerfile 來Build Docker image。每個 image 會分別標註為：
    - peixuan911/2025cloud:backend（後端）
    - peixuan911/2025cloud:frontend（前端）

4. Push Images to Docker Hub：成功建構後，將 Docker 映像檔推送至 Docker Hub，使其可以隨時從 Docker Hub 拉取並運行。

## Docker Tag 選擇邏輯
在專案中，我們將 Docker 映像檔 Tag 分為兩類：前端（frontend） 和 後端（backend）。
讓專案中的不同部分使用不同 Tag 管理。
