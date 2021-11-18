---
title: Çevrimdışı yükleme oluşturma
description: Güvenilir olmayan bir İnternet bağlantınız Visual Studio bant genişliğiniz olduğunda çevrimdışı yükleme hakkında bilgi alın.
ms.date: 4/16/2021
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 51ba8207b2357681ce92e89c9a51b47cffbcf690
ms.sourcegitcommit: 76541583274c4af4218ac2a8ab4308077a7e340e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "132733224"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

Çeşitli Visual Studio ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarlanmıştır. Çevrimiçi güncelleştirmeleri düzenli [olarak kontrol](https://visualstudio.microsoft.com/downloads)eden ve tüm en son düzeltmeler ve özelliklerle güncel kalmanıza yardımcı olan küçük bir dosya olan Visual Studio Yükleyicisi 'i kullanmanız önerilir. Ancak, bazen çevrimiçi erişim sorunlu olabilir. Örneğin, güvenilir olmayan bir İnternet bağlantınız olabilir veya İnternet bağlantınız düşük bant genişliğine sahip olabilir. Bu gibi durumlarda, daha fazla bilgi için birkaç yöntem daha Visual Studio. Yüklemeden önce  Dosyaları yerel makinede yerel bir önbelleğe indirmek için Visual Studio Yükleyicisi'den Yükleme ve yükleme özelliğini kullanabilir veya komut satırıyla daha sonra yüklemek üzere dosyaların yerel önbelleğini oluşturabilirsiniz.

> [!NOTE]
> İstemci iş istasyonları ağına bir Visual Studio dağıtımı gerçekleştirmek isteyen bir kurumsal IT yöneticisiyseniz, Visual Studio [Yöneticileri Kılavuzumuza bakın.](https://aka.ms/vs/admin/guide)

## <a name="use-the-download-all-then-install-feature"></a>"Hepsini indir, sonra yükle" özelliğini kullanın

Bu Visual Studio Yükleyicisi İş Yükleri **sekmesinde,** iletişim kutusunun altındaki  açılan listeden Hepsini indir ve yükle seçeneğini belirleyebilirsiniz. Bu özelliğin amacı, Visual Studio paketlerinin indirdikten sonra yüklemesini planla aynı bilgisayara Visual Studio. Paketleri önce yerel bir önbelleğe indirerek, yüklemeden önce İnternet bağlantısını güvenli bir şekilde Visual Studio.

   !["Hepsini indir, sonra yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

> [!IMPORTANT]
> Hepsini indir **özelliğini, ardından başka bir bilgisayara** aktarmayı niyetli bir yerel önbellek oluşturmak için uygulamayın. Bu şekilde çalışacak şekilde tasarlanmaz. 

Güncelleştirmelerinizi, Hepsini indir'e ve ardından **yükleme davranışına göre de yapılandırabilirsiniz.** Daha fazla bilgi için Güncelleştirme ayarlarını [özelleştirme belgelerine](/visualstudio/install/update-visual-studio?#installation-and-download-behaviors-1) bakın.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırı kullanma

Küçük bir önyükleyici dosyası indirebilir ve ardından komut satırı kullanarak yerel önbellek oluşturabilirsiniz. Önbellek oluşturulduktan sonra, bu önbelleği kullanarak Visual Studio. 

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>1. Adım : Önyükleyiciyi Visual Studio indirme

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15.9 için en son önyükleyicileri almak için aşağıdaki dosyalardan birini indirin. Bu önyükleyiciler, her zaman Visual Studio 2017'nin en son sürümünü yüklür.

| Sürüm                                      | Önyükleyici            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Professional sürüm 15.9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio 2017 Enterprise sürüm 15.9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)   |
| Visual Studio 2017 Derleme Araçları sürüm 15.9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

::: moniker-end

::: moniker range="vs-2019"

her zaman en son 16.11 sürümünü yükecek Visual Studio 2019 için en son önyükleyicileri almak için aşağıdaki dosyalardan birini indirin. Alternatif olarak, Visual Studio 2019'un belirli bir sürümünü yüklemek için, her bakım sürümü için sabit sürüm önyükleyicilerine bağlantılar içeren Visual Studio [2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler sayfasına gidin. 

| Sürüm                         | Önyükleyici                                                                    |
|---------------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Professional sürüm 16.11 | [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 Enterprise sürüm 16.11 | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe) |
| Visual Studio 2019 Derleme Araçları sürüm 16.11 | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe) |

::: moniker-end

::: moniker range="vs-2022"

Her zaman Geçerli kanalın en son sürümünü yükecek Visual Studio 2022 için en son önyükleyicileri almak için aşağıdaki dosyalardan birini indirin. Alternatif olarak, belirli bir sürümü veya belirli bir Visual Studio 2022 kanalını yüklemek için, her bakım sürümü için sabit sürüm önyükleyicilerine bağlantılar içeren [Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasına gidin. 

| Sürüm                         | Önyükleyici                                                               |
|---------------------------------|-------------------------------------------------------------------------|
| Visual Studio 2022 Community    | [vs_community.exe](https://aka.ms/vs/17/release/vs_community.exe)       |
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/release/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/release/vs_enterprise.exe)     |
| Visual Studio 2022 Derleme Araçları   | [vs_buildtools.exe](https://aka.ms/vs/17/release/vs_buildtools.exe)         |

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce Visual Studio [2019](/visualstudio/releases/2019/history#release-dates-and-build-numbers) Sürümler sayfasından belirli bir önyükleyici dosyasını indirdiy ve hangi sürümün yükleycegini doğrulamak için aşağıdaki şekilde bir önyükleyici dosyası indirdiyebilirsiniz. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini** seçin ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu slanı bir Visual Studio için sayfanın en altındaki tabloya bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün yüklen kuracaklarını doğrulamak için aşağıdaki şekilde devam edin. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın,  Özellikler'i seçin ve ardından Ayrıntılar **sekmesini** seçin. Ürün **sürümü** alanı, [önyükleyicinin](/visualstudio/releases/2022/vs2022-release-rhythm) yükleyecek kanalı ve sürümü açıklar. Sürüm numarası her zaman "belirtilenin en son bakım sürümü" olarak okunması ve kanal açıkça belirtilmemişse Geçerli olması gerekir. Bu nedenle, LTSC 17.0 Ürün sürümüne sahip bir önyükleyici, 17.0 LTSC kanalında kullanılabilen en son 17.0.x bakım sürümünü yükleyecek. Yalnızca Visual Studio 2022 sürümünün Geçerli kanala Visual Studio 2022'nin en son sürümünü yükley olduğunu söyleyen bir Ürün sürümüne sahip bir önyükleyici.

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>2. Adım - Yerel yükleme önbelleği oluşturma

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

Bir komut istemi açın ve önyükleyicinin parametrelerini Yerel yükleme önbelleğinizi oluşturmak üzere [Visual Studio](use-command-line-parameters-to-install-visual-studio.md) yüklemek için komut satırı parametrelerini kullanın. Önyükleyici Enterprise yaygın örnekler aşağıda ve komut satırı parametre [örnekleri sayfasında gösterilmiştir.](command-line-parameter-examples.md) Dil yerel ayarları listesinden bir yerele değiştirerek İngilizce dışında bir dil yükleyebilir ve yerel önbelleğinizi daha fazla özelleştirmek için bileşen ve iş yükleri `en-US` listesini kullanabilirsiniz. [](#list-of-language-locales) [](workload-and-component-ids.md)

> [!TIP]
> Bir hatayı önlemek için tam yükleme yol 80 karakterden az olduğundan emin olun.

::: moniker range="<=vs-2019"

- .NET web ve .NET masaüstü geliştirme için şunları çalıştırın:
::: moniker range="<=vs-2019"
   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```
::: moniker-end

::: moniker range=">=vs-2022"
   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional --lang en-US
    ```
::: moniker-end

::: moniker-end

::: moniker range="vs-2022"

- For .NET web and .NET desktop development, run:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional --lang en-US
    ```

::: moniker-end

- For .NET desktop and Office development, run:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- For C++ desktop development, run:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- To create a complete local cache, English only, with all features (this will take a long time&mdash;we have _lots_ of features!), run:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > A complete local cache of Visual Studio requires a minimum of 35 GB of disk space. For more information, see [System requirements](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > A complete local cache of Visual Studio requires a minimum of 41 GB of disk space. For more information, see [System requirements](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2022"

   > [!NOTE]
   > A complete local cache of Visual Studio requires a minimum of 45 GB of disk space. For more information, see [System requirements](/visualstudio/releases/2022/system-requirements/).

::: moniker-end

### Step 3 - Install Visual Studio from the local cache
When you install Visual Studio from a local install cache, the Visual Studio installer uses the local cached versions of the files. But, if you select components during installation that aren't in the cache, then the Visual Studio installer will attempt to download them from the internet. To make sure that you install only the files that you've previously downloaded, use the same [command-line options](use-command-line-parameters-to-install-visual-studio.md) that you used to create the local cache. To make sure your installer doesn't try to access the internet, use the `--noweb` switch.

For example, if you created a local installation cache with the following command:

::: moniker range="<=vs-2019"

```shell
vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Ardından bu komutu kullanarak yükleme işlemini çalıştırın:

```shell
c:\localVScache\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

::: moniker-end

::: moniker range="vs-2022"

```shell
vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional --lang en-US
```

Ardından bu komutu kullanarak yükleme işlemini çalıştırın:

```shell
c:\localVScache\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional
```

::: moniker-end

> [!IMPORTANT]
> Visual Studio Community kullanıyorsanız, üründe yüklemeden sonra 30 gün içinde oturum açmak için etkinleştirmeniz gerekir. Etkinleştirme için bir İnternet bağlantısı gerekir.

> [!NOTE]
> İmzanın geçersiz olduğuyla ilgili bir hata alırsanız, güncelleştirilmiş [sertifikaları yüklemeniz gerekir.](install-certificates-for-visual-studio-offline.md) Yerel önbelleğinizin Sertifikalar klasörünü açın. Sertifika dosyalarının her biri için çift tıklayın ve ardından Sertifika Yöneticisi sihirbazına tıklayın. Parola istenirse boş bırakın.


### <a name="list-of-language-locales"></a>Dil yerellerinin listesi

| **Dil yereli** | **Dil**          |
|---------------------|-----------------------|
| cs-CZ               | Çekçe                 |
| de-DE               | Almanca                |
| en-US               | İngilizce               |
| es-ES               | İspanyolca               |
| fr-FR               | Fransızca                |
| it-IT               | İtalyanca               |
| ja-JP               | Japonca              |
| ko-KR               | Korece                |
| pl-PL               | Lehçe                |
| pt-BR               | Portekizce - Brezilya   |
| ru-RU               | Rusça               |
| tr-TR               | Türkçe               |
| zh-CN               | Basitleştirilmiş Çince  |
| zh-TW               | Geleneksel Çince |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Yöneticileri Kılavuzu](https://aka.ms/vs/admin/guide)
- [Çevrimdışı yükleme için Visual Studio sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
