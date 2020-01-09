---
title: Kuruluş dağıtımları için varsayılanları ayarlama
description: Etki alanı ilkeleri ve diğer Visual Studio kuruluş dağıtımları için yapılandırma işlemleri hakkında bilgi edinin.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 305b0398550a64722f6029a3d50082e6397643cb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594532"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio kuruluş dağıtımları için varsayılanları ayarlama

Visual Studio dağıtımını etkileyen kayıt defteri ilkeler ayarlayabilir. Bu ilkeler için yeni yükleyici geneldir ve etkiler:

- Diğer sürümleri veya örnekleri ile paylaşılan bazı paketler yüklendiği
- Paketlerin önbelleğe alındığı
- Olup tüm paketlerin önbelleğe alındığı

Bazı kullanarak bu ilkeleri ayarlayabilirsiniz [komut satırı seçenekleri](use-command-line-parameters-to-install-visual-studio.md)makinenizde kayıt defteri değerlerini ayarlayın veya hatta bir kuruluş genelindeki Grup İlkesi kullanarak bunları dağıtın.

## <a name="registry-keys"></a>Kayıt defteri anahtarları

Kurumsal Varsayılanları, Grup İlkesi kullanılarak veya doğrudan kayıt defterinde kendi denetimini etkinleştirmek için ayarlayabileceğiniz birkaç konum vardır. Visual Studio, Kurumsal ilkelerle ayarladığınız durumlarda görmek için sırayla arar; bir ilke değeri sırayla bulunduktan hemen sonra kalan anahtarlar yoksayılır.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64-bit işletim sistemlerinde)

> [!IMPORTANT]
> Ayarlanmamış olması halinde `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` anahtarı ve bunun yerine ayarlanmış diğer anahtarlar biri, her iki diğer anahtarlar 64-bit işletim sistemlerinde ayarlamalıdır. Gelecekteki ürün güncelleştirmede bu sorun giderilmiştir.

Bazı kayıt defteri değerlerini, bunların kullanılan değilse zaten ayarlanmış ilk kez otomatik olarak ayarlanır. Bu uygulama, sonraki yüklemeler aynı değerleri kullanmanızı sağlar. Bu değerler ikinci kayıt defteri anahtarında depolanır `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Aşağıdaki kayıt defteri değerlerini ayarlayabilirsiniz:

| **Ad** | **Türü** | **Default** | **Açıklama** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Burada paket bildirimlerini dizini ve isteğe bağlı, yükü depolanır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1\. | Hatta yüklendikten sonra paket yüklerini tutun. Değer dilediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakma örneği onarmak veya değiştirmek için herhangi bir önbelleğe alınan paket yüklerini kaldırır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası. |
| `SharedInstallationPath` | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramFiles (x86) %\Microsoft Visual Studio\Shared | Visual Studio örneklerini sürümleri arasında paylaşılan bazı paketler yüklendiği dizin. Değeri dilediğiniz zaman değiştirebilirsiniz, ancak gelecekteki yüklemeleri etkiler. Eski konuma yüklenmiş olan tüm ürünler taşınmamalıdır veya düzgün çalışmayabilir. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1\. | Kurulumun tüm yüklü Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmasını engelleyin. Değer dilediğiniz zaman değiştirebilirsiniz. |

> [!IMPORTANT]
> Herhangi bir yüklemeden sonra `CachePath` kayıt defteri ilkesini değiştirirseniz, mevcut paket önbelleğini yeni konuma taşımanız ve `SYSTEM` ve `Administrators` tam denetime sahip olduğundan ve `Everyone` okuma erişimine sahip olması için güvenli olduğundan emin olmanız gerekir.
> Mevcut önbelleğin taşınamaması veya güvenliğinin sağlanması gelecekteki yüklemelerde sorunlara neden olabilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleyin](install-visual-studio.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
