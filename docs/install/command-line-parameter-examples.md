---
title: Yükleme için komut satırı parametresi örnekleri
description: Kendi komut satırı yüklemenizi oluşturmak için bu örnekleri özelleştirin Visual Studio.
ms.date: 11/23/2021
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3935ad632f186af6274118b4e1116b7a6d53c0df
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108724"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Uygulama yüklemesi için komut Visual Studio örnekleri

komut satırı parametrelerini [kullanarak Visual Studio'i](use-command-line-parameters-to-install-visual-studio.md)nasıl yükleyebileceğinizi göstermek için, aşağıda gereksinimlerinize göre özelleştirebileceğiniz birkaç örnek verilmiştir.

Her örnekte, ve , indirme işlemini `vs_enterprise.exe` `vs_professional.exe` `vs_community.exe` başlatan küçük (yaklaşık 1 MB) dosya olan Visual Studio önyükleyici sürümünü temsil eder. Farklı bir sürüm kullanıyorsanız, uygun önyükleyici adını yerine yazın.

Tüm komutlar yönetici yükseltmesi gerektirir ve işlem yükseltilmiş bir istemden başlamazsa bir Kullanıcı Hesabı Denetimi istemi görüntülenir.

Komut satırı `^` sonundaki karakterini kullanarak birden çok satırı tek bir komutta bir genişletilebilir. Alternatif olarak bu satırları tek bir satıra da yer veebilirsiniz. PowerShell'de eşdeğeri, backtick ( `` ` `` ) karakteridir.

Komut satırı kullanarak yükleyebilirsiniz iş yüklerinin ve bileşenlerin listeleri için, Visual Studio iş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın.

## <a name="install-using---installpath"></a>--installPath kullanarak yükleme

* Etkileşimli istemler görüntülenmeden ancak Visual Studio küçük bir örnek yükleyin:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```
  
* Fransızca dil paketiyle Visual Studio bir masaüstü örneğini yükleyin ve yalnızca ürün yüklü olduğunda döndürebilirsiniz.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="update-in-two-steps"></a>İki adımda güncelleştirme

* Etkileşimli Visual Studio ancak ilerleme durumu görüntülenmeden komut satırı aracılığıyla bir örnek güncelleştirin. Önyükleyici istemci makinede ise, bunu istemciden çalıştırsanız. Aksi takdirde, bunu düzenden çalıştırmalısınız. İlk komut yükleyiciyi, ikinci komut ise yükleyiciyi Visual Studio günceller.

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Her iki komut da önerilir. İlk komut, Visual Studio Yükleyicisi. İkinci komut, Visual Studio ler. Kullanıcı Hesabı Denetimi iletişim kutusundan kaçınmak için komut istemini Yönetici olarak çalıştırın.

## <a name="using---wait"></a>--wait kullanma

* Sonraki komut yürütülmeden önce toplu iş Visual Studio betiklerde komutunu `--wait` kullanın. Toplu iş dosyaları için bir ortam değişkeni, Komut satırı parametrelerini kullanarak komut satırı parametrelerini kullanma sayfasında belgelenmiş olan `%ERRORLEVEL%` [komutun Visual Studio](use-command-line-parameters-to-install-visual-studio.md) içerir. Bazı komut yardımcı programları, tamamlanmasını beklemek ve yükleyicinin dönüş değerini almak için ek parametreler gerektirir. Aşağıda, 'Start-Process' PowerShell betik komutuyla kullanılan ek parametrelerin bir örneği yer almaktadır:

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

* İlk '--wait' Visual Studio Yükleyicisi, ikinci '-Wait' ise tamamlanmasını beklemek için 'Start-Process' tarafından kullanılır. '-PassThru' parametresi, dönüş değeri için yükleyicinin çıkış kodunu kullanmak üzere 'Start-Process' tarafından kullanılır.

## <a name="using---layout-to-create-a-network-layout-or-a-local-cache"></a>Ağ düzeni veya yerel önbellek oluşturmak için --layout kullanma

* Temel Visual Studio düzenleyicisini (en düşük Visual Studio indirin. Yalnızca İngilizce dil paketini dahil etmek için:

  ```shell
   vs_professional.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Tüm önerilen bileşenlerle birlikte .NET masaüstü ve .NET web iş yüklerini indirin. Yalnızca İngilizce dil paketini dahil etmek için:

  ```shell
   vs_professional.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended
  ```

## <a name="using---all-to-acquire-the-entire-product"></a>Ürünün tamamını almak için --all kullanma

* Visual Studio Enterprise sürümüyle kullanılabilen tüm iş yüklerinin ve bileşenlerin etkileşimli bir Visual Studio Enterprise başlatın:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>--includeRecommended kullanma

* Visual Studio Community sürümünün yüklü olduğu bir makinede takma ad kullanarak Visual Studio Professional'nin ikinci bir örneğini yükleyin ve bu da Node.js destek sağlar:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>--remove kullanma

::: moniker range="vs-2017"

* Aşağıdaki Profil Oluşturma Araçları varsayılan yüklü örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Aşağıdaki Profil Oluşturma Araçları varsayılan yüklü örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Aşağıdaki Profil Oluşturma Araçları varsayılan yüklü örnekten Visual Studio kaldırın:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>--path kullanma

* Yükleme, önbellek ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Yalnızca yükleme ve önbellek yollarını kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Yalnızca yükleme ve paylaşılan yolları kullanma:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Yalnızca yükleme yolunu kullanarak:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Dışarı aktarmayı kullanma

* Yüklemeden seçimi kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Özel seçimi sıfırdan kaydetmek için dışarı aktarmayı kullanma:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--config kullanma

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
