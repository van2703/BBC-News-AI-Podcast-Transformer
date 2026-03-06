**Project Name:** BBC News AI Podcast Transformer

**Version:** 1.0 (Initial Draft)

**Developer:** vanpham

#### **1\. Tổng quan dự án (Project Overview)**

Hệ thống tự động hóa việc lấy tin tức từ BBC News, sử dụng AI để biên tập kịch bản, tạo file âm thanh podcast (5 phút) với nhạc nền phù hợp cảm xúc, và hiển thị lên website để người dùng nghe và tra cứu.

#### **2\. Luồng tính năng chính (Core Features)**

-   **Thu thập tin tức:** Tự động quét 5 bài báo chuyên sâu từ các chuyên mục cố định của BBC.
-   **Biên tập nội dung (AI Scripting):** \* Tóm tắt.
    -   Tự động quyết định phong cách: Độc thoại (1 giọng) hoặc Đối thoại (2 giọng).
    -   Thêm từ đệm tự nhiên, Intro/Outro cố định, trích dẫn nguồn bài báo.
-   **Sản xuất âm thanh (AI Audio):**
    -   Chuyển đổi văn bản thành giọng nói (TTS).
    -   **Sentiment Music:** Tự động phân tích cảm xúc kịch bản để lồng nhạc nền phù hợp (buồn, kịch tính, sôi động...).
-   **Website hiển thị:**
    -   Giao diện đơn giản, danh sách podcast mới nhất ở trên đầu.
    -   Cung cấp trình phát nhạc (Audio Player) và nút Tải về (Download).
    -   Hiển thị link nguồn BBC.
    -   Tính năng tìm kiếm các tập cũ dựa trên kịch bản lưu trữ.

#### **3\. Đặc tả kỹ thuật (Technical Stack)**

-   **Ngôn ngữ chính:** Python.
-   **AI Engine:** openrouter API (Xử lý kịch bản & Phân tích cảm xúc).
-   **Âm thanh:** Thư viện Python (gTTS/Edge-TTS) + MoviePy (để trộn nhạc nền).
-   **Website:** Streamlit hoặc FastAPI (Ưu tiên Streamlit để làm Admin Dashboard nhanh).
-   **Lưu trữ (Storage):** Google Drive API (Tài khoản riêng).
-   **Cơ sở dữ liệu:** SQLite (Lưu thông tin kịch bản, link, metadata).

#### **4\. Vận hành và Bảo trì (Ops & Maintenance)**

-   **Lịch trình:** Tự động chạy lúc 06:00 sáng hàng ngày.
-   **Chính sách lưu trữ (Data Retention):**
    -   File Audio (.mp3): Tự động xóa sau 1-2 tuần để tiết kiệm dung lượng Drive.
    -   Kịch bản (Text): Lưu trữ vĩnh viễn trong database để tra cứu.
-   **Thông báo:** Gửi Email báo cáo tình trạng sau mỗi lần thực thi.
-   **Xử lý lỗi:** Nếu không có tin mới, hệ thống tự chọn các bài báo "Evergreen" (bất hủ) để sản xuất podcast thay thế.
-   **Nhật ký (Logging):** Lưu file log trên Google Drive để theo dõi lỗi.

#### **5\. Trang quản trị (Admin Dashboard)**

-   Giao diện đơn giản để chị có thể:
    -   Bấm nút chạy hệ thống thủ công.
    -   Xóa các tập podcast không mong muốn.
    -   Xem lịch sử chạy và file log.

\+ các tính năng optional: podcast dịch sang tiếng việt, nhạc cảm xúc

\+ nếu gặp khó khăn về kỹ thuật hoặc về cost thì có thể tạm cắt các tính năng nà

### **TL;DR (Tóm tắt nhanh)**

Hệ thống này giống như một tòa soạn báo mini: Python đi nhặt tin -> Gemini viết kịch bản -> AI đọc & lồng nhạc -> Đẩy lên Web Streamlit lưu trên Drive. Tự động xóa file nặng sau 2 tuần, giữ lại kịch bản để tìm kiếm.