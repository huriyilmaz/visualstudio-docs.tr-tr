---
title: Yükleme için komut satırı parametre örnekleri
description: Visual Studio 'nun kendi komut satırı yüklemenizi oluşturmak için bu örnekleri özelleştirin.
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
ms.openlocfilehash: 1f182351cbb0351256ebe32b4ab70543022ed92c
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114251"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio yüklemesi için komut satırı parametresi örnekleri

[Visual Studio 'yu yüklemek için komut satırı parametrelerinin nasıl kullanılacağını](use-command-line-parameters-to-install-visual-studio.md)göstermek için, gereksinimlerinize uyacak şekilde özelleştirebileceğiniz birkaç örnek aşağıda verilmiştir.

Her örnekte, `vs_enterprise.exe` ve, `vs_professional.exe` `vs_community.exe` indirme işlemini başlatan küçük (yaklaşık 1 MB) bir dosya olan Visual Studio önyükleyici 'nin ilgili sürümünü temsil eder. Farklı bir sürüm kullanıyorsanız, uygun önyükleyici adını yerine koyun.

> [!NOTE]
> Tüm komutlar yönetici yükseltmesi gerektirir ve işlem yükseltilmiş bir komut isteminden başlatılmamışsa bir kullanıcı hesabı denetimi istemi görüntülenir.
>
> [!NOTE]
> `^`Birden çok satırı tek bir komutta birleştirmek için komut satırının sonundaki karakteri kullanabilirsiniz. Alternatif olarak, bu satırları tek bir satır üzerine yerleştirebilirsiniz. PowerShell 'de, eş değer ( `` ` `` ) karakteridir.

Komut satırını kullanarak yükleyebileceğiniz iş yüklerinin ve bileşenlerin listesi için bkz. [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="using---installpath"></a>--InstallPath kullanma

* Etkileşimli istemler olmadan, ancak ilerleme görüntülenirken, Visual Studio 'nun minimal bir örneğini yükler:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Komut satırını kullanarak bir Visual Studio örneğini güncelleştirme etkileşimli istemler, ancak ilerleme görüntülendi:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut de önerilir. İlk komut Visual Studio Yükleyicisi güncelleştirir. İkinci komut, Visual Studio örneğini güncelleştirir. Kullanıcı hesabı denetimi iletişim kutusunu önlemek için komut istemi ' ni yönetici olarak çalıştırın.

* Fransızca dil paketiyle, Visual Studio 'nun bir masaüstü örneğini sessizce, yalnızca ürün yüklendiğinde geri yükleme yapın.

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
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
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

## <a name="using---layout"></a>--Layout kullanma

* Visual Studio çekirdek Düzenleyicisi 'ni (en düşük Visual Studio yapılandırması) indirin. Yalnızca Ingilizce dil paketini dahil edin:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .NET masaüstü ve .NET Web iş yüklerini ve tüm önerilen bileşenlerle birlikte GitHub uzantısını indirin. Yalnızca Ingilizce dil paketini dahil edin:

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

## <a name="using---includerecommended"></a>Kullanarak--ıncludereyorumded

* Node.js geliştirme desteğiyle, Visual Studio Community Edition 'ın zaten yüklü olduğu bir makineye ikinci, adlandırılmış bir Visual Studio Professional örneğini yükleyin:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>--Remove kullanma

::: moniker range="vs-2017"

* Profil Oluşturma Araçları bileşenini varsayılan yüklü Visual Studio örneğinden kaldırın:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Profil Oluşturma Araçları bileşenini varsayılan yüklü Visual Studio örneğinden kaldırın:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>--Path kullanma

::: moniker range="vs-2017"

Bu komut satırı parametreleri **15,7 ' de yenidir**. Bunlarla ilgili daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Yüklemeyi, önbelleği ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Yalnızca Install ve Cache yollarını kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Yalnızca yüklemeyi ve paylaşılan yolları kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Yalnızca yüklemenin yolunu kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Dışarı aktarma kullanma

::: moniker range="vs-2017"

Bu komut satırı komutu **15,9 sürümünde yenidir**. BT hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Seçimi bir yüklemeden kaydetmek için dışarı aktarmayı kullanma:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Özel seçimi sıfırdan kaydetmek için dışarı aktarmayı kullanma:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--Config kullanma

::: moniker range="vs-2017"

Bu komut satırı parametresi **15,9 ' de yenidir**. BT hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfası.

::: moniker-end

* Önceden kaydedilmiş bir yükleme yapılandırma dosyasından iş yüklerini ve bileşenleri yüklemek için--config kullanma:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Var olan bir yüklemeye iş yüklerini ve bileşenleri eklemek için--config kullanma:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
