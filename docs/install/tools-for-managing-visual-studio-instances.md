---
title: Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar
titleSuffix: ''
description: Algılama ve Visual Studio yüklemeleri istemci makinelerinde yönetmek için kullanabileceğiniz araçları hakkında bilgi edinin.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d6e46c95584cb3732d6339a02f6098976f2bab85
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115039"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar

Visual Studio yüklemeleri istemci makinelerinde algılamaya ve yüklemelerini çok yönetmek için kullanabileceğiniz birçok araç vardır.

## <a name="detecting-existing-visual-studio-instances"></a>Var olan algılama Visual Studio Örnekleri

Kullanılabilir algılamak ve istemci makinelerde yüklü Visual Studio örneklerini yönetmenize yardımcı olacak birkaç araç yaptık:

* [vswhere](https://github.com/microsoft/vswhere): belirli bir makinedeki tüm Visual Studio örneklerinin konumunu bulmanıza yardımcı olan, Visual Studio 'da yerleşik olan veya ayrı bir dağıtım için kullanılabilen bir çalıştırılabilir dosya.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): PowerShell betikleri, Visual Studio'nun yüklü örnekleri belirlemek için Kurulum yapılandırması API'yi kullanın.
* [VS ayarlama örnekleri](https://github.com/microsoft/vs-setup-samples): Kurulum yapılandırma API'si var olan bir yüklemesini sorgulamak için nasıl kullanılacağını gösteren C# ve C++ örnekleri.

Ayrıca, [kurulum yapılandırma API'si](<xref:Microsoft.VisualStudio.Setup.Configuration>) interrogating Visual Studio örnekleri için kendi yardımcı programlar oluşturmak isteyen geliştiriciler için arabirim sağlar.

## <a name="using-vswhereexe"></a>Vswhere.exe kullanma

`vswhere.exe`, Visual Studio 'Ya (Visual Studio 2017 sürüm 15,2 ve sonraki sürümlerle başlayarak) otomatik olarak eklenir veya [vswhere yayınları sayfasından](https://github.com/Microsoft/vswhere/releases)indirebilirsiniz. Kullanım `vswhere -?` aracı hakkında Yardım bilgilerini almak için. Örnek olarak, bu komut, Visual Studio 'nun önceki ve paylaşmamız sürümleri de dahil olmak üzere tüm Visual Studio sürümlerini gösterir ve sonuçları JSON biçiminde verir:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 2017 yüklemesi hakkında daha fazla bilgi için bkz. [Visual Studio Kurulum arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio örneği için kayıt defterini düzenleme

Visual Studio 'da, kayıt defteri ayarları aynı makinede aynı Visual Studio sürümünün birden çok yan yana örneğini sağlayan özel bir konumda depolanır.

Bu girişler genel kayıt defterinde depolanmaz gibi kayıt defteri ayarlarında değişiklik yapmak için Kayıt Defteri Düzenleyicisi'ni kullanarak yönelik özel yönergeler vardır:

1. Visual Studio 'nun açık bir örneğine sahipseniz kapatın.

1. Başlangıç `regedit.exe`.

1. Seçin `HKEY_LOCAL_MACHINE` düğümü.

1. Regedit ana menüsünde **dosya** > **Hive yükle...** öğesini seçin ve ardından **Appdata\Local** klasöründe depolanan özel kayıt defteri dosyasını seçin. Örneğin:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` gözatmak istediğiniz Visual Studio örneğine karşılık gelir.

Yalıtılmış, hive adı haline gelir bir hive adı sağlamanız istenir. Bunu yaptıktan sonra oluşturduğunuz yalıtılmış hive altındaki kayıt defterine Gözat olmalıdır.

> [!IMPORTANT]
> Visual Studio yeniden başlamadan önce sizin oluşturduğunuz yalıtılmış kovanını gerekir. Bunu yapmak için, regedit ana menüsünden **dosya** > **kaldırma Hive** ' yi seçin. (Bunu yapmazsanız, dosyanın kilitli kalır ve Visual Studio başlatmanız mümkün olmayacaktır.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yöneticiler Kılavuzu](visual-studio-administrator-guide.md)
