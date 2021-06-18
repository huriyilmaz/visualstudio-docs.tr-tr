---
title: Kurumsal dağıtımlar için varsayılanları ayarlama
description: Etki alanı ilkeleri ve kurumsal dağıtımlar için diğer yapılandırma işlemleri hakkında bilgi Visual Studio.
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cc88e6ffe91b111626fa76057742233527bf203f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306910"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio kuruluş dağıtımları için varsayılanları ayarlama

Uygulama dağıtımını etkileyen kayıt defteri ilkelerini Visual Studio. Bu ilkeler makine için geneldir ve şunları etkiler:

- Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklü olduğu yer
- Paketlerin önbelleğe alınıp alınıp alınıp
- Yönetici güncelleştirmelerinin uygulanması gerekir

Komut satırı seçeneklerini kullanarak bu ilkelerden [bazılarını](use-command-line-parameters-to-install-visual-studio.md)ayarlama, makinenize kayıt defteri değerleri ayarlama ve hatta bunları kuruluş genelinde grup ilkesi dağıtabilirsiniz.

## <a name="registry-keys"></a>Kayıt defteri anahtarları

Denetimlerini doğrudan kayıt defteri üzerinden veya doğrudan kayıt defterinde etkinleştirmek için kurumsal varsayılanları grup ilkesi çeşitli konumlar vardır. Visual Studio kurumsal ilkelerin ayar olup olduğunu görmek için sırayla bir görünüme sahip olur; bir ilke değeri aşağıdaki sırayla keşfedilsin, kalan anahtarlar yoksayılır.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 bit işletim sistemlerinde)

Henüz ayarlanmazsa, bazı kayıt defteri değerleri ilk kez kullanıldıkları zaman otomatik olarak ayarlanır. Bu uygulama, sonraki yüklemelerin aynı değerleri kullanmalarını sağlar. Bu değerler ikinci kayıt defteri anahtarında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` depolanır.

Aşağıdaki kayıt defteri değerlerini ayarlayın:

::: moniker range="vs-2017"

| **Ad**                      | **Tür**                    | **Varsayılan**                                         | **Açıklama**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                   | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Paket bildirimlerinin ve isteğe bağlı olarak yüklerin depolandığı dizin. Daha fazla bilgi için [bkz. Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`      | `REG_DWORD`                 | 1                                                   | Yüklendikten sonra bile paket yüklerini tutabilirsiniz. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkenin devre dışı bırakılması, onarım veya değiştirme işlemi için önbelleğe alınmış paket yüklerini kaldırır. Daha fazla bilgi için [bkz. Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                             |
| `SharedInstallationPath`      | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared  | Uygulama örneklerinin sürümleri arasında paylaşılan bazı paketlerin Visual Studio yüklenir. Değeri istediğiniz zaman değiştirebilirsiniz, ancak bu yalnızca gelecekteki yüklemeleri etkiler. Eski konuma zaten yüklenmiş olan ürünler taşınmamış olmalı veya düzgün çalışmayabilir.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`  | `REG_DWORD`                 | 0                                                   | Kurulumun tüm yüklü ürün ve ürünler için güncelleştirmeleri otomatik Visual Studio önle. Değeri dilediğiniz zaman değiştirebilirsiniz.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled` | `REG_DWORD`                 | 0                                                   | Yönetici güncelleştirmelerinin istemci bilgisayara uygulanmasına izin verir. Bu değer eksikse veya 0 olarak ayarlanırsa yönetici güncelleştirmeleri engellenir. Bu değer yönetimsel kullanım içindir. Daha fazla bilgi için [bkz. Yönetici Güncelleştirmelerini Etkinleştirme.](enabling-administrator-updates.md)                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`  | `REG_DWORD`                 | 0                                                   | Kullanıcının kullanıcıya yönetici güncelleştirmeleri almak Visual Studio. Kayıt defteri değerinin olmaması veya 0 değerinin ayarlanmış olmaması, Visual Studio kullanıcının kayıt defterine yönetici güncelleştirmeleri Visual Studio. Bu, geliştirici kullanıcıya (istemci makinede yönetici izinlerine sahipse) içindir. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md#understanding-configuration-options) |
| `UpdateConfigurationFile`     | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Yönetim Güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesini yapılandırma yöntemleri.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)                                                                                                                                                                                                                                             |

::: moniker-end

::: moniker range="vs-2019"

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Paket bildirimlerinin ve isteğe bağlı olarak yüklerin depolandığı dizin. Daha fazla bilgi için [bkz. Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | Yüklendikten sonra bile paket yüklerini tutabilirsiniz. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkenin devre dışı bırakılması, onarım veya değiştirme işlemi için önbelleğe alınmış paket yüklerini kaldırır. Daha fazla bilgi için [bkz. Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared  | Uygulama örneklerinin sürümleri arasında paylaşılan bazı paketlerin Visual Studio yüklenir. Değeri istediğiniz zaman değiştirebilirsiniz, ancak bu yalnızca gelecekteki yüklemeleri etkiler. Eski konuma zaten yüklenmiş olan ürünler taşınmamış olmalı veya düzgün çalışmayabilir.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | Kurulumun tüm yüklü ürün ve ürünler için güncelleştirmeleri otomatik Visual Studio önle. Değeri dilediğiniz zaman değiştirebilirsiniz.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | Yönetici güncelleştirmelerinin istemci bilgisayara uygulanmasına izin verir. Bu değer eksikse veya 0 olarak ayarlanırsa yönetici güncelleştirmeleri engellenir. Bu değer yönetimsel kullanım içindir. Daha fazla bilgi için [bkz. Yönetici Güncelleştirmelerini Etkinleştirme.](enabling-administrator-updates.md)                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının kullanıcıya yönetici güncelleştirmeleri almak Visual Studio. Kayıt defteri değerinin olmaması veya 0 değerinin ayarlanmış olmaması, Visual Studio kullanıcının kayıt defterine yönetici güncelleştirmeleri Visual Studio. Bu, geliştirici kullanıcıya (istemci makinede yönetici izinlerine sahipse) içindir. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md#understanding-configuration-options) |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Yönetim Güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesini yapılandırma yöntemleri.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` veya `REG_EXPAND_SZ` | `16.7.0`                                            | İstemcinin kalması gereken hizmet temeli ikincil sürümü. Daha fazla bilgi için yönetici [güncelleştirmelerini uygulama sayfasına](../install/applying-administrator-updates.md#understanding-configuration-options) bakın.                                                                                                                                                                                                                                                    |

::: moniker-end

::: moniker range=">=vs-2022"

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Paket bildirimlerinin ve isteğe bağlı olarak yüklerin depolandığı dizin. Daha fazla bilgi için [bkz. Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | Yüklendikten sonra bile paket yüklerini tutabilirsiniz. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkenin devre dışı bırakılması, onararak veya değiştirerek örneğin önbelleğe alınmış paket yüklerini kaldırır. Daha fazla bilgi için bkz. [Paket önbelleği sayfasını devre dışı bırakma veya](disable-or-move-the-package-cache.md) taşıma.                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramFiles%\Microsoft Visual Studio\Shared       | Uygulama örneklerinin sürümleri arasında paylaşılan bazı paketlerin Visual Studio yüklenir. Değeri istediğiniz zaman değiştirebilirsiniz, ancak bu yalnızca gelecekteki yüklemeleri etkiler. Eski konuma zaten yüklenmiş olan ürünler taşınmamış olmalı veya düzgün çalışmayabilir.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | Kurulumun tüm yüklü ürün ve ürünler için güncelleştirmeleri otomatik Visual Studio önle. Değeri dilediğiniz zaman değiştirebilirsiniz.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | Yönetici güncelleştirmelerinin istemci bilgisayara uygulanmasına izin verir. Bu değer eksikse veya 0 olarak ayarlanırsa yönetici güncelleştirmeleri engellenir. Bu değer yönetimsel kullanım içindir. Daha fazla bilgi için [bkz. Yönetici Güncelleştirmelerini Etkinleştirme.](enabling-administrator-updates.md)                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının kullanıcıya yönetici güncelleştirmeleri almak Visual Studio. Kayıt defteri değerinin veya 0'ın ayarlanmış bir değerinin olmaması, Visual Studio kullanıcının kayıt defterine yönetici güncelleştirmeleri Visual Studio. Bu, geliştirici kullanıcıya (istemci makinede yönetici izinlerine sahipse) için. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md#understanding-configuration-options) |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Yönetim Güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesini yapılandırma yöntemleri.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` veya `REG_EXPAND_SZ` | `16.7.0`                                            | İstemcinin kalması gereken hizmet temeli ikincil sürümü. Daha fazla bilgi için yönetici [güncelleştirmelerini uygulama sayfasına](../install/applying-administrator-updates.md#understanding-configuration-options) bakın.                                                                                                                                                                                                                                                    |

::: moniker-end

> [!IMPORTANT]
> Herhangi bir yüklemeden sonra kayıt defteri ilkesi değiştirirseniz, var olan paket önbelleğini yeni konuma taşımalı ve tam denetime sahip ve Okuma erişimine sahip olacak şekilde güvenli olduğundan `CachePath` `SYSTEM` emin `Administrators` `Everyone` olun.
> Mevcut önbelleğin taşınamama veya güvenli hale getirmenin başarısız olması, gelecekteki yüklemelerde sorunlara neden olabilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](install-visual-studio.md)
- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
