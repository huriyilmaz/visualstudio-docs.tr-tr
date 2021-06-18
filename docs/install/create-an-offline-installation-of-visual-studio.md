---
title: Çevrimdışı yükleme oluşturma
description: Güvenilir olmayan bir internet bağlantınız veya düşük bant genişliğiniz olduğunda Visual Studio 'Yu çevrimdışı yüklemeyi öğrenin.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: eef6a8bbdf5afc3aa5f36b0afdb374fd5beac471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307498"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

::: moniker range="vs-2017"

Visual Studio 2017 ' i çeşitli ağ ve bilgisayar yapılandırmalarında iyi bir şekilde çalışacak şekilde tasarlıyoruz. [Visual Studio Web Yükleyicisi](https://visualstudio.microsoft.com/vs/older-downloads)'ni denemenizi öneririz. Bu, &mdash; en son düzeltmeler ve özelliklerle güncel kalabileceğinizi anladığımız, bu küçük bir dosyadır &mdash; .

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 2019 ve üstünü, çeşitli ağ ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarlıyoruz. [Visual Studio Web Yükleyicisi](https://visualstudio.microsoft.com/downloads)'ni denemenizi öneririz. Bu, &mdash; en son düzeltmeler ve özelliklerle güncel kalabileceğinizi anladığımız, bu küçük bir dosyadır &mdash; .

::: moniker-end

Örneğin, güvenilir olmayan bir internet bağlantınız veya düşük bant genişliğine sahip olabilirsiniz. Bu durumda, birkaç seçeneğiniz vardır: yüklemeden önce dosyaları indirmek için yeni "tümünü Indir, sonra Yükle" özelliğini kullanabilir veya dosyaların yerel bir önbelleğini oluşturmak için komut satırını kullanabilirsiniz.

> [!NOTE]
> Bir Visual Studio 'nun Internet 'ten güvenlik duvarı olan bir istemci iş istasyonu ağına dağıtımını gerçekleştirmek isteyen bir kuruluş yöneticisiyseniz, Visual Studio ['nun ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md) ve [Visual Studio çevrimdışı yükleme sayfaları Için gereken sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md) sayfasına bakın.

## <a name="use-the-download-all-then-install-feature"></a>"Tümünü Indir, sonra Yükle" özelliğini kullanın

::: moniker range="vs-2017"

[**Sürüm 15,8 ' deki yenilikler**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): web yükleyicisini indirdikten sonra, Visual Studio yükleyicisi yeni **Tümünü İndir '** i seçin ve sonra yükleyin. Ardından, yüklemenize devam edin.

   !["Tümünü Indir, sonra Yükle" seçeneği](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

Web yükleyicisini indirdikten sonra, yeni **Tümünü İndir '** i seçin ve sonra Visual Studio yükleyicisi seçeneğini yükleyin. Ardından, yüklemenize devam edin.

   !["Tümünü Indir, sonra Yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Visual Studio 'Yu indirdiğiniz aynı bilgisayar için tek bir yükleme olarak indirebilmeniz için "tümünü Indir ve Yükle" özelliğini tasarladık. Bu şekilde, Visual Studio 'Yu yüklemeden önce Web ile güvenli bir şekilde bağlantıyı kesebilirsiniz.

> [!IMPORTANT]
> Başka bir bilgisayara aktarmayı planladığınız çevrimdışı bir önbellek oluşturmak için "tümünü Indir ve Yükle" özelliğini kullanmayın. Bu şekilde çalışacak şekilde tasarlanmamıştır. <br><br>Yerel bilgisayarda, daha sonra Visual Studio 'Yu yüklemek için kullanabileceğiniz çevrimdışı bir önbellek oluşturmak isterseniz, aşağıdaki [bir yerel önbellek oluşturmak için komut satırını kullanma](#use-the-command-line-to-create-a-local-cache) bölümüne bakın.  Alternatif olarak, [Visual Studio 'nun ağ yüklemesi oluştur](../install/create-a-network-installation-of-visual-studio.md) sayfası, ağda bir önbellek oluşturma hakkında bilgi sağlar.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırını kullanın
::: moniker range="vs-2017"

Küçük bir önyükleyici indirdikten sonra, yerel bir önbellek oluşturmak için komut satırını kullanın. Ardından, Visual Studio 'Yu yüklemek için yerel önbelleği kullanın. (Bu işlem önceki sürümler için kullanılabilir olan ISO dosyalarının yerini alır). 

::: moniker-end

::: moniker range=">=vs-2019"

Küçük bir önyükleyici dosyasını indirdikten sonra, yerel bir önbellek oluşturmak için komut satırını kullanın. Ardından, Visual Studio 'Yu yüklemek için yerel önbelleği kullanın.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Adım 1-Visual Studio önyükleyici 'yi Indirin

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15,9 için en son önyükleyici almak üzere [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasına gidin ve aşağıdaki önyükleyici dosyalarından birini indirin:

| Sürüm                                      | Kısaltın            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 sürüm 15,9 | vs_professional.exe |
| Visual Studio Enterprise 2017 sürüm 15,9   | vs_enterprise.exe   |
| Visual Studio Derleme Araçları 2017 sürüm 15,9  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 önyükleyici 'yi Visual Studio [İndirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya Visual Studio 'nun seçili sürümü için visual Studio [2019 yayınlar](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasından indirerek başlayın. Kurulum dosyanız &mdash; veya önyükleyici &mdash; , aşağıdakilerden biri ile eşleşecektir veya aşağıdakine benzer olacaktır:

| Sürüm                         | Dosya                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 derleme araçları  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Visual Studio 2022 ' nin yayınlanan sürümleri henüz kullanılamamaktadır, aşağıdaki Bootstrap, Visual Studio 2022 ' nin önizleme sürümüne yöneliktir.
>Visual Studio [İndirmeleri sayfasından](https://aka.ms/vs2022preview)visual Studio 2022 önyükleyici indirerek başlayın.

| Sürüm                         | İndir                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için [Visual Studio derleme numaraları ve sürüm tarihleri](/visual-studio-build-numbers-and-release-dates.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için [Visual studio 2019 yayımları](/visualstudio/releases/2019/history) sayfasına bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için [Visual studio 2022 yayımları](/visualstudio/releases/2022/history) sayfasına bakın.

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>2. adım-yerel bir yüklemesi önbelleği oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

Bir komut istemi açın ve önyükleyici parametrelerini, yerel yükleme önbelleğinizi oluşturmak için [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) sayfasında tanımlandığı şekilde kullanın. Kurumsal önyükleyici kullanan ortak örnekler aşağıda ve [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasında gösterilmektedir. Dil yerel ayarları listesinden bir yerel ayara geçiş yaparak Ingilizce dışında bir dil yükleyebilirsiniz `en-US` ve [](#list-of-language-locales)önbelleğinizi daha fazla özelleştirmek için [bileşenlerin ve iş yüklerinin listesini](workload-and-component-ids.md) kullanabilirsiniz.

> [!TIP]
> Bir hatayı engellemek için, tam yükleme yolunuz 80 karakterden az olduğundan emin olun.

- .NET Web ve .NET masaüstü geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- .NET masaüstü ve Office geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- C++ masaüstü geliştirme için şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Tam bir yerel düzen oluşturmak için, tüm özelliklerle birlikte yalnızca Ingilizce ( &mdash; _çok fazla_ özellik olması uzun sürer!), şunu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Tamamen Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Tamamen Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>3. adım-yerel önbellekten Visual Studio 'Yu yükler
Visual Studio 'Yu yerel yükleme önbelleğinden yüklediğinizde, Visual Studio yükleyicisi dosyaların yerel önbelleğe alınmış sürümlerini kullanır. Ancak, yükleme sırasında önbellekte olmayan bileşenler ' i seçerseniz, Visual Studio yükleyicisi bunları internet 'ten indirmeyi dener. Yalnızca daha önce indirdiğiniz dosyaları yüklediğinizden emin olmak için, düzen önbelleğini oluşturmak için kullandığınız [komut satırı seçeneklerini](use-command-line-parameters-to-install-visual-studio.md) kullanın. 

Örneğin, aşağıdaki komutla bir yerel yükleme önbelleği oluşturduysanız:

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Yüklemeyi çalıştırmak için bu komutu kullanın:

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Visual Studio Community kullanıyorsanız, 30 gün sonra ürünün içinde oturum açarak etkinleştirmeniz gerekir. Etkinleştirme bir internet bağlantısı gerektirir.

> [!NOTE]
> İmzanın geçersiz olduğunu belirten bir hata alırsanız, [güncelleştirilmiş sertifikaları yüklemelisiniz](install-certificates-for-visual-studio-offline.md). Çevrimdışı önbelleğinizin Sertifikalar klasörünü açın. Sertifika dosyalarının her birine çift tıklayın ve ardından Sertifika Yöneticisi Sihirbazı ' na tıklayın. Parola istenirse boş bırakın.

::: moniker range=">=vs-2019"
> [!TIP]
> Çevrimdışı yüklemeler için, "aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" ifadesini içeren bir hata iletisi alırsanız, `--noweb` anahtarı 16.3.5 veya sonraki bir sürümüyle kullandığınızdan emin olun.

::: moniker-end

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

- [Visual Studio 'nun ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
