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
| 11/04 | `nw_policy_alignment_and_ops` | 노쇼·환불 정책을 안내 내용과 일치, 시작 10분 전 체크인, 자동 퇴실, 민원 답변 알림, 제한 해제, 공용 설정 표 |
| 11/04 | `nw_member_passes` | 멤버십 구매 기록 저장, 사용 중인 룸·사물함 조회, 탈퇴 시 기록 삭제 |
| 11/04 | `nw_tighten_new_table_grants` | 새 표의 비로그인 권한 축소 |
| 11/04 | `nw_polling_indexes` | 5초 갱신 조회용 색인 |
| 11/04 | `nw_pay_with_member_pass` | 시간권·자유석 예약, 취소 시 시간 복구, 잔여 시간은 DB 함수만 변경 |
| 11/04 | `nw_pass_notice_hours_format` | 알림의 시간 표기 정리 |
| 11/04 | `nw_team_room_reopen_on_checkout` | 입실한 팀원이 모두 퇴실하면 룸 예약 종료, 좌석 상태 1분마다 갱신 |
| 11/04 | `nw_team_room_booking_and_pass_refunds` | 팀 프로젝트룸 묶음 예약·노쇼·취소, 팀 전용 룸 보호, 멤버십 환불 요청·처리, 결제자 이메일 채움 |
| 11/04 | `nw_notify_on_member_pass_deleted` | 관리자가 멤버십 삭제 시 구매자·팀원 알림 |
| 11/04 | `nw_membership_alerts_and_venue_delete_notice` | 멤버십 구매 시 구매자·관리자·팀원 알림, 나중에 가입한 팀원 알림, 관리자 업장 삭제 시 등록자 알림 |

## 설정 변경

| 항목 | 내용 |
|---|---|
| 이용 규칙 | 2번 규칙을 "결제와 예약 확정"(버전 3)으로 교체, 1번 규칙의 "당일" 문구를 이용 날짜로 교체(버전 2) |
| 노쇼 정책 | 유예 15분, 최근 30일 3회, 7일 예약 제한 (이전: 유예 10분, 제한 없음) |
| 환불 정책 | 시작 2시간 전까지 100%, 30분 전까지 50%, 이후 0% (이전: 정책 없음) |
| 메일 | Authentication의 SMTP를 Gmail로 설정 |
| 관리자 | 관리자 이메일 목록에 운영 계정 추가 |
