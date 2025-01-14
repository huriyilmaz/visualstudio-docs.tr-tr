---
title: Paket önbelleğini devre dışı bırakma veya taşıma
description: Dağıtımlar için paket önbelleğini devre dışı bırakmayı, etkinleştirmeyi veya taşımayı Visual Studio öğrenin.
ms.date: 04/14/2017
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
ms.openlocfilehash: 5a32d27cda2b414a8b62357db03efe2980dd98e7
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453988"
---
# <a name="disable-or-move-the-package-cache"></a>Paket önbelleğini devre dışı bırakma veya taşıma

Paket önbelleği, İnternet bağlantınız olmadığınız durumlarda bir Visual Studio veya diğer ilgili ürünleri onarmanız gereksin diye yüklü paketlerin kaynağını sağlar. Ancak bazı sürücüler veya sistem ayarlamaları ile bu paketlerin hepsini tutmak istemeyebilirsiniz.
Yükleyici gerektiğinde bunları indirir, bu nedenle disk alanını kaydetmek veya kurtarmak için paket önbelleğini devre dışı indirebilirsiniz veya taşıyabilirsiniz.

## <a name="disable-the-package-cache"></a>Paket önbelleğini devre dışı bırakma

Yeni yükleyici ile bir veya Visual Studio ürünleri yüklemeden, değiştirmeden veya onarmadan önce yükleyiciyi `--nocache` yükleyiciye geçişle başlatabilirsiniz.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Herhangi bir üründe yapılan tüm işlem, bu ürün için mevcut paketleri kaldırır ve yüklendikten sonra paket kaydetmeyi önler. Gerekli olan tüm Visual Studio ve paketleri değiştirir veya onarsanız, bunlar yüklendikten sonra otomatik olarak indirilir ve kaldırılır.

Önbelleği yeniden etkinleştirmek için bunun yerine `--cache` geçişlerini kullanın. Yalnızca gerekli olan paketler önbelleğe alınacak, bu nedenle tüm paketleri geri yüklemeniz gerekirse ağ bağlantısını Visual Studio önce bu paketleri onarmanız gerekir.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Ayrıca kayıt defteri `KeepDownloadedPayloads` [ilkesini, verileri yüklemeden,](set-defaults-for-enterprise-deployments.md) değiştirmeden veya onarmadan önce önbelleği devre dışı Visual Studio.

## <a name="move-the-package-cache"></a>Paket önbelleğini taşıma

Yaygın bir sistem yapılandırması, Windows, program ikili dosyaları ve daha fazlası gibi geliştirme ihtiyaçları için daha büyük bir sabit diske (veya daha fazla) sahip bir SSD'ye yüklü olmasıdır. Çevrimdışı çalışmak istiyorsanız bunun yerine paket önbelleğini taşıyabilirsiniz.

Şu anda bunu yalnızca kayıt defteri ilkenizi yüklemeden, değiştirmeden veya onarmadan `CachePath` [](set-defaults-for-enterprise-deployments.md) önce Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Kurumsal dağıtımlar için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
