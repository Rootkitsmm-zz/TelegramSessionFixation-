#The Bug
based on our researches on (https://github.com/telegramdesktop/tdesktop)[Telegram Desktop application], we found a Session Fixation bug, which could lead to full account hijack, alongside with bypassing two-step verification and logging in without any sessions getting recorded.

#Preface
Telegram Desktop application does not generate a new token for login when an invalid token(not logged in) is there in the tdata folder.
So that if we put an invalid token inside a tdata folder in someone's Telegram folder, our invalid token get's used for login, and we'll be able to hijack his account, without creating any sessions on his account, and off course bypassing two-step verification.

#Description
The Session Fixation bug appears on the app because "when a session is closed (or when there is an invalid token there in the tdata), the token assigned to it does get revoked, but doesn't get replaced by a new one, so it gets re-used for the next login".

So that if you do the following steps, you can demo the bug:

1. Get a copy of Telegram Desktop application.
2. Login using one of your accounts to Telegram.
3. Copy the tdata folder (or the whole Telegram folder (just tdata matters)) to somewhere else.
4. Kill the session you opened in step 2 on your other device; so that both Telegram folders now are logged out.
5. Use one of those Telegram folder copies to login to another Telegram account.
6. Now if you open the other folder, it will open the same session as the other one.
It IS a bug for sure, and it's (https://www.owasp.org/index.php/Session_fixation)[Session Fixation].
