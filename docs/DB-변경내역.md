# DB 변경 내역

Supabase 프로젝트에 적용된 변경입니다. 전체 SQL은 Supabase 대시보드의 **Database › Migrations**에서 볼 수 있습니다.
기본 테이블과 함수는 이 기록 이전에 만들어져 여기에 포함되어 있지 않습니다.

| 적용일 | 이름 | 내용 |
|---|---|---|
| 10/28 | 이름 없는 수정 (SQL Editor) | 7일 이내 예약 허용(`assert_today`), 시간별 요금 트리거 |
| 10/28 | `nw_withdrawal_erases_login_account` | 탈퇴 시 로그인 계정 제거 |
| 10/28 | `nw_erase_auth_user_finite_ban` | 접속 차단 기한을 실제 날짜로 수정 |
| 10/28 | `nw_admin_delete_reservation` | 관리자 예약 기록 삭제 |
| 10/28 | `nw_withdrawal_deletes_personal_records` | 탈퇴 시 알림·대기·QR 삭제 |
| 10/28 | `nw_auto_no_show_job` | pg_cron으로 노쇼 1분 주기 자동 처리 |
| 10/28 | `nw_demo_easy_pay` | 시연용 간편결제, 즉시 확정 |
| 10/28 | `nw_demo_refund_compute_by_rule` | 시연 결제 자동 환불 계산 |
| 10/28 | `nw_admin_delete_member` | 관리자 회원 삭제 |
| 10/28 | `nw_erase_removes_profile` | 탈퇴 회원을 회원 목록에서 제거 |
| 10/29 | `nw_venues_partner_listing` | 파트너 업장 테이블·사진 저장소 |
| 10/29 | `nw_venues_revoke_trigger_exec` | 트리거 함수 직접 실행 차단 |
| 10/29 | `nw_venues_split_read_policies` | 업장 조회 권한 분리 |
| 11/04 | `nw_venue_phone_formats_and_photo_select` | 전화번호 형식 확대, 본인 사진 조회 권한 |

## 설정 변경

| 항목 | 내용 |
|---|---|
| 이용 규칙 | 2번 규칙을 "결제와 예약 확정"(버전 3)으로 교체 |
| 메일 | Authentication의 SMTP를 Gmail로 설정 |
| 관리자 | 관리자 이메일 목록에 운영 계정 추가 |
