---
title: Yükleme için komut satırı parametresi örnekleri
description: Bu örnekleri kendi Visual Studio komut satırı yüklemesi oluşturmak için özelleştirin.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8fc43cef8526b2ca79bb0b88a1d56ef4f4a2a65a
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275260"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio yüklemesi için komut satırı parametresi örnekleri

[Visual Studio 'yu yüklemek için komut satırı parametrelerinin nasıl kullanılacağını](use-command-line-parameters-to-install-visual-studio.md)göstermek için, gereksinimlerinize uyacak şekilde özelleştirebileceğiniz birkaç örnek aşağıda verilmiştir.

Her örnekte `vs_enterprise.exe`, `vs_professional.exe` ve `vs_community.exe`, indirme işlemini başlatan küçük (yaklaşık 1 MB) bir dosya olan Visual Studio önyükleyici 'nin ilgili sürümünü temsil eder. Farklı bir sürümü kullanıyorsanız, uygun önyükleyici adıyla değiştirin.

> [!NOTE]
> Tüm komutlar, yönetimsel ayrıcalık ve işlemin yükseltilmiş isteminden başlamamışsa istemi görüntülenecek olan bir kullanıcı hesabı denetimi gerektirir.
>
> [!NOTE]
> Birden çok satırı tek bir komutta birleştirmek için komut satırının sonundaki `^` karakterini kullanabilirsiniz. Alternatif olarak, yalnızca bu satırlara birlikte tek bir satır yerleştirebilirsiniz. PowerShell 'de, eş değer (`` ` ``) karakteridir.

Komut satırını kullanarak yükleyebileceğiniz iş yüklerinin ve bileşenlerin listesi için bkz. [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="using---installpath"></a>--İnstallPath kullanma

* Visual Studio, en az bir örneğini hiçbir etkileşimli istemleri ancak görüntülenen ilerleme durumu ile yükleyin:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Hiçbir etkileşimli istemleri ancak görüntülenen ilerleme durumu ile komut satırını kullanarak bir Visual Studio örneği güncelleştirin:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut de önerilir. İlk komut, Visual Studio yükleyicisi güncelleştirir. İkinci komut, Visual Studio örneğini güncelleştirir. Bir kullanıcı hesabı denetimi iletişim önlemek için komut istemini yönetici olarak çalıştırın.

* Bir masaüstü Visual Studio örneğini sessiz bir şekilde, yalnızca ürün yüklendiğinde döndüren Fransızca Dil paketi yükleyin.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>--Wait kullanma

* Sonraki komut yürütülmeden önce Visual Studio yükleyicisi 'nin tamamlanmasını beklemek için Batch dosyalarında veya betiklerinizde kullanın. Toplu iş dosyaları için, bir `%ERRORLEVEL%` ortam değişkeni, [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfasına belgelendiği gibi komutun dönüş değerini içerir. Bazı komut yardımcı programları, tamamlama için beklemek ve yükleyicinin dönüş değerini almak için ek parametreler gerektirir. Aşağıda, ' Start-Process ' PowerShell betiği komutuyla kullanılan ek parametrelerin bir örneği verilmiştir:

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   ```

   veya

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* İlk '--Wait ' Visual Studio Yükleyicisi tarafından kullanılır ve ikinci '-Wait ' ' Start-Process ' tarafından tamamlanmasını beklemek için kullanılır. '-Passby ' parametresi, dönüş değeri için yükleyicinin çıkış kodunu kullanmak üzere ' Start-Process ' tarafından kullanılır.

## <a name="using---layout"></a>Kullanarak--düzeni

* Visual Studio çekirdek Düzenleyicisi'ni (en az Visual Studio yapılandırması) indirin. Yalnızca İngilizce dil paketi içerir:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .NET Masaüstü ve .NET web iş yüklerinin yanı sıra tüm önerilen bileşenleri ve GitHub uzantısı'nı indirin. Yalnızca İngilizce dil paketi içerir:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Kullanarak--tümü

* Visual Studio Enterprise sürümünde bulunan tüm iş yüklerinin ve bileşenlerin etkileşimli bir yüklemesini başlatın:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>--İncludeRecommended kullanma

* Node. js geliştirme desteğiyle, Visual Studio Community Edition 'ın zaten yüklü olduğu bir makineye ikinci, adlandırılmış bir Visual Studio Professional örneğini yükleyin:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Kullanarak--Kaldır

::: moniker range="vs-2017"

* Profil oluşturma araçları bileşeni yüklü varsayılan Visual Studio örneği kaldırın:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Profil oluşturma araçları bileşeni yüklü varsayılan Visual Studio örneği kaldırın:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Kullanarak--yolu

::: moniker range="vs-2017"

Bu komut satırı parametreleri **15,7 ' de yenidir**. Bunlarla ilgili daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Yükleme, önbellek ve paylaşılan yollarını kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Yalnızca yükleme ve önbellek yollarını kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Yalnızca yükleme ve paylaşılan yolları kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Yükleme yolu kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Dışarı aktarma hizmetini kullanarak

::: moniker range="vs-2017"

Bu komut satırı komutu **15,9 sürümünde yenidir**. BT hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Bir yükleme seçimini kaydetmek için dışarı aktarma kullanarak:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Sıfırdan özel seçimini kaydetmek için dışarı aktarma kullanarak:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--Config'ı kullanma

::: moniker range="vs-2017"

Bu komut satırı parametresi **15,9 ' de yenidir**. BT hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Önceden kaydedilen yükleme yapılandırma dosyasından iş yüklerini ve bileşenlerini yüklemek için--config'ı kullanma:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Mevcut bir yüklemeye iş yüklerinin ve bileşenlerin eklemek için--config'ı kullanma:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
