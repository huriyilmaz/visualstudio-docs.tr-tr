---
title: Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar
titleSuffix: ''
description: İstemci makinelerde Visual Studio yüklemelerini algılamak ve yönetmek için kullanabileceğiniz araçlar hakkında bilgi edinin.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115039"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar

İstemci makinelerde Visual Studio yüklemelerini algılamak ve yüklemeleri de yönetmek için kullanabileceğiniz çeşitli araçlar vardır.

## <a name="detecting-existing-visual-studio-instances"></a>Mevcut Visual Studio örnekleri algılanıyor

İstemci makinelerde yüklü Visual Studio örneklerini tespit etmenize ve yönetmenize yardımcı olacak çeşitli araçlar yaptık:

* [vswhere](https://github.com/microsoft/vswhere): belirli bir makinedeki tüm Visual Studio örneklerinin konumunu bulmanıza yardımcı olan, Visual Studio 'da yerleşik olan veya ayrı bir dağıtım için kullanılabilen bir çalıştırılabilir dosya.
* [Vssetup. PowerShell](https://github.com/microsoft/vssetup.powershell): Visual Studio 'nun yüklü örneklerini tanımlamak Için kurulum yapılandırma API 'sini kullanan PowerShell betikleri.
* [Vs-Setup-Samples](https://github.com/microsoft/vs-setup-samples): C# ve C++ örnekleri, var olan bir yüklemeyi sorgulamak Için kurulum yapılandırma API 'sini nasıl kullanacağınızı gösterir.

Ayrıca, [Kurulum yapılandırması API 'si](<xref:Microsoft.VisualStudio.Setup.Configuration>) , Visual Studio örnekleri için kendi yardımcı programlarını oluşturmak isteyen geliştiriciler için arabirimler sağlar.

## <a name="using-vswhereexe"></a>vswhere.exe kullanma

`vswhere.exe` Visual Studio 'Ya (Visual Studio 2017 sürüm 15,2 ve sonraki sürümlerle başlayarak) otomatik olarak dahildir veya [vswhere yayınları sayfasından](https://github.com/Microsoft/vswhere/releases)indirebilirsiniz. `vswhere -?`Araçla ilgili yardım bilgilerini almak için kullanın. Örnek olarak, bu komut, Visual Studio 'nun önceki ve paylaşmamız sürümleri de dahil olmak üzere tüm Visual Studio sürümlerini gösterir ve sonuçları JSON biçiminde verir:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 2017 yüklemesi hakkında daha fazla bilgi için bkz. [Visual Studio Kurulum arşivleri](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio örneği için kayıt defterini Düzenle

Visual Studio 'da, kayıt defteri ayarları aynı makinede aynı Visual Studio sürümünün birden çok yan yana örneğini sağlayan özel bir konumda depolanır.

Bu girişler genel kayıt defterinde depolanmadığından, kayıt defteri ayarlarında değişiklik yapmak için kayıt defteri Düzenleyicisi 'ni kullanmaya yönelik özel yönergeler vardır:

1. Visual Studio 'nun açık bir örneğine sahipseniz kapatın.

1. Başlatın `regedit.exe` .

1. Düğümü seçin `HKEY_LOCAL_MACHINE` .

1. Regedit ana menüsünde **Dosya**  >  **yükleme Hive...** öğesini seçin ve ardından **Appdata\Local** klasöründe depolanan özel kayıt defteri dosyasını seçin. Örneğin:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` gezinmek istediğiniz Visual Studio örneğine karşılık gelir.

Yalıtılmış Hive adı haline gelen bir Hive adı sağlamanız istenir. Bunu yaptıktan sonra, oluşturduğunuz yalıtılmış Hive altında kayıt defterine gözatabilmelisiniz.

> [!IMPORTANT]
> Visual Studio 'Yu yeniden başlatmaya başlamadan önce, oluşturduğunuz yalıtılmış Hive 'yi kaldırmanız gerekir. Bunu yapmak için, **File**  >  Regedit ana menüsünden dosya**kaldırma Hive** ' yi seçin. (Bunu yapmazsanız, dosya kilitli kalır ve Visual Studio başlayamaz.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yöneticileri Kılavuzu](visual-studio-administrator-guide.md)
