---
title: Paket önbelleğini devre dışı bırakma veya taşıma
description: Visual Studio dağıtımları için paket önbelleğini devre dışı bırakma, etkinleştirme veya taşıma hakkında bilgi edinin.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e328bf8420f9cc7cf207ede6b6447ed291b77745
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949460"
---
# <a name="disable-or-move-the-package-cache"></a>Paket önbelleğini devre dışı bırakma veya taşıma

Paket önbelleği, Internet bağlantınızın olmadığı durumlarda Visual Studio 'Yu veya diğer ilgili ürünleri onarmanız gerektiğinde yüklü paketlerin bir kaynağını sağlar. Ancak bazı sürücülerle veya sistem kümesiyle birlikte, tüm bu paketlerin etrafında tutulması istemeyebilirsiniz.
Yükleyici, gerektiğinde bunları indirir, bu nedenle disk alanını kaydetmek veya kurtarmak istiyorsanız, paket önbelleğini devre dışı bırakabilir veya taşıyabilirsiniz.

## <a name="disable-the-package-cache"></a>Paket önbelleğini devre dışı bırak

Yeni yükleyiciyle Visual Studio 'Yu veya diğer ürünleri yüklemeden, değiştirmeden veya onarmadan önce, yükleyiciyi `--nocache` yükleyiciye geçiş ile başlatabilirsiniz.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Herhangi bir üründe yaptığınız herhangi bir işlem, söz konusu ürüne ait mevcut paketleri kaldırır ve yüklendikten sonra herhangi bir paketi kaydetmekten kaçınır. Visual Studio 'Yu değiştirir veya onarır ve paketler gerekliyse, bunlar otomatik olarak indirilir ve yüklendikten sonra kaldırılır.

Önbelleği yeniden etkinleştirmek istiyorsanız, `--cache` bunun yerine geçiş yapın. Yalnızca gerekli paketler önbelleğe alınır, bu nedenle tüm paketleri geri yüklemeniz gerekiyorsa, ağınızdan bağlantıyı kesmeden önce Visual Studio 'Yu onarmanız gerekir.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Ayrıca, `KeepDownloadedPayloads` Visual Studio 'yu yüklemeden, değiştirmeden veya onarmadan önce önbelleğin devre dışı bırakılması için [kayıt defteri ilkesini](set-defaults-for-enterprise-deployments.md) ayarlayabilirsiniz.

## <a name="move-the-package-cache"></a>Paket önbelleğini taşıma

Ortak sistem yapılandırması, Windows 'un kaynak kodu, program ikilileri ve daha fazlası gibi geliştirme ihtiyaçları için daha büyük bir sabit disk (veya daha fazla) ile bir SSD üzerinde yüklü olmasını sağlar. Çevrimdışı çalışmak istiyorsanız bunun yerine paket önbelleğini taşıyabilirsiniz.

Şu anda bunu, `CachePath` Visual Studio 'yu yüklemeden, değiştirmeden veya onarmadan önce [kayıt defteri ilkesini](set-defaults-for-enterprise-deployments.md) ayarlarsanız yapabilirsiniz.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Kurumsal dağıtımlar için Varsayılanları Ayarla](set-defaults-for-enterprise-deployments.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
