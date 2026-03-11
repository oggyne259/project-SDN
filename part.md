1) Auth (đăng ký / OTP / đăng nhập)

POST /auth/register/request-otp (request OTP khi đăng ký / resend OTP cũng dùng lại endpoint này)

POST /auth/register/verify (verify OTP + hoàn tất đăng ký)

POST /auth/register (register)

POST /auth/login (login)

GET /users/me/profile (lấy profile user hiện tại)

Frontend tự attach Authorization: Bearer <token> từ localStorage.token cho mọi request.

2) User / Admin Users / Search donors
User profile

GET /users/me/profile

PUT /users/me/profile (update profile)

Search donors theo vị trí

POST /users/search/donors-by-location

Admin quản lý user

GET /admin/users (có query params: page,size,sort,keyword,...filters)

POST /admin/users

GET /admin/users/{userId}

PUT /admin/users/{userId}

DELETE /admin/users/{userId} (soft delete/disable)

3) Blood Requests

POST /blood-requests (tạo request, kể cả emergency cũng dùng endpoint này)

GET /blood-requests (pagination: page,size)

GET /blood-requests/{id}

PUT /blood-requests/{requestId}/status?newStatus={NEW_STATUS} (update status)

GET /blood-requests/search/active (search active, dùng query params)

GET /blood-requests/search/completed (pagination + status, FE set status=FULFILLED)

POST /blood-requests/{requestId}/pledge (pledge đăng ký hiến máu cho request)

4) Blood Types

GET /blood-types

GET /blood-types/{id}

POST /blood-types

PUT /blood-types/{id}

DELETE /blood-types/{id}

GET /blood-types/{id}/users (lấy users theo blood type)

5) Blood Compatibility

GET /blood-compatibility (pagination: page,size, sort FE set sort=id,asc)

GET /blood-compatibility/{id}

POST /blood-compatibility

PUT /blood-compatibility/{id}

DELETE /blood-compatibility/{id}

6) Donations (quy trình hiến máu)

POST /donations/request (user tạo yêu cầu hiến máu)

GET /donations/my-history (lịch sử hiến máu của tôi)

GET /donations/requests (admin/staff xem list requests)

PUT /donations/requests/{processId}/status (update trạng thái quy trình)

POST /donations/{processId}/health-check

POST /donations/{processId}/collect (mark collected)

POST /donations/{processId}/test-result

7) Inventory

GET /inventory

GET /inventory/summary

GET /inventory/recent