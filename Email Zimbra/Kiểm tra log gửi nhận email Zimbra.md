# Kiểm tra log gửi/nhận email Zimbra
Việc kiểm tra log gửi nhận của email server zimbra là cần thiết, giúp xác định được một email đã gửi/nhận thành công hay chưa và nếu chưa thành công thì bị dừng ở bước nào và báo lỗi ra sao
- Đường dẫn file log
`/var/log/maillog`
- Chu trình gửi thư => Connect tới email server => MTA kiểm tra địa chỉ người nhận => Kiểm tra qua các rule filter, đánh giá spam, virus => Xếp vào queue => Gửi thư => Xóa khỏi queue => Thông báo `Message accepted for delivery`

```sh
Mar 15 09:16:40 mail postfix/postscreen[9391]: CONNECT from [103.124.94.220]:59578 to [103.124.94.220]:25
Mar 15 09:16:40 mail postfix/postscreen[9391]: ALLOWLISTED [103.124.94.220]:59578
Mar 15 09:16:40 mail postfix/smtpd[9392]: connect from mail.tubui.xyz[103.124.94.220]
Mar 15 09:16:40 mail postfix/smtpd[9392]: NOQUEUE: filter: RCPT from mail.tubui.xyz[103.124.94.220]: <admin@tubui.xyz>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10026; from=<admin@tubui.xyz> to=<tubui16091999@gmail.com> proto=ESMTP helo=<mail.tubui.xyz>
Mar 15 09:16:40 mail postfix/smtpd[9392]: 7663A160D70: client=mail.tubui.xyz[103.124.94.220]
Mar 15 09:16:40 mail postfix/cleanup[9394]: 7663A160D70: message-id=<556380065.11.1647310600386.JavaMail.zimbra@tubui.xyz>
Mar 15 09:16:40 mail postfix/smtpd[9392]: disconnect from mail.tubui.xyz[103.124.94.220] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 15 09:16:40 mail postfix/qmgr[4054]: 7663A160D70: from=<admin@tubui.xyz>, size=1115, nrcpt=1 (queue active)
Mar 15 09:16:40 mail amavis[2526]: (02526-20) ESMTP :10026 /opt/zimbra/data/amavisd/tmp/amavis-20220315T050001-02526-WK1FJfLF: <admin@tubui.xyz> -> <tubui16091999@gmail.com> Received: from mail.tubui.xyz ([127.0.0.1]) by localhost (mail.tubui.xyz [127.0.0.1]) (amavisd-new, port 10026) with ESMTP for <tubui16091999@gmail.com>; Tue, 15 Mar 2022 09:16:40 +0700 (+07)
Mar 15 09:16:40 mail amavis[2526]: (02526-20) Checking: 2mwr_Uo4Q4fX ORIGINATING/MYNETS [103.124.94.220] <admin@tubui.xyz> -> <tubui16091999@gmail.com>
Mar 15 09:16:40 mail postfix/dkimmilter/smtpd[4475]: connect from localhost[127.0.0.1]
Mar 15 09:16:40 mail postfix/dkimmilter/smtpd[4475]: 9B378160D71: client=localhost[127.0.0.1]
Mar 15 09:16:40 mail postfix/cleanup[9394]: 9B378160D71: message-id=<556380065.11.1647310600386.JavaMail.zimbra@tubui.xyz>
Mar 15 09:16:40 mail postfix/qmgr[4054]: 9B378160D71: from=<admin@tubui.xyz>, size=1587, nrcpt=1 (queue active)
Mar 15 09:16:40 mail postfix/dkimmilter/smtpd[4475]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 15 09:16:40 mail amavis[2526]: (02526-20) 2mwr_Uo4Q4fX FWD from <admin@tubui.xyz> -> <tubui16091999@gmail.com>, BODY=7BIT 250 2.0.0 from MTA(smtp:[127.0.0.1]:10030): 250 2.0.0 Ok: queued as 9B378160D71
Mar 15 09:16:40 mail amavis[2526]: (02526-20) Passed CLEAN {RelayedOutbound}, ORIGINATING/MYNETS LOCAL [103.124.94.220]:59578 [103.124.94.220] <admin@tubui.xyz> -> <tubui16091999@gmail.com>, Queue-ID: 7663A160D70, Message-ID: <556380065.11.1647310600386.JavaMail.zimbra@tubui.xyz>, mail_id: 2mwr_Uo4Q4fX, Hits: -, size: 1114, queued_as: 9B378160D71, 223 ms
Mar 15 09:16:40 mail postfix/smtp[9395]: 7663A160D70: to=<tubui16091999@gmail.com>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.26, delays=0.02/0.01/0.01/0.22, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10030): 250 2.0.0 Ok: queued as 9B378160D71)
Mar 15 09:16:40 mail postfix/qmgr[4054]: 7663A160D70: removed
Mar 15 09:16:40 mail amavis[10050]: (10050-10) ESMTP :10032 /opt/zimbra/data/amavisd/tmp/amavis-20220315T072001-10050-zLSlO5H1: <admin@tubui.xyz> -> <tubui16091999@gmail.com> SIZE=1587 Received: from mail.tubui.xyz ([127.0.0.1]) by localhost (mail.tubui.xyz [127.0.0.1]) (amavisd-new, port 10032) with ESMTP for <tubui16091999@gmail.com>; Tue, 15 Mar 2022 09:16:40 +0700 (+07)
Mar 15 09:16:40 mail amavis[10050]: (10050-10) Checking: LTo-eHGIVjxE ORIGINATING_POST/MYNETS [127.0.0.1] <admin@tubui.xyz> -> <tubui16091999@gmail.com>
Mar 15 09:16:42 mail postfix/amavisd/smtpd[4569]: connect from localhost[127.0.0.1]
Mar 15 09:16:42 mail postfix/amavisd/smtpd[4569]: 1EF3E160D70: client=localhost[127.0.0.1]
Mar 15 09:16:42 mail postfix/cleanup[9394]: 1EF3E160D70: message-id=<556380065.11.1647310600386.JavaMail.zimbra@tubui.xyz>
Mar 15 09:16:42 mail postfix/amavisd/smtpd[4569]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 15 09:16:42 mail postfix/qmgr[4054]: 1EF3E160D70: from=<admin@tubui.xyz>, size=2593, nrcpt=1 (queue active)
Mar 15 09:16:42 mail amavis[10050]: (10050-10) LTo-eHGIVjxE FWD from <admin@tubui.xyz> -> <tubui16091999@gmail.com>, BODY=7BIT 250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1EF3E160D70
Mar 15 09:16:42 mail amavis[10050]: (10050-10) Passed CLEAN {RelayedOutbound}, ORIGINATING_POST/MYNETS LOCAL [127.0.0.1]:47596 [103.124.94.220] <admin@tubui.xyz> -> <tubui16091999@gmail.com>, Queue-ID: 9B378160D71, Message-ID: <556380065.11.1647310600386.JavaMail.zimbra@tubui.xyz>, mail_id: LTo-eHGIVjxE, Hits: 4.099, size: 2200, queued_as: 1EF3E160D70, dkim_sd=0E3AF0A4-A377-11EC-9010-6D41164FB587:tubui.xyz, 1503 ms
Mar 15 09:16:42 mail postfix/smtp[9395]: 9B378160D71: to=<tubui16091999@gmail.com>, relay=127.0.0.1[127.0.0.1]:10032, delay=1.6, delays=0.09/0.01/0.01/1.5, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1EF3E160D70)
Mar 15 09:16:42 mail postfix/qmgr[4054]: 9B378160D71: removed
Mar 15 09:16:44 mail postfix/smtp[9402]: 1EF3E160D70: to=<tubui16091999@gmail.com>, relay=gmail-smtp-in.l.google.com[172.217.194.26]:25, delay=2.6, delays=0.11/0.01/1.2/1.2, dsn=2.0.0, status=sent (250 2.0.0 OK  1647310605 d9-20020a631d09000000b0037562967a7fsi16174220pgd.160 - gsmtp)
Mar 15 09:16:44 mail postfix/qmgr[4054]: 1EF3E160D70: removed
```

- Chu trình nhận: Chấp nhận kết nối từ email server gửi => Kiểm tra qua các rule filter, đánh giá spam, virus => Xếp vào queue => Nhận thư và xóa khỏi queue => Thông báo nhận thư `250 2.1.5 Delivery OK`

```sh
Mar 15 09:25:06 mail postfix/amavisd/smtpd[11562]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 commands=4
Mar 15 09:25:08 mail postfix/postscreen[13794]: CONNECT from [209.85.210.173]:44683 to [103.124.94.220]:25
Mar 15 09:25:14 mail postfix/postscreen[13794]: PASS NEW [209.85.210.173]:44683
Mar 15 09:25:14 mail postfix/smtpd[13829]: connect from mail-pf1-f173.google.com[209.85.210.173]
Mar 15 09:25:15 mail postfix/smtpd[13829]: Anonymous TLS connection established from mail-pf1-f173.google.com[209.85.210.173]: TLSv1.3 with cipher TLS_AES_128_GCM_SHA256 (128/128 bits) key-exchange X25519 server-signature RSA-PSS (2048 bits) server-digest SHA256
Mar 15 09:25:15 mail postfix/smtpd[13829]: NOQUEUE: filter: RCPT from mail-pf1-f173.google.com[209.85.210.173]: <tubui16091999@gmail.com>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10026; from=<tubui16091999@gmail.com> to=<admin@tubui.xyz> proto=ESMTP helo=<mail-pf1-f173.google.com>
Mar 15 09:25:15 mail postfix/smtpd[13829]: warning: permit_tls_clientcerts is requested, but "smtpd_tls_ask_ccert = no"
Mar 15 09:25:15 mail postfix/smtpd[13829]: NOQUEUE: filter: RCPT from mail-pf1-f173.google.com[209.85.210.173]: <tubui16091999@gmail.com>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10024; from=<tubui16091999@gmail.com> to=<admin@tubui.xyz> proto=ESMTP helo=<mail-pf1-f173.google.com>
Mar 15 09:25:15 mail postfix/smtpd[13829]: E511C160D75: client=mail-pf1-f173.google.com[209.85.210.173]
Mar 15 09:25:15 mail postfix/cleanup[13947]: E511C160D75: message-id=<CAJVV1btF7DS2PPVxuC8hY12W8N89_YXa5rP6S1enx4ckcW5_vw@mail.gmail.com>
Mar 15 09:25:15 mail postfix/qmgr[4054]: E511C160D75: from=<tubui16091999@gmail.com>, size=2569, nrcpt=1 (queue active)
Mar 15 09:25:16 mail amavis[11463]: (11463-01) ESMTP :10024 /opt/zimbra/data/amavisd/tmp/amavis-20220315T092515-11463-hc9Wg8UR: <tubui16091999@gmail.com> -> <admin@tubui.xyz> SIZE=2569 Received: from mail.tubui.xyz ([127.0.0.1]) by localhost (mail.tubui.xyz [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <admin@tubui.xyz>; Tue, 15 Mar 2022 09:25:15 +0700 (+07)
Mar 15 09:25:16 mail amavis[11463]: (11463-01) Checking: wJaUl1M0hUI2 [209.85.210.173] <tubui16091999@gmail.com> -> <admin@tubui.xyz>
Mar 15 09:25:16 mail postfix/amavisd/smtpd[13951]: connect from localhost[127.0.0.1]
Mar 15 09:25:16 mail postfix/amavisd/smtpd[13951]: 30056160D76: client=localhost[127.0.0.1]
Mar 15 09:25:16 mail postfix/cleanup[13947]: 30056160D76: message-id=<CAJVV1btF7DS2PPVxuC8hY12W8N89_YXa5rP6S1enx4ckcW5_vw@mail.gmail.com>
Mar 15 09:25:16 mail postfix/qmgr[4054]: 30056160D76: from=<tubui16091999@gmail.com>, size=3224, nrcpt=1 (queue active)
Mar 15 09:25:16 mail amavis[11463]: (11463-01) wJaUl1M0hUI2 FWD from <tubui16091999@gmail.com> -> <admin@tubui.xyz>, BODY=7BIT 250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 30056160D76
Mar 15 09:25:16 mail amavis[11463]: (11463-01) Passed CLEAN {RelayedInbound}, [209.85.210.173]:44683 [209.85.210.173] <tubui16091999@gmail.com> -> <admin@tubui.xyz>, Queue-ID: E511C160D75, Message-ID: <CAJVV1btF7DS2PPVxuC8hY12W8N89_YXa5rP6S1enx4ckcW5_vw@mail.gmail.com>, mail_id: wJaUl1M0hUI2, Hits: -, size: 2569, queued_as: 30056160D76, dkim_sd=20210112:gmail.com, 260 ms
Mar 15 09:25:16 mail postfix/smtp[13948]: E511C160D75: to=<admin@tubui.xyz>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.28, delays=0.01/0/0.02/0.25, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 30056160D76)
Mar 15 09:25:16 mail postfix/qmgr[4054]: E511C160D75: removed
Mar 15 09:25:16 mail amavis[11463]: (11463-01) extra modules loaded: Mozilla/CA.pm
Mar 15 09:25:16 mail postfix/smtpd[13829]: disconnect from mail-pf1-f173.google.com[209.85.210.173] ehlo=2 starttls=1 mail=1 rcpt=1 bdat=1 quit=1 commands=7
Mar 15 09:25:18 mail postfix/lmtp[13952]: 30056160D76: to=<admin@tubui.xyz>, relay=mail.tubui.xyz[103.124.94.220]:7025, delay=2.3, delays=0.01/0/2.2/0.1, dsn=2.1.5, status=sent (250 2.1.5 Delivery OK)
Mar 15 09:25:18 mail postfix/qmgr[4054]: 30056160D76: removed
```

