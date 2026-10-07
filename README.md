# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Nguyễn Thị Minh Khánh
- MSSV / mã học viên: 2A202602546
- Lớp: Track 1
- Ngành đã chọn: Y tế và chăm sóc sức khỏe (Healthcare & Medical Care)

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **Tổn hại sức khỏe và đe dọa tính mạng** bệnh nhân do chẩn đoán sai, bỏ sót ca bệnh cấp tính hoặc đề xuất phác đồ điều trị nguy hiểm; **bất bình đẳng y tế** khi thuật toán phân biệt đối xử đối với nhóm yếm thế; **quá tải hệ thống y tế** do báo động giả hàng loạt (alert fatigue); **rò rỉ dữ liệu sức khỏe cá nhân** (thông tin bệnh án, sinh trắc học). Bệnh nhân, y bác sĩ và cơ sở y tế là những bên chịu ảnh hưởng trực tiếp. |
| Mức độ high-stakes | **Cao (High / Critical):** Quyết định trong y tế can thiệp trực tiếp đến sự sống, thể chất, sự an toàn và quyền được chăm sóc sức khỏe của con người. Một quyết định sai lệch từ AI có thể dẫn đến biến chứng vĩnh viễn, suy giảm cơ hội sống sót hoặc tử vong mà không có cơ hội phục hồi. |
| Dữ liệu nhạy cảm có thể được sử dụng | Hồ sơ bệnh án điện tử (EHR/EMR), tiền sử bệnh tật và dùng thuốc, hình ảnh chẩn đoán y khoa (X-quang, MRI, CT), dữ liệu giải trình tự gen/DNA, dữ liệu sinh hiệu thời gian thực (nhịp tim, huyết áp, SPO2), thông tin bảo hiểm y tế và chi phí khám chữa bệnh. |
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
| High-risk moment | Thời điểm hệ thống AI tự động xếp hạng điểm rủi ro (risk score) và xuất danh sách các bệnh nhân được ưu tiên vào chương trình hỗ trợ y tế đặc biệt. |
| Stakeholder bị ảnh hưởng | Bệnh nhân người Mỹ gốc Phi (bị tước bỏ quyền lợi chăm sóc y tế chuyên sâu), các bệnh viện/bảo hiểm (bị khiếu nại phân biệt đối xử, phân bổ sai nguồn lực y tế). |
| Failure mode | Bias / Proxy variable misalignment (Thiên lệch dữ liệu do chọn sai biến đại diện: đồng nhất chi phí y tế với tình trạng sức khỏe). |
| Layer bắt đầu lỗi | **Model & Grounding:** Lựa chọn biến mục tiêu (target variable/proxy) sai lệch ngay từ khâu thiết kế dữ liệu huấn luyện và định nghĩa bài toán của mô hình. |
| Harm xảy ra là gì? | Hàng chục ngàn bệnh nhân da đen mắc bệnh mãn tính nặng bị tước mất cơ hội tiếp cận hỗ trợ y tế chủ động (**Đã xảy ra** trên diện rộng trong nhiều năm triển khai). |
| Harm lens | Tác hại công bằng xã hội (Fairness/Equity harm) & Tác hại sức khỏe gián tiếp (Health harm do mất cơ hội điều trị sớm). |
| Severity | **High:** Bệnh nhân không nhận được can thiệp sớm dẫn đến nguy cơ suy thoái sức khỏe nghiêm trọng và tăng biến chứng bệnh lý mãn tính. |
| Scale | **Rộng lớn (Vĩ mô):** Áp dụng cho tập khách hàng tiềm năng lên đến 200 triệu người trên khắp các mạng lưới bệnh viện và công ty bảo hiểm tại Mỹ. |
| Probability | **Certain / Đã xảy ra (100%):** Thiên lệch được chứng minh bằng thực nghiệm toán học và thống kê trên toàn bộ tập dữ liệu mẫu. |
| Frequency | **Continuous:** Diễn ra liên tục trong mọi chu kỳ chạy thuật toán phân bổ bệnh nhân hàng tháng/hàng năm. |
| Vì sao? | Đánh giá dựa trên bài báo khoa học bình duyệt (peer-reviewed) trên tạp chí đầu ngành *Science* với tập dữ liệu thực tế gồm 49.618 bệnh nhân. |

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
| High-risk moment | Khi bác sĩ điều trị nhận báo cáo phác đồ khuyến nghị từ Watson for Oncology để ra quyết định kê đơn thuốc/hóa trị cho bệnh nhân ung thư. |
| Stakeholder bị ảnh hưởng | Bệnh nhân ung thư (nguy cơ sốc thuốc, biến chứng xuất huyết), bác sĩ điều trị (nguy cơ sai sót y khoa), các bệnh viện (thiệt hại hàng triệu USD chi phí đầu tư phần mềm). |
| Failure mode | Hallucination / Training Distribution Shift (Đưa ra khuyến nghị sai lệch do dữ liệu huấn luyện là ca bệnh giả định hạn hẹp, không tổng quát hóa được cho thực tế lâm sàng). |
| Layer bắt đầu lỗi | **Grounding & Model:** Thiếu dữ liệu thực tế khách quan đa trung tâm; quy trình nạp tri thức y khoa dựa trên ý kiến chủ quan của một nhóm nhỏ chuyên gia MSKCC. |
| Harm xảy ra là gì? | Đề xuất thuốc nguy hiểm đến tính mạng (**Nguy cơ cao** được ghi nhận trong báo cáo nội bộ; chưa ghi nhận ca tử vong thực tế do bác sĩ đã phát hiện và bác bỏ). Gây thiệt hại tài chính lớn và lãng phí thời gian điều trị của bệnh viện (**Đã xảy ra**). |
| Harm lens | Tác hại an toàn sinh mạng (Physical Safety harm) & Tác hại tài chính/lãng phí nguồn lực (Financial/Resource harm). |
| Severity | **Critical:** Sai sót trong điều trị ung thư (ví dụ gây xuất huyết không kiểm soát) có thể dẫn tới tử vong trực tiếp cho bệnh nhân. |
| Scale | **Medium - Large:** Hơn 140 cơ sở y tế tại nhiều quốc gia (Mỹ, Hàn Quốc, Ấn Độ, Trung Quốc...) đã áp dụng thử nghiệm. |
| Probability | **High (về mặt tạo lỗi sai):** Đã xảy ra nhiều lần trong môi trường thử nghiệm và kiểm thử lâm sàng. |
| Frequency | **Frequent:** Tần suất đưa ra phác đồ không tương thích với bác sĩ địa phương lên tới hơn 50% ở một số loại ung thư (như đại trực tràng). |
| Vì sao? | Căn cứ từ tài liệu nội bộ mật của IBM bị rò rỉ, các bài phóng sự điều tra của *STAT News* và các nghiên cứu lâm sàng độc lập tại các bệnh viện Hàn Quốc, Ấn Độ. |

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
| High-risk moment | Khi hệ thống tự động nhảy cửa sổ pop-up cảnh báo đỏ hoặc khi bệnh nhân đang chuyển biến xấu nhưng AI không phát tín hiệu cảnh báo. |
| Stakeholder bị ảnh hưởng | Bệnh nhân nội trú (nguy cơ tử vong do sốc nhiễm trùng không được cấp cứu sớm), bác sĩ và điều dưỡng trực (bị stress, kiệt sức vì báo động giả). |
| Failure mode | High False Alarm Rate & Low Sensitivity (Độ nhạy thấp dẫn đến bỏ sót ca bệnh nguy kịch + Tỷ lệ báo động giả cực cao). |
| Layer bắt đầu lỗi | **Model & UX:** Mô hình phân loại kém chính xác (Model layer) kết hợp với thiết kế giao diện cảnh báo dạng pop-up liên tục thiếu chọn lọc (UX layer) làm gia tăng hiện tượng alert fatigue. |
| Harm xảy ra là gì? | Bỏ sót 67% ca nhiễm trùng huyết thực tế (**Đã xảy ra**); gây quá tải tâm lý và phân tâm cho y tá, bác sĩ trong ca trực (**Đã xảy ra**). |
| Harm lens | Tác hại tính mạng/sức khỏe (Physical Harm) & Tác hại năng suất làm việc của nhân viên y tế (Cognitive Overload). |
| Severity | **Critical:** Nhiễm trùng huyết là nguyên nhân gây tử vong hàng đầu tại bệnh viện nếu không được truyền kháng sinh trong "giờ vàng" đầu tiên. |
| Scale | **Large:** Triển khai trên hàng trăm bệnh viện sử dụng phần mềm EHR của Epic trên toàn nước Mỹ. |
| Probability | **Certain / Đã xảy ra (100%):** Tỷ lệ báo động giả 88% xảy ra đều đặn hàng ngày trong quy trình vận hành. |
| Frequency | **Continuous:** Hàng nghìn cảnh báo được kích hoạt mỗi ngày trên toàn bộ các khoa phòng bệnh viện. |
| Vì sao? | Dựa trên kết quả nghiên cứu kiểm định độc lập được bình duyệt và đăng tải trên tạp chí y khoa hàng đầu *JAMA Internal Medicine*. |
