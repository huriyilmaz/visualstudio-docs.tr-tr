---
title: Çevrimdışı yükleme oluşturma
description: Güvenilmez bir internet bağlantınız veya düşük bant genişliğiniz olduğunda Visual Studio'yı çevrimdışı olarak nasıl yükleyin.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d52dd064e895b1e35230b93c85a7a8499032943e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114828"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

::: moniker range="vs-2017"

Visual Studio 2017'yi çeşitli ağ ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarladık. Biz küçük bir dosya olan [Visual Studio web yükleyicisini](https://visualstudio.microsoft.com/vs/older-downloads)&mdash;denemenizi tavsiye ederken ve en&mdash;son düzeltmeler ve özelliklerle güncel kalmanızı sağlar, bunu mümkün olamayabileceğinizi anlıyoruz.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019'u çeşitli ağ ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarladık. Biz küçük bir dosya olan [Visual Studio web yükleyicisini](https://visualstudio.microsoft.com/downloads)&mdash;denemenizi tavsiye ederken ve en&mdash;son düzeltmeler ve özelliklerle güncel kalmanızı sağlar, bunu mümkün olamayabileceğinizi anlıyoruz.

::: moniker-end

Örneğin, güvenilmez bir internet bağlantınız veya bant genişliği düşük olabilir. Eğer öyleyse, birkaç seçeneğiniz varsa: Yüklemeden önce dosyaları indirmek için yeni "Tümlerini indirin, sonra yükleyin" özelliğini kullanabilir veya dosyaların yerel önbelleğini oluşturmak için komut satırını kullanabilirsiniz.

> [!NOTE]
> Visual Studio'yu internetten güvenlik duvarı olan istemci iş istasyonları ağına dağıtmak isteyen bir kuruluş yöneticisiyseniz, Visual Studio çevrimdışı yükleme sayfaları için gerekli [olan Visual Studio](../install/create-a-network-installation-of-visual-studio.md) ağ yüklemesi oluştur ve [sertifikayükleyin'](../install/install-certificates-for-visual-studio-offline.md) e bakın.

## <a name="use-the-download-all-then-install-feature"></a>"Tümlerini indirin, sonra yükle" özelliğini kullanın

::: moniker range="vs-2017"

[**Sürüm 15.8'de Yeni**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): Web yükleyicisini indirdikten sonra, **yeni İndir tümünü** seçin ve Visual Studio Installer'dan seçeneğini yükleyin. Ardından yüklemenize devam edin.

   !["Tümlerini indirin, sonra yükle" seçeneği](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Web yükleyicisini indirdikten sonra, **yeni Tümünü İndir'i** seçin ve ardından Visual Studio Installer'dan seçeneğini yükleyin. Ardından yüklemenize devam edin.

   !["Tümlerini indirin, sonra yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

"Tümlerini indirin, sonra yükleyin" özelliğini, visual studio'yu indirdiğiniz aynı bilgisayar için tek bir yükleme olarak indirebilmeniz için tasarladık. Bu şekilde, Visual Studio'yu yüklemeden önce web bağlantısını güvenli bir şekilde kesebilirsiniz.

> [!IMPORTANT]
> Başka bir bilgisayara aktarmak istediğiniz çevrimdışı önbellek oluşturmak için "Tümlerini indirin, sonra yükleyin" özelliğini kullanmayın. Bu şekilde çalışmak için tasarlanmadı. <br><br>Visual Studio'yu başka bir bilgisayara yüklemek için çevrimdışı önbellek oluşturmak istiyorsanız, yerel önbellek oluşturma hakkında bilgi almak için bu sayfanın [yerel önbellek](#use-the-command-line-to-create-a-local-cache) bölümünü oluşturmak için komut satırını kullanın veya ağ önbelleği oluşturma hakkında bilgi için Visual Studio [sayfasının ağ yüklemesi](../install/create-a-network-installation-of-visual-studio.md) oluştur'una bakın.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırını kullanma

Küçük bir bootstrapper indirdikten sonra, yerel bir önbellek oluşturmak için komut satırını kullanın. Ardından, Visual Studio'yu yüklemek için yerel önbelleği kullanın. (Bu işlem, önceki sürümler için kullanılabilen ISO dosyalarının yerini alır.)

Aşağıdaki adımları uygulayın:

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Adım 1 - Visual Studio bootstrapper indirin

Bu adımı tamamlamak için bir internet bağlantınız olmalıdır.

::: moniker range="vs-2017"

Visual Studio 2017 için bir bootstrapper almak için, nasıl yapılacağını hakkında ayrıntılı bilgi için [Visual Studio önceki sürümleri](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

Kurulumunuzun&mdash;yürütülebilir veya daha spesifik olması&mdash;için, bootstrapper dosyası aşağıdakilerden biriyle eşleşmeli veya benzer olmalıdır.

| Sürüm | Dosyaadı |
|-------------|-----------------------|
|Visual Studio Community | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Derleme Araçları   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Visual Studio seçtiğiniz baskı için Visual Studio bootstrapper indirerek başlayın. Kurulum dosyanız&mdash;veya&mdash;bootstrapper'ınız aşağıdakilerden biriyle eşleşecek veya benzer olacaktır.

| Sürüm                    | Dosya                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Derleme Araçları   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Daha önce bir bootstrapper dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, şu şekilde. Windows'da Dosya Gezgini'ni açın, bootstrapper dosyasına sağ tıklayın, **Özellikler'i**seçin, **Ayrıntılar** sekmesini seçin ve ardından **Ürün sürüm** numarasını görüntüleyin. Bu sayıyı Visual Studio'nun bir sürümüyle eşleştirmek için [Visual Studio'nun sayı ve çıkış tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfasına bakın.

### <a name="step-2---create-a-local-install-cache"></a>Adım 2 - Yerel yükleme önbelleği oluşturma

Bu adımı tamamlamak için bir internet bağlantınız olmalıdır.

> [!IMPORTANT]
> Visual Studio Community'yi yüklerseniz, yüklemeden sonraki 30 gün içinde etkinleştirmeniz gerekir. Bunun için internet bağlantısı gerekiyor.

Bir komut istemi açın ve aşağıdaki örneklerden komutlardan birini kullanın. Burada listelenen örnekler, Visual Studio'nun Topluluk sürümünü kullandığınızı varsayar; komutu baskınıza uygun şekilde ayarlayın.

> [!TIP]
> Bir hatayı önlemek için, tam yükleme yolunuzuzun 80 karakterden az olduğundan emin olun.

- .NET web ve .NET masaüstü geliştirme için çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- .NET masaüstü ve Office geliştirme için çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- C++ masaüstü geliştirme için çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Tüm özellikleri ile tam bir yerel düzen oluşturmak&mdash;için (bu biz birçok özelliklere _sahip_ uzun zaman alacak!), çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Tam bir Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için [Sistem gereksinimlerine](/visualstudio/productinfo/vs2017-system-requirements-vs/)bakın. Yalnızca yüklemek istediğiniz bileşenlerle nasıl bir düzen oluşturabileceğiniz hakkında bilgi için [Visual Studio'yu yüklemek için komut satırı parametrelerini kullanın'a](use-command-line-parameters-to-install-visual-studio.md)bakın.

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Tam bir Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için [Sistem gereksinimlerine](/visualstudio/releases/2019/system-requirements/)bakın. Yalnızca yüklemek istediğiniz bileşenlerle nasıl bir düzen oluşturabileceğiniz hakkında bilgi için [Visual Studio'yu yüklemek için komut satırı parametrelerini kullanın'a](use-command-line-parameters-to-install-visual-studio.md)bakın.

::: moniker-end

İngilizce dışında bir dil yüklemek istiyorsanız, `en-US` [dil yerelleri listesinden](#list-of-language-locales)bir yerel olarak değiştirin. Ardından, yükleme önbelleğinizi daha da özelleştirmek için [kullanılabilir bileşenlerin ve iş yüklerinin listesini](workload-and-component-ids.md) kullanın.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Adım 3 - Yerel önbellekten Visual Studio'yu yükleyin

> [!TIP]
> Yerel bir yükleme önbelleğinden çalıştırdığınızda, kurulum bu dosyaların her birinin yerel sürümlerini kullanır. Ancak yükleme sırasında önbellekte olmayan bileşenleri seçerseniz, kurulum bunları internetten indirmeye çalışır.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için, "Aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" yazan bir hata iletisi `--noweb` alırsanız, anahtarı sürüm 16.3.5 veya sonraki sürümlerle kullandığınızdan emin olun.
>
::: moniker-end

Yalnızca daha önce indirdiğiniz dosyaları yüklediğinizden emin olmak için, düzen önbelleğini oluşturmak için kullandığınız komut satırı seçeneklerini kullanın. Örneğin, aşağıdaki komutu içeren bir düzen önbelleği oluşturduysanız:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Ardından yüklemeyi çalıştırmak için bu komutu kullanın:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

[Komut satırı parametrelerinin](use-command-line-parameters-to-install-visual-studio.md)nasıl kullanılacağına daha fazla örnek için Visual Studio yükleme sayfası için Komut [satırı parametre örneklerine](command-line-parameter-examples.md) bakın. 

> [!NOTE]
> İmzanın geçersiz olduğu yla ilgili bir hata alırsanız, güncelleştirilmiş sertifikalar yüklemeniz gerekir. Çevrimdışı önbelleğinizdeki Sertifikalar klasörünü açın. Sertifika dosyalarının her birini çift tıklatın ve ardından Sertifika Yöneticisi sihirbazını tıklatın. Parolanız istenirse, parolayı boş bırakın.

### <a name="list-of-language-locales"></a>Dil yerelleri listesi

| **Dil-yerel** | **Dil** |
| ----------------------- | --------------- |
| cs-CZ | Çekçe |
| de-DE | Almanca |
| tr-TR | Türkçe |
| es-ES | İspanyolca |
| fr-FR | Fransızca |
| it-IT | İtalyanca |
| ja-JP | Japonca |
| ko-KR | Korece |
| pl-PL | Lehçe |
| pt-BR | Portekizce - Brezilya |
| ru-RU | Rusça |
| tr-TR | Türkçe |
| zh-CN | Çince - Basitleştirilmiş |
| zh-TW | Çince - Geleneksel |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun ağ yüklemesini oluşturma](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio çevrimdışı yüklemesi için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
