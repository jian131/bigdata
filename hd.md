# HƯỚNG DẪN CHẠY DỰ ÁN MULTIMODAL SEARCH

## ỨNG DỤNG ELASTICSEARCH XÂY DỰNG HỆ THỐNG TÌM KIẾM ĐA PHƯƠNG TIỆN

---

## 📋 MỤC LỤC

1. [Yêu cầu hệ thống](#1-yêu-cầu-hệ-thống)
2. [Cài đặt môi trường](#2-cài-đặt-môi-trường)
3. [Download dataset & source code](#3-download-dataset--source-code)
4. [Cấu trúc thư mục](#4-cấu-trúc-thư-mục)
5. [Khởi động Elasticsearch Cluster](#5-khởi-động-elasticsearch-cluster)
6. [Tạo embeddings](#6-tạo-embeddings)
7. [Index dữ liệu vào Elasticsearch](#7-index-dữ-liệu-vào-elasticsearch)
8. [Chạy demo tìm kiếm](#8-chạy-demo-tìm-kiếm)
9. [Benchmark & đánh giá](#9-benchmark--đánh-giá)
10. [Troubleshooting](#10-troubleshooting)

---

## 1. YÊU CẦU HỆ THỐNG

### 💻 Hardware tối thiểu:

- **CPU:** 4 cores (Intel i5/AMD Ryzen 5 trở lên)
- **RAM:** 8GB (khuyến nghị 16GB)
- **Disk:** 5GB trống (dataset 900MB + Docker images ~2GB)
- **Network:** Kết nối internet (để download models & dependencies)

### 🖥️ Software:

- **OS:** Windows 10/11, macOS, Linux
- **Docker:** Version 20.10+
- **Docker Compose:** Version 2.0+
- **Python:** 3.10, 3.11, hoặc 3.12
- **Git:** (optional - để clone repo)

### ✅ Kiểm tra trước khi bắt đầu:

**Windows PowerShell:**

```powershell
# Kiểm tra Docker
docker --version
docker-compose --version

# Kiểm tra Python
python --version

# Kiểm tra RAM & CPU
systeminfo | findstr /C:"Total Physical Memory" /C:"Processor"
```

**Linux/macOS:**

```bash
# Kiểm tra Docker
docker --version
docker-compose --version

# Kiểm tra Python
python3 --version

# Kiểm tra RAM & CPU
free -h
lscpu | grep "CPU(s)"
```

---

## 2. CÀI ĐẶT MÔI TRƯỜNG

### Bước 1: Cài Docker Desktop

**Windows/macOS:**

1. Download từ: https://www.docker.com/products/docker-desktop
2. Cài đặt và khởi động Docker Desktop
3. Verify: `docker run hello-world`

**Linux (Ubuntu/Debian):**

```bash
# Cài Docker Engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker

# Verify
docker run hello-world
```

### Bước 2: Cài Python

**Windows:**

1. Download Python 3.11 từ: https://www.python.org/downloads/
2. Chọn "Add Python to PATH" khi cài đặt
3. Verify: `python --version`

**Linux:**

```bash
sudo apt-get update
sudo apt-get install python3.11 python3.11-venv python3-pip
```

**macOS:**

```bash
brew install python@3.11
```

---

## 3. DOWNLOAD DATASET & SOURCE CODE

### Option 1: Từ Google Drive (Khuyến nghị)

```powershell
# Tạo thư mục dự án
mkdir BigData
cd BigData

# Download 2 file ZIP từ Google Drive:
# 1. BigData_Dataset.zip (899 MB) - chứa 1,010 files multimedia
# 2. BigData_SourceCode.zip (49 KB) - chứa source code

# Link Google Drive:
# [THAY BẰNG LINK THỰC TẾ CỦA BẠN]
```

**Giải nén:**

```powershell
# Windows
Expand-Archive -Path BigData_Dataset.zip -DestinationPath .
Expand-Archive -Path BigData_SourceCode.zip -DestinationPath .

# Linux/macOS
unzip BigData_Dataset.zip
unzip BigData_SourceCode.zip
```

### Option 2: Clone từ GitHub (nếu có)

```bash
git clone https://github.com/[username]/BigData-Multimodal-Search.git
cd BigData-Multimodal-Search

# Download dataset riêng (vì quá lớn, không push lên Git)
# Sử dụng Google Drive link
```

---

## 4. CẤU TRÚC THỦ MỤC

Sau khi download & giải nén, cấu trúc như sau:

```
BigData/
│
├── data/
│   ├── raw/                          # 911 MB multimedia files
│   │   ├── images/                   # 800 JPEG files (55 MB)
│   │   ├── pexels_videos/            # 10 MP4 HD videos (738 MB)
│   │   └── audios/                   # 200 WAV files (118 MB)
│   │
│   └── embeddings/                   # Sẽ được tạo ở bước 6
│       ├── images_embeddings.npy
│       ├── videos_embeddings.npy
│       └── audios_embeddings.npy
│
├── scripts/
│   ├── setup/
│   │   ├── 1_download_pexels_videos.py
│   │   ├── 2a_generate_images.py
│   │   └── 2b_generate_audios.py
│   │
│   ├── main/
│   │   ├── 3_create_embeddings.py    # ⭐ QUAN TRỌNG
│   │   ├── 4_index_to_elasticsearch.py # ⭐ QUAN TRỌNG
│   │   └── 5_elasticsearch_search.py
│   │
│   └── benchmarks/
│       ├── benchmark_cluster.py
│       └── compare_es_solr.py
│
├── docker-compose-cluster.yml        # ⭐ QUAN TRỌNG
├── demo_multimodal_search.py         # ⭐ DEMO CHÍNH
├── requirements.txt                  # Python dependencies
├── .env.example                      # Environment variables template
│
├── BAO_CAO.txt                       # Báo cáo chi tiết
├── SLIDE_BAO_CAO.md                  # Slide thuyết trình
└── README.md                         # Hướng dẫn ngắn gọn
```

---

## 5. KHỞI ĐỘNG ELASTICSEARCH CLUSTER

### Bước 1: Tạo Python Virtual Environment

**Windows PowerShell:**

```powershell
# Tạo virtual environment
python -m venv venv

# Activate
.\venv\Scripts\Activate.ps1

# Nếu lỗi ExecutionPolicy:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Linux/macOS:**

```bash
# Tạo virtual environment
python3 -m venv venv

# Activate
source venv/bin/activate
```

### Bước 2: Cài đặt Python dependencies

```powershell
# Upgrade pip
pip install --upgrade pip

# Cài packages
pip install -r requirements.txt

# Danh sách packages chính:
# - elasticsearch==8.11.1
# - torch==2.1.0
# - transformers==4.35.0
# - pillow==10.1.0
# - opencv-python==4.8.1.78
# - numpy==1.26.2
# - scipy==1.11.4
# - requests==2.31.0
```

**⏱️ Thời gian:** ~5-10 phút (tùy tốc độ mạng)

### Bước 3: Cấu hình Docker memory

**Docker Desktop → Settings → Resources:**

- Memory: Tối thiểu 4GB (khuyến nghị 6GB)
- CPUs: Tối thiểu 2 cores (khuyến nghị 4 cores)
- Swap: 1GB
- Disk: 20GB

**Apply & Restart Docker Desktop**

### Bước 4: Khởi động Elasticsearch 3-node cluster

```powershell
# Kiểm tra docker-compose file
cat docker-compose-cluster.yml

# Khởi động cluster (3 nodes + Kibana)
docker-compose -f docker-compose-cluster.yml up -d

# Xem logs
docker-compose -f docker-compose-cluster.yml logs -f

# Chờ ~30-60 giây cho cluster khởi động
```

### Bước 5: Verify cluster status

```powershell
# Kiểm tra nodes
curl http://localhost:9200/_cat/nodes?v

# Output mong đợi:
# ip         heap.percent ram.percent cpu load_1m node.role master name
# 172.18.0.2           45          80   8    0.50 cdfhilmrstw *      es01
# 172.18.0.3           42          80   7    0.50 cdfhilmrstw -      es02
# 172.18.0.4           40          80   6    0.50 cdfhilmrstw -      es03

# Kiểm tra cluster health
curl http://localhost:9200/_cluster/health?pretty

# Output mong đợi:
# {
#   "cluster_name" : "bigdata-cluster",
#   "status" : "green",        ← PHẢI LÀ GREEN
#   "number_of_nodes" : 3,
#   "active_shards" : 6
# }
```

### Bước 6: Truy cập Kibana (optional)

Mở browser: http://localhost:5601

- Username: `elastic`
- Password: `changeme`

**Kibana Menu → Dev Tools** để test queries

---

## 6. TẠO EMBEDDINGS

### Bước 1: Download CLIP model (lần đầu tiên)

```powershell
# Model sẽ tự động download khi chạy lần đầu
# Size: ~350MB
# Location: ~/.cache/huggingface/ (Linux/Mac) hoặc C:\Users\<User>\.cache\huggingface\ (Windows)

# Test download model trước:
python -c "from transformers import CLIPModel, CLIPProcessor; model = CLIPModel.from_pretrained('openai/clip-vit-base-patch32'); print('Model downloaded!')"
```

**⏱️ Thời gian download:** ~3-5 phút (tùy tốc độ mạng)

### Bước 2: Tạo embeddings cho toàn bộ dataset

```powershell
# Chạy script tạo embeddings
python scripts/main/3_create_embeddings.py

# Process:
# [1/3] Processing images...    (800 files)   → images_embeddings.npy
# [2/3] Processing videos...    (10 files)    → videos_embeddings.npy
# [3/3] Processing audios...    (200 files)   → audios_embeddings.npy
```

**Output:**

```
Processing images: 100%|████████████████| 800/800 [02:15<00:00, 5.89it/s]
✓ Saved: data/embeddings/images_embeddings.npy (shape: 800, 512)

Processing videos: 100%|████████████████| 10/10 [01:20<00:00, 8.0s/it]
✓ Saved: data/embeddings/videos_embeddings.npy (shape: 10, 512)

Processing audios: 100%|████████████████| 200/200 [00:45<00:00, 4.44it/s]
✓ Saved: data/embeddings/audios_embeddings.npy (shape: 200, 512)

Total embeddings: 1,010 vectors (512-d)
Total size: ~2.1 MB
```

**⏱️ Thời gian:**

- CPU only: ~8-12 phút
- GPU (nếu có): ~2-3 phút

### Bước 3: Verify embeddings

```powershell
# Kiểm tra files đã tạo
ls data/embeddings/

# Output:
# images_embeddings.npy    (~1.6 MB)
# videos_embeddings.npy    (~20 KB)
# audios_embeddings.npy    (~410 KB)

# Test load embeddings
python -c "import numpy as np; emb = np.load('data/embeddings/images_embeddings.npy'); print(f'Shape: {emb.shape}, Type: {emb.dtype}')"
# Output: Shape: (800, 512), Type: float32
```

---

## 7. INDEX DỮ LIỆU VÀO ELASTICSEARCH

### Bước 1: Tạo index với mapping

```powershell
python scripts/main/4_index_to_elasticsearch.py
```

**Process:**

```
Step 1: Creating index 'multimedia'...
  ✓ Index created with dense_vector mapping (512 dimensions)

Step 2: Indexing data...
  [1/3] Indexing images...   100%|████████| 800/800 [00:12<00:00]
  [2/3] Indexing videos...   100%|██████████| 10/10 [00:01<00:00]
  [3/3] Indexing audios...   100%|████████| 200/200 [00:03<00:00]

Step 3: Refreshing index...
  ✓ Index refreshed

Step 4: Verifying...
  ✓ Total documents indexed: 1,010
  ✓ Index size: 2.4 MB
  ✓ Shards: 3 primary + 3 replica = 6 total (100% active)

✅ INDEXING COMPLETED!
```

**⏱️ Thời gian:** ~20-30 giây

### Bước 2: Verify index

```powershell
# Kiểm tra index stats
curl http://localhost:9200/multimedia/_stats?pretty

# Kiểm tra số documents
curl http://localhost:9200/multimedia/_count?pretty
# Output: { "count": 1010 }

# Kiểm tra sample document
curl http://localhost:9200/multimedia/_search?size=1&pretty
```

### Bước 3: Kiểm tra shard distribution

```powershell
curl http://localhost:9200/_cat/shards/multimedia?v

# Output:
# index       shard prirep state   docs  size node
# multimedia  0     p      STARTED  337  800kb es01
# multimedia  0     r      STARTED  337  800kb es02
# multimedia  1     p      STARTED  336  798kb es02
# multimedia  1     r      STARTED  336  798kb es03
# multimedia  2     p      STARTED  337  802kb es03
# multimedia  2     r      STARTED  337  802kb es01
```

**✅ Kiểm tra:** 6 shards (3 primary + 3 replica), tất cả STARTED

---

## 8. CHẠY DEMO TÌM KIẾM

### Bước 1: Chạy interactive demo

```powershell
python demo_multimodal_search.py
```

**Menu chính:**

```
╔══════════════════════════════════════════════════════════╗
║   MULTIMODAL SEARCH DEMO - ELASTICSEARCH CLUSTER         ║
╚══════════════════════════════════════════════════════════╝

[1] 🔍 Text-to-Media Search
[2] 🖼️  Image-to-Media Search
[3] 🔄 Cross-Modal Search
[4] ⚡ Performance Test
[5] 💚 Health Check
[0] ❌ Exit

Enter your choice:
```

### Bước 2: Thử các tính năng

**[1] Text-to-Media Search:**

```
Enter search query: a person playing guitar

🔍 Searching for: "a person playing guitar"
⏱️  Search time: 68 ms

Results (Top 5):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. pexels_1192116.mp4 (video)
   Score: 0.824 ⭐⭐⭐⭐
   Path: data/raw/pexels_videos/pexels_1192116.mp4

2. image_0432.jpg (image)
   Score: 0.791 ⭐⭐⭐⭐
   Path: data/raw/images/image_0432.jpg

3. audio_142.wav (audio)
   Score: 0.768 ⭐⭐⭐⭐
   Path: data/raw/audios/audio_142.wav
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**[2] Image-to-Media Search:**

```
Enter image path: data/raw/images/image_0001.jpg

🖼️  Loading image...
⏱️  Search time: 72 ms

Results (Top 5):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. image_0001.jpg (image) - SELF
   Score: 1.000 ⭐⭐⭐⭐⭐

2. image_0234.jpg (image)
   Score: 0.912 ⭐⭐⭐⭐⭐

3. pexels_3571264.mp4 (video)
   Score: 0.887 ⭐⭐⭐⭐
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**[4] Performance Test:**

```
Running performance test...
Queries: 100
Threads: 5

Progress: 100%|████████████████████████| 100/100 [00:05<00:00]

📊 PERFORMANCE METRICS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Average Latency:  74.3 ms
P95 Latency:      102.1 ms
P99 Latency:      125.8 ms
QPS (sustained):  13.4 queries/sec
Peak QPS:         22.1 queries/sec
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**[5] Health Check:**

```
Checking Elasticsearch cluster...

✅ CLUSTER STATUS: GREEN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Cluster Name:     bigdata-cluster
Active Nodes:     3/3
Active Shards:    6/6 (100%)
Documents:        1,010
Index Size:       2.4 MB
Unassigned Shards: 0
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Nodes:
  es01 (172.18.0.2) - Master, Data - Heap: 45%
  es02 (172.18.0.3) - Data         - Heap: 42%
  es03 (172.18.0.4) - Data         - Heap: 40%
```

---

## 9. BENCHMARK & ĐÁNH GIÁ

### Option 1: Benchmark Elasticsearch Cluster

```powershell
python scripts/benchmarks/benchmark_cluster.py

# Output:
Running benchmark on 3-node Elasticsearch cluster...
Warmup: 20 queries... Done!
Testing: 1000 queries with 10 threads...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ELASTICSEARCH CLUSTER PERFORMANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Queries:     1,000
Duration:          74.4 seconds
Average Latency:   74.40 ms
Median Latency:    71.20 ms
P95 Latency:       102.10 ms
P99 Latency:       125.80 ms
Min Latency:       45.30 ms
Max Latency:       189.20 ms
QPS (sustained):   13.44 queries/sec
Peak QPS:          22.10 queries/sec
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Option 2: So sánh Elasticsearch vs Solr

**Khởi động Solr (optional):**

```powershell
# Uncomment Solr trong docker-compose-cluster.yml
docker-compose -f docker-compose-cluster.yml up -d solr

# Verify Solr
curl http://localhost:8983/solr/admin/info/system?wt=json
```

**Chạy comparison:**

```powershell
python scripts/benchmarks/compare_es_solr.py

# Output:
╔══════════════════════════════════════════════════════════╗
║        ELASTICSEARCH VS SOLR COMPARISON                  ║
╚══════════════════════════════════════════════════════════╝

Testing Elasticsearch... Done! (1000 queries)
Testing Solr...          Done! (1000 queries)

┌──────────────────┬──────────────┬─────────────┬──────────┐
│ Metric           │ Elasticsearch│ Solr        │ Winner   │
├──────────────────┼──────────────┼─────────────┼──────────┤
│ Avg Latency      │ 74.4 ms      │ 82.1 ms     │ ES ✓     │
│ P95 Latency      │ 102.1 ms     │ 115.3 ms    │ ES ✓     │
│ QPS              │ 13.44        │ 12.17       │ ES ✓     │
│ Configuration    │ JSON/API     │ XML files   │ ES ✓     │
│ Vector Search    │ Native       │ Plugin      │ ES ✓     │
│ Auto Sharding    │ Yes          │ Manual      │ ES ✓     │
└──────────────────┴──────────────┴─────────────┴──────────┘

🏆 Winner: Elasticsearch (6/6 metrics)
```

---

## 10. TROUBLESHOOTING

### ❌ Lỗi 1: Docker out of memory

**Hiện tượng:**

```
elasticsearch_es01 exited with code 137
```

**Giải pháp:**

```powershell
# Docker Desktop → Settings → Resources
# Tăng Memory lên 6-8GB
# Restart Docker Desktop

# Hoặc giảm heap size trong docker-compose-cluster.yml:
# ES_JAVA_OPTS: "-Xms256m -Xmx512m"  (thay vì 1g)
```

---

### ❌ Lỗi 2: Cluster status YELLOW/RED

**Hiện tượng:**

```
"status": "yellow"
```

**Giải pháp:**

```powershell
# Kiểm tra unassigned shards
curl http://localhost:9200/_cat/shards?v | findstr UNASSIGNED

# Giảm số replica nếu chỉ có 1-2 nodes
curl -X PUT "http://localhost:9200/multimedia/_settings" -H "Content-Type: application/json" -d '{
  "index": {
    "number_of_replicas": 1
  }
}'

# Restart cluster
docker-compose -f docker-compose-cluster.yml restart
```

---

### ❌ Lỗi 3: CLIP model download failed

**Hiện tượng:**

```
OSError: Can't load weights for 'openai/clip-vit-base-patch32'
```

**Giải pháp:**

```powershell
# Option 1: Retry download
pip install --upgrade transformers torch

# Option 2: Download manually
python -c "from transformers import CLIPModel, CLIPProcessor; CLIPModel.from_pretrained('openai/clip-vit-base-patch32')"

# Option 3: Sử dụng proxy (nếu bị chặn mạng)
set HF_ENDPOINT=https://hf-mirror.com
python scripts/main/3_create_embeddings.py
```

---

### ❌ Lỗi 4: Port đã được sử dụng

**Hiện tượng:**

```
Error: bind: address already in use (port 9200)
```

**Giải pháp:**

```powershell
# Tìm process đang dùng port
netstat -ano | findstr :9200

# Kill process (thay <PID> bằng process ID)
taskkill /PID <PID> /F

# Hoặc đổi port trong docker-compose-cluster.yml
# "9200:9200" → "9300:9200"
```

---

### ❌ Lỗi 5: Embedding shape mismatch

**Hiện tượng:**

```
ValueError: Expected 512 dimensions, got 768
```

**Giải pháp:**

```powershell
# Xóa embeddings cũ
Remove-Item data\embeddings\*.npy

# Tạo lại với đúng model
python scripts/main/3_create_embeddings.py

# Verify dimension
python -c "import numpy as np; print(np.load('data/embeddings/images_embeddings.npy').shape)"
# Output phải là: (800, 512)
```

---

### ❌ Lỗi 6: Slow performance (<5 QPS)

**Nguyên nhân & Giải pháp:**

1. **CPU throttling:**

   - Đóng các ứng dụng khác
   - Check Task Manager → CPU usage

2. **Disk I/O slow:**

   - Chuyển dataset sang SSD (nếu đang dùng HDD)
   - Disable Windows Defender scanning cho thư mục BigData

3. **Network latency:**

   - Elasticsearch chạy trên localhost (không qua network)
   - Check `docker network inspect` để verify

4. **Heap size quá nhỏ:**
   ```yaml
   # Tăng heap trong docker-compose-cluster.yml
   ES_JAVA_OPTS: "-Xms1g -Xmx2g"
   ```

---

### ❌ Lỗi 7: Demo crash khi search

**Hiện tượng:**

```
ConnectionError: Connection refused (localhost:9200)
```

**Giải pháp:**

```powershell
# Kiểm tra Elasticsearch có chạy không
docker ps | findstr elasticsearch

# Nếu không chạy, restart:
docker-compose -f docker-compose-cluster.yml up -d

# Kiểm tra logs
docker logs bigdata_es01

# Test connection
curl http://localhost:9200

# Nếu vẫn lỗi, check firewall:
netsh advfirewall firewall add rule name="ES9200" dir=in action=allow protocol=TCP localport=9200
```

---

## 📊 CHECKLIST HOÀN THÀNH

Sau khi hoàn tất tất cả các bước, bạn phải có:

### ✅ Infrastructure:

- [ ] Docker Desktop running
- [ ] 3 Elasticsearch nodes (GREEN status)
- [ ] Kibana accessible at http://localhost:5601
- [ ] (Optional) Solr accessible at http://localhost:8983

### ✅ Data:

- [ ] 1,010 multimedia files (900MB)
  - [ ] 800 images (55 MB)
  - [ ] 10 videos (738 MB)
  - [ ] 200 audios (118 MB)
- [ ] 1,010 embeddings (512-d vectors)
  - [ ] images_embeddings.npy
  - [ ] videos_embeddings.npy
  - [ ] audios_embeddings.npy

### ✅ Elasticsearch:

- [ ] Index `multimedia` created
- [ ] 1,010 documents indexed
- [ ] 6 shards active (3 primary + 3 replica)
- [ ] Search latency < 100ms
- [ ] QPS > 10

### ✅ Demo:

- [ ] Text search working
- [ ] Image search working
- [ ] Cross-modal search working
- [ ] Performance test passing
- [ ] Health check GREEN

---

## 🎯 NEXT STEPS

Sau khi hoàn tất setup:

1. **Chạy full benchmark:**

   ```powershell
   python scripts/benchmarks/benchmark_cluster.py
   python scripts/benchmarks/compare_es_solr.py
   ```

2. **Chụp screenshots cho báo cáo:**

   - Kibana monitoring dashboard
   - Demo search results
   - Performance metrics
   - Cluster health

3. **Tạo video demo (2-3 phút):**

   - Screen record demo_multimodal_search.py
   - Show text search → results
   - Show performance test
   - Show Kibana dashboard

4. **Chuẩn bị slide thuyết trình:**
   - Sử dụng `SLIDE_BAO_CAO.md`
   - Thêm screenshots vào slide
   - Practice 15-20 phút

---

## 📞 HỖ TRỢ

### Tài liệu tham khảo:

- **Elasticsearch Guide:** https://www.elastic.co/guide/en/elasticsearch/reference/8.11/
- **CLIP Model:** https://huggingface.co/openai/clip-vit-base-patch32
- **Docker Compose:** https://docs.docker.com/compose/

### Báo cáo lỗi:

- GitHub Issues: [link repo]
- Email: [email]

### Files quan trọng:

- `BAO_CAO.txt` - Báo cáo chi tiết (2,077 dòng)
- `SLIDE_BAO_CAO.md` - Slide thuyết trình (20 slides)
- `HUONG_DAN_CHAY_DU_AN.md` - File này

---

## ⏱️ TỔNG THỜI GIAN SETUP

**Ước tính tổng thời gian:**

1. Cài đặt môi trường: 15-20 phút
2. Download dataset & code: 10-15 phút
3. Cài Python dependencies: 5-10 phút
4. Khởi động Docker cluster: 2-3 phút
5. Tạo embeddings: 8-12 phút
6. Index vào Elasticsearch: 0.5-1 phút
7. Test & verify: 5-10 phút

**TỔNG:** ~50-70 phút (lần đầu tiên)

**Lần sau:** ~5 phút (chỉ cần `docker-compose up -d` + activate venv)

---

## 🎓 KẾT LUẬN

Bạn đã hoàn thành setup hệ thống tìm kiếm multimodal với:

✅ **900MB dataset** (1,010 files multimedia)
✅ **3-node Elasticsearch cluster** (distributed, high availability)
✅ **CLIP AI embeddings** (512-d vectors, cross-modal)
✅ **Performance:** 74ms latency, 13.4 QPS
✅ **Demo interactive** với 5 tính năng

**Chúc bạn thành công với bài báo cáo Big Data!** 🚀

---

**Tác giả:** [Tên của bạn]
**Ngày tạo:** October 30, 2025
**Version:** 1.0
**License:** MIT
