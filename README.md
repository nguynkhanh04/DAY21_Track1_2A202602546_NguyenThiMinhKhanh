# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Nguyễn Thị Minh Khánh
- MSSV / mã học viên: 2A202602546
- Lớp: Track 1
- Ngành đã chọn: Y tế và chăm sóc sức khỏe (Healthcare & Medical Care)

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **Tổn hại sức khỏe và tính mạng (injury)** do chẩn đoán sai, bỏ sót ca bệnh cấp tính hoặc đề xuất phác đồ điều trị nguy hiểm; **mất cơ hội tiếp cận y tế công bằng (opportunity loss)** khi thuật toán phân biệt đối xử với nhóm yếm thế; **quá tải nhận thức / mệt mỏi vì báo động (alert fatigue)** cho nhân viên y tế do báo động giả; **mất quyền riêng tư (privacy loss)** khi rò rỉ hồ sơ bệnh án cá nhân. Bệnh nhân, y bác sĩ và cơ sở y tế là các bên chịu ảnh hưởng trực tiếp. |
| Mức độ high-stakes | **Cao (High / Critical):** Quyết định trong y tế can thiệp trực tiếp đến sự sống, thể chất, sự an toàn và quyền được chăm sóc sức khỏe của con người. Một quyết định sai lệch từ AI có thể dẫn đến biến chứng vĩnh viễn, tàn tật hoặc tử vong mà không có cơ hội phục hồi. |
| Dữ liệu nhạy cảm có thể được sử dụng | Hồ sơ bệnh án điện tử (EHR/EMR), tiền sử bệnh lý và phác đồ dùng thuốc, hình ảnh chẩn đoán y khoa (X-quang, MRI, CT), dữ liệu giải trình tự gen/DNA, dữ liệu sinh hiệu thời gian thực (nhịp tim, huyết áp, SPO2), thông tin bảo hiểm y tế và chi phí khám chữa bệnh. |
| Nhu cầu human review | **Cao (Bắt buộc Human-in-the-loop):** Bác sĩ chuyên khoa hoặc chuyên viên y tế có chứng chỉ hành nghề phải trực tiếp kiểm tra và phê duyệt ở bước ra quyết định lâm sàng (chẩn đoán, kê đơn, phác đồ điều trị, xếp mức ưu tiên cấp cứu). AI chỉ đóng vai trò hỗ trợ tham vấn (clinical decision support), tuyệt đối không để AI tự động ban hành quyết định điều trị trực tiếp lên bệnh nhân. |

---

### 2. Case study 1 — Thuật toán phân bổ chăm sóc sức khỏe Optum (Racial Bias in Health Risk-Prediction)

#### Brief Case
- Tổ chức / sản phẩm AI: Thuật toán phân bổ rủi ro thương mại của Optum (Impact Pro / Commercial Risk-Prediction Algorithm).
- Thời gian, địa điểm / bối cảnh: Công bố vào tháng 10/2019 tại Hoa Kỳ bởi nhóm nghiên cứu đứng đầu là Ziad Obermeyer (Đại học California, Berkeley).
- AI được dùng để làm gì: Dự đoán "điểm rủi ro sức khỏe" (risk score) của bệnh nhân nhằm tự động sàng lọc và đề xuất đưa những người có nguy cơ cao vào các chương trình Quản lý chăm sóc đặc biệt (High-Risk Care Management - bổ sung y tá riêng, theo dõi định kỳ và hỗ trợ chăm sóc tích cực).
- Vấn đề hoặc sự kiện đáng chú ý: Thuật toán xuất hiện thiên lệch chủng tộc có hệ thống (systemic racial bias). Cùng một mức điểm số rủi ro do AI ấn định, bệnh nhân người Mỹ gốc Phi trên thực tế có mức độ bệnh tật và bệnh mãn tính nặng hơn đáng kể so với bệnh nhân người da trắng. Nguyên nhân do mô hình dùng **chi phí y tế phát sinh trong quá khứ** (healthcare costs) làm biến đại diện (proxy) cho **nhu cầu sức khỏe thực tế** (health needs). Do rào cản tài chính và bất bình đẳng tiếp cận bảo hiểm, người da đen chi tiêu ít hơn cho y tế, khiến AI kết luận sai lầm rằng họ khỏe mạnh hơn.
- Số liệu có nguồn:
  - Thuật toán được ước tính áp dụng cho hệ thống quản lý chăm sóc khoảng **200 triệu người** mỗi năm tại Mỹ (theo *Science*, 2019).
  - Tỷ lệ bệnh nhân da đen được tự động xếp vào chương trình chăm sóc đặc biệt theo AI chỉ đạt **17.7%**. Nếu khắc phục thiên lệch để phản ánh đúng mức độ bệnh tật thực tế, con số này tăng lên **46.5%** (hơn gấp đôi, đồng nghĩa AI đã gạt bỏ hơn 50% cơ hội tiếp cận của người da đen).
  - Ở cùng mức độ bệnh lý thực tế, chi phí y tế hàng năm của bệnh nhân da đen thấp hơn bệnh nhân da trắng trung bình **1.801 USD**, khiến AI đánh giá sai lệch toàn bộ rủi ro.
- Nguồn:
  - Nghiên cứu gốc: Obermeyer, Z., Powers, B., Vogeli, C., & Mullainathan, S. (2019). *Dissecting racial bias in an algorithm used to manage the health of populations*. **Science**, 366(6464), 447–453. DOI: [10.1126/science.aax2342](https://www.science.org/doi/10.1126/science.aax2342).
  - Báo chí phân tích: *Nature* (24/10/2019) — "Racial bias found in a major health care risk algorithm".
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Thuật toán sử dụng chi phí y tế làm biến mục tiêu dẫn đến thiên lệch chủng tộc nghiêm trọng làm giảm tỷ lệ tiếp cận chăm sóc của người da đen từ 46.5% xuống 17.7%.
  - *Điều suy luận / nhận định cá nhân:* Tác hại sức khỏe lâu dài (như bệnh mãn tính tiến triển nặng hơn hoặc tử vong sớm do không được vào chương trình can thiệp kịp thời) là nguy cơ thực tế rất cao nhưng nghiên cứu không thể truy vết cụ thể từng ca tử vong riêng lẻ.

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm hệ thống AI tính toán điểm rủi ro sức khỏe (risk score) và tự động xuất danh sách đề xuất các bệnh nhân được ưu tiên tham gia chương trình Quản lý chăm sóc đặc biệt (High-Risk Care Management). |
| Stakeholder bị ảnh hưởng | Bệnh nhân người Mỹ gốc Phi bị tước bỏ quyền lợi chăm sóc y tế chuyên sâu; các bệnh viện và công ty bảo hiểm đối mặt với nguy cơ pháp lý và phân bổ sai lệch nguồn lực y tế. |
| Failure mode | **Bias / fairness** (AI tạo ra kết quả phân biệt đối xử bất công bằng giữa các nhóm chủng tộc do dùng sai biến đại diện proxy chi phí y tế). |
| Layer bắt đầu lỗi | **Grounding & Model:** Ở tầng Grounding, dữ liệu đầu vào và định nghĩa mục tiêu bị méo mó (chi phí y tế quá khứ phản ánh khả năng tài chính thay vì mức độ bệnh); ở tầng Model, hàm mục tiêu tối ưu hóa sai biến dự đoán. |
| Harm xảy ra là gì? | **Bệnh nhân người Mỹ gốc Phi bị mất cơ hội tiếp cận chương trình chăm sóc y tế chủ động khi thuật toán đánh giá thấp mức độ bệnh tật của họ** (*Đã xảy ra* trên diện rộng trong nhiều năm). Nguy cơ biến chứng bệnh mãn tính trở nặng do thiếu can thiệp sớm (*Nguy cơ cao*). |
| Harm lens | **opportunity loss** (mất cơ hội tiếp cận dịch vụ y tế nâng cao) và **injury** (nguy cơ tổn hại thể chất gián tiếp). |
| Severity | **High:** Ảnh hưởng trực tiếp đến việc kiểm soát bệnh mãn tính và làm gia tăng nguy cơ biến chứng y tế nghiêm trọng cho nhóm bệnh nhân yếu thế. |
| Scale | **High (Quy mô lớn):** Thuật toán được áp dụng cho tập khách hàng quản lý sức khỏe tiềm năng lên tới 200 triệu người tại các bệnh viện và hãng bảo hiểm tại Mỹ. |
| Probability | **High (Chắc chắn / Đã xảy ra 100%):** Thiên lệch được chứng minh bằng thực nghiệm toán học và thống kê cụ thể trên toàn bộ tập dữ liệu mẫu 49.618 bệnh nhân. |
| Frequency | **High (Liên tục):** Diễn ra định kỳ trong mọi chu kỳ chạy thuật toán phân bổ bệnh nhân hàng tháng/hàng năm của hệ thống. |
| Vì sao? | Đánh giá dựa trên nghiên cứu khoa học bình duyệt trên tạp chí đầu ngành *Science* (2019) với số liệu đo lường cụ thể; giới hạn là chưa có số liệu định lượng về các ca tử vong cụ thể phát sinh. |

---

### 3. Case study 2 — IBM Watson for Oncology (Đề xuất phác đồ điều trị ung thư không an toàn)

#### Brief Case
- Tổ chức / sản phẩm AI: IBM Watson for Oncology (sản phẩm hợp tác giữa Tập đoàn IBM và Bệnh viện Ung bướu Memorial Sloan Kettering - MSKCC, New York, Mỹ).
- Thời gian, địa điểm / bối cảnh: Triển khai từ năm 2013 tại nhiều bệnh viện trên thế giới (Mỹ, Hàn Quốc, Thái Lan, Ấn Độ, v.v.); sự cố bị phanh phui qua cuộc điều tra nội bộ và báo chí năm 2017–2018.
- AI được dùng để làm gì: Đọc bệnh án của bệnh nhân ung thư, tổng hợp y văn thế giới và đề xuất các phác đồ điều trị y khoa cá nhân hóa (hóa trị, thuốc đích) cho bác sĩ ung bướu.
- Vấn đề hoặc sự kiện đáng chú ý: Hệ thống đưa ra nhiều phác đồ điều trị "sai sót và nguy hiểm đến tính mạng" (unsafe and incorrect recommendations). Điển hình là trường hợp AI đề xuất dùng thuốc chống đông máu kết hợp phác đồ hóa trị liều cao cho một bệnh nhân ung thư phổi đang có dấu hiệu xuất huyết nặng — phác đồ này có thể khiến bệnh nhân chảy máu đến tử vong. Nguyên nhân do AI không được huấn luyện trên dữ liệu bệnh nhân thực tế quy mô lớn mà chỉ được "dạy" trên các kịch bản bệnh án giả định (synthetic cases) do một nhóm nhỏ bác sĩ tại MSKCC tự biên soạn, dẫn đến thiên lệch theo thói quen điều trị cục bộ của bệnh viện này.
- Số liệu có nguồn:
  - Hệ thống đã được bán và triển khai tại hơn **140 bệnh viện và tổ chức y tế** trên toàn cầu trước khi bị dừng hoặc thu hẹp (theo tài liệu nội bộ do *STAT News* công bố năm 2018).
  - Nghiên cứu tại Bệnh viện Bundang - Đại học Quốc gia Seoul (Hàn Quốc) cho thấy tỷ lệ đồng thuận (concordance rate) giữa đề xuất của Watson và hội đồng bác sĩ đối với bệnh nhân ung thư đại tràng chỉ đạt **48.8%** (chưa đến một nửa).
  - Báo cáo nội bộ của Phó Giám đốc y khoa IBM tiết lộ có hàng chục trường hợp phác đồ bị bác sĩ đánh giá là "không khả thi và nguy hiểm".
- Nguồn:
  - Báo cáo điều tra: Ross, C., & Swetlitz, I. (2018). *IBM's Watson supercomputer recommended 'unsafe and incorrect' cancer treatments, internal documents show*. **STAT News** (25/07/2018). [Link bài viết](https://www.statnews.com/2018/07/25/ibm-watson-oncology-unsafe-treatments-internal-documents/).
  - Phân tích chuyên sâu: Strickland, E. (2019). *How IBM Watson Overpromised and Underdelivered on AI Health Care*. **IEEE Spectrum**. [Link bài viết](https://spectrum.ieee.org/how-ibm-watson-overpromised-and-underdelivered-on-ai-health-care).
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Tài liệu nội bộ rò rỉ xác nhận AI đưa ra phác đồ sai nguy hiểm; tỷ lệ không đồng thuận của bác sĩ thực tế ở mức cao; hệ thống được huấn luyện trên ca bệnh giả định thay vì dữ liệu đời thực phong phú.
  - *Điều suy luận / nhận định cá nhân:* Hầu hết các sai sót được ngăn chặn kịp thời do bác sĩ lâm sàng từ chối làm theo đề xuất của AI (nhờ có Human-in-the-loop), do đó nguy cơ tử vong trực tiếp cho bệnh nhân đã được chặn lại trong thực tế nhưng uy tín của AI y tế bị suy giảm trầm trọng.

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm hệ thống AI xuất báo cáo đề xuất phác đồ điều trị (kê đơn thuốc đặc trị, phác đồ hóa trị) để bác sĩ lâm sàng cân nhắc chỉ định cho bệnh nhân ung thư. |
| Stakeholder bị ảnh hưởng | Bệnh nhân ung thư (nguy cơ bị ngộ độc hoặc tử vong do phác đồ sai), bác sĩ ung bướu (nguy cơ sai sót y khoa và trách nhiệm nghề nghiệp), các bệnh viện (thiệt hại hàng triệu USD đầu tư và suy giảm uy tín). |
| Failure mode | **Harmful advice** (AI đưa ra lời khuyên phác đồ điều trị gây nguy hiểm tính mạng) và **Hallucination** (AI suy diễn phác đồ điều trị sai lệch từ tập ca bệnh giả định). |
| Layer bắt đầu lỗi | **Grounding & Safety:** Ở tầng Grounding, nguồn dữ liệu đào tạo thiếu khách quan (dùng ca bệnh giả định của một nhóm nhỏ bác sĩ MSKCC); ở tầng Safety, hệ thống thiếu bộ lọc kiểm tra chéo các chống chỉ định cấp cứu (chảy máu/xuất huyết) trước khi đưa ra phác đồ. |
| Harm xảy ra là gì? | **Bệnh nhân ung thư đối mặt với nguy cơ tử vong do xuất huyết khi AI khuyến nghị phác đồ thuốc chống chỉ định** (*Nguy cơ rất cao* ghi nhận trong tài liệu nội bộ; thực tế chưa có ca tử vong do bác sĩ đã phát hiện và chặn lại). Các bệnh viện bị thiệt hại hàng triệu USD chi phí triển khai phần mềm không hiệu quả (*Đã xảy ra*). |
| Harm lens | **injury** (nguy cơ tổn hại thể chất/tính mạng nghiêm trọng) và **misinformation** (thông tin tư vấn y khoa sai lệch). |
| Severity | **Critical:** Sai sót trong chỉ định thuốc ung bướu (gây xuất huyết không kiểm soát) có thể cướp đi sinh mạng bệnh nhân chỉ sau một liều dùng. |
| Scale | **Medium:** Đã triển khai thử nghiệm tại hơn 140 cơ sở y tế trên toàn cầu trước khi bị dừng hoặc hủy bỏ hợp đồng. |
| Probability | **Medium:** Tỷ lệ đưa ra phác đồ không tương thích với bác sĩ lên tới hơn 51% đối với một số loại ung thư như ung thư đại trực tràng. |
| Frequency | **Medium:** Xuất hiện lặp lại ở các ca bệnh có diễn biến lâm sàng phức tạp hoặc có nhiều bệnh nền kết hợp. |
| Vì sao? | Căn cứ từ tài liệu mật nội bộ rò rỉ của IBM do *STAT News* điều tra và các báo cáo thử nghiệm lâm sàng độc lập tại Bệnh viện Bundang (Hàn Quốc); giới hạn là không có ca tử vong thực tế nhờ có sự kiểm tra của bác sĩ (Human-in-the-loop). |

---

### 4. Case study 3 — Epic Sepsis Model (Mô hình cảnh báo sớm nhiễm trùng huyết gây quá tải báo động giả)

#### Brief Case
- Tổ chức / sản phẩm AI: Mô hình cảnh báo nhiễm trùng huyết Epic Sepsis Model (ESM) tích hợp trong hệ thống hồ sơ bệnh án điện tử của Tập đoàn Epic Systems (Mỹ).
- Thời gian, địa điểm / bối cảnh: Triển khai từ năm 2016 trên hàng trăm bệnh viện tại Mỹ; được kiểm định độc lập và công bố vào tháng 6/2021 bởi nhóm nghiên cứu Đại học Michigan trên tạp chí y khoa *JAMA Internal Medicine*.
- AI được dùng để làm gì: Tự động phân tích các chỉ số sinh hiệu (vital signs), kết quả xét nghiệm máu và ghi chú lâm sàng theo thời gian thực để đưa ra cảnh báo sớm cho bác sĩ/y tá về nguy cơ bệnh nhân bị nhiễm trùng huyết (sepsis) nhằm cấp cứu kịp thời.
- Vấn đề hoặc sự kiện đáng chú ý: Mô hình hoạt động kém xa so với tuyên bố của nhà phát triển. AI tạo ra một lượng khổng lồ các cảnh báo giả, gây ra hiện tượng "mệt mỏi vì báo động" (alert fatigue) khiến nhân viên y tế bị quá tải và bỏ qua cảnh báo; đồng thời bỏ sót phần lớn các ca nhiễm trùng huyết thực sự phát sinh trong bệnh viện.
- Số liệu có nguồn:
  - Nghiên cứu kiểm định độc lập trên **38.455 đợt nhập viện** của **27.697 bệnh nhân** tại hệ thống bệnh viện Michigan Medicine trong vòng 1 năm.
  - Epic Sepsis Model bỏ sót tới **67%** (hai phần ba) số ca nhiễm trùng huyết thực tế (AI không hề phát cảnh báo đối với các ca bệnh này).
  - Trong tổng số các cảnh báo đỏ phát ra, có đến **88%** là báo động giả (chỉ có 12% cảnh báo là phát hiện đúng bệnh nhân thực sự bị sepsis).
  - Độ chính xác thực tế của mô hình (AUROC) chỉ đạt **0.63**, kém hơn rất nhiều so với mức **0.73 - 0.83** do nhà phát triển Epic tự công bố nội bộ.
- Nguồn:
  - Nghiên cứu gốc: Wong, A., Otles, E., Donnelly, J. P., et al. (2021). *External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients*. **JAMA Internal Medicine**, 181(8), 1065–1070. DOI: [10.1001/jamainternmed.2021.2626](https://jamanetwork.com/journals/jamainternmed/fullarticle/2781307).
  - Báo chí y khoa: *STAT News* (21/06/2021) — "Popular predictive algorithm for sepsis misses most cases, study finds".
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Nghiên cứu lâm sàng độc lập xác nhận tỷ lệ bỏ sót ca bệnh là 67% và tỷ lệ báo động giả là 88%, dẫn đến nguy cơ mệt mỏi báo động nghiêm trọng trong bệnh viện.
  - *Điều suy luận / nhận định cá nhân:* Việc nhân viên y tế bị chai lỳ cảm xúc trước các cảnh báo giả liên tục có thể dẫn đến việc họ vô tình bỏ qua những ca nhiễm trùng huyết thật khi bệnh nhân chuyển biến xấu nhanh, gây nguy hiểm tính mạng.

#### Harm Map Worksheet
| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Thời điểm hệ thống AI tự động kích hoạt cửa sổ pop-up cảnh báo đỏ sốc nhiễm trùng huyết trên giao diện bệnh án điện tử, hoặc khi bệnh nhân chuyển biến xấu nặng nhưng AI không phát tín hiệu cảnh báo. |
| Stakeholder bị ảnh hưởng | Bệnh nhân nội trú (nguy cơ tử vong do không được can thiệp điều trị nhiễm trùng huyết kịp thời), bác sĩ và điều dưỡng trực (bị căng thẳng nhận thức, quá tải tâm lý vì báo động giả liên tục). |
| Failure mode | **Escalation failure** (AI không phát hiện và không chuyển tiếp/cảnh báo kịp thời cho 67% ca nhiễm trùng huyết thật) và **Over-reliance / Alert fatigue** (báo động giả 88% làm suy giảm tính cảnh giác của nhân viên y tế). |
| Layer bắt đầu lỗi | **Model & UX:** Ở tầng Model, thuật toán phân loại có độ nhạy kém và AUC thực tế chỉ đạt 0.63; ở tầng UX, thiết kế giao diện thông báo dạng pop-up liên tục thiếu phân loại mức độ ưu tiên làm trầm trọng thêm tình trạng quá tải nhận thức. |
| Harm xảy ra là gì? | **Bệnh nhân nội trú bị bỏ sót điều trị nhiễm trùng huyết trong "giờ vàng" khi AI không phát cảnh báo ở 67% ca bệnh thực tế** (*Đã xảy ra*); **Y bác sĩ và điều dưỡng bị kiệt sức nhận thức và suy giảm phản xạ cấp cứu khi 88% cảnh báo nhận được là báo động giả** (*Đã xảy ra*). |
| Harm lens | **injury** (tổn hại thể chất, nguy cơ tử vong do nhiễm trùng huyết) và **misinformation** (cảnh báo giả gây sai lệch nhận định lâm sàng). |
| Severity | **Critical:** Nhiễm trùng huyết là nguyên nhân gây tử vong hàng đầu trong bệnh viện nếu chậm trễ truyền kháng sinh cấp cứu. |
| Scale | **High:** Triển khai trên hàng trăm bệnh viện sử dụng hệ thống hồ sơ bệnh án điện tử Epic tại Hoa Kỳ; nghiên cứu thực nghiệm đo lường trên 38.455 ca nhập viện. |
| Probability | **High (Đã xảy ra 100%):** Tỷ lệ báo động giả 88% và tỷ lệ bỏ sót 67% được đo lường chính xác bằng thực nghiệm lâm sàng. |
| Frequency | **High (Liên tục):** Hàng nghìn cảnh báo giả phát ra liên tục mỗi ngày trên toàn bộ các khoa phòng nội trú. |
| Vì sao? | Đánh giá dựa trên nghiên cứu kiểm định độc lập được bình duyệt và đăng tải trên tạp chí y khoa hàng đầu *JAMA Internal Medicine* (2021) với dữ liệu thực tế từ 27.697 bệnh nhân. |
