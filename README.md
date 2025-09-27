# Ma_Hoa
Nguyễn Thị Kim Huệ-K225480106026

BÀI TẬP 1: TÌM HIỂU CÁC PHƯƠNG PHÁP MÃ HOÁ CỔ ĐIỂN

1.Caesar

2.Affine

3.Hoán vị

4.Vigenère

5.Playfair

Với mỗi phương pháp, hãy tìm hiểu:

1.Tên gọi

2.Thuật toán mã hoá, thuật toán giải mã

3.Không gian khóa

4.Cách phá mã (mà không cần khoá)

5.Cài đặt thuật toán mã hoá và giải mã bằng code C++ và bằng html+css+javascript  

Bài làm :
1. Mã hoá Caesar
   
Tên gọi : Mã Caesar (Shift cipher) Thuật toán :

Mã hóa(ký tự P → số p 0..25) : C = (P + k) mod  26

Giải mã: P = (C − k) mod  26

Trong đó :

P: ký tự bản rõ (plaintext, dạng số 0–25)

C: ký tự bản mã (ciphertext)

k: khóa (số bước dịch chuyển).

Không gian khóa : k ∈ {0,1,…,25} → 26 khả năng.

Ví dụ : Với k=3, "HELLO" → "KHOOR".

Cách phá mã (không cần khóa):

Brute-force: thử 26 giá trị k (rất rẻ).

Nếu biết ngôn ngữ: kiểm tra kết quả bằng dictionary / tần suất chữ (E, A, T …).

Kỹ thuật tần suất: khớp tần suất ký tự trong bản mã với tần suất ngôn ngữ.

Dùng HTML,CSS,JS

Mã hoá
<img width="1134" height="602" alt="Ảnh chụp màn hình 2025-09-25 154622" src="https://github.com/user-attachments/assets/2b7e4d37-e20b-41df-ac36-26be3b582f7b" />  
Giải mã  
<img width="1101" height="602" alt="Ảnh chụp màn hình 2025-09-25 154629" src="https://github.com/user-attachments/assets/12382854-e6f5-4535-8e6e-44debd36baaa" />  
2. Mã hoá Affine

Tên gọi: Mã Affine

Thuật toán :

Mã hóa : C = (a.P + b) mod 26

với điều kiện gcd(a,26) = 1 (để có nghịch đảo modulo 26)

Giải mã: P=a^(−1).(C − b) mod 26

a^(−1) là nghịch đảo modulo 26 (số x sao cho a.x ≡ 1 mod 26 )

Trong đó :

a,b là khóa. Điều kiện: gcd(a, 26) = 1 (để tồn tại nghịch đảo).

a^(-1): nghịch đảo modular của a.  

Dùng HTML,CSS,JS

Mã hóa  
<img width="1190" height="687" alt="Ảnh chụp màn hình 2025-09-25 154158" src="https://github.com/user-attachments/assets/811d7ddf-38d4-4c47-9ce7-b636a4144513" />  
Giải mã  
<img width="1155" height="633" alt="Ảnh chụp màn hình 2025-09-25 154204" src="https://github.com/user-attachments/assets/e787ead0-43cb-4437-94f9-259d9d733ab1" />  
3. Mã hoá hoán vị

Tên gọi : Mã hoán vị (block permutation cipher / columnar-like simple)
Thuật toán :

  Chọn kích thước khối k và một hoán vị perm = [p0,p1,...,p(k-1)] (mỗi pi ∈ {0..k-1} duy nhất).
  
  Chia bản rõ thành khối độ dài k (pad ký tự X nếu cần).
  
  Mỗi khối block (length k): bản mã khối cblock[i] = block[perm[i]].
  
Giải mã : cần hoán vị nghịch inv sao cho inv[perm[i]] = i. Sau đó block[i] = cblock[inv[i]].

Không gian khóa : số hoán vị của k phần tử: k! (k factorial). Nếu k nhỏ (ví dụ 4) thì 4! = 24; nếu k lớn, không gian lớn nhưng thường bị giới hạn vì k nhỏ trong triển khai học thuật.
Cách phá mã (không cần khóa):

  Brute-force trên k! khả năng (hiệu quả nếu k nhỏ).
  
  Nếu biết cấu trúc ngôn ngữ, kiểm tra từng candidate bằng thống kê / dictionary.
  
  Nếu attacker có bản rõ một phần (known-plaintext) thì dễ tìm hoán vị.
  
Dùng HTML,CSS,JS

Mã hoá  
<img width="1401" height="676" alt="Ảnh chụp màn hình 2025-09-25 155634" src="https://github.com/user-attachments/assets/f945c8c6-22ff-4088-81ec-7010645e6328" />   
Giải mã  
<img width="1350" height="633" alt="Ảnh chụp màn hình 2025-09-25 155644" src="https://github.com/user-attachments/assets/d76b0ad8-bdcc-400b-b3ac-ff4251e2074f" />   
4. Mã hoá Vigenère

Tên gọi : Mã Vigenère (polyalphabetic substitution cipher)
Thuật toán :

Key: chuỗi K (key) lặp lại.

Mã hóa : Ci = (Pi + Ki) mod  26

Giải mã: Pi = (Ci − Ki) mod  26

Trong đó:

Với mỗi ký tự i (P_i ∈ 0..25), K_i ∈ 0..25

Không gian khóa : mọi chuỗi ký tự. Nếu giới hạn độ dài key ≤ m và alphabet 26, thì số khóa ≈ 26^m (rất lớn khi m lớn).

Cách phá mã (không cần khóa):

Kasiski examination: tìm khoảng cách giữa các xuất hiện lặp lại của cùng một đoạn để suy ra độ dài khóa. 

Friedman test (Index of Coincidence) để ước lượng độ dài khóa.

Sau khi biết độ dài L, tách ciphertext thành L chuỗi đơn ký tự, mỗi chuỗi có thể bị tấn công bằng frequency analysis (giống Caesar).

Dùng HTML,CSS,JS

Mã hoá  
<img width="1126" height="617" alt="Ảnh chụp màn hình 2025-09-25 155605" src="https://github.com/user-attachments/assets/a4b821fd-9f30-4fae-83b4-949dc5c9ac01" />   
Giải mã  
<img width="1229" height="682" alt="Ảnh chụp màn hình 2025-09-25 155616" src="https://github.com/user-attachments/assets/f5206bbe-bb92-4655-9444-cba98ed22fc4" />  
5. Mã hoá Playfair

Tên gọi: Mã Playfair (digraph substitution cipher)

Thuật toán :

  Tạo bảng 5×5 từ khóa (ghép I/J hoặc loại J).
  
  Tiền xử lý bản rõ: gộp chữ hoa, thay J→I, bỏ ký tự không phải chữ, tách thành cặp (digraph), nếu hai ký tự trong cặp giống nhau → chèn 'X' giữa; nếu cuối cùng lẻ → thêm 'X'.
  
  Mã hóa từng cặp (A,B): tìm (r1,c1) và (r2,c2) trong bảng:
  
  Nếu cùng hàng → thay bằng ký tự bên phải (vòng).
  
  Nếu cùng cột → thay bằng ký tự bên dưới (vòng).
  
  Nếu khác hàng & cột → thay mỗi ký tự bằng ký tự cùng hàng nhưng cột của ký tự kia (hình chữ nhật).
  
Giải mã: tương tự nhưng di chuyển sang trái / lên thay vì phải / xuống. 

Dùng HTML,CSS,JS

Mã hoá  
<img width="1264" height="708" alt="Ảnh chụp màn hình 2025-09-25 155801" src="https://github.com/user-attachments/assets/215257db-0864-4c9c-95da-b31e5ca295e0" />  
Giải mã  
<img width="1202" height="667" alt="Ảnh chụp màn hình 2025-09-25 155811" src="https://github.com/user-attachments/assets/3c813f55-4b0a-4b3f-82b0-709090ae6534" />  










