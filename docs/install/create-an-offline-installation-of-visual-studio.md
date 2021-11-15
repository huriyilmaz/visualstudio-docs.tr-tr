---
title: Çevrimdışı yükleme oluşturma
description: güvenilir olmayan bir internet bağlantınız veya düşük bant genişliğiniz olduğunda Visual Studio çevrimdışı olarak yüklemeyi öğrenin.
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
ms.openlocfilehash: 8ca9b7b669c99e1d3ea35476bf661af902ef6963
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453418"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

çeşitli ağ ve bilgisayar yapılandırmalarında iyi şekilde çalışacak Visual Studio tasarlıyoruz. düzenli aralıklarla çevrimiçi güncelleştirmeleri denetleyen küçük bir dosya olan [Visual Studio Yükleyicisi](https://visualstudio.microsoft.com/downloads)kullanmanızı öneririz ve en son düzeltmeler ve özelliklerle güncel kalabilmenizi sağlar. Ancak, bazen çevrimiçi erişim sorunlu olur. Örneğin, güvenilir olmayan bir internet bağlantınız olabilir veya internet bağlantınızın bant genişliği düşük olabilir. Bunlar gibi durumlarda, Visual Studio almak için kullanabileceğiniz birkaç farklı yöntem yaptık. yüklemeden önce dosyaları yerel makinede yerel bir önbelleğe indirmek için Visual Studio Yükleyicisi **tümünü indir, sonra yükle** özelliğini kullanabilir veya daha sonra yüklenecek dosyaların yerel bir önbelleğini oluşturmak için komut satırını kullanabilirsiniz.

> [!NOTE]
> istemci iş istasyonları ağına Visual Studio dağıtımı gerçekleştirmek isteyen bir kurumsal bt yöneticisiyseniz, [Visual Studio yöneticileri kılavuzumuzu](https://aka.ms/vs/admin/guide)inceleyin.

## <a name="use-the-download-all-then-install-feature"></a>"Tümünü Indir, sonra Yükle" özelliğini kullanın

Visual Studio Yükleyicisi, **iş yükleri** sekmesinde, iletişim kutusunun alt kısmındaki açılan menüde **tümünü indir ve yükle** seçeneğini belirleyebilirsiniz. bu özelliğin amacı, Visual Studio paketlerinin indirilmesini, sonunda Visual Studio yüklerken planladığınız aynı bilgisayara yüklemek için önde gelecektir. Paketleri önce yerel bir önbelleğe indirerek, Visual Studio yüklemeden önce internet bağlantısını güvenle kesebilirsiniz.

   !["Tümünü Indir, sonra Yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

> [!IMPORTANT]
> Başka bir bilgisayara aktarmak istediğiniz yerel bir önbellek oluşturmak için **Tümünü indir ve yükle** özelliğini kullanmayın. Bu şekilde çalışacak şekilde tasarlanmamıştır. 

Ayrıca güncelleştirmelerinizi **, tümünü indir ve sonra Yükle** davranışı açısından yapılandırabilirsiniz. Daha fazla bilgi için [güncelleştirme ayarlarını özelleştirme](/visualstudio/install/update-visual-studio?#installation-and-download-behaviors-1) belgelerine bakın.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırını kullanın

Küçük bir önyükleyici dosyası indirebilir ve ardından komut satırını kullanarak yerel bir önbellek oluşturabilirsiniz. Önbellek oluşturulduktan sonra, Visual Studio yüklemek için kullanabilirsiniz. 

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>1. adım-Visual Studio bootstrapper yükleme

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15,9 için en son bootstrap'yi almak için aşağıdaki dosyalardan birini indirin. bu bootstrap, çalıştırdığınızda Visual Studio 2017 ' nin en son sürümünü her zaman yükler.

| Sürüm                                      | Önyükleyici            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Professional sürüm 15,9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio 2017 Enterprise sürüm 15,9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)   |
| Visual Studio 2017 derleme araçları sürüm 15,9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

::: moniker-end

::: moniker range="vs-2019"

her zaman 16,11 ' nin en son sürümünü yükleyecek Visual Studio 2019 için en son bootstrap'ı almak için aşağıdaki dosyalardan birini indirin. alternatif olarak, Visual Studio 2019 ' nin belirli bir sürümünü yüklemek istiyorsanız, her bakım sürümü için sabit sürüm bootstrapbağlantıları olan [Visual Studio 2019 yayınlar](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasına gidin. 

| Sürüm                         | Önyükleyici                                                                    |
|---------------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Professional sürüm 16,11 | [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 Enterprise sürüm 16,11 | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe) |
| Visual Studio 2019 derleme araçları sürüm 16,11 | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe) |

::: moniker-end

::: moniker range="vs-2022"

geçerli kanalın en son sürümünü her zaman yükleyecek Visual Studio 2022 için en son bootstrap'ı almak için aşağıdaki dosyalardan birini indirin. alternatif olarak, belirli bir sürümü veya Visual Studio 2022 ' nin belirli bir kanalını yüklemek isterseniz, her bir bakım sürümü için sabit sürüm bootstrapbağlantılarına bağlantıları olan [Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasına gidin. 

| Sürüm                         | Önyükleyici                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 Community | [vs_community.exe](https://aka.ms/vs/17/release/vs_community.exe) |
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |
| Visual Studio 2022 Professional | [vs_buildtools.exe](https://aka.ms/vs/17/pre/vs_buildtools.exe) |

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>[Visual Studio 2019 yayınları](/visualstudio/releases/2019/history#release-dates-and-build-numbers) sayfasından belirli bir önyükleyici dosyasını daha önce indirdiyseniz ve hangi sürümün yükleneceğini doğrulamak istiyorsanız, şu şekilde olur. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler**' i seçin, **ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. bu numarayı bir Visual Studio sürümüyle eşleştirmek için, bu sayfanın en altındaki tabloya bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün yükleneceğini doğrulamak istiyorsanız, şöyle olur. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler** ' i seçin ve **ayrıntılar** sekmesini seçin. **Ürün sürümü** alanı, önyükleyicinin yükleneceği [kanalı ve sürümü](/visualstudio/releases/2022/vs2022-release-rhythm) anlatmaktadır. Sürüm numarası her zaman "belirtilen sayının en son bakım sürümü" olarak okunmalı ve açıkça belirtilmediği sürece kanal geçerli olur. Bu nedenle, LTSC 17,0 ürün sürümüne sahip bir önyükleyici, 17,0 LTSC kanalında bulunan en son 17.0. x bakım sürümünü yükler. yalnızca Visual Studio 2022 ' i belirten ürün sürümüne sahip bir önyükleyici, geçerli kanala Visual Studio 2022 ' nin en son sürümünü yükler.

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>2. adım-yerel bir yüklemesi önbelleği oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

bir komut istemi açın ve önyükleyici parametrelerini kullanarak, yerel yükleme önbelleğinizi oluşturmak için [Visual Studio sayfasını yüklemek üzere komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) bölümünde tanımlandığı şekilde kullanın. Enterprise önyükleyici kullanan ortak örnekler aşağıda ve [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasında gösterilmektedir. `en-US`Yerel önbelleğinizi daha fazla özelleştirmek için, İngilizce dışında [bir dil yükleyebilirsiniz](#list-of-language-locales)ve [bileşen ve iş yüklerinin listesini](workload-and-component-ids.md) kullanabilirsiniz.

> [!TIP]
> Bir hatayı engellemek için, tam yükleme yolunuz 80 karakterden az olduğundan emin olun.

::: moniker range="<=vs-2019"

- .NET Web ve .NET masaüstü geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

::: moniker-end

::: moniker range="vs-2022"

- .NET Web ve .NET masaüstü geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional --lang en-US
    ```

::: moniker-end

- .net masaüstü ve Office geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- C++ masaüstü geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Tam bir yerel önbellek oluşturmak için, tüm özelliklerle birlikte yalnızca Ingilizce ( &mdash; _çok fazla_ özellik olması uzun sürer!), şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\localVScache --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Visual Studio 'ın tamamen yerel önbelleği, en az 35 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Visual Studio 'ın tamamen yerel önbelleği, en az 41 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2022"

   > [!NOTE]
   > Visual Studio 'ın tamamen yerel önbelleği, en az 45 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/releases/2022/system-requirements/).

::: moniker-end

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>3. adım-yerel önbellekten Visual Studio yüklemesi
bir yerel yükleme önbelleğinden Visual Studio yüklediğinizde, Visual Studio yükleyicisi dosyaların yerel önbelleğe alınmış sürümlerini kullanır. ancak, yükleme sırasında önbellekte olmayan bileşenler ' i seçerseniz Visual Studio yükleyicisi bunları internetten indirmeyi dener. Yalnızca daha önce indirdiğiniz dosyaları yüklediğinizden emin olmak için, yerel önbellek oluşturmak için kullandığınız [komut satırı seçeneklerini](use-command-line-parameters-to-install-visual-studio.md) kullanın. Yükleyicinizin internet 'e erişmeyi denemediğinden emin olmak için `--noweb` anahtarını kullanın.

Örneğin, aşağıdaki komutla bir yerel yükleme önbelleği oluşturduysanız:

::: moniker range="<=vs-2019"

```shell
vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Yüklemeyi çalıştırmak için bu komutu kullanın:

```shell
c:\localVScache\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

::: moniker-end

::: moniker range="vs-2022"

```shell
vs_enterprise.exe --layout c:\localVScache --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional --lang en-US
```

Yüklemeyi çalıştırmak için bu komutu kullanın:

```shell
c:\localVScache\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --includeOptional
```

::: moniker-end

> [!IMPORTANT]
> Visual Studio Community kullanıyorsanız, yükleme 30 gün içinde üründe oturum açarak etkinleştirmeniz gerekir. Etkinleştirme bir internet bağlantısı gerektirir.

> [!NOTE]
> İmzanın geçersiz olduğunu belirten bir hata alırsanız, [güncelleştirilmiş sertifikaları yüklemelisiniz](install-certificates-for-visual-studio-offline.md). Yerel önbelleğinizin Sertifikalar klasörünü açın. Sertifika dosyalarının her birine çift tıklayın ve ardından Sertifika Yöneticisi Sihirbazı ' na tıklayın. Parola istenirse boş bırakın.


### <a name="list-of-language-locales"></a>Dil yerel ayarları listesi

| **Dil yerel ayarı** | **Dil**          |
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

- [Visual Studio yöneticileri kılavuzu](https://aka.ms/vs/admin/guide)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
