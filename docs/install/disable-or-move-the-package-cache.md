---
title: Paket önbelleğini devre dışı bırakma veya taşıma
description: Visual Studio dağıtımları için paket önbelleğini nasıl devre dışı kakacağını, etkinleştireceğinizi veya taşıyacağını öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f38757931cb22e9072571d96b015f37882dd500
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114798"
---
# <a name="disable-or-move-the-package-cache"></a>Paket önbelleğini devre dışı bırakma veya taşıma

Paket önbelleği, Internet bağlantınız olmayan durumlarda Visual Studio'yu veya diğer ilgili ürünleri onarmanız gerektiğinde yüklü paketlerin kaynağını sağlar. Ancak, bazı sürücüler veya sistem kurulumları ile, tüm bu paketleri etrafında tutmak istemeyebilirsiniz.
Yükleyici gerektiğinde bunları karşıdan yükler, böylece disk alanını kaydetmek veya kurtarmak istiyorsanız, paket önbelleğini devre dışı bırakabilir veya taşıyabilirsiniz.

## <a name="disable-the-package-cache"></a>Paket önbelleğini devre dışı

Visual Studio veya diğer ürünleri yeni yükleyiciyle yüklemeden, değiştirmeden veya onarmadan önce, yükleyiciyi yükleyiciye `--nocache` geçişle başlatabilirsiniz.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Herhangi bir ürünüzerinde yapacağınız herhangi bir işlem, o ürün için mevcut paketleri kaldırır ve yüklendikten sonra herhangi bir paket tenedir. Visual Studio'da değişiklik veya onarım yapılırsanız ve paketler yüklendikten sonra otomatik olarak indirilir ve kaldırılır.

Önbelleği yeniden etkinleştirmek istiyorsanız, `--cache` bunun yerine geçirin. Yalnızca gerekli olan paketler önbelleğe alınır, bu nedenle tüm paketleri geri yüklemeniz gerekiyorsa, ağınızın bağlantısını kesmeden önce Visual Studio'u onarmalısınız.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Ayrıca, Visual `KeepDownloadedPayloads` Studio'yu yüklemeden, değiştirmeden veya onarmadan önce önbelleği devre dışı bırakacak [şekilde kayıt defteri ilkesini](set-defaults-for-enterprise-deployments.md) ayarlayabilirsiniz.

## <a name="move-the-package-cache"></a>Paket önbelleğini taşıma

Ortak bir sistem yapılandırması, Windows'un kaynak kodu, program ikilileri ve daha fazlası gibi geliştirme gereksinimleri için daha büyük bir sabit diske (veya daha fazlasına) sahip bir SSD'ye yüklenmesidir. Çevrimdışı çalışmak istiyorsanız, bunun yerine paket önbelleğini taşıyabilirsiniz.

Şu anda, bunu yalnızca Visual `CachePath` Studio'yu yüklemeden, değiştirmeden veya onarmadan önce [kayıt defteri ilkesini](set-defaults-for-enterprise-deployments.md) ayarlarsanız yapabilirsiniz.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Kurumsal dağıtımlar için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
