---
title: 2 要素認証クレデンシャルをなくした際のアカウントの回復
intro: 2 要素認証の認証情報にアクセスできなくなった場合、リカバリコードまたはその他のリカバリ方法を使用して、アカウントへのアクセスを回復できます。
redirect_from:
  - /articles/recovering-your-account-if-you-lost-your-2fa-credentials/
  - /articles/authenticating-with-an-account-recovery-token/
  - /articles/recovering-your-account-if-you-lose-your-2fa-credentials
  - /github/authenticating-to-github/recovering-your-account-if-you-lose-your-2fa-credentials
  - /github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa/recovering-your-account-if-you-lose-your-2fa-credentials
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
topics:
  - 2FA
shortTitle: Recover an account with 2FA
---

{% ifversion fpt or ghec %}

{% warning %}

**警告**: {% data reusables.two_fa.support-may-not-help %}

{% endwarning %}

{% endif %}

## 2 要素認証リカバリコードを使用する

リカバリコードのうち 1 つを使用して、アカウントへのエントリを自動で再取得します。 リカバリコード は、多くの場合、パスワードマネージャまたはご使用のコンピュータのダウンロードフォルダに保存されています。 リカバリコードのデフォルトのファイル名は `github-recovery-codes.txt` です。 リカバリコードの詳しい情報については「[2 要素認証リカバリ方法を設定する](/articles/configuring-two-factor-authentication-recovery-methods#downloading-your-two-factor-authentication-recovery-codes)」を参照してください。

{% data reusables.two_fa.username-password %}{% ifversion fpt or ghec %}
2. [Having Problems?] の下で、[**Enter a two-factor recovery code**] をクリックします。 ![Link to use a recovery code](/assets/images/help/2fa/2fa-recovery-code-link.png){% else %}
2. [2FA] ページで、[Don't have your phone?] の下にある [**Enter a two-factor recovery code**] をクリックします。 ![Link to use a recovery code](/assets/images/help/2fa/2fa_recovery_dialog_box.png){% endif %}
3. リカバリコードを 1 つ入力して、[**Verify**] をクリックします。 ![リカバリコードを入力するフィールドおよび [Verify] ボタン](/assets/images/help/2fa/2fa-type-verify-recovery-code.png)

{% ifversion fpt or ghec %}
## フォールバック番号による認証

プライマリ TOTP アプリケーションや電話番号へのアクセスをなくした場合でも、 フォールバック番号に送信されている 2 要素認証コードを入力すれば、アカウントへのアクセスを自動で再取得できます。
{% endif %}

## セキュリティキーによる認証

セキュリティキーを使用して 2 要素認証を設定した場合は、セキュリティキーをセカンダリ認証方式として使用すると、アカウントへのアクセスを自動で再取得できます。 詳しい情報については、「[2 要素認証を設定する](/articles/configuring-two-factor-authentication#configuring-two-factor-authentication-using-a-security-key)」を参照してください。

{% ifversion fpt or ghec %}
## 検証済みのデバイス、SSHトークン、または個人アクセストークンを使用した認証

If you know your {% data variables.product.product_name %} password but don't have the two-factor authentication credentials or your two-factor authentication recovery codes, you can have a one-time password sent to your verified email address to begin the verification process and regain access to your account.

{% note %}

**注釈**: セキュリティ上の理由から、ワンタイムパスワードで認証してアカウントへのアクセスを回復するには、3〜5 営業日かかる場合があります。 この間に送信された追加のリクエストはレビューされません。

{% endnote %}

2要素認証の認証情報または 2 要素認証のリカバリコードを使用して、3〜5 日間の待機期間中にいつでもアカウントへのアクセスを回復できます。

1. 認証を求めるためにユーザ名とパスワードを入力してください。 If you do not know your {% data variables.product.product_name %} password, you will not be able to generate a one-time password.
2. [Having Problems?] の下で、[**Can't access your two factor device or valid recovery codes?**] をクリックします。 ![2fa デバイスまたはリカバリコードがない場合のリンク](/assets/images/help/2fa/no-access-link.png)
3. [**I understand, get started**] をクリックして、認証設定のリセットをリクエストします。 ![認証設定のリセットボタン](/assets/images/help/2fa/reset-auth-settings.png)
4. [**Send one-time password**] をクリックして、アカウントに関連付けられているすべてのメールアドレスにワンタイムパスワードを送信します。 ![ワンタイムパスワードの送信ボタン](/assets/images/help/2fa/send-one-time-password.png)
5. [One-time password] の下で、送信されたリカバリメール{% data variables.product.prodname_dotcom %}の一時パスワードを入力します。 ![ワンタイムパスワードフィールド](/assets/images/help/2fa/one-time-password-field.png)
6. [**Verify email address**] をクリックします。
7. 別の検証要素を選択します。
    - 以前に現在のデバイスを使用してこのアカウントにログインしたことがあり、検証にそのデバイスを使用する場合は、[**Verify with this device**] をクリックします。
    - 以前にこのアカウントで SSH キーを設定しており、検証にその SSH キーを使用する場合は、[** SSH key**] をクリックします。
    - 以前に個人アクセストークンを設定しており、検証にその個人アクセストークンを使用する場合は、[**Personal access token**] をクリックします。 ![代替検証ボタン](/assets/images/help/2fa/alt-verifications.png)
8. {% data variables.contact.github_support %}のメンバーがリクエストをレビューし、3〜5 営業日以内にメールでお知らせします。 リクエストが承認されると、アカウントリカバリプロセスを完了するためのリンクが送信されます。 リクエストが拒否された場合、追加の質問がある場合のサポートへの問い合わせ方法がメールに記載されます。

## アカウントリカバリトークンによる認証

{% warning %}

**Warning:** Account recovery tokens are deprecated and will be disabled on **December 1st, 2021**. Please ensure you have configured other two-factor recovery methods. For more information, see "[Configuring two-factor authentication recovery methods](/articles/configuring-two-factor-authentication-recovery-methods)."

{% endwarning %}

If you lose access to the two-factor authentication methods for your account on {% data variables.product.product_location %}, you can retrieve your account recovery token from a partner recovery provider and ask {% data variables.product.prodname_dotcom %} Support to review it.

2 要素認証方式やリカバリコードへのアクセスがない場合でも、Recovery Accounts Elsewhere を使用して Facebook にアカウントリカバリトークンを格納してあれば、トークンを使用してアカウントへのアクセスを再取得できる可能性があります。

アカウントへのアクセスを回復できない場合は、ワンタイムパスワードを生成してアクセスを回復します。 詳しい情報については、「[検証済みのデバイス、SSHトークン、または個人アクセストークンを使用した認証](#authenticating-with-a-verified-device-ssh-token-or-personal-access-token)」を参照してください。

{% warning %}

**警告:**
- アカウントリカバリトークンを再取得する前に、[2 要素認証コード](/articles/accessing-github-using-two-factor-authentication)か 2 要素認証リカバリコードを使用してアカウントへのアクセスの再取得を試行してください。 詳しい情報については[2FA クレデンシャルをなくした際のアカウントの回復](/articles/recovering-your-account-if-you-lose-your-2fa-credentials)を参照してください。

{% endwarning %}

1. Facebook で、[セキュリティ設定](https://www.facebook.com/settings?tab=security)に移動し、[**Recovery Accounts Elsewhere**] をクリックします。 ![Facebook のセキュリティ設定ページと Recovery Accounts Elsewhere リンク](/assets/images/help/settings/security-facebook-security-settings-page.png)
2. Click the recovery token associated with your account on {% data variables.product.product_location %}. ![Facebook に格納されているリカバリトークンのリスト](/assets/images/help/settings/security-github-rae-token-on-facebook.png)
3. アカウントリカバリトークンを引き換えるため、[**Recover This Account**] をクリックします。 新しいウィンドウが開き、{% data variables.product.product_name %}に戻ります。 ![リカバリトークンについての情報を表示するモーダルボックスおよび [Recover This Account] ボタン](/assets/images/help/settings/security-recover-account-facebook.png)
4. {% data variables.contact.contact_support %} に連絡して、アカウントリカバリトークンはレビューの準備ができていることを知らせます。
{% endif %}

## 参考リンク

- [2 要素認証について](/articles/about-two-factor-authentication)
- [2 要素認証の設定](/articles/configuring-two-factor-authentication)
- [2 要素認証のリカバリ方法の設定](/articles/configuring-two-factor-authentication-recovery-methods)
- [2 要素認証を使用して {% data variables.product.prodname_dotcom %} にアクセスする](/articles/accessing-github-using-two-factor-authentication)
