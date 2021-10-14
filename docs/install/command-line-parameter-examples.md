---
title: Yükleme için komut satırı parametresi örnekleri
description: Kendi komut satırı yüklemenizi oluşturmak için bu örnekleri özelleştirin Visual Studio.
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
ms.openlocfilehash: bba8646ece080a66098555dc4b0ec5310c35a556
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969469"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Uygulama yüklemesi için komut Visual Studio örnekleri

komut satırı parametrelerini [kullanarak Visual Studio'i](use-command-line-parameters-to-install-visual-studio.md)nasıl yükleyebileceğinizi göstermek için, aşağıda gereksinimlerinize göre özelleştirebileceğiniz birkaç örnek verilmiştir.

Her örnekte, ve , indirme işlemini `vs_enterprise.exe` `vs_professional.exe` `vs_community.exe` başlatan küçük (yaklaşık 1 MB) dosya olan Visual Studio önyükleyici sürümünü temsil eder. Farklı bir sürüm kullanıyorsanız, uygun önyükleyici adını yerine yazın.

> [!NOTE]
> Tüm komutlar yönetici yükseltmesi gerektirir ve işlem yükseltilmiş bir istemden başlamazsa bir Kullanıcı Hesabı Denetimi istemi görüntülenir.
>
> [!NOTE]
> Komut satırı `^` sonundaki karakterini kullanarak birden çok satırı tek bir komutta bir genişletilebilir. Alternatif olarak bu satırları tek bir satıra da yer veebilirsiniz. PowerShell'de eşdeğeri, backtick ( `` ` `` ) karakteridir.

Komut satırı kullanarak yükleyebilirsiniz iş yüklerinin ve bileşenlerin listeleri için, Visual Studio iş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın.

## <a name="using---installpath"></a>--installPath kullanma

* Etkileşimli istemler görüntülenmeden ancak Visual Studio küçük bir örnek yükleyin:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Etkileşimli Visual Studio ama ilerleme durumu görüntülenmeden komut satırı kullanarak bir örnek örneği güncelleştirin:

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut da önerilir. İlk komut, Visual Studio Yükleyicisi. İkinci komut, Visual Studio ler. Kullanıcı Hesabı Denetimi iletişim kutusundan kaçınmak için komut istemini Yönetici olarak çalıştırın.

* Fransızca dil paketiyle Visual Studio bir masaüstü örneğini yükleyin ve yalnızca ürün yüklü olduğunda döndürebilirsiniz.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>--wait kullanma

* Sonraki komut yürütülmeden önce toplu iş Visual Studio betiklerde komutunu kullanın. Toplu iş dosyaları için bir ortam değişkeni, Komut satırı parametrelerini kullanarak komut satırı parametrelerini kullanma sayfasında belgelenmiş olan `%ERRORLEVEL%` [komutun Visual Studio](use-command-line-parameters-to-install-visual-studio.md) içerir. Bazı komut yardımcı programları, tamamlanmasını beklemek ve yükleyicinin dönüş değerini almak için ek parametreler gerektirir. Aşağıda, 'Start-Process' PowerShell betik komutuyla kullanılan ek parametrelerin bir örneği yer almaktadır:

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

* İlk '--wait' Visual Studio Yükleyicisi, ikinci '-Wait' ise tamamlanmasını beklemek için 'Start-Process' tarafından kullanılır. '-PassThru' parametresi, 'Start-Process' tarafından, dönüş değeri için yükleyicinin çıkış kodunu kullanmak üzere kullanılır.

## <a name="using---layout"></a>--layout kullanma

* Temel Visual Studio düzenleyicisini (en düşük yapılandırma Visual Studio indirin. Yalnızca İngilizce dil paketini dahil etmek için:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .NET masaüstü ve .NET web iş yüklerinin yanı sıra tüm önerilen bileşenleri ve GitHub indirin. Yalnızca İngilizce dil paketini dahil etmek için:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>--all kullanma

* Visual Studio Enterprise yayında kullanılabilen tüm iş yüklerinin ve bileşenlerin etkileşimli bir Visual Studio Enterprise başlatın:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>--includeRecommended kullanma

* Visual Studio Community sürümünün yüklü olduğu bir makineye, Visual Studio Professional adlı ikinci bir örneğini, geliştirme desteğiyle Node.js yükleyin:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>--remove kullanma

::: moniker range="vs-2017"

* Varsayılan Profil Oluşturma Araçları yüklenmiş örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Varsayılan Profil Oluşturma Araçları yüklenmiş örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Varsayılan Profil Oluşturma Araçları yüklenmiş örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>--path kullanma

::: moniker range="vs-2017"

Bu komut satırı parametreleri **15.7'de yenidir.** Bu parametreler hakkında daha fazla bilgi için [Komut satırı parametrelerini kullanarak](use-command-line-parameters-to-install-visual-studio.md) yükleme Visual Studio bakın.

::: moniker-end

* Yükleme, önbellek ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Yalnızca yükleme ve önbellek yollarını kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Yalnızca yükleme ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Yalnızca yükleme yolunu kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Dışarı aktarmayı kullanma

::: moniker range="vs-2017"

Bu komut satırı komutu **15.9'da yenidir.** Bu konuda daha fazla bilgi için Komut satırı parametrelerini [kullanarak yükleme Visual Studio](use-command-line-parameters-to-install-visual-studio.md) bakın.

::: moniker-end

* Yüklemeden seçimi kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Özel seçimi sıfırdan kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--config kullanma

::: moniker range="vs-2017"

Bu komut satırı parametresi **15.9'da yenidir.** Bu konuda daha fazla bilgi için Komut satırı parametrelerini [kullanarak yükleme Visual Studio](use-command-line-parameters-to-install-visual-studio.md) bakın.

::: moniker-end

* Önceden kaydedilmiş bir yükleme yapılandırma dosyasından iş yüklerini ve bileşenleri yüklemek için --config kullanma:

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Mevcut bir yüklemeye iş yükleri ve bileşenler eklemek için --config kullanma:

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
