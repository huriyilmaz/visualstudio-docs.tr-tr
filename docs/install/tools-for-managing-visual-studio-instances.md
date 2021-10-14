---
title: Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar
titleSuffix: ''
description: İstemci makinelerde yüklemeleri algılamak ve yönetmek için Visual Studio araçları öğrenin.
ms.date: 04/06/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2865d117d3379f0d07b8bb6fb4c7631e51059b70
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972316"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar

İstemci makinelerde yüklemeleri algılamak ve Visual Studio yönetmek için kullanabileceğiniz çeşitli araçlar vardır.

## <a name="detecting-existing-visual-studio-instances"></a>Mevcut Visual Studio algılama

Aşağıdaki araçlar ve yardımcı programlar, istemci makinelerde yüklü Visual Studio ve yönetmenize yardımcı olur:

* [**vswhere**](https://github.com/microsoft/vswhere): belirli bir makinede Visual Studio veya ayrı dağıtım için kullanılabilir olan, yerleşik olarak bulunan ve tüm Visual Studio bir yürütülebilir dosyadır.
* [**VSSetup.PowerShell:**](https://github.com/microsoft/vssetup.powershell)Kurulum Yapılandırma API'sini kullanan PowerShell betikleri, uygulamanın yüklü Visual Studio.
* [**VS-Setup-Samples:**](https://github.com/microsoft/vs-setup-samples)Mevcut bir yüklemeyi sorgulamak için Kurulum Yapılandırma API'sini kullanmayı gösteren C# ve C++ örnekleri.
* [**Windows Yönetim Araçları (WMI)**](/windows/win32/wmisdk/wmi-start-page): Visual Studio bilgileri, Visual Studio sınıfı MSFT_VSInstance.
* Kurulum [**Yapılandırma API'si,**](<xref:Microsoft.VisualStudio.Setup.Configuration>) örnekleri sorgulamak için kendi yardımcı programlarını oluşturmak isteyen geliştiricilere Visual Studio sağlar.
* [**Microsoft Endpoint Configuration Manager envanteri:**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory)istemci cihazlardaki örnek Visual Studio bilgi toplamak için kullanılabilir.

## <a name="using-vswhereexe"></a>vswhere.exe

`vswhere.exe`, 2017 Visual Studio ve sonraki sürümlere otomatik olarak dahil edilir veya [vswhere sürümler sayfasından indirebilirsiniz.](https://github.com/Microsoft/vswhere/releases) Araç `vswhere -?` hakkında yardım bilgileri almak için kullanın. Örneğin, bu komut ürünün önceki sürümleri ve Visual Studio dahil olmak üzere tüm yayınlarını gösterir ve sonuçları JSON biçiminde verir:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Windows Yönetim Araçları'nın (WMI) kullanımı

Makinede Visual Studio İstemci Algılayıcısı Yardımcı Programı yüklüyse, WMI kullanarak Visual Studio örnek bilgilerini sorguabilirsiniz. Visual Studio Client Detector Utility varsayılan olarak 12 Mayıs 2020 veya sonrasında yayımlanan tüm Visual Studio 2017, Visual Studio 2019 ve Visual Studio 2022 güncelleştirmeleriyle birlikte yüklenir. Ayrıca, bağımsız olarak [yüklemek Microsoft Update Katalog'da](https://catalog.update.microsoft.com/) da kullanılabilir.  Örnek bilgilerini geri almak için yardımcı programını kullanma Visual Studio, PowerShell'i istemci makinede yönetici olarak açın ve aşağıdaki komutu yazın:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager kullanma

[Microsoft Endpoint Configuration Manager envanteri özellikleri,](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) istemci cihazlardaki örnek örnekleri hakkında Visual Studio ve toplamak için kullanılabilir. Örneğin, aşağıdaki sorgu tüm yüklü Visual Studio 2017 ve 2019 örnekleri için görünen adı, sürümü ve Visual Studio adını verir:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
```

::: moniker range="vs-2017"

> [!TIP]
> 2017 yüklemesi Visual Studio daha fazla bilgi için [bkz. Visual Studio Kurulum Arşivleri.](https://devblogs.microsoft.com/setup/tag/vs2017/)

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Bir örnek için kayıt Visual Studio düzenleme

Bu Visual Studio kayıt defteri ayarları, aynı makinede aynı sürümün birden çok yan yana örneğini sağlayan Visual Studio bir konumda depolanır.

Bu girişler genel kayıt defterinde depolanmaz, kayıt defteri ayarlarında değişiklik yapmak için Kayıt Defteri Düzenleyicisi'ni kullanmaya ilişkin özel yönergeler vardır:

1. Açık bir örnek varsa Visual Studio kapatın.

1. 'i `regedit.exe` başlatma.

1. Düğümü `HKEY_LOCAL_MACHINE` seçin.

1. Regedit ana menüsünden Dosya **Yükleme**  >  **Kovanı...** öğesini ve ardından **AppData\Local** klasöründe depolanan özel kayıt defteri dosyasını seçin. Örneğin:

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>`, göz atmak Visual Studio örneğine karşılık gelen örnektir.

Yalıtılmış kovanının adı olan bir hive adı girmeniz istenir. Bunu yaptıktan sonra, oluşturduğunuz yalıtılmış kovan altındaki kayıt defterine göz atabileceksiniz.

> [!IMPORTANT]
> Yeniden başlatmadan Visual Studio oluşturduğunuz yalıtılmış kovanı kaldırmalısınız. Bunu yapmak için   >  Regedit **ana menüsünden** Dosya Hive'ı Kaldır'ı seçin. (Bunu yoksa, dosya kilitli kalır ve Visual Studio başlatılamayacaktır.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
