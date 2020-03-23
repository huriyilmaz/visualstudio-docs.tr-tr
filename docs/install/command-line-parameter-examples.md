---
title: Yükleme için komut satırı parametre örnekleri
description: Visual Studio'nun kendi komut satırı yüklemenizi oluşturmak için bu örnekleri özelleştirin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275260"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio kurulumu için komut satırı parametre örnekleri

[Visual Studio'u yüklemek için komut satırı parametrelerinin](use-command-line-parameters-to-install-visual-studio.md)nasıl kullanılacağını göstermek için, gereksinimlerinize uyacak şekilde özelleştirebileceğiniz birkaç örnek aşağıda verilmiştir.

Her `vs_enterprise.exe`örnekte, `vs_professional.exe` `vs_community.exe` ve indirme işlemini başlatan küçük (yaklaşık 1MB) dosya olan Visual Studio bootstrapper, ilgili sürümünü temsil eder. Farklı bir sürüm kullanıyorsanız, uygun bootstrapper adını değiştirin.

> [!NOTE]
> Tüm komutlar yönetim yüksekliği gerektirir ve işlem yükseltilmiş bir istemden başlatılmazsa Kullanıcı Hesabı Denetimi istemi görüntülenir.
>
> [!NOTE]
> Birden çok `^` satırı tek bir komuta dönüştürmek için komut satırının sonundaki karakteri kullanabilirsiniz. Alternatif olarak, bu satırları tek bir satırüzerine bir araya getirebilirsiniz. PowerShell'de eşdeğeri backtick`` ` ``( ) karakteridir.

Komut satırını kullanarak yükleyebileceğiniz iş yüklerinin ve bileşenlerinin listeleri için [Visual Studio iş yükü ve bileşen işleri sayfasına](workload-and-component-ids.md) bakın.

## <a name="using---installpath"></a>Kullanma --installPath

* Etkileşimli istemler ancak görüntülenen ilerleme ile Visual Studio'nun en az bir örneğini yükleyin:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Etkileşimli istemler olmadan, görüntülenerek komut satırını kullanarak Visual Studio örneğini güncelleştirin:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut da tavsiye edilir. İlk komut Visual Studio Yükleyici'yi güncelleştirir. İkinci komut Visual Studio örneğini güncelleştirir. Kullanıcı Hesabı Denetimi iletişim kutusunu önlemek için komut istemini Yönetici olarak çalıştırın.

* Visual Studio'nun bir masaüstü örneğini sessizce, Fransızca dil paketiyle yükleyin ve yalnızca ürün yüklendiğinde geri dönün.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Kullanma --bekletme

* Bir sonraki komut yürütülmeden önce Visual Studio yükleyicisinin tamamlanmasını beklemek için toplu dosyalarda veya komut dosyalarında kullanın. Toplu iş dosyaları `%ERRORLEVEL%` için bir ortam değişkeni, Visual Studio sayfasını yüklemek için Komut Satırı Kullan parametrelerinde belirtildiği gibi [komutun](use-command-line-parameters-to-install-visual-studio.md) geri dönüş değerini içerir. Bazı komut yardımcı programları tamamlanmayı beklemek ve yükleyicinin geri dönüş değerini almak için ek parametreler gerektirir. PowerShell komut komutu 'Start-Process' ile kullanılan ek parametrelere bir örnek aşağıda verilmiştir:

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   ```

   or

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* İlk '--bekle' Visual Studio Installer tarafından kullanılır ve ikinci '-Bekle' tamamlanmayı beklemek için 'Başlat-İşlemi' tarafından kullanılır. '-PassThru' parametresi, 'Başlat-İşlemi' tarafından, yükleyicinin çıkış kodunu iade değeri için kullanmak için kullanılır.

## <a name="using---layout"></a>Kullanma --düzeni

* Visual Studio çekirdek düzenleyicisini (en az Visual Studio yapılandırması) indirin. Yalnızca İngilizce dil paketini ekleyin:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Önerilen tüm bileşenler ve GitHub uzantısı ile birlikte .NET masaüstü ve .NET web iş yüklerini indirin. Yalnızca İngilizce dil paketini ekleyin:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Kullanma --tüm

* Visual Studio Enterprise sürümünde bulunan tüm iş yüklerinin ve bileşenlerinin etkileşimli bir yüklemesini başlatın:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Kullanma --includeRecommended

* İkinci bir yükleyin, Visual Studio Community sürümü zaten yüklü bir makinede Visual Studio Professional adlı örnek, Node.js geliştirme desteği ile:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Kullanma --kaldırma

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

## <a name="using---path"></a>Kullanma -yol

::: moniker range="vs-2017"

Bu komut satırı parametreleri **15.7'de yenidir.** Bunlar hakkında daha fazla bilgi için Visual Studio sayfasını yüklemek için komut satırı parametrelerini [kullan'a](use-command-line-parameters-to-install-visual-studio.md) bakın.

::: moniker-end

* Yükleme, önbellek ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Yalnızca yükleme ve önbellek yollarını kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Yalnızca yükleme ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Yalnızca yükleme yolunu kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Dışa aktarmayı kullanma

::: moniker range="vs-2017"

Bu komut satırı komutu **15.9'da yenidir.** Bu konuda daha fazla bilgi için Visual Studio sayfasını yüklemek için komut satırı parametrelerini [kullan'a](use-command-line-parameters-to-install-visual-studio.md) bakın.

::: moniker-end

* Seçimi yüklemeden kaydetmek için dışa aktarmayı kullanma:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Özel seçimi sıfırdan kaydetmek için dışa aktarmayı kullanma:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Kullanma --config

::: moniker range="vs-2017"

Bu komut satırı parametresi **15.9'da yenidir.** Bu konuda daha fazla bilgi için Visual Studio sayfasını yüklemek için komut satırı parametrelerini [kullan'a](use-command-line-parameters-to-install-visual-studio.md) bakın.

::: moniker-end

* Daha önce kaydedilmiş bir yükleme yapılandırma dosyasındaki iş yüklerini ve bileşenleri yüklemek için --config kullanma:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Varolan bir yüklemeye iş yükleri ve bileşenler eklemek için --config kullanma:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio'nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
