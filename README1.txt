MONROE UNIVERSITY STUDENT RECOVERY - RESTRICTED TEST PACKAGE

NOT DEPLOYED. Do not expose to all students before live testing.

1. Run 001_recovery_attempts.sql in Supabase SQL Editor. Confirm the table exists and RLS is enabled.
2. Verify these Edge secrets already exist: RESEND_REMINDER_API_KEY, RECOVERY_ALLOWED_EMAILS, RECOVERY_TEST_STUDENT_IDS.
3. For test only: RECOVERY_ALLOWED_EMAILS=fkassoh@monroeu.edu, RECOVERY_TEST_STUDENT_IDS=0308040.
4. Publish reset-password/index.html at https://monroeu.github.io/student/reset-password/ BEFORE triggering a recovery email. This page must be reachable via HTTPS and is already included in allowed redirect URLs.
5. Replace draft student-email-recovery code with index.ts and deploy with JWT verification OFF (endpoint begins unauthenticated). Restriction remains enforced by allowlisted test IDs/emails and database throttle.
6. Request recovery ONLY for test Student ID 0308040. Confirm inbox, click one-time link, change password, sign in again using the original Student ID, verify previously recorded assignments and progress.
7. Rollout to students only after testing, and only after verifying each student's email ownership. Remove test restrictions only with proper enrollment-controlled opt-in verification and abuse protection.
8. Instructor reset remains available as fallback. Existing student-auth-api is unchanged.

Note: recovery email delivery does not mean password reset is complete. The dedicated page must establish a Supabase recovery session before updating password.
