---
title: 为设备配置密码扫描
shortTitle: 配置密码扫描
intro: '您可以为 {% data variables.product.product_location %} 启用、配置和禁用 {% data variables.product.prodname_secret_scanning %}。 {% data variables.product.prodname_secret_scanning_caps %} 允许用户扫描代码以寻找意外泄露的密码。'
product: '{% data reusables.gated-features.secret-scanning %}'
miniTocMaxHeadingLevel: 3
redirect_from:
  - /admin/configuration/configuring-secret-scanning-for-your-appliance
versions:
  ghes: '*'
type: how_to
topics:
  - Advanced Security
  - Enterprise
  - Secret scanning
  - Security
---

{% data reusables.secret-scanning.beta %}

## 关于 {% data variables.product.prodname_secret_scanning %}

{% data reusables.secret-scanning.about-secret-scanning %} 更多信息请参阅“[关于 {% data variables.product.prodname_secret_scanning %}](/github/administering-a-repository/about-secret-scanning)”。

## {% data variables.product.prodname_secret_scanning %} 的前提条件


- [SSSE3](https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-optimization-manual.pdf#G3.1106470)（补充流式传输 SIMD 扩展 3）CPU 标志需要在运行 {% data variables.product.product_location %} 的 VM/KVM 上启用。

- {% data variables.product.prodname_GH_advanced_security %} 的许可{% ifversion ghes > 3.0 %}（请参阅“[关于 {% data variables.product.prodname_GH_advanced_security %} 的计费](/billing/managing-billing-for-github-advanced-security/about-billing-for-github-advanced-security)”）{% endif %}

- 在管理控制台中启用的 {% data variables.product.prodname_secret_scanning_caps %}（请参阅“[为企业启用 {% data variables.product.prodname_GH_advanced_security %}](/admin/advanced-security/enabling-github-advanced-security-for-your-enterprise)”）

## 检查您的 vCPU 上的 SSSE3 标志的支持

SSSE3 指令集是必需的，因为 {% data variables.product.prodname_secret_scanning %} 利用硬件加速模式匹配来查找提交给 {% data variables.product.prodname_dotcom %} 仓库的潜在凭据。 大多数现代 CPU 都启用了 SSSE3。 您可以检查您的 {% data variables.product.prodname_ghe_server %} 实例的可用 vCPU 是否启用了 SSSE3。

1. 连接到 {% data variables.product.prodname_ghe_server %} 实例的管理 shell。 更多信息请参阅“[访问管理 shell (SSH)](/admin/configuration/accessing-the-administrative-shell-ssh)。”
2. 输入以下命令：

```shell
grep -iE '^flags.*ssse3' /proc/cpuinfo >/dev/null | echo $?
```

如果返回值 `0`，则意味着 SSSE3 标志可用并且已启用。 您现在可以为 {% data variables.product.product_location %} 启用 {% data variables.product.prodname_secret_scanning %}。 更多信息请参阅下面的“[启用 {% data variables.product.prodname_secret_scanning %}](#enabling-secret-scanning)”。

如果不返回 `0`，则 SSSE3 未在您的 VM/KVM 上启用。 您需要参考硬件/虚拟机监控程序的文档，以了解如何启用该标志，或者如何使其可用于访客 VM。

### 检查您是否拥有 {% data variables.product.prodname_advanced_security %} 许可

{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.management-console %}
1. 检查在左侧边栏是否有 {% ifversion ghes < 3.2 %} **{% data variables.product.prodname_advanced_security %}**{% else %}个 **安全**{% endif %}入口。
{% ifversion ghes < 3.2 %}
   ![高级安全侧边栏](/assets/images/enterprise/management-console/sidebar-advanced-security.png)
{% else %}
   ![安全侧边栏](/assets/images/enterprise/3.2/management-console/sidebar-security.png)
{% endif %}

{% data reusables.enterprise_management_console.advanced-security-license %}

## 启用 {% data variables.product.prodname_secret_scanning %}

{% data reusables.enterprise_management_console.enable-disable-security-features %}

{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.management-console %}
{% data reusables.enterprise_management_console.advanced-security-tab %}
1. 在“{% ifversion ghes < 3.2 %}{% data variables.product.prodname_advanced_security %}{% else %}安全{% endif %}”下，点击 **{% data variables.product.prodname_secret_scanning_caps %}**。 ![用于启用或禁用 {% data variables.product.prodname_secret_scanning %} 的复选框](/assets/images/enterprise/management-console/enable-secret-scanning-checkbox.png)
{% data reusables.enterprise_management_console.save-settings %}

## 禁用 {% data variables.product.prodname_secret_scanning %}

{% data reusables.enterprise_management_console.enable-disable-security-features %}

{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.management-console %}
{% data reusables.enterprise_management_console.advanced-security-tab %}
1. 在“{% ifversion ghes < 3.2 %}{% data variables.product.prodname_advanced_security %}{% else %}安全{% endif %}”下，取消选择 **{% data variables.product.prodname_secret_scanning_caps %}**。 ![用于启用或禁用 {% data variables.product.prodname_secret_scanning %} 的复选框](/assets/images/enterprise/management-console/secret-scanning-disable.png)
{% data reusables.enterprise_management_console.save-settings %}
