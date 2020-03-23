---
title: Kurumsal dağıtımlar için varsayılanları ayarlama
description: Visual Studio'nun kurumsal dağıtımları için etki alanı ilkeleri ve diğer yapılandırma işlemleri hakkında bilgi edinin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114288"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio kuruluş dağıtımları için varsayılanları ayarlama

Visual Studio'nun dağıtımını etkileyen kayıt defteri ilkeleri ayarlayabilirsiniz. Bu ilkeler yeni yükleyici için geneldir ve aşağıdakileri etkiler:

- Diğer sürümlerle veya örneklerle paylaşılan bazı paketlerin yüklendiği
- Paketlerin önbelleğe alındığü yerler
- Tüm paketlerin önbelleğe alıp almadığı

Bu ilkelerden bazılarını komut [satırı seçeneklerini](use-command-line-parameters-to-install-visual-studio.md)kullanarak ayarlayabilir, kayıt defteri değerlerini makinenizde ayarlayabilir ve hatta grup ilkesini kullanarak bir kuruluş genelinde dağıtabilirsiniz.

## <a name="registry-keys"></a>Kayıt defteri anahtarları

Grup İlkesi aracılığıyla veya doğrudan kayıt defterinde denetimlerini etkinleştirmek için kurumsal varsayılanları ayarlayabileceğiniz birkaç konum vardır. Visual Studio, herhangi bir kurumsal ilke ayarlıp ayarlandığını görmek için sırayla bakar; Aşağıdaki sırada bir ilke değeri bulunduğunda, kalan anahtarlar yoksayılır.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(64 bit işletim sistemlerinde)

> [!IMPORTANT]
> `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` Anahtarı ayarlamaz ve bunun yerine diğer tuşlardan birini ayarlarsanız, diğer her iki anahtarı da 64 bit işletim sistemlerine ayarlamanız gerekir. Bu sorun gelecekteki bir ürün güncelleştirmesinde giderilir.

Bazı kayıt defteri değerleri, önceden ayarlanmadıkları takdirde ilk kez kullanıldıklarında otomatik olarak ayarlanır. Bu uygulama, sonraki yüklemelerin aynı değerleri kullanmasını sağlar. Bu değerler ikinci kayıt defteri anahtarında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`depolanır.

Aşağıdaki kayıt defteri değerlerini ayarlayabilirsiniz:

| **Adı** | **Tür** | **Varsayılan** | **Açıklama** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Paketleri | Paketin ve isteğe bağlı olarak yüklerin depolandığı dizin. Daha fazla bilgi için Devre Dışı Bırakma sayfasına bakın [veya paket önbelleği sayfasını taşıyın.](disable-or-move-the-package-cache.md) |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Paket yüklerini yüklendikten sonra bile saklayın. Değeri istediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakmak, onarma veya değiştirme örneği için önbelleğe alınmış paket yüklerini kaldırır. Daha fazla bilgi için Devre Dışı Bırakma sayfasına bakın [veya paket önbelleği sayfasını taşıyın.](disable-or-move-the-package-cache.md) |
| `SharedInstallationPath` | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Paylaşılan | Visual Studio örneklerinin sürümleri arasında paylaşılan bazı paketlerin yüklendiği dizin. Değeri istediğiniz zaman değiştirebilirsiniz, ancak yalnızca gelecekteki yüklemeleri etkiler. Eski konuma zaten yüklenmiş olan ürünler taşınmamalıdır veya doğru çalışmayabilir. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Yüklü tüm Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmeyi engelleyin. Değeri istediğiniz zaman değiştirebilirsiniz. |

> [!IMPORTANT]
> Herhangi bir `CachePath` yüklemeden sonra kayıt defteri ilkesini değiştirirseniz, varolan paket önbelleğini yeni konuma taşımanız ve güvenli olduğundan `SYSTEM` emin olmalısınız ve `Administrators` Tam Denetime sahip ve Read erişimi `Everyone` ne olur.
> Varolan önbelleğin taşınamaması veya güvenliğinin sağlanamaması gelecekteki yüklemelerle ilgili sorunlara neden olabilir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yükleme](install-visual-studio.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
