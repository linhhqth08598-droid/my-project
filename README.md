Nội dung từ nhánh MAIN
# 📘 TỪ ĐIỂN TOÀN THƯ LINHSCRIPT (HQL) - CHI TIẾT TỪNG LỆNH
**Tác giả:** Hà Quang Linh (2009) | **Phiên bản Engine:** 1.0 (2026)

Tài liệu này là cẩm nang tra cứu toàn diện nhất cho lập trình viên HQL. Giải thích từng dấu câu, từng từ khóa và toàn bộ các hàm thuộc 20 thư viện lõi.

---

## I. TỪ ĐIỂN DẤU CÂU & KÝ HIỆU (PUNCTUATION & OPERATORS)

* `.` **(Dấu chấm):** Dùng để truy cập thuộc tính hoặc gọi hàm của một đối tượng. Cho phép gọi liên hoàn (Method Chaining). *VD: `text.trim().toLowerCase()`*
* `@` **(A-còng):** Dùng để định nghĩa phạm vi Public/Toàn cục. Biến/Hàm có `@` đứng trước có thể được gọi từ file khác. *VD: `var @globalVar = 10;`*
* `[]` **(Ngoặc vuông):** Dùng để tạo Mảng (List) hoặc truy cập phần tử theo chỉ số (Index bắt đầu từ 0). *VD: `mang[0]`*
* `{}` **(Ngoặc nhọn):** Dùng để mở/đóng một khối lệnh (Block Scope) cho hàm, vòng lặp, if/else.
* `()` **(Ngoặc đơn):** Dùng để bọc tham số truyền vào hàm hoặc gom nhóm biểu thức tính toán.
* `//` hoặc `#`: Ghi chú (Comment) trên 1 dòng. Trình biên dịch sẽ bỏ qua chữ phía sau nó.
* `/* ... */`: Ghi chú nhiều dòng. Mọi chữ nằm giữa 2 ký hiệu này đều bị bỏ qua.
* `+`, `-`, `*`, `/`, `%`, `^`: Các phép toán cơ bản (Cộng, Trừ, Nhân, Chia, Chia lấy dư, Lũy thừa).
* `++`, `--`: Tăng hoặc giảm biến đi 1 đơn vị. *VD: `i++`*
* `=`, `+=`, `-=`, `*=`, `/=`: Phép gán và gán dồn. *VD: `a += 5` nghĩa là `a = a + 5`*.
* `==`, `!=`, `>`, `<`, `>=`, `<=`: Phép so sánh (Bằng, Khác, Lớn hơn, Bé hơn...). Trả về `true` hoặc `false`.
* `? :` **(Toán tử 3 ngôi):** Dùng để viết If/Else siêu tốc. *VD: `(1 > 0) ? "Đúng" : "Sai"`*

---

## II. TỪ ĐIỂN TỪ KHÓA HỆ THỐNG (KEYWORDS)

Đây là các từ khóa được bảo vệ, bạn không được dùng làm tên biến:

### 1. Khai báo & Cấu trúc
* `var`: Dùng để khai báo một biến mới. *VD: `var a = 10;`*
* `func`: Dùng để khai báo một hàm mới. *VD: `func tinhTong(a, b) { return a + b; }`*
* `return`: Trả kết quả về cho hàm và thoát khỏi hàm đó ngay lập tức.
* `class`: Định nghĩa một lớp đối tượng (OOP).
* `extends`: Dùng trong `class` để kế thừa một lớp cha.
* `new`: Tạo ra một thực thể (object) mới từ một `class`.
* `import`: Nạp toàn bộ code từ một file `.hql` khác vào file hiện tại.
* `use`: Kích hoạt một thư viện lõi của hệ thống. *VD: `use hql.math;`*

### 2. Điều khiển luồng (Control Flow)
* `if` / `else`: Cấu trúc rẽ nhánh điều kiện. Nếu `if` đúng thì chạy, sai thì nhảy sang `else`.
* `switch` / `case` / `default`: Rẽ nhiều nhánh dựa trên giá trị của 1 biến.
* `for` / `in` / `to`: Dùng để tạo vòng lặp. *VD: `for i in 1 .. 5` hoặc `for item in mang`*
* `while`: Vòng lặp chạy liên tục chừng nào điều kiện còn bằng `true`.
* `break`: Đập vỡ và thoát ngay lập tức khỏi vòng lặp hoặc `switch`.
* `continue`: Bỏ qua các lệnh bên dưới, nhảy thẳng sang chu kỳ lặp tiếp theo.
* `try` / `catch` / `finally`: Bắt lỗi chương trình. Nếu code trong `try` bị lỗi, nó sẽ nhảy xuống `catch` thay vì làm sập App. `finally` luôn chạy cuối cùng.
* `throw`: Cố tình ném ra một lỗi để ngắt chương trình và đẩy xuống `catch`.

### 3. Logic & Giá trị đặc biệt
* `true` / `false`: Giá trị logic Đúng / Sai.
* `null`: Đại diện cho một biến rỗng, không có giá trị (Nhưng biến đó đã tồn tại).
* `undefined`: Đại diện cho một biến chưa từng được định nghĩa.
* `and` / `&&`: Phép VÀ logic (Cả 2 vế phải true).
* `or` / `||`: Phép HOẶC logic (Chỉ cần 1 vế true).
* `not` / `!`: Phép PHỦ ĐỊNH (Đảo ngược true thành false và ngược lại).

---

## III. CÁC HÀM LÕI CƠ BẢN (BUILT-IN CORE)
Luôn có sẵn không cần `use` thư viện nào:

* `print(x)`: In ra màn hình giá trị của `x`.
* `input()`: Chờ người dùng nhập dữ liệu từ bàn phím. Tự động ép kiểu (nếu nhập số sẽ tự thành biến số).
* `type(x)`: Trả về tên kiểu dữ liệu của biến (VD: trả về `"string"`, `"number"`, `"list"`...).
* `str(x)`: Ép dữ liệu thành dạng Chuỗi (String).
* `num(x)`: Ép dữ liệu thành dạng Số (Number).
* `bool(x)`: Ép dữ liệu thành dạng Logic (0 là false, 1 là true).
* `len(x)` / `size(x)`: Lấy độ dài của chuỗi hoặc số phần tử của mảng.
* `call(tên_hàm, tham_số...)`: Gọi một hàm thông qua tên hàm dạng chuỗi chữ (Dùng khi tên hàm lưu trong biến).

---

## IV. TỪ ĐIỂN PHƯƠNG THỨC MẢNG VÀ CHUỖI

### 1. Hàm cho Mảng (Array Methods)
Được gọi bằng cách dùng dấu chấm sau tên mảng. *VD: `mang.push(5)`*
* `push(x)` / `add(x)`: Đẩy thêm phần tử `x` vào cuối mảng.
* `pop()`: Xóa và lấy ra phần tử cuối cùng của mảng.
* `insert(index, x)`: Nhét phần tử `x` vào đúng vị trí số `index`.
* `removeAt(index)`: Xóa phần tử tại vị trí `index`.
* `indexOf(x)`: Trả về vị trí (index) của phần tử `x` trong mảng. Nếu không có trả về -1.
* `join(str)`: Nối tất cả phần tử mảng thành 1 câu, cách nhau bởi `str`.
* `map(hàm)`: Chạy `hàm` lên từng phần tử để biến đổi mảng thành mảng mới.
* `filter(hàm)`: Chạy `hàm` lên từng phần tử, giữ lại những phần tử trả về `true`.
* `reduce(hàm, khởi_tạo)`: Cuộn mảng thành 1 giá trị duy nhất (Ví dụ tính tổng).

### 2. Hàm cho Chuỗi (String Methods)
* `trim()` / `strip()`: Xóa dấu cách dư thừa ở đầu và cuối chuỗi.
* `lstrip()` / `rstrip()`: Chỉ xóa dấu cách dư ở bên Trái (l) hoặc bên Phải (r).
* `split(str)`: Băm chuỗi ra thành Mảng dựa trên ký tự phân cách `str`.
* `substring(start, end)`: Cắt lấy 1 khúc chữ từ vị trí `start` đến `end`.
* `toLowerCase()`: Biến tất cả chữ thành in thường.
* `toUpperCase()`: Biến tất cả chữ thành IN HOA.
* `indexOf(str)` / `lastIndexOf(str)`: Tìm vị trí xuất hiện đầu tiên / cuối cùng của từ `str`.
* `startsWith(str)` / `endsWith(str)`: Kiểm tra chuỗi có bắt đầu / kết thúc bằng `str` không (trả về true/false).
* `replace(cũ, mới)`: Tìm từ `cũ` và thay thế bằng từ `mới`.
* `insert(index, str)`: Nhét thêm chữ `str` vào vị trí `index`.
* `removeAt(index)`: Xóa 1 ký tự tại vị trí `index`.
* `contains(str)`: Kiểm tra xem chuỗi có chứa từ `str` không.
* `containsRegex(regex)` / `matches(regex)`: Kiểm tra chuỗi có khớp với biểu thức chính quy (Regex) không.

---

## V. TỪ ĐIỂN 20 THƯ VIỆN LÕI CHI TIẾT

### 1. `hql.io` (Quản lý File & Thư mục)
* **Đọc / Ghi File (I/O Cơ bản):** `read(path)`: Đọc toàn bộ nội dung file văn bản thành một chuỗi (String). `write(path, nội_dung, ghi_đè?)`: Ghi một chuỗi vào file. `readA(path)`: Đọc file ra thành một Mảng (List). `writeA(path, mảng, ghi_đè?)`: Ghi một Mảng xuống file.
* **Thao tác Hệ thống:** `create(path)`: Khởi tạo thông minh. `delete(path)`: Xóa file hoặc thư mục. `copy(nguồn, đích)`: Sao chép tệp tin. `move(nguồn, đích)`: Di chuyển hoặc đổi tên. `exists(path)`: Kiểm tra xem tệp tin hoặc thư mục có tồn tại hay không.
* **Trích xuất Thông tin (Metadata):** `fileSize(path)`: Trả về dung lượng. `getName(path)`: Lấy tên của tệp tin. `extension(path)`: Lấy phần đuôi mở rộng. `isDir(path)`: Kiểm tra xem có phải Thư mục không. `lastModified(path)`: Lấy mốc thời gian sửa cuối.
* **Duyệt và Tìm kiếm:** `list(path)`: Liệt kê danh sách file con. `listFull(path)`: Liệt kê đường dẫn tuyệt đối. `find(đuôi_file, thư_mục_gốc)`: Công cụ tìm kiếm đệ quy.
* **Ổ cứng & Đường dẫn:** `freeSpace()`: Trả về dung lượng trống. `totalSpace()`: Trả về tổng dung lượng. `homeDir()`: Lấy đường dẫn gốc của user. `workingDir()`: Lấy đường dẫn nơi Engine chạy.
* **Nén dữ liệu:** `zip(thư_mục_nguồn, file_zip_đích)`: Nén thư mục. `unzip(file_zip_nguồn, thư_mục_đích)`: Giải nén thư mục.

### 2. `hql.math` (Toán học & Thống kê)
* **Hằng số:** `PI` (3.14159...), `E` (2.71828...), `TAU` (2*PI), `INF` (Vô cực), `NAN` (Lỗi số học).
* **Toán cơ bản:** `sqrt(x)`: Căn bậc 2. `cbrt(x)`: Căn bậc 3. `pow(x, y)`: Tính x mũ y. `abs(x)`: Trị tuyệt đối. `hypot(x, y)`: Tính cạnh huyền tam giác vuông. `isqrt(x)`: Căn bậc 2 nguyên. `exp(x)`: Tính e mũ x.
* **Làm tròn:** `round(x)`: Làm tròn chuẩn. `ceil(x)`: Làm tròn lên. `floor(x)`: Làm tròn xuống. `trunc(x)`: Cắt phần thập phân.
* **Lượng giác:** `sin(x)`, `cos(x)`, `tan(x)`, `toRadians(độ)`, `degrees(rad)`.
* **Logarit:** `log(x)`, `log10(x)`, `log2(x)`.
* **Tổ hợp & Thuật toán:** `factorial(x)`: Giai thừa. `gcd(a, b)`: UCLN. `lcm(a, b)`: BCNN. `comb(n, k)`: Tổ hợp. `perm(n, k)`: Chỉnh hợp.
* **Tiện ích số:** `max(a, b)`, `min(a, b)`. `clamp(x, min, max)`. `random(min, max)`. `fsum(mảng)`. `isclose(a, b)`. `isnan(x)`, `isinf(x)`.
* **Thống kê:** `mean(mảng)`, `median(mảng)`, `variance(mảng)`, `stddev(mảng)`, `correlation(mảngX, mảngY)`, `linearRegression(mảngX, mảngY)`.
* **Ma trận:** `matrixMultiply(A, B)`, `matrixTranspose(M)`, `matrixDeterminant(M)`, `matrixInverse(M)`.
* **Đổi đơn vị:** `unitConvert(giá_trị, từ_đơn_vị, sang_đơn_vị)`. `listUnits()`. `unitCompare(v1, u1, v2, u2)`. `celsiusToFahrenheit(c)`, `fahrenheitToCelsius(f)`.

### 3. `hql.net` (Mạng Internet & Server)
* **Cấu hình Request:** `addHeader("Auth", "Token")`, `setCookie("Session=123")`, `setTimeout(ms)`, `setProxy(ip, port)`, `ignoreSSL()`.
* **Gửi Request:** `httpGet(url)`: Cào dữ liệu. `httpPost(url, chuỗi_body)`: Gửi data lên Server. `download(url, save_path)`: Tải file.
* **Đọc Response:** `getStatusCode()`, `getContentType()`, `getResponseHeader("Tên-Header")`.
* **Tiện ích Mạng:** `isOnline()`, `getIP()`, `getHost()`, `ping(ip)`, `checkPort(ip, port)`.
* **Server:** `createServer(cổng, "Tên_Hàm_Xử_Lý")`: Dựng Web Server cục bộ.

### 4. `hql.sys` (Phần cứng & Hệ thống)
* **CPU:** `cpuModel()`, `cpuCores()`, `cpuThreads()`, `cpuSpeed()`, `cpuVendor()`.
* **GPU & Màn hình:** `gpuModel()`, `gpuMemory()`, `gpuDriver()`, `resolution()`.
* **RAM:** `totalRam()`, `freeRam()`, `usedRam()`, `ramSpeed()`.
* **Mainboard:** `mainboard()`, `biosVersion()`, `serialNumber()`.
* **Ổ cứng:** `diskName()`, `diskStatus()`, `diskTemp()`, `diskWear()`.
* **OS:** `osName()`, `osArch()`, `userName()`, `uptime()`.
* **Điều khiển:** `exec("lệnh")`, `execRead("lệnh")`, `exit(code)`, `env("biến")`, `gc()`.

### 5. `hql.util` (Tiện ích chung)
* `sort(mảng)`: Sắp xếp mảng.
* `reverse(mảng)`: Đảo ngược mảng.
* `shuffle(mảng)`: Xáo trộn mảng.
* `unique(mảng)`: Xóa các phần tử trùng lặp.
* `count(mảng, x)`: Đếm xem phần tử `x` xuất hiện mấy lần.
* `uuid()`: Tạo ra chuỗi ID ngẫu nhiên.
* `toJson(biến)`: Biến Mảng/Object thành chuỗi JSON.
* `fromJson(chuỗi_json)`: Giải mã chuỗi JSON.
* `sleep(ms)`: Dừng chương trình lại.
* `range(start, end, step)`: Tạo mảng số.

### 6. `hql.ui` (Giao diện Desktop)
* **Popup nhanh:** `alert(chữ)`, `confirm(chữ)`, `prompt(chữ)`, `chooseFile()`, `chooseColor()`.
* **Cửa sổ & Layout:** `window(title, w, h)`, `setLayout("grid"|"flow")`, `show()`, `hide()`, `close()`.
* **Thành phần (Widgets):** `label(id, text)`, `button(id, text, tên_hàm)`, `textField(id)`, `textArea(id)`, `image(id, path)`, `checkbox(id, text)`, `radioButton(id, group, text)`, `comboBox(id, mảng_lựa_chọn)`, `table(id, mảng_cột, mảng_dòng)`, `progressBar(id, phần_trăm)`.
* **Sự kiện & Dữ liệu:** `onHover(id, tên_hàm)`, `onKeyPress(id, tên_hàm)`, `getText(id)`, `setStyle(id, "color", "#f3669a")`, `setInterval(tên_hàm, mili_giây)`.

### 7. `hql.crypto` (Mã hóa & Bảo mật)
* **Băm (Hash):** `md5(str)`, `sha256(str)`.
* **Băm mật khẩu:** `pbkdf2(password, salt)`.
* **Base64:** `base64Encode(str)`, `base64Decode(str)`.
* **Tạo mã bảo mật:** `secureRandom(độ_dài)`.
* **Mã hóa Đối xứng (AES):** `encrypt(data, key)`, `decrypt(cipher, key)`.
* **Mã hóa Bất đối xứng (RSA):** `generateKeys()`, `sign(data, private_key)`, `verify(data, signature, public_key)`.

### 8. `hql.database` (Cơ sở dữ liệu)
* `connect("mysql"|"sqlite"|"sqlserver", ...)`: Mở cổng kết nối DB.
* `closeDB()`, `isOpen()`.
* `query("SELECT...")`, `querySafe("SELECT...", [1])`: Lấy dữ liệu.
* `execute("DELETE...")`, `executeSafe("INSERT...", [biến])`: Chạy lệnh sửa/xóa.
* `identity()`: Lấy ID tự động tăng.
* `procedure("Tên_Proc", [tham_số])`: Kích hoạt Stored Procedure.
* `beginTransaction()`, `commit()`, `rollback()`.
* `tables()`, `columns("tên_bảng")`: Khám phá cấu trúc DB.
* `fetchOne(...)`: Lấy 1 dòng.
* `exportCSV("SELECT...", "file.csv")`: Đổ data ra file Excel nhẹ.

### 9. `hql.time` (Thời gian)
* `now()`, `today()`, `currentTime()`.
* `format(date, mẫu)`, `parse(chuỗi, mẫu)`.
* `addMinutes()`, `addDays()`, `addMonths()`, `addYears()`.
* `daysBetween(date1, date2)`.
* `getYear(d)`, `getMonth(d)`, `getDay(d)`, `getWeekday(d)`.
* `age(date_of_birth)`.
* `isWeekend(d)`, `isPast(d)`.
* `countdown(target_date)`.

### 10. `hql.regex` (Biểu thức chính quy)
* `compile(pattern)`, `quote(chuỗi)`.
* `matches(chuỗi, regex)`: Kiểm tra chuỗi khớp 100%.
* `containsRegex(chuỗi, regex)`: Kiểm tra chuỗi có chứa đoạn khớp không.
* `findRegex(chuỗi, regex)`: Trả về vị trí bắt đầu.
* `findAll(chuỗi, regex)`: Trả về mảng các cụm khớp.
* `replaceRegex(chuỗi, regex, mới)`, `replaceFirst(chuỗi, regex, mới)`.
* `splitRegex(chuỗi, regex)`.
* `group(chuỗi, regex, thứ_tự)`, `groups(...)`.

### 11. `hql.game` (Làm Game 2D)
* **Khởi tạo:** `gameWindow(title, w, h)`, `setTitle(title)`, `closeGame()`.
* **Đồ họa cơ sở:** `clear(màu)`, `drawRect()`, `fillRect()`, `drawCircle()`, `fillCircle()`, `drawLine()`, `drawText()`, `drawImage()`, `getTextWidth()`.
* **Sprite:** `sprite()`, `moveTo()`, `moveBy()`, `rotateSprite()`, `scaleSprite()`, `collide()`, `removeSprite()`, `spritePos()`.
* **Input:** `isKeyDown()`, `isKeyPressed()`, `mouseX()`, `mouseY()`, `isMouseDown()`, `setCamera(x, y)`.
* **Vòng lặp:** `gameLoop(Update, Draw)`, `distance()`, `randomInt()`, `frameCount()`.
* **Âm thanh:** `playSound(path, loop?)`, `stopSound()`, `setVolume(%)`.

### 12. `hql.pc` (Auto / Macro Bàn phím Chuột)
* `pos()`: Lấy tọa độ chuột.
* `scroll(số_nấc)`: Lăn chuột.
* `press("phím")`, `release("phím")`: Nhấn/Nhả.
* `combo("K1", "K2")`: Tổ hợp phím.
* `findPixel("#Màu", x, y, w, h)`: Tự động tìm tọa độ pixel theo màu.
* `getClip()`, `setClip("Chữ")`: Tương tác với Clipboard.

### 13. `hql.logging` (Nhật ký Hệ thống chuẩn)
* **Ghi log:** `logInfo(msg)`, `logWarning(msg)`, `logError(msg)`, `logDebug(msg)`.
* **Cấu hình:** `setLogLevel(level)`, `setLogFile(path)`, `logReset()`.

### 14. `hql.image` (Xử lý Đồ họa ẢNH)
* `loadImage(path)`, `saveImage(id, định_dạng, path)`.
* `imageWidth(id)`, `imageHeight(id)`.
* `resizeImage(id, w, h)`, `cropImage(id, x, y, w, h)`.
* `rotateImage(id, góc)`, `flipImage(id, "h"|"v")`.
* `grayscaleImage(id)`, `blurImage(id, mức_độ)`, `invertImage(id)`.
* `getPixelColor(id, x, y)`, `setPixelColor(id, x, y, "#Màu")`.
* `imageToSvg(id, path)`, `svgToImage(svg_text_or_path)`.

### 15. `hql.chart` (Vẽ biểu đồ phân tích Data)
* `drawBarChart(Mảng_Y, Mảng_Nhãn, "Tiêu Đề")`.
* `drawLineChart(...)`.
* `drawPieChart(...)`.
* `drawScatterChart(...)`.
* `drawHistogram(...)`.
* `setChartSize(id, w, h)`, `setChartColor(id, màu)`.
* `chartTitle(id)`.
* `saveChart(id, "file.png")`.

### 16. `hql.config` (Đọc/Ghi File INI)
* `loadConfig(file_path)`.
* `getConfig(id, "Key")`, `setConfig(id, "Key", "Value")`.
* `hasConfigKey()`, `removeConfigKey()`, `listConfigKeys()`.
* `getSectionConfig()`, `setSectionConfig()`.
* `listSections()`, `listSectionKeys()`, `removeSection()`.
* `saveConfig(id, file_path)`.

### 17. `hql.csv` (Thao tác file Bảng Excel CSV)
* `readCsvFile(path)`, `readDelimitedFile(path, ký_tự_ngăn)`.
* `readCsvRecords(path)`.
* `writeCsvFile(...)`, `writeDelimitedFile(...)`, `writeCsvRecords(...)`.
* `csvRowCount(mảng)`, `csvColumnCount(mảng)`.
* `getCsvCell(...)`, `setCsvCell(...)`, `getCsvField(...)`, `setCsvField(...)`.
* `addCsvRow(...)`, `addCsvRecord(...)`, `removeCsvRow(...)`, `removeCsvRecord(...)`.
* `sortCsvByColumn(...)`, `sortCsvRecordsByField(...)`.
* `filterCsvByColumn(...)`, `filterCsvRecordsByField(...)`.
* `csvRecordsToJson(...)`, `jsonToCsvRecords(...)`.

### 18. `hql.xml` (Bóc tách dữ liệu XML/HTML)
* `xmlReadFile(path)`, `xmlParseString(text)`.
* `xmlWriteFile(...)`, `xmlToString(obj)`.
* `xmlCreateRoot("Tên_Thẻ")`.
* `xmlXpathQuery(...)`, `xmlXpathAttr(...)`.
* `xmlFindNodes(...)`, `xmlGetNode(...)`, `xmlGetAttr(...)`.
* `xmlToJson(...)`, `jsonToXml(...)`, `xmlToCsv(...)`, `csvToXml(...)`.
* `xmlSetNode(...)`, `xmlSetAttr(...)`, `xmlAddChild(...)`, `xmlRemoveNode(...)`, `xmlRemoveAttr(...)`.
* `xmlChildrenCount(...)`, `xmlHasNode(...)`.

### 19. `hql.binary` (Xử lý Byte nhị phân & Hex - Cực sâu)
* `binaryRead(path)`, `binaryWrite(path, chuỗi_hex)`.
* `binaryReadByte(...)`, `binaryWriteByte(...)`.
* `binaryReadBytes(...)`, `binaryWriteBytes(...)`.
* `binaryFileSize(path)`.
* `binaryPack("Định_dạng", Mảng_giá_trị)`, `binaryUnpack("Định_dạng", chuỗi_hex)`.
* `binaryPackToFile(...)`, `binaryUnpackFromFile(...)`.
* `binaryCalcSize("Định_dạng")`.
* `binaryHexDump(...)`, `binaryHexToBytes(...)`, `binaryBytesToHex(...)`.
* `binarySlice(...)`, `binaryConcat(...)`, `binaryRepeat(...)`.
* `binaryReverse(hex)`, `binaryCompare(h1, h2)`.
* `binaryXor(hex_data, hex_key)`.
* `binaryCRC32(hex)`, `binaryMD5(hex)`, `binarySHA256(hex)`.
* `binaryToBase64(hex)`, `binaryFromBase64(b64)`.

### 20. `hql.color` (Chuyên gia Phân tích Màu sắc)
* **Chuyển đổi Hệ Màu:** `colorRgbToHex()`, `colorHexToRgb()`, `colorRgbToHsv()`, `colorHsvToRgb()`, `colorRgbToHsl()`, `colorHslToRgb()`, `colorRgbToCmyk()`, `colorCmykToRgb()`.
* **Tên màu CSS:** `colorNameToRgb()`, `colorRgbToName()`.
* **Phối trộn (Blend):** `colorBlend()`, `colorMultiBlend()`.
* **Dải màu (Gradient):** `colorGradient()`, `colorMultiGradient()`, `colorRandomGradient()`.
* **Chỉnh tông màu:** `colorLighten()`, `colorDarken()`, `colorSaturate()`, `colorDesaturate()`, `colorAdjustHue()`.
* **Thêm độ trong suốt:** `colorWithOpacity()`.
* **Phân tích WCAG:** `colorLuminance()`, `colorContrastRatio()`, `colorIsLight()`, `colorIsDark()`.
* **Khoảng cách:** `colorDistance()`, `colorSimilarity()`.
* **Bộ lọc ảo:** `colorToGreyscale()`, `colorExtractPalette()`.
* **Tạo màu tự động:** `colorRandomHex()`, `colorRandomRgb()`, `colorRandomPalette()`.
