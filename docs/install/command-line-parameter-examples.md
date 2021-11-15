---
title: Yükleme için komut satırı parametre örnekleri
description: Visual Studio kendi komut satırı yüklemenizi oluşturmak için bu örnekleri özelleştirin.
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fb26f39b7613e8f5c2bc904fcbb29ecce65c082c
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453860"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio yükleme için komut satırı parametresi örnekleri

[Visual Studio yüklemek için komut satırı parametrelerinin nasıl kullanılacağını](use-command-line-parameters-to-install-visual-studio.md)göstermek için, gereksinimlerinize uyacak şekilde özelleştirebileceğiniz birkaç örnek aşağıda verilmiştir.

her örnekte, `vs_enterprise.exe` ve, `vs_professional.exe` `vs_community.exe` indirme işlemini başlatan küçük (yaklaşık 1 mb) bir dosya olan Visual Studio önyükleyici 'nin ilgili sürümünü temsil eder. Farklı bir sürüm kullanıyorsanız, uygun önyükleyici adını yerine koyun.

> [!NOTE]
> Tüm komutlar yönetici yükseltmesi gerektirir ve işlem yükseltilmiş bir komut isteminden başlatılmamışsa bir kullanıcı hesabı denetimi istemi görüntülenir.
>
> [!NOTE]
> `^`Birden çok satırı tek bir komutta birleştirmek için komut satırının sonundaki karakteri kullanabilirsiniz. Alternatif olarak, bu satırları tek bir satır üzerine yerleştirebilirsiniz. PowerShell 'de, eş değer ( `` ` `` ) karakteridir.

komut satırını kullanarak yükleyebileceğiniz iş yüklerinin ve bileşenlerin listesi için, [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfasına bakın.

## <a name="using---installpath"></a>--InstallPath kullanma

* Visual Studio en az bir örneğini, etkileşimli istemler olmadan ve ilerleme görüntülenmiş olarak yükler:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* komut satırını kullanarak, etkileşimli istemler olmadan, ancak ilerleme görüntülenmiş bir Visual Studio örneğini güncelleştirin:

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut de önerilir. ilk komut Visual Studio Yükleyicisi güncelleştirir. ikinci komut Visual Studio örneğini güncelleştirir. Kullanıcı hesabı denetimi iletişim kutusunu önlemek için komut istemi ' ni yönetici olarak çalıştırın.

* fransızca dil paketiyle yalnızca ürün yüklendiğinde döndürülen bir Visual Studio masaüstü örneğini sessizce bir biçimde yükleme.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>--Wait kullanma

* sonraki komut yürütülmeden önce Visual Studio yükleyicinin tamamlanmasını beklemek için batch dosyalarında veya komut dosyalarında kullanın. toplu iş dosyaları için, bir `%ERRORLEVEL%` ortam değişkeni, [Visual Studio yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) bölümünde belirtildiği gibi komutun dönüş değerini içerir. Bazı komut yardımcı programları, tamamlama için beklemek ve yükleyicinin dönüş değerini almak için ek parametreler gerektirir. Aşağıda, ' Start-Process ' PowerShell betiği komutuyla kullanılan ek parametrelerin bir örneği verilmiştir:

   ```shell
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

* ilk '--wait ' Visual Studio Yükleyicisi tarafından kullanılır ve ikinci '-wait ' ' Start-Process ' tarafından tamamlanmasını beklemek için kullanılır. '-Passby ' parametresi, dönüş değeri için yükleyicinin çıkış kodunu kullanmak üzere ' Start-Process ' tarafından kullanılır.

## <a name="using---layout"></a>--Layout kullanma

* Visual Studio çekirdek düzenleyicisini indirin (en düşük Visual Studio yapılandırma). Yalnızca Ingilizce dil paketini dahil edin:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .net masaüstü ve .net web iş yüklerini, tüm önerilen bileşenlerle ve GitHub uzantısıyla birlikte indirin. Yalnızca Ingilizce dil paketini dahil edin:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Kullanarak--tümü

* Visual Studio Enterprise sürümünde bulunan tüm iş yüklerinin ve bileşenlerin etkileşimli bir yüklemesini başlatın:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Kullanarak--ıncludereyorumded

* Node.js geliştirme desteğiyle Visual Studio Community sürümünün zaten yüklü olduğu bir makineye Visual Studio Professional adlı ikinci bir örneği yükleyin:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>--Remove kullanma

::: moniker range="vs-2017"

* Profil Oluşturma Araçları bileşenini varsayılan yüklü Visual Studio örneğinden kaldır:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Profil Oluşturma Araçları bileşenini varsayılan yüklü Visual Studio örneğinden kaldır:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Profil Oluşturma Araçları bileşenini varsayılan yüklü Visual Studio örneğinden kaldır:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>--Path kullanma

::: moniker range="vs-2017"

Bu komut satırı parametreleri **15,7 ' de yenidir**. bunlarla ilgili daha fazla bilgi için, [Visual Studio yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfasına bakın.

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

Bu komut satırı komutu **15,9 sürümünde yenidir**. bunun hakkında daha fazla bilgi için, [Visual Studio yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfasına bakın.

::: moniker-end

* Seçimi bir yüklemeden kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Özel seçimi sıfırdan kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--Config kullanma

::: moniker range="vs-2017"

Bu komut satırı parametresi **15,9 ' de yenidir**. bunun hakkında daha fazla bilgi için, [Visual Studio yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfasına bakın.

::: moniker-end

* Önceden kaydedilmiş bir yükleme yapılandırma dosyasından iş yüklerini ve bileşenleri yüklemek için--config kullanma:

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Var olan bir yüklemeye iş yüklerini ve bileşenleri eklemek için--config kullanma:

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
