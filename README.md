# learn-backend
# LÝ THUYẾT
1. Cấu tạo nên 1 web cần 3 phần:  front end, backend, database
2. FE và BE là 2 phần mềm khác nhau chạy trên post khác nhau
3. Sử dụng BE để bảo mật tốt và xử lý những tác vụ phức tạp  
4. FE và BE sẽ giao tiếp với nhau thông qua API (Application Protocol Interface) và mục tiêu của BE là trả ra API

# THỰC HÀNH
1. Tạo 1 phần mềm BE : npm init => tạo 1 file package.json 
    - Sau khi init thành công thì sẽ tạo được 1 ứng dụng NodeJs
    - Mỗi ứng dụng có 1 file main trong package.json: index.js
    - Cú pháp để chạy file index.js: node src/index.js
    - Chúng ta có thể định nghĩa 1 lệnh ngắn để chạy trong file package.json:
        {
        "start":"node src/index.js"
        }
2. Cài thư viện typescript: Code trên JS sẽ bị giới hạn về việc định nghĩa kiểu dữ liệu vì vậy sinh ra TS để hỗ trợ về định nghĩa model, interface, làm cấu trúc dữ liệu chặt chẽ ràng buộc hơn
    - Cài thư viện: npm install typescript => Xuất hiện folder node_modules 
    - Để chuyển đổi APP JS hiện tại sang APP TS: npx tsc --init
    - Sau khi chuyển đổi từ JS sang TS thay đổi các file đuôi .js thành .ts để chạy được các syntax ts mà không báo lỗi
    - Tuy nhiên, TS là ngôn ngữ để hỗ trợ người đọc hiểu dễ hơn chứ k phải dành cho máy đọc nên bất kì khi nào start project, luôn cần chuyển đổi file index.ts sang dạng index.js trước rồi mới npm start    
        =>  Lệnh chuyển đổi: npx tsc 
    - Thêm lệnh trong package.json để tạo 1 folder dist chứa các file JS chuyển đổi:  "outDir": "dist"
    - Việc build và start diễn ra thường xuyên nên để nhanh hơn mình có thể vừa build vừa start bằng cách thêm lệnh sau vào package.json
        "scripts": {
            "start": "npx tsc; node dist/index.js"
        }, 
3. Một số thư viện cần sử dụng: 
    - Khi số lượng file nhiều lên thì để rút gọn ta sử dụng thư viện ts-node để đọc thẳng vào file TS mà k cần chuyển đổi. 
        * Cài đặt: npm i ts-node
        * Cú pháp run: ts-node src/index.ts
    - Để không cần phải liên tục start mỗi lần dev xong thì ta có thể sử dụng thư viện nodemon để lắng nghe sự kiện khi các file thay đổi 
        * Cài đặt: npm i nodemon 
        * Với thư viện này phải tạo một file nodemon.json với nội dung sau:
                {
                    "watch": ["src"], // danh sách thư mục bạn muốn lắng nghe
                    "ext": "ts,json", // các định dạng file bạn cần lắng nghe trong thư mục
                    "ignore": ["src/**/*.spec.ts"], // danh sách file k cần lắng nghe
                    "exec": "ts-node ./src/index.ts" // danh sách lệnh bạn muốn thực hiện khi có sự thay đổi trên các file đã chỉ định
                }
        * Cú pháp run: npx nodemon