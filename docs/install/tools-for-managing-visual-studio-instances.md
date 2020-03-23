---
title: Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar
titleSuffix: ''
description: İstemci makinelerindeki Visual Studio yüklemelerini algılamak ve yönetmek için kullanabileceğiniz araçlar hakkında bilgi edinin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115039"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar

İstemci makinelerinde Visual Studio yüklemelerini algılamak ve yüklemeleri yönetmek için de kullanabileceğiniz çeşitli araçlar vardır.

## <a name="detecting-existing-visual-studio-instances"></a>Varolan Visual Studio örneklerini algılama

İstemci makinelerinde yüklü Visual Studio örneklerini algılamanıza ve yönetmenize yardımcı olacak çeşitli araçlar kullanıma sunulduk:

* [vswhere](https://github.com/microsoft/vswhere): Visual Studio'da yerleşik olarak bulunan veya belirli bir makinedeki tüm Visual Studio örneklerinin konumunu bulmanıza yardımcı olan ayrı bir dağıtım için kullanılabilir bir çalıştırılabilir.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): Visual Studio'nun yüklü örneklerini tanımlamak için Kurulum Yapılandırma API'sini kullanan PowerShell komut dosyaları.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): Varolan bir yüklemeyi sorgulamak için Kurulum Yapılandırma API'sinin nasıl kullanılacağını gösteren C# ve C++ örnekleri.

Buna ek olarak, [Kurulum Yapılandırma API](<xref:Microsoft.VisualStudio.Setup.Configuration>) Visual Studio örneklerini sorgulamak için kendi yardımcı programları oluşturmak isteyen geliştiriciler için arabirimler sağlar.

## <a name="using-vswhereexe"></a>vswhere.exe kullanma

`vswhere.exe`visual studio otomatik olarak dahil edilir (Visual Studio ile başlayan 2017 sürüm 15.2 ve sonraki sürümleri), ya da [vswhere bültenleri sayfasından](https://github.com/Microsoft/vswhere/releases)indirebilirsiniz. Araç `vswhere -?` hakkında yardım bilgileri almak için kullanın. Örnek olarak, bu komut Visual Studio'nun ürünün önceki sürümleri ve ön sürümler de dahil olmak üzere tüm sürümlerini gösterir ve sonuçları JSON biçiminde verir:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 2017 kurulumu hakkında daha fazla bilgi için [Visual Studio Kurulum Arşivleri'ne](https://devblogs.microsoft.com/setup/tag/vs2017/)bakın.

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio örneği için kayıt defterini düzenleme

Visual Studio'da, kayıt defteri ayarları, Aynı makinede Visual Studio'nun aynı sürümünün birden çok yan yana örneğini etkinleştiren özel bir konumda depolanır.

Bu girişler genel kayıt defterinde depolanmadığı için, kayıt defteri ayarlarında değişiklik yapmak için Kayıt Defteri Düzenleyicisi'ni kullanmak için özel yönergeler vardır:

1. Visual Studio'nun açık bir örneğini zedebilirsiniz, kapatın.

1. Başlat. `regedit.exe`

1. `HKEY_LOCAL_MACHINE` Düğümü seçin.

1. Regedit ana menüsünden **Dosya** > **Yük Kovanı...** seçeneğini belirleyin ve ardından **AppData\Local** klasöründe depolanan özel kayıt defteri dosyasını seçin. Örnek:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>`göz atmak istediğiniz Visual Studio örneğine karşılık gelir.

İzole edilmiş kovanın adı olacak bir kovan adı vermeniz istenecektir. Bunu yaptıktan sonra, oluşturduğunuz yalıtılmış kovan altında kayıt defterine göz atmak gerekir.

> [!IMPORTANT]
> Visual Studio'yu yeniden başlatmadan önce, oluşturduğunuz yalıtılmış kovanı boşaltmanız gerekir. Bunu yapmak için Regedit ana menüsünden **Dosya** > **Boşaltma Kovanı'nı** seçin. (Bunu yapmazsanız, dosya kilitli kalır ve Visual Studio başlatılamaz.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yöneticileri Kılavuzu](visual-studio-administrator-guide.md)
