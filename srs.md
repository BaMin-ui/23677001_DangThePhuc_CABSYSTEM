# TÀI LIỆU ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS)
## Dự án: Xây dựng Hệ thống CAB System – Nền tảng Đặt xe

**Thời gian triển khai:** 7 tuần
**Đơn vị:** Công ty ABC

---

## 1. Stakeholder (Các Bên Liên Quan)

| # | Stakeholder | Vai trò / Mô tả |
|---|---|---|
| 1 | Ban lãnh đạo / Ban giám đốc Công ty ABC | Phê duyệt định hướng, ngân sách, kỳ vọng chiến lược về nền tảng CAB |
| 2 | Khách hàng (Passenger) | Người dùng cuối, đặt xe, theo dõi chuyến đi, thanh toán, đánh giá tài xế |
| 3 | Tài xế (Driver) | Nhận và thực hiện chuyến đi, cập nhật trạng thái, cập nhật vị trí |
| 4 | Nhân viên vận hành (Operation Staff) | Quản trị khách hàng, tài xế, phương tiện, chuyến đi; xử lý sự cố |
| 5 | Bộ phận vận hành (Operations Department) | Theo dõi hoạt động, báo cáo doanh thu, tỷ lệ hoàn thành/hủy chuyến |
| 6 | Nhà cung cấp thanh toán bên ngoài (Payment Gateway Provider) | Xử lý giao dịch thanh toán điện tử, không lưu dữ liệu nhạy cảm trong hệ thống CAB |
| 7 | Nhóm phát triển (Development Team) | Thiết kế, xây dựng, triển khai hệ thống |
| 8 | Business Analyst (BA) | Làm rõ yêu cầu, phạm vi, quy trình nghiệp vụ với các bên liên quan |
| 9 | Bộ phận vận hành hệ thống/hạ tầng (System Operations/DevOps) | Đảm bảo hệ thống hoạt động ổn định, khả năng mở rộng khi tải tăng |
| 10 | Đơn vị cung cấp dịch vụ thông báo (Notification Provider) | Gửi thông báo (push/SMS/email) tới khách hàng và tài xế |

---

## 2. Stakeholder Matrix

Ma trận đánh giá mức độ **Quyền lực (Power)** và **Mức độ quan tâm/Ảnh hưởng (Interest)**:

| Stakeholder | Quyền lực (Power) | Mức độ quan tâm (Interest) | Chiến lược quản lý |
|---|---|---|---|
| Ban lãnh đạo / Ban giám đốc | Cao | Cao | Quản lý chặt chẽ (Manage Closely) |
| Khách hàng | Thấp | Cao | Thông báo thường xuyên (Keep Informed) |
| Tài xế | Thấp | Cao | Thông báo thường xuyên (Keep Informed) |
| Nhân viên vận hành | Trung bình | Cao | Quản lý chặt chẽ (Manage Closely) |
| Bộ phận vận hành (báo cáo) | Trung bình | Trung bình | Theo dõi định kỳ (Keep Satisfied) |
| Nhà cung cấp thanh toán | Trung bình | Trung bình | Theo dõi định kỳ (Keep Satisfied) |
| Nhóm phát triển | Cao | Cao | Quản lý chặt chẽ (Manage Closely) |
| Business Analyst | Cao | Cao | Quản lý chặt chẽ (Manage Closely) |
| System Operations/DevOps | Trung bình | Trung bình | Theo dõi định kỳ (Keep Satisfied) |
| Notification Provider | Thấp | Thấp | Giám sát tối thiểu (Monitor) |

---

## 3. Sơ đồ Quan hệ giữa các Stakeholder

```mermaid
graph TD
    BLD[Ban lãnh đạo / Ban giám đốc]
    BA[Business Analyst]
    DEV[Nhóm phát triển]
    KH[Khách hàng - Passenger]
    TX[Tài xế - Driver]
    NVVH[Nhân viên vận hành]
    BPVH[Bộ phận vận hành]
    TT[Nhà cung cấp thanh toán]
    TB[Nhà cung cấp thông báo]
    OPS[System Operations / DevOps]

    BLD -->|Định hướng, phê duyệt| BA
    BLD -->|Yêu cầu báo cáo| BPVH
    BA -->|Làm rõ yêu cầu, đặc tả| DEV
    BA -->|Thu thập yêu cầu| KH
    BA -->|Thu thập yêu cầu| TX
    BA -->|Thu thập yêu cầu| NVVH
    DEV -->|Xây dựng hệ thống CAB| SYS((Hệ thống CAB))
    KH -->|Đặt xe, thanh toán, đánh giá| SYS
    TX -->|Nhận chuyến, cập nhật trạng thái| SYS
    NVVH -->|Quản trị, xử lý sự cố| SYS
    SYS -->|Kết nối thanh toán| TT
    SYS -->|Gửi thông báo| TB
    SYS -->|Vận hành, mở rộng hạ tầng| OPS
    NVVH -->|Báo cáo hoạt động| BPVH
    BPVH -->|Báo cáo doanh thu, hiệu quả| BLD
```

---

## 4. Mục tiêu Kinh doanh (Business Goals)

1. **BG-01:** Xây dựng nền tảng CAB tự động hóa việc phân công tài xế, thay thế quy trình thủ công hiện tại.
2. **BG-02:** Nâng cao trải nghiệm khách hàng thông qua khả năng theo dõi chuyến đi theo thời gian thực.
3. **BG-03:** Quản lý tập trung thông tin thanh toán và cước phí, đảm bảo minh bạch và an toàn dữ liệu.
4. **BG-04:** Xây dựng hệ thống có khả năng mở rộng (scalable) để phục vụ số lượng lớn khách hàng và tài xế.
6. **BG-05:** Cung cấp công cụ báo cáo, thống kê giúp ban lãnh đạo ra quyết định (số chuyến, doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả tài xế).
7. **BG-06:** Đảm bảo hệ thống hoạt động ổn định, có khả năng chịu tải cao và cô lập lỗi giữa các phân hệ (thanh toán, thông báo không làm sập toàn hệ thống).
8. **BG-07:** Đảm bảo an toàn, bảo mật dữ liệu cá nhân, dữ liệu vị trí và dữ liệu giao dịch.

---

## 5. Yêu cầu Kinh doanh (Business Requirements)

### 5.1 Yêu cầu Chức năng (Functional Requirements)

#### A. Nhóm Khách hàng (Customer)
| ID | Yêu cầu chức năng |
|---|---|
| FR-01 | Hệ thống cho phép khách hàng đăng ký tài khoản và đăng nhập |
| FR-02 | Hệ thống cho phép khách hàng cập nhật thông tin cá nhân |
| FR-03 | Hệ thống cho phép khách hàng nhập điểm đón, điểm đến và chọn loại xe |
| FR-04 | Hệ thống cho phép khách hàng gửi yêu cầu đặt xe |
| FR-05 | Hệ thống cho phép khách hàng theo dõi trạng thái chuyến đi theo thời gian thực (đang tìm tài xế, tài xế đã nhận, thời gian dự kiến đến, trạng thái hiện tại) |
| FR-06 | Hệ thống cho phép khách hàng xem lịch sử chuyến đi và số tiền đã thanh toán |
| FR-07 | Hệ thống cho phép khách hàng đánh giá tài xế sau khi hoàn thành chuyến |
| FR-08 | Hệ thống thông báo cho khách hàng khi không tìm được tài xế phù hợp |

#### B. Nhóm Tài xế (Driver)
| ID | Yêu cầu chức năng |
|---|---|
| FR-09 | Hệ thống cho phép tài xế đăng ký tài khoản, hoặc được nhân viên vận hành tạo tài khoản |
| FR-10 | Hệ thống cho phép tài xế cập nhật hồ sơ, thông tin phương tiện |
| FR-11 | Hệ thống cho phép tài xế chuyển đổi trạng thái sẵn sàng nhận chuyến |
| FR-12 | Hệ thống gửi thông báo cho tài xế khi có chuyến phù hợp, cho phép chấp nhận hoặc từ chối |
| FR-13 | Hệ thống cho phép tài xế cập nhật trạng thái chuyến (đã đến điểm đón, đã đón khách, đang di chuyển, hoàn thành) |
| FR-14 | Hệ thống lưu và cập nhật vị trí tài xế theo thời gian thực |

#### C. Nhóm Tìm và Phân công Tài xế (Matching)
| ID | Yêu cầu chức năng |
|---|---|
| FR-15 | Hệ thống tự động xác định các tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và tiêu chí vận hành |
| FR-16 | Hệ thống ưu tiên đề xuất tài xế gần khách hàng nhất, phù hợp nhất |
| FR-17 | Hệ thống tự động tìm tài xế khác nếu tài xế được đề xuất không phản hồi hoặc từ chối, không yêu cầu khách hàng tạo lại yêu cầu |
| FR-18 | Hệ thống thông báo cho khách hàng khi không tìm được tài xế nào phù hợp |

#### D. Nhóm Thanh toán & Tính cước (Payment & Fare)
| ID | Yêu cầu chức năng |
|---|---|
| FR-19 | Hệ thống tính số tiền khách hàng phải trả dựa trên loại dịch vụ và thông tin chuyến đi |
| FR-20 | Hệ thống hỗ trợ thanh toán bằng tiền mặt và thanh toán điện tử |
| FR-21 | Hệ thống tích hợp với nhà cung cấp thanh toán bên ngoài, không lưu trực tiếp thông tin thẻ/tài khoản nhạy cảm |
| FR-22 | Hệ thống thông báo cho khách hàng khi giao dịch điện tử thất bại và cho phép xử lý lại theo chính sách |

#### E. Nhóm Thông báo (Notification)
| ID | Yêu cầu chức năng |
|---|---|
| FR-23 | Hệ thống gửi thông báo cho khách hàng khi: yêu cầu được tiếp nhận, tài xế nhận chuyến, tài xế đến điểm đón, chuyến hoàn thành, kết quả thanh toán |
| FR-24 | Hệ thống gửi thông báo cho tài xế về chuyến mới hoặc thay đổi liên quan đến chuyến đang thực hiện |
| FR-25 | Kiến trúc thông báo cho phép mở rộng thêm kênh thông báo mới trong tương lai |

#### F. Nhóm Quản trị / Vận hành (Admin/Operation)
| ID | Yêu cầu chức năng |
|---|---|
| FR-26 | Hệ thống cung cấp giao diện quản trị để quản lý khách hàng, tài xế, phương tiện, chuyến đi |
| FR-27 | Nhân viên vận hành có thể xem các chuyến đang diễn ra, kiểm tra trạng thái tài xế |
| FR-28 | Nhân viên vận hành có thể hỗ trợ xử lý các chuyến bị lỗi |
| FR-29 | Nhân viên vận hành có thể tra cứu lịch sử giao dịch |
| FR-30 | Hệ thống phân quyền chức năng quản trị, giới hạn thao tác nhạy cảm |
| FR-31 | Hệ thống cung cấp báo cáo: số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy, hiệu quả hoạt động tài xế |

## Sơ đồ use case 
```mermaid
flowchart LR
    KH((Khách hàng))
    TX((Tài xế))
    NVVH((Nhân viên vận hành))
    BLD((Ban lãnh đạo))
    PG((Payment Gateway))
    NP((Notification Provider))

    subgraph SYS[" Hệ thống CAB "]
        UC1([Đăng ký / Đăng nhập])
        UC2([Cập nhật thông tin cá nhân])
        UC3([Đặt xe])
        UC4([Theo dõi chuyến đi])
        UC5([Xem lịch sử chuyến đi])
        UC6([Đánh giá tài xế])
        UC7([Cập nhật hồ sơ / phương tiện])
        UC8([Chuyển trạng thái sẵn sàng])
        UC9([Chấp nhận / Từ chối chuyến])
        UC10([Cập nhật trạng thái chuyến])
        UC11([Cập nhật vị trí])
        UC12([Tìm tài xế phù hợp])
        UC13([Tính cước])
        UC14([Thanh toán])
        UC15([Gửi thông báo])
        UC16([Quản lý khách hàng / tài xế / phương tiện])
        UC17([Xử lý sự cố chuyến])
        UC18([Tra cứu lịch sử giao dịch])
        UC19([Xem báo cáo thống kê])
        UC20([Phân quyền thao tác nhạy cảm])
    end

    %% Actor - Use Case (association)
    KH --> UC1
    KH --> UC2
    KH --> UC3
    KH --> UC4
    KH --> UC5
    KH --> UC6

    TX --> UC1
    TX --> UC7
    TX --> UC8
    TX --> UC9
    TX --> UC10
    TX --> UC11

    NVVH --> UC16
    NVVH --> UC17
    NVVH --> UC18
    NVVH --> UC19

    BLD --> UC19

    PG --- UC14
    NP --- UC15

    %% Use Case - Use Case (include, chỉ áp dụng giữa các use case với nhau)
    UC3 -.include.-> UC12
    UC3 -.include.-> UC15
    UC10 -.include.-> UC15
    UC12 -.include.-> UC13
    UC13 -.include.-> UC14
    UC19 -.include.-> UC20
```
### 5.2 Yêu cầu Phi Chức năng (Non-Functional Requirements)

| ID | Loại | Mô tả |
|---|---|---|
| NFR-01 | Hiệu năng (Performance) | Hệ thống phải hoạt động ổn định vào các thời điểm nhu cầu tăng cao (giờ cao điểm) |
| NFR-02 | Khả năng mở rộng (Scalability) | Các thành phần hệ thống có khả năng mở rộng (scale) độc lập khi tải tăng |
| NFR-03 | Tính sẵn sàng (Availability) | Lỗi ở chức năng thanh toán hoặc thông báo không được làm ngừng toàn bộ hệ thống đặt xe (cô lập lỗi - fault isolation) |
| NFR-04 | Khả năng triển khai (Deployability) | Chức năng mới có thể triển khai từng phần, hạn chế ảnh hưởng đến chức năng đang hoạt động |
| NFR-05 | Bảo mật - Xác thực (Authentication) | Khách hàng và tài xế phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản |
| NFR-06 | Bảo mật - Phân quyền (Authorization) | Thao tác quản trị phải được kiểm soát quyền truy cập (role-based access control) |
| NFR-07 | Bảo mật dữ liệu (Data Security) | Thông tin cá nhân, thông tin phương tiện, dữ liệu vị trí, dữ liệu giao dịch phải được bảo vệ (mã hóa, kiểm soát truy cập) |
| NFR-08 | Tuân thủ thanh toán (Payment Compliance) | Không lưu trực tiếp thông tin nhạy cảm thẻ/tài khoản thanh toán trong hệ thống CAB (tuân thủ PCI-DSS thông qua bên thứ ba) |
| NFR-09 | Nhật ký kiểm toán (Audit Trail) | Hệ thống phải lưu vết các thao tác quan trọng phục vụ kiểm tra khi có sự cố |
| NFR-10 | Khả năng bảo trì/mở rộng (Maintainability/Extensibility) | Kiến trúc đủ linh hoạt để bổ sung dịch vụ mới, phương thức thanh toán mới, nhà cung cấp thông báo mới, hoặc thay đổi thành phần kỹ thuật mà không cần xây dựng lại toàn bộ hệ thống |
| NFR-11 | Thời gian phản hồi vị trí | Dữ liệu vị trí tài xế cần được cập nhật đủ nhanh để hỗ trợ tìm tài xế gần và dự kiến thời gian đến chính xác |

---

## 6. Mô hình Quy trình Nghiệp vụ (Business Process Model)

### 6.1 Quy trình tổng thể: Từ đặt xe đến đánh giá sau chuyến

```mermaid
flowchart TD
    A([Khách hàng tạo yêu cầu đặt xe]) --> B[Hệ thống tiếp nhận yêu cầu]
    B --> C[Hệ thống tìm kiếm tài xế phù hợp]
    C --> D{Tìm thấy tài xế phù hợp?}
    D -- Không --> E[Thông báo khách hàng không tìm được tài xế]
    E --> Z1([Kết thúc])
    D -- Có --> F[Gửi thông báo mời chuyến cho tài xế]
    F --> G{Tài xế phản hồi?}
    G -- Từ chối / Không phản hồi --> C
    G -- Chấp nhận --> H[Xác nhận tài xế cho chuyến]
    H --> I[Thông báo khách hàng: tài xế đã nhận chuyến]
    I --> J[Tài xế di chuyển đến điểm đón]
    J --> K[Tài xế cập nhật: đã đến điểm đón]
    K --> L[Thông báo khách hàng: tài xế đã đến]
    L --> M[Tài xế cập nhật: đã đón khách]
    M --> N[Tài xế cập nhật: đang di chuyển]
    N --> O[Tài xế cập nhật: hoàn thành chuyến]
    O --> P[Hệ thống tính cước]
    P --> Q{Phương thức thanh toán?}
    Q -- Tiền mặt --> R[Ghi nhận thanh toán tiền mặt]
    Q -- Điện tử --> S[Gọi cổng thanh toán bên ngoài]
    S --> T{Giao dịch thành công?}
    T -- Không --> U[Thông báo lỗi thanh toán, cho phép thử lại]
    U --> S
    T -- Có --> V[Ghi nhận thanh toán thành công]
    R --> W[Thông báo kết quả thanh toán cho khách hàng]
    V --> W
    W --> X[Khách hàng đánh giá tài xế]
    X --> Z2([Kết thúc])
```

### 6.2 Quy trình quản trị vận hành

```mermaid
flowchart LR
    NV([Nhân viên vận hành]) --> QLK[Quản lý khách hàng]
    NV --> QLTX[Quản lý tài xế]
    NV --> QLPT[Quản lý phương tiện]
    NV --> XLCD[Xem/Xử lý chuyến đang diễn ra]
    XLCD --> SC{Chuyến gặp lỗi?}
    SC -- Có --> XL[Hỗ trợ xử lý sự cố]
    SC -- Không --> TD[Theo dõi trạng thái]
    NV --> TCLS[Tra cứu lịch sử giao dịch]
    NV --> BC[Xem báo cáo hoạt động]
    BC --> BLD([Ban lãnh đạo])
```

---

## 7. Phân Tích Chức Năng Nghiệp Vụ

| Nhóm chức năng | Tác nhân chính | Mô tả nghiệp vụ | Đầu vào | Đầu ra |
|---|---|---|---|---|
| Đăng ký/Đăng nhập | Khách hàng, Tài xế | Xác thực người dùng trước khi sử dụng hệ thống | Thông tin tài khoản | Tài khoản được kích hoạt |
| Đặt xe | Khách hàng | Tạo yêu cầu chuyến đi với điểm đón/đến, loại xe | Điểm đón, điểm đến, loại xe | Yêu cầu chuyến đi (Trip Request) |
| Tìm & phân công tài xế | Hệ thống (Matching Engine) | Tìm tài xế phù hợp, xử lý từ chối/không phản hồi | Vị trí khách hàng, trạng thái tài xế | Tài xế được gán cho chuyến |
| Theo dõi chuyến đi | Khách hàng, Tài xế | Cập nhật và hiển thị trạng thái chuyến theo thời gian thực | Trạng thái chuyến | Cập nhật trạng thái hiển thị |
| Tính cước | Hệ thống | Tính số tiền dựa trên loại dịch vụ, quãng đường, thời gian | Thông tin chuyến hoàn thành | Số tiền cần thanh toán |
| Thanh toán | Khách hàng, Payment Gateway | Xử lý thanh toán tiền mặt hoặc điện tử | Số tiền, phương thức thanh toán | Trạng thái giao dịch |
| Thông báo | Hệ thống, Notification Provider | Gửi thông báo tới khách hàng/tài xế theo sự kiện | Sự kiện hệ thống | Thông báo được gửi |
| Đánh giá | Khách hàng | Đánh giá tài xế sau chuyến | Điểm đánh giá, nhận xét | Đánh giá được lưu |
| Quản trị hệ thống | Nhân viên vận hành | Quản lý dữ liệu người dùng, phương tiện, xử lý sự cố | Yêu cầu quản trị | Dữ liệu được cập nhật |
| Báo cáo thống kê | Nhân viên vận hành, Ban lãnh đạo | Tổng hợp số liệu vận hành | Dữ liệu giao dịch, chuyến đi | Báo cáo (doanh thu, tỷ lệ hoàn thành/hủy...) |

---

## 8. Quy Tắc Nghiệp Vụ (Business Rules)

| ID | Quy tắc nghiệp vụ |
|---|---|
| BR-01 | Khách hàng và tài xế phải có tài khoản đã xác thực mới có thể sử dụng chức năng yêu cầu đăng nhập |
| BR-02 | Tài xế chỉ nhận được thông báo mời chuyến khi đang ở trạng thái "sẵn sàng nhận chuyến" |
| BR-03 | Nếu tài xế được đề xuất không phản hồi hoặc từ chối, hệ thống phải tự động tìm tài xế tiếp theo mà không yêu cầu khách hàng tạo lại yêu cầu |
| BR-04 | Nếu không tìm được tài xế phù hợp, hệ thống phải thông báo rõ ràng cho khách hàng |
| BR-05 | Số tiền cước phải được xác định dựa trên loại dịch vụ và thông tin chuyến đi sau khi chuyến hoàn thành |
| BR-06 | Thông tin nhạy cảm của thẻ/tài khoản thanh toán không được lưu trực tiếp trong hệ thống CAB |
| BR-07 | Nếu giao dịch thanh toán điện tử thất bại, hệ thống phải thông báo cho khách hàng và cho phép xử lý lại theo chính sách doanh nghiệp |
| BR-08 | Một số chức năng quản trị (thao tác nhạy cảm) chỉ được thực hiện bởi nhân viên có quyền phù hợp, không áp dụng cho nhân viên vận hành thông thường |
| BR-09 | Mọi thao tác quan trọng trên hệ thống phải được ghi log để phục vụ kiểm tra khi có sự cố |
| BR-10 | Lỗi tại phân hệ thanh toán hoặc thông báo không được làm gián đoạn chức năng đặt xe cốt lõi |
| BR-11 | Vị trí tài xế phải được cập nhật liên tục để phục vụ việc tìm tài xế gần khách hàng |


## 9. Xác Định Entity (Thực Thể Dữ Liệu)

| Entity | Mô tả | Thuộc tính chính (đề xuất) |
|---|---|---|
| **Customer** | Khách hàng sử dụng dịch vụ | customer_id, full_name, phone, email, password_hash, created_at |
| **Driver** | Tài xế cung cấp dịch vụ | driver_id, full_name, phone, license_no, status (available/busy/offline), rating_avg, created_at |
| **Vehicle** | Phương tiện của tài xế | vehicle_id, driver_id (FK), plate_number, vehicle_type, brand, model, status |
| **Trip** | Chuyến đi | trip_id, customer_id (FK), driver_id (FK), pickup_location, dropoff_location, vehicle_type, status, requested_at, started_at, completed_at |
| **TripStatusHistory** | Lịch sử thay đổi trạng thái chuyến | history_id, trip_id (FK), status, changed_at |
| **DriverLocation** | Vị trí tài xế theo thời gian thực | driver_id (FK), latitude, longitude, updated_at |
| **Fare** | Thông tin tính cước của chuyến | fare_id, trip_id (FK), base_fare, distance_fare, time_fare, total_amount |
| **Payment** | Giao dịch thanh toán | payment_id, trip_id (FK), amount, method (cash/e-payment), status, payment_gateway_ref, created_at |
| **Notification** | Thông báo gửi tới người dùng | notification_id, recipient_id, recipient_type (customer/driver), channel, content, status, sent_at |
| **Rating** | Đánh giá tài xế sau chuyến | rating_id, trip_id (FK), customer_id (FK), driver_id (FK), score, comment, created_at |
| **OperationStaff** | Nhân viên vận hành | staff_id, full_name, role, permission_level, created_at |
| **AuditLog** | Nhật ký thao tác quan trọng | log_id, actor_id, actor_type, action, target_entity, target_id, created_at |

---

## 10. Sơ Đồ Quan Hệ Entity (ERD)

```mermaid
erDiagram
    CUSTOMER ||--o{ TRIP : "tạo yêu cầu"
    DRIVER ||--o{ TRIP : "thực hiện"
    DRIVER ||--o{ VEHICLE : "sở hữu/sử dụng"
    DRIVER ||--o{ DRIVERLOCATION : "cập nhật vị trí"
    TRIP ||--o{ TRIPSTATUSHISTORY : "có lịch sử trạng thái"
    TRIP ||--|| FARE : "được tính cước"
    TRIP ||--o{ PAYMENT : "được thanh toán"
    TRIP ||--o| RATING : "được đánh giá"
    CUSTOMER ||--o{ RATING : "đánh giá"
    CUSTOMER ||--o{ NOTIFICATION : "nhận thông báo"
    DRIVER ||--o{ NOTIFICATION : "nhận thông báo"
    OPERATIONSTAFF ||--o{ AUDITLOG : "thực hiện thao tác"
    OPERATIONSTAFF ||--o{ DRIVER : "hỗ trợ tạo tài khoản"

    CUSTOMER {
        string customer_id PK
        string full_name
        string phone
        string email
        datetime created_at
    }
    DRIVER {
        string driver_id PK
        string full_name
        string phone
        string license_no
        string status
        float rating_avg
    }
    VEHICLE {
        string vehicle_id PK
        string driver_id FK
        string plate_number
        string vehicle_type
    }
    TRIP {
        string trip_id PK
        string customer_id FK
        string driver_id FK
        string pickup_location
        string dropoff_location
        string status
        datetime requested_at
        datetime completed_at
    }
    TRIPSTATUSHISTORY {
        string history_id PK
        string trip_id FK
        string status
        datetime changed_at
    }
    DRIVERLOCATION {
        string driver_id FK
        float latitude
        float longitude
        datetime updated_at
    }
    FARE {
        string fare_id PK
        string trip_id FK
        float base_fare
        float distance_fare
        float total_amount
    }
    PAYMENT {
        string payment_id PK
        string trip_id FK
        float amount
        string method
        string status
    }
    RATING {
        string rating_id PK
        string trip_id FK
        string customer_id FK
        string driver_id FK
        int score
        string comment
    }
    NOTIFICATION {
        string notification_id PK
        string recipient_id
        string recipient_type
        string channel
        string status
    }
    OPERATIONSTAFF {
        string staff_id PK
        string full_name
        string role
        string permission_level
    }
    AUDITLOG {
        string log_id PK
        string actor_id
        string actor_type
        string action
        datetime created_at
    }
```

---

## 11. Tiêu Chí Chấp Nhận (Acceptance Criteria)

### 11.1 Đặt xe & Tìm tài xế
- **AC-01:** Given khách hàng đã đăng nhập và nhập đầy đủ điểm đón/điểm đến/loại xe, When khách hàng bấm "Đặt xe", Then hệ thống tạo yêu cầu chuyến đi và chuyển sang trạng thái "Đang tìm tài xế".
- **AC-02:** Given hệ thống đang tìm tài xế, When tài xế đầu tiên được đề xuất từ chối hoặc không phản hồi trong thời gian quy định, Then hệ thống tự động chuyển sang đề xuất tài xế tiếp theo mà không yêu cầu khách hàng tạo lại yêu cầu.
- **AC-03:** Given không có tài xế nào phù hợp sau khi đã thử các ứng viên, When quá trình tìm kiếm kết thúc, Then hệ thống thông báo rõ ràng cho khách hàng rằng không tìm được tài xế.

### 11.2 Theo dõi chuyến đi
- **AC-04:** Given tài xế đã nhận chuyến, When trạng thái chuyến thay đổi (đến điểm đón, đón khách, di chuyển, hoàn thành), Then khách hàng thấy trạng thái cập nhật theo thời gian thực trên ứng dụng.

### 11.3 Thanh toán
- **AC-05:** Given chuyến đi đã hoàn thành, When hệ thống tính cước, Then số tiền hiển thị phải khớp với loại dịch vụ và thông tin chuyến đi đã ghi nhận.
- **AC-06:** Given khách hàng chọn thanh toán điện tử, When giao dịch thất bại, Then hệ thống thông báo lỗi cho khách hàng và cho phép thử lại theo chính sách doanh nghiệp.
- **AC-07:** Given hệ thống tích hợp với nhà cung cấp thanh toán ngoài, When giao dịch được xử lý, Then thông tin thẻ/tài khoản nhạy cảm không được lưu trực tiếp trong cơ sở dữ liệu hệ thống CAB.

### 11.4 Thông báo
- **AC-08:** Given một sự kiện xảy ra trong vòng đời chuyến đi (tiếp nhận yêu cầu, tài xế nhận chuyến, tài xế đến, hoàn thành, kết quả thanh toán), When sự kiện được kích hoạt, Then khách hàng nhận được thông báo tương ứng.
- **AC-09:** Given tài xế có chuyến mới hoặc thay đổi liên quan đến chuyến đang thực hiện, When sự kiện xảy ra, Then tài xế nhận được thông báo tương ứng.

### 11.5 Quản trị
- **AC-10:** Given nhân viên vận hành thông thường đăng nhập, When họ cố gắng thực hiện thao tác quản trị nhạy cảm, Then hệ thống từ chối thao tác do không đủ quyền.
- **AC-11:** Given ban lãnh đạo yêu cầu xem báo cáo, When truy cập màn hình báo cáo, Then hệ thống hiển thị số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế trong khoảng thời gian được chọn.

### 11.6 Độ ổn định & Bảo mật
- **AC-12:** Given phân hệ thanh toán hoặc thông báo gặp sự cố, When lỗi xảy ra, Then chức năng đặt xe cốt lõi (tạo yêu cầu, tìm tài xế, theo dõi chuyến) vẫn hoạt động bình thường.
- **AC-13:** Given người dùng chưa xác thực, When họ cố truy cập chức năng yêu cầu tài khoản, Then hệ thống từ chối truy cập và yêu cầu đăng nhập.
- **AC-14:** Given một thao tác quan trọng được thực hiện trên hệ thống (thanh toán, phân quyền, chỉnh sửa dữ liệu tài xế...), When thao tác hoàn tất, Then hệ thống ghi lại nhật ký (audit log) đầy đủ thông tin tác nhân, hành động và thời gian.

---


## 13. Rủi ro (Risks)

| ID | Rủi ro | Mô tả | Ảnh hưởng | Khả năng xảy ra | Biện pháp giảm thiểu |
|---|---|---|---|---|---|
| RISK-01 | Thời gian triển khai ngắn (7 tuần) | Phạm vi nghiệp vụ lớn (3 nhóm actor, matching, thanh toán, thông báo, báo cáo) có thể vượt quá khả năng hoàn thành trong 7 tuần | Cao | Cao | Ưu tiên hóa yêu cầu theo MoSCoW, triển khai theo từng giai đoạn (MVP trước, mở rộng sau) |
| RISK-02 | Chưa chốt quy tắc nghiệp vụ (cách tính cước, tiêu chí ưu tiên tài xế, chính sách hủy...) | Có thể dẫn tới thiết kế/code phải làm lại khi khách hàng chốt yêu cầu muộn | Cao | Cao | BA làm rõ và chốt các quy tắc còn thiếu ngay trong giai đoạn phân tích, trước khi dev bắt đầu |
| RISK-03 | Phụ thuộc vào nhà cung cấp thanh toán bên thứ ba | Nếu bên thứ ba thay đổi API, downtime, hoặc chậm phản hồi sẽ ảnh hưởng luồng thanh toán | Cao | Trung bình | Thiết kế theo hướng tách rời (adapter pattern), có cơ chế retry và fallback (cho phép thanh toán tiền mặt) |
| RISK-04 | Sai lệch trong thuật toán tìm tài xế (Matching) | Nếu logic ưu tiên/khoảng cách không chính xác có thể khiến khách hàng chờ lâu hoặc tài xế không được phân công công bằng | Trung bình | Trung bình | Viết test case riêng cho matching engine, giám sát thời gian tìm tài xế trung bình sau khi go-live |
| RISK-05 | Tải hệ thống tăng cao vào giờ cao điểm | Có thể gây nghẽn cổ chai (bottleneck) nếu kiến trúc không tách rời các phân hệ | Cao | Trung bình | Thiết kế kiến trúc microservice/tách module, có khả năng scale độc lập, load test trước khi go-live |
| RISK-06 | Lỗi bảo mật dữ liệu cá nhân / vị trí / giao dịch | Rò rỉ dữ liệu nhạy cảm gây thiệt hại uy tín và pháp lý | Cao | Thấp | Mã hóa dữ liệu, kiểm soát truy cập theo vai trò (RBAC), audit log đầy đủ |
| RISK-07 | Thông tin thẻ thanh toán bị lưu trực tiếp trong hệ thống (vi phạm PCI-DSS) | Vi phạm quy định bảo mật thanh toán nếu thiết kế sai | Cao | Thấp | Đảm bảo mọi thông tin nhạy cảm được xử lý và lưu trữ tại bên thứ ba (tokenization), không lưu trong DB của CAB |
| RISK-08 | Tài xế/khách hàng mất kết nối mạng giữa chuyến đi | Trạng thái chuyến có thể không đồng bộ, gây tranh chấp về cước phí hoặc trạng thái hoàn thành | Trung bình | Trung bình | Cần BA làm rõ chính sách xử lý mất kết nối; áp dụng cơ chế đồng bộ lại trạng thái khi có kết nối trở lại |
| RISK-09 | Thiếu nhân sự/tài nguyên phát triển trong thời gian ngắn | Không đủ người để hoàn thành tất cả các module đúng hạn | Trung bình | Trung bình | Lập kế hoạch nguồn lực rõ ràng ngay từ đầu, xác định phạm vi MVP để giảm tải |
| RISK-10 | Thay đổi yêu cầu giữa chừng (scope creep) | Khách hàng bổ sung yêu cầu mới trong quá trình phát triển làm ảnh hưởng tiến độ 7 tuần | Trung bình | Cao | Áp dụng quy trình kiểm soát thay đổi (Change Request), đánh giá tác động trước khi chấp nhận thay đổi |

---

## 14. Bảng Test Case

Bảng dưới đây liên kết Test Case với **Yêu cầu Chức năng (FR)**, **Quy tắc Nghiệp vụ (BR)** và **Tiêu chí Chấp nhận (AC)** tương ứng để đảm bảo khả năng truy vết (traceability).

| TC ID | Mô tả Test Case | FR liên quan | BR liên quan | AC liên quan | Tiền điều kiện | Bước thực hiện | Kết quả mong đợi |
|---|---|---|---|---|---|---|---|
| TC-01 | Khách hàng đặt xe thành công | FR-01, FR-03, FR-04 | BR-01 | AC-01 | Khách hàng đã đăng nhập | 1. Nhập điểm đón/đến 2. Chọn loại xe 3. Bấm "Đặt xe" | Hệ thống tạo yêu cầu chuyến, trạng thái chuyển "Đang tìm tài xế" |
| TC-02 | Tài xế từ chối chuyến, hệ thống tự tìm tài xế khác | FR-15, FR-17 | BR-03 | AC-02 | Có ít nhất 2 tài xế khả dụng gần khách hàng | 1. Tài xế A nhận thông báo mời chuyến 2. Tài xế A từ chối | Hệ thống tự động gửi mời chuyến cho tài xế B mà không yêu cầu khách hàng đặt lại |
| TC-03 | Không tìm được tài xế phù hợp | FR-15, FR-18 | BR-04 | AC-03 | Không có tài xế nào ở trạng thái sẵn sàng trong khu vực | 1. Khách hàng đặt xe 2. Hệ thống tìm kiếm hết danh sách tài xế khả dụng | Hệ thống hiển thị thông báo "Không tìm được tài xế" cho khách hàng |
| TC-04 | Tài xế chỉ nhận mời chuyến khi ở trạng thái sẵn sàng | FR-11, FR-12 | BR-02 | — | Tài xế đang ở trạng thái "offline"/"bận" | 1. Hệ thống thực hiện matching | Tài xế không nhận được thông báo mời chuyến |
| TC-05 | Cập nhật trạng thái chuyến theo thời gian thực | FR-13, FR-05 | BR-11 | AC-04 | Tài xế đã nhận chuyến | 1. Tài xế cập nhật "đã đến điểm đón" 2. Tài xế cập nhật "đã đón khách" | Khách hàng thấy trạng thái cập nhật ngay trên ứng dụng |
| TC-06 | Tính cước sau khi chuyến hoàn thành | FR-19 | BR-05 | AC-05 | Chuyến đi đã hoàn thành, có đủ dữ liệu quãng đường/thời gian | 1. Tài xế cập nhật "hoàn thành chuyến" 2. Hệ thống tính cước | Số tiền hiển thị khớp với loại dịch vụ và thông tin chuyến đi |
| TC-07 | Thanh toán điện tử thất bại | FR-20, FR-22 | BR-07 | AC-06 | Khách hàng chọn thanh toán điện tử, cổng thanh toán trả về lỗi | 1. Khách hàng xác nhận thanh toán 2. Giao dịch bị từ chối bởi cổng thanh toán | Hệ thống thông báo lỗi và cho phép khách hàng thử lại |
| TC-08 | Không lưu thông tin thẻ nhạy cảm trong hệ thống CAB | FR-21 | BR-06 | AC-07 | Khách hàng thực hiện thanh toán điện tử thành công | 1. Kiểm tra database hệ thống CAB sau giao dịch | Không có trường lưu số thẻ/CVV/thông tin tài khoản thanh toán đầy đủ trong DB CAB |
| TC-09 | Gửi thông báo đầy đủ vòng đời chuyến đi cho khách hàng | FR-23 | — | AC-08 | Chuyến đi được tạo và thực hiện đầy đủ các bước | 1. Theo dõi các mốc: tiếp nhận, tài xế nhận, tài xế đến, hoàn thành, kết quả thanh toán | Khách hàng nhận đủ 5 loại thông báo tương ứng từng mốc |
| TC-10 | Gửi thông báo cho tài xế khi có thay đổi chuyến | FR-24 | — | AC-09 | Tài xế đang thực hiện chuyến, có thay đổi (VD: khách hủy) | 1. Khách hàng hủy chuyến giữa chừng | Tài xế nhận được thông báo về thay đổi |
| TC-11 | Nhân viên vận hành thông thường không thể thực hiện thao tác nhạy cảm | FR-30 | BR-08 | AC-10 | Đăng nhập với tài khoản nhân viên vận hành, quyền hạn thấp | 1. Truy cập chức năng quản trị nhạy cảm (VD: xóa tài xế, chỉnh sửa giao dịch) | Hệ thống từ chối thao tác, hiển thị lỗi không đủ quyền |
| TC-12 | Xem báo cáo thống kê vận hành | FR-31 | — | AC-11 | Người dùng có quyền xem báo cáo (ban lãnh đạo/nhân viên có quyền) | 1. Truy cập màn hình báo cáo 2. Chọn khoảng thời gian | Hiển thị đúng số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy, hiệu quả tài xế |
| TC-13 | Hệ thống đặt xe vẫn hoạt động khi phân hệ thanh toán lỗi | NFR-03 | BR-10 | AC-12 | Mô phỏng lỗi/downtime ở service thanh toán | 1. Khách hàng đặt xe trong lúc service thanh toán bị lỗi | Chức năng đặt xe, tìm tài xế, theo dõi chuyến vẫn hoạt động bình thường |
| TC-14 | Chặn truy cập chức năng yêu cầu tài khoản khi chưa xác thực | FR-01 | — | AC-13 | Người dùng chưa đăng nhập | 1. Truy cập trực tiếp chức năng đặt xe/xem lịch sử | Hệ thống chuyển hướng về màn hình đăng nhập, từ chối truy cập |
| TC-15 | Ghi nhật ký khi thực hiện thao tác quan trọng | FR-30 | BR-09 | AC-14 | Nhân viên vận hành có quyền thực hiện thao tác nhạy cảm | 1. Thực hiện thao tác (VD: khóa tài khoản tài xế) | Hệ thống ghi lại audit log gồm tác nhân, hành động, đối tượng, thời gian |
| TC-16 | Vị trí tài xế được cập nhật liên tục | FR-14 | BR-11 | — | Tài xế đang ở trạng thái hoạt động (online) | 1. Tài xế di chuyển 2. Kiểm tra bảng DriverLocation | Vị trí tài xế được cập nhật theo khoảng thời gian định kỳ hợp lý |
| TC-17 | Khách hàng đánh giá tài xế sau chuyến | FR-07 | — | — | Chuyến đi đã hoàn thành và thanh toán xong | 1. Khách hàng chọn điểm đánh giá và nhận xét 2. Gửi đánh giá | Đánh giá được lưu và liên kết đúng với trip_id, driver_id |
| TC-18 | Tài xế được tạo tài khoản bởi nhân viên vận hành | FR-09 | — | — | Nhân viên vận hành đăng nhập với quyền quản lý tài xế | 1. Nhân viên tạo tài khoản tài xế mới với đầy đủ thông tin | Tài khoản tài xế được tạo thành công, trạng thái mặc định hợp lệ |
