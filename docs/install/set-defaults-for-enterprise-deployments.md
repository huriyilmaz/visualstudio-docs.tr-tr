---
title: Kurumsal dağıtımlar için Varsayılanları Ayarla
description: Visual Studio 'nun kurumsal dağıtımları için etki alanı ilkeleri ve diğer yapılandırma işlemleri hakkında bilgi edinin.
ms.date: 03/30/2019
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d03912eecd7b3cfa3563fc095453fee3ddf9b163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114288"
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

| **Ad** | **Tür** | **Varsayılanını** | **Açıklama** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\microsoft\visualstudio\paketleri | Paket bildirimlerinin ve isteğe bağlı olarak yüklerinin depolandığı dizin. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Yüklendiklerinde bile paket yüklerini saklayın. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakmak, tamir ettiğiniz veya değiştirdiğiniz örnek için önbelleğe alınmış tüm paket yüklerini kaldırır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `SharedInstallationPath` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Visual Studio örneklerinin sürümleri arasında paylaşılan bazı paketlerin yüklü olduğu dizin. Değeri dilediğiniz zaman değiştirebilirsiniz, ancak gelecekteki yüklemeleri etkiler. Eski konuma yüklenmiş olan tüm ürünler taşınmamalıdır veya düzgün çalışmayabilir. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Kurulumun tüm yüklü Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmasını engelleyin. Değeri dilediğiniz zaman değiştirebilirsiniz. |

> [!IMPORTANT]
> `CachePath`Herhangi bir yüklemeden sonra kayıt defteri ilkesini değiştirirseniz, mevcut paket önbelleğini yeni konuma taşımanız ve `SYSTEM` `Administrators` tam denetime sahip olmak ve okuma erişimi olması için güvenli olduğundan emin olmanız gerekir `Everyone` .
> Mevcut önbelleğin taşınamaması veya güvenliğinin sağlanması gelecekteki yüklemelerde sorunlara neden olabilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](install-visual-studio.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
