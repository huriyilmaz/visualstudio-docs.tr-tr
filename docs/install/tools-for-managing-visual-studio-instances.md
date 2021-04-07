---
title: Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar
titleSuffix: ''
description: İstemci makinelerde Visual Studio yüklemelerini algılamak ve yönetmek için kullanabileceğiniz araçlar hakkında bilgi edinin.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b6b641081c9b969cadd2c9517967adb8cc4cb1e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547446"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar

İstemci makinelerde Visual Studio yüklemelerini algılamak ve yüklemeleri yönetmek için kullanabileceğiniz çeşitli araçlar vardır.

## <a name="detecting-existing-visual-studio-instances"></a>Mevcut Visual Studio örnekleri algılanıyor

Aşağıdaki araçlar ve yardımcı programlar, istemci makinelerde yüklü Visual Studio örneklerini tespit etmenize ve yönetmenize yardımcı olur:

* [**vswhere**](https://github.com/microsoft/vswhere): belirli bir makinedeki tüm Visual Studio örneklerinin konumunu bulmanıza yardımcı olan, Visual Studio 'da yerleşik olan veya ayrı bir dağıtım için kullanılabilen bir çalıştırılabilir dosya.
* [**Vssetup. PowerShell**](https://github.com/microsoft/vssetup.powershell): Visual Studio 'nun yüklü örneklerini tanımlamak Için kurulum yapılandırma API 'sini kullanan PowerShell betikleri.
* [**Vs-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): C# ve C++ örnekleri, var olan bir yüklemeyi sorgulamak Için kurulum yapılandırma API 'sini nasıl kullanacağınızı gösterir.
* [**Windows Yönetim Araçları (WMI)**](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page): Visual Studio örnek bilgileri, Visual studio sınıf MSFT_VSInstance aracılığıyla sorgulanabilir. 
* [**Kurulum yapılandırması API 'si**](<xref:Microsoft.VisualStudio.Setup.Configuration>) , Visual Studio örnekleri için kendi yardımcı programlarını derlemek isteyen geliştiriciler için arabirimler sağlar.
* [**Microsoft uç noktası Configuration Manager yazılım envanteri**](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): istemci cihazlarındaki Visual Studio örnekleri hakkında bilgi toplamak için kullanılabilir. 

## <a name="using-vswhereexe"></a>vswhere.exe kullanma

`vswhere.exe` , Visual Studio 2017 ve sonraki sürümlere otomatik olarak dahil edilir veya [vswhere yayınları sayfasından](https://github.com/Microsoft/vswhere/releases)indirebilirsiniz. `vswhere -?`Araçla ilgili yardım bilgilerini almak için kullanın. Örneğin, bu komut, ürünün önceki sürümleri ve paylaşmamız dahil olmak üzere Visual Studio 'nun tüm sürümlerini gösterir ve sonuçları JSON biçiminde verir:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Windows Yönetim Araçları kullanma (WMI)

Makinede Visual Studio Istemci algılayıcısı yardımcı programı yüklüyse, WMI kullanarak Visual Studio örnek bilgileri için sorgulama yapabilirsiniz. Visual Studio Istemci algılayıcısı yardımcı programı, 12 Mayıs 2020 tarihinde veya sonrasında yayınlanan her Visual Studio 2017 ve Visual Studio 2019 güncelleştirmesiyle varsayılan olarak yüklenir. Ayrıca, bağımsız olarak yüklemek istiyorsanız [Microsoft Update kataloğunda](https://catalog.update.microsoft.com/) de kullanılabilir.  Visual Studio örnek bilgilerini döndürmek için yardımcı programın nasıl kullanılacağına ilişkin bir örnek için, PowerShell 'i istemci makinede yönetici olarak açın ve şu komutu yazın:

```cmd
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Microsoft uç noktası Configuration Manager kullanma 

[Microsoft uç nokta Configuration Manager yazılım envanteri](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) özellikleri, istemci cihazlarındaki Visual Studio örnekleri hakkındaki bilgileri sorgulamak ve toplamak için kullanılabilir. Örneğin, aşağıdaki sorgu, tüm yüklü Visual Studio 2017 ve 2019 örnekleri için, Visual Studio 'nun yüklü olduğu görünen adı, sürümü ve cihaz adını döndürür: 

```WQL 
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
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

1. Regedit ana menüsünde **Dosya**  >  **yükleme Hive...** öğesini seçin ve ardından **Appdata\Local** klasöründe depolanan özel kayıt defteri dosyasını seçin. Örnek:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` gezinmek istediğiniz Visual Studio örneğine karşılık gelir.

Yalıtılmış Hive adı haline gelen bir Hive adı sağlamanız istenir. Bunu yaptıktan sonra, oluşturduğunuz yalıtılmış Hive altında kayıt defterine gözatabilmelisiniz.

> [!IMPORTANT]
> Visual Studio 'Yu yeniden başlatmaya başlamadan önce, oluşturduğunuz yalıtılmış Hive 'yi kaldırmanız gerekir. Bunu yapmak için,   >  Regedit ana menüsünden dosya **kaldırma Hive** ' yi seçin. (Bunu yapmazsanız, dosya kilitli kalır ve Visual Studio başlayamaz.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
