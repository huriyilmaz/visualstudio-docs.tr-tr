---
title: Kurumsal dağıtımlar için Varsayılanları Ayarla
description: Visual Studio 'nun kurumsal dağıtımları için etki alanı ilkeleri ve diğer yapılandırma işlemleri hakkında bilgi edinin.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d3d6f658e3d24f3c82737c0c457323b9d4eb4b6
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547472"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio kuruluş dağıtımları için varsayılanları ayarlama

Visual Studio 'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayabilirsiniz. Bu ilkeler, yeni yükleyici için geneldir ve şunları etkiler:

- Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği yer
- Paketlerin önbelleğe alındığı yer
- Tüm paketlerin önbelleğe alınıp alınmayacağını belirtir

[Komut satırı seçeneklerini](use-command-line-parameters-to-install-visual-studio.md)kullanarak bu ilkelerin bazılarını ayarlayabilir, makinenizde kayıt defteri değerlerini ayarlayabilir veya hatta bir kuruluş genelinde Grup İlkesi kullanarak dağıtabilirsiniz.

## <a name="registry-keys"></a>Kayıt defteri anahtarları

Kurumsal Varsayılanları ayarlayabileceğiniz, grup ilkesi veya doğrudan kayıt defterindeki denetimini etkinleştirmek için çeşitli konumlar vardır. Visual Studio, herhangi bir kurumsal ilkenin ayarlanmış olup olmadığını görmek için ardışık olarak görünür; aşağıdaki sırada bir ilke değeri bulunduğunda, kalan anahtarlar yok sayılır.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 bit işletim sistemlerinde)

> [!IMPORTANT]
> `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`Anahtarı ayarlamayın ve bunun yerine diğer anahtarlardan birini ayarlarsanız, 64 bit işletim sistemlerinde her iki anahtarı da ayarlamanız gerekir. Bu sorun, gelecekteki bir ürün güncelleştirmesinde giderilmiştir.

Bazı kayıt defteri değerleri, henüz ayarlanmamışsa ilk kez otomatik olarak ayarlanır. Bu uygulama, sonraki yüklemelerinin aynı değerleri kullanmasını sağlar. Bu değerler ikinci kayıt defteri anahtarında depolanır `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` .

Aşağıdaki kayıt defteri değerlerini ayarlayabilirsiniz:

::: moniker range="vs-2017"
| **Ad** | **Tür** | **Varsayılanını** | **Açıklama** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\microsoft\visualstudio\paketleri | Paket bildirimlerinin ve isteğe bağlı olarak yüklerinin depolandığı dizin. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Yüklendiklerinde bile paket yüklerini saklayın. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakmak, tamir ettiğiniz veya değiştirdiğiniz örnek için önbelleğe alınmış tüm paket yüklerini kaldırır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `SharedInstallationPath` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Visual Studio örneklerinin sürümleri arasında paylaşılan bazı paketlerin yüklü olduğu dizin. Değeri dilediğiniz zaman değiştirebilirsiniz, ancak gelecekteki yüklemeleri etkiler. Eski konuma yüklenmiş olan tüm ürünler taşınmamalıdır veya düzgün çalışmayabilir. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Kurulumun tüm yüklü Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmasını engelleyin. Değeri dilediğiniz zaman değiştirebilirsiniz. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | İstemci bilgisayara yönetici güncelleştirmelerinin uygulanmasını sağlar. Bu değer eksikse veya 0 olarak ayarlandıysa, yönetici güncelleştirmeleri engellenir. Bu değer, yönetim kullanımı içindir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Kullanıcının, yönetici güncelleştirmelerini Visual Studio 'ya almak istediğini belirtir. Kayıt defteri değerinin yokluğu veya 0 kümesi değeri, Visual Studio kullanıcısının Visual Studio 'ya yönetici güncelleştirmelerini almak istediği anlamına gelir. Bu geliştirici kullanıcısına yöneliktir (istemci makinesinde yönetici izinleri varsa). Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | Yönetim güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için bkz. [yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
::: moniker-end

::: moniker range="vs-2019"
| **Ad** | **Tür** | **Varsayılanını** | **Açıklama** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\microsoft\visualstudio\paketleri | Paket bildirimlerinin ve isteğe bağlı olarak yüklerinin depolandığı dizin. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Yüklendiklerinde bile paket yüklerini saklayın. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakmak, tamir ettiğiniz veya değiştirdiğiniz örnek için önbelleğe alınmış tüm paket yüklerini kaldırır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `SharedInstallationPath` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Visual Studio örneklerinin sürümleri arasında paylaşılan bazı paketlerin yüklü olduğu dizin. Değeri dilediğiniz zaman değiştirebilirsiniz, ancak gelecekteki yüklemeleri etkiler. Eski konuma yüklenmiş olan tüm ürünler taşınmamalıdır veya düzgün çalışmayabilir. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Kurulumun tüm yüklü Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmasını engelleyin. Değeri dilediğiniz zaman değiştirebilirsiniz. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | İstemci bilgisayara yönetici güncelleştirmelerinin uygulanmasını sağlar. Bu değer eksikse veya 0 olarak ayarlandıysa, yönetici güncelleştirmeleri engellenir. Bu değer, yönetim kullanımı içindir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Kullanıcının, yönetici güncelleştirmelerini Visual Studio 'ya almak istediğini belirtir. Kayıt defteri değerinin yokluğu veya 0 kümesi değeri, Visual Studio kullanıcısının Visual Studio 'ya yönetici güncelleştirmelerini almak istediği anlamına gelir. Bu geliştirici kullanıcısına yöneliktir (istemci makinesinde yönetici izinleri varsa). Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | Yönetim güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için bkz. [yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
| `BaselineStickinessVersions2019` | `REG_SZ` veya `REG_EXPAND_SZ` | `ALL` veya `16.4.0,16.7.0,16.9.0` | Güncelleştirmeleri veren sürümler, belirtilen hizmet temelleri üzerinde kalır. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options) sayfası. | 
::: moniker-end

> [!IMPORTANT]
> `CachePath`Herhangi bir yüklemeden sonra kayıt defteri ilkesini değiştirirseniz, mevcut paket önbelleğini yeni konuma taşımanız ve `SYSTEM` `Administrators` tam denetime sahip olmak ve okuma erişimi olması için güvenli olduğundan emin olmanız gerekir `Everyone` .
> Mevcut önbelleğin taşınamaması veya güvenliğinin sağlanması gelecekteki yüklemelerde sorunlara neden olabilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](install-visual-studio.md)
- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
