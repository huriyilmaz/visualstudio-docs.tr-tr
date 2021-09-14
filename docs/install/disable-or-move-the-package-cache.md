---
title: Paket önbelleğini devre dışı bırakma veya taşıma
description: Dağıtımlar için paket önbelleğini devre dışı bırakmayı, etkinleştirmeyi veya taşımayı Visual Studio öğrenin.
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
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8a16be51c603befac88f1576a2cd42fed5b75d3c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627075"
---
# <a name="disable-or-move-the-package-cache"></a>Paket önbelleğini devre dışı bırakma veya taşıma

Paket önbelleği, İnternet bağlantınız olmadığınız durumlarda bir Visual Studio veya diğer ilgili ürünleri onarmanız gereksin diye yüklü paketlerin kaynağını sağlar. Ancak bazı sürücüler veya sistem ayarlamaları ile bu paketlerin hepsini tutmak istemeyebilirsiniz.
Yükleyici gerektiğinde bunları indirir, bu nedenle disk alanını kaydetmek veya kurtarmak için paket önbelleğini devre dışı indirebilirsiniz veya taşıyabilirsiniz.

## <a name="disable-the-package-cache"></a>Paket önbelleğini devre dışı bırakma

Yükleme, değiştirme veya Visual Studio veya diğer ürünleri yeni yükleyiciyle onarmadan önce yükleyiciyi yükleyiciye geçiş `--nocache` ile başlatabilirsiniz.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Herhangi bir üründe yapılan tüm işlem, bu ürün için mevcut paketleri kaldırır ve yüklendikten sonra paketlerden tasarruf etmekten kaçınacak. Gerekli olan tüm Visual Studio ve paketleri değiştirir veya onarsanız, bunlar yüklendikten sonra otomatik olarak indirilir ve kaldırılır.

Önbelleği yeniden etkinleştirmek için bunun yerine `--cache` geçişlerini kullanın. Yalnızca gerekli olan paketler önbelleğe alınacak, bu nedenle tüm paketleri geri yüklemeniz gerekirse ağ bağlantısını Visual Studio önce bu paketleri onarmanız gerekir.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Ayrıca kayıt defteri ilkesi' `KeepDownloadedPayloads` [ni, verileri yüklemeden,](set-defaults-for-enterprise-deployments.md) değiştirmeden veya onarmadan önce önbelleği devre dışı Visual Studio.

## <a name="move-the-package-cache"></a>Paket önbelleğini taşıma

Yaygın bir sistem yapılandırması, Windows, program ikili dosyaları ve daha fazlası gibi geliştirme ihtiyaçları için daha büyük bir sabit diske (veya daha fazla) sahip bir SSD'ye yüklenmiş bir diske sahip olmaktır. Çevrimdışı çalışmak istiyorsanız, bunun yerine paket önbelleğini taşıyabilirsiniz.

Şu anda bunu yalnızca kayıt defteri ilkenizi yüklemeden, değiştirmeden veya onarmadan önce `CachePath` [](set-defaults-for-enterprise-deployments.md) Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Kurumsal dağıtımlar için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
