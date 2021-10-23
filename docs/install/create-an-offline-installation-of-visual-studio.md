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
ms.openlocfilehash: 096beaa6dda4f75db03c6b9dc7a65144ea370300
ms.sourcegitcommit: 0257750be796cc46e01cebd8976f637743d29417
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "130290713"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

::: moniker range="vs-2017"

2017 Visual Studio çeşitli ağ ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarladık. Mümkün olmadığını anlıyoruz [tüm en son düzeltmeler](https://visualstudio.microsoft.com/vs/older-downloads)ve özelliklerle güncel kalmanız için küçük bir dosya olan Visual Studio web yükleyicisini &mdash; &mdash; denemenizi öneririz.

::: moniker-end

::: moniker range=">=vs-2019"

2019 Visual Studio ve sonraki bir yıl için çeşitli ağ ve bilgisayar yapılandırmalarında iyi çalışacak şekilde tasarladık. Mümkün olmadığını anlıyoruz [tüm en son düzeltmeler](https://visualstudio.microsoft.com/downloads)ve özelliklerle güncel kalmanız için küçük bir dosya olan Visual Studio web yükleyicisini &mdash; &mdash; denemenizi öneririz.

::: moniker-end

Örneğin, güvenilir olmayan bir İnternet bağlantınız veya düşük bant genişliğine sahip bir bağlantınız olabilir. Öyleyse, birkaç seçeneğiniz vardır: Yüklemeden önce dosyaları indirmek için yeni "Hepsini indir, sonra yükle" özelliğini kullanabilir veya komut satırıyla dosyaların yerel önbelleğini oluşturabilirsiniz.

> [!NOTE]
> Visual Studio'nin internetten güvenlik duvarı olan bir istemci iş istasyonları ağına dağıtımını gerçekleştirmek isteyen bir kuruluş yöneticisiyseniz, [Visual Studio'nin](../install/create-a-network-installation-of-visual-studio.md) ağ yüklemesi oluşturma ve Visual Studio çevrimdışı yükleme sayfaları için gerekli [sertifikaları](../install/install-certificates-for-visual-studio-offline.md) yükleme sayfamıza bakın.

## <a name="use-the-download-all-then-install-feature"></a>"Hepsini indir, sonra yükle" özelliğini kullanın

::: moniker range="vs-2017"

[**Sürüm 15.8'de**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)yeni: Web yükleyicisini indirdikten sonra yeni Hepsini indir'i seçin **ve** ardından yükleme Visual Studio Yükleyicisi. Ardından, yüklemenize devam edin.

   !["Hepsini indir, sonra yükle" seçeneği](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

Web yükleyicisini indirdikten sonra, yeni Hepsini **indir'i seçin ve ardından yükleme** Visual Studio Yükleyicisi. Ardından, yüklemenize devam edin.

   !["Hepsini indir, sonra yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

"Hepsini indir, sonra yükle" özelliğini, indirdiğiniz bilgisayar Visual Studio tek bir yükleme olarak indirilsin diye tasarladık. Bu şekilde, web'i yüklemeden önce web bağlantısını güvenli Visual Studio.

> [!IMPORTANT]
> Başka bir bilgisayara aktarmayı niyetli bir çevrimdışı önbellek oluşturmak için "Hepsini indir, sonra yükle" özelliğini kullanmayın. Bu şekilde çalışacak şekilde tasarlanmaz. <br><br>Yerel bilgisayarda daha sonra yerel bir önbellek oluşturmak istiyorsanız, Visual Studio yüklemek için kullanabileceğiniz bir çevrimdışı önbellek oluşturmak istiyorsanız, aşağıdaki Yerel önbellek oluşturmak [için komut satırı](#use-the-command-line-to-create-a-local-cache) kullanma bölümüne bakın.  Alternatif olarak, [Ağ yüklemesi oluşturma Visual Studio,](../install/create-a-network-installation-of-visual-studio.md) ağ üzerinde önbellek oluşturma hakkında bilgi sağlar.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırı kullanma
::: moniker range="vs-2017"

Küçük bir önyükleyici indirdikten sonra, yerel önbellek oluşturmak için komut satırı kullanın. Ardından, yerel önbelleği kullanarak Visual Studio. (Bu işlem, önceki sürümlerde kullanılabilen ISO dosyalarının yerini alır). 

::: moniker-end

::: moniker range=">=vs-2019"

Küçük bir önyükleyici dosyasını indirdikten sonra, yerel önbellek oluşturmak için komut satırı kullanın. Ardından, yerel önbelleği kullanarak Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>1. Adım : Önyükleyiciyi Visual Studio indirme

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15.9 için en son önyükleyiciyi [](https://visualstudio.microsoft.com/vs/older-downloads/) almak için Visual Studio önceki sürümler sayfasına gidin ve aşağıdaki önyükleyici dosyalarından birini indirin:

| Sürüm                                      | Dosyaadı            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 sürüm 15.9 | vs_professional.exe |
| Visual Studio Enterprise 2017 sürüm 15.9   | vs_enterprise.exe   |
| Visual Studio Derleme Araçları 2017 sürüm 15.9  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

başlangıç olarak Visual Studio 2019 önyükleyiciyi Visual Studio indirmeleri sayfasından veya [seçtiğiniz](https://visualstudio.microsoft.com/downloads) sürüm ve sürüm için [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler sayfasından Visual Studio. Kurulum dosyanız &mdash; veya önyükleyiciniz &mdash; aşağıdakilerden biri ile eşler veya benzer olur:

| Sürüm                         | Dosya                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 Derleme Araçları  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Visual Studio 2022'nin yayımlanan sürümleri henüz kullanılamıyor, aşağıdaki önyükleyiciler Visual Studio 2022'nin önizleme sürümü için.
>Visual Studio indirme sayfasından Visual Studio 2022 [önyükleyicisi'Visual Studio indirin.](https://aka.ms/vs2022preview)

| Sürüm                         | İndir                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. İlk Windows'Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu slanın yayın tarihiyle Visual Studio için Visual Studio numaraları ve yayın [tarihleri sayfasına](/visualstudio/releasenotes/vs2017-relnotes-history) bakın.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve sürümünü doğrulamak için aşağıdaki şekilde devam edin. İlk Windows'Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu sayıyla bir Visual Studio eşleşmesi için Visual Studio [2019 Yayın sayfasına](/visualstudio/releases/2019/history) bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve sürümünü doğrulamak için aşağıdaki şekilde devam edin. İlk Windows'Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu sayıyla bir Visual Studio eşleşmesi için Visual Studio [2022 Yayın sayfasına](/visualstudio/releases/2022/release-notes) bakın.

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>2. Adım - Yerel yükleme önbelleği oluşturma

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

Bir komut istemi açın ve önyükleyicinin parametrelerini Yerel yükleme önbelleğinizi oluşturmak üzere [Visual Studio](use-command-line-parameters-to-install-visual-studio.md) yüklemek için komut satırı parametrelerini kullanma sayfasında tanımlanan şekilde kullanın. Önyükleyici Enterprise yaygın örnekler aşağıda ve komut satırı parametre [örnekleri sayfasında gösterilmiştir.](command-line-parameter-examples.md) Dil yerel ayarları listesinden bir yerele değiştirerek İngilizce dışında bir dil yükleyebilir ve önbelleğinizi daha fazla özelleştirmek için bileşen ve iş yükleri `en-US` listesini kullanabilirsiniz. [](#list-of-language-locales) [](workload-and-component-ids.md)

> [!TIP]
> Bir hatayı önlemek için tam yükleme yol 80 karakterden az olduğundan emin olun.

- .NET web ve .NET masaüstü geliştirme için şunları çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- .NET masaüstü ve Office için şu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- C++ masaüstü geliştirme için şu çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Yalnızca İngilizce ve tüm özelliklerle eksiksiz bir yerel düzen oluşturmak için (bu çok fazla özellik &mdash; _çok uzun_ sürer!) şu işlemi çalıştırın:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Tam bir Visual Studio düzeni için en az 35 GB disk alanı gerekir. Daha fazla bilgi için [bkz. Sistem gereksinimleri.](/visualstudio/productinfo/vs2017-system-requirements-vs/) 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Tam bir Visual Studio düzeni için en az 41 GB disk alanı gerekir. Daha fazla bilgi için [bkz. Sistem gereksinimleri.](/visualstudio/releases/2019/system-requirements/)

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>3. Adım : Visual Studio önbellekten yükleme
Yerel yükleme Visual Studio yükleme önbelleğinden yükleme, Visual Studio yükleyicisi dosyaların yerel önbelleğe alınmış sürümlerini kullanır. Ancak, yükleme sırasında önbellekte olmayan bileşenleri seçersiniz, Visual Studio yükleyici bunları internetten indirmeyi dener. Yalnızca daha önce indirdiğiniz dosyaları yükledikten emin olmak için [](use-command-line-parameters-to-install-visual-studio.md) düzen önbelleğini oluşturmak için kullanılan komut satırı seçeneklerini kullanın. 

Örneğin, aşağıdaki komutla bir yerel yükleme önbelleği oluşturduysanız:

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Ardından bu komutu kullanarak yükleme işlemini çalıştırın:

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Visual Studio Community kullanıyorsanız, üründe yüklemeden sonra 30 gün içinde oturum açmak için etkinleştirmeniz gerekir. Etkinleştirme için bir İnternet bağlantısı gerekir.

> [!NOTE]
> İmzanın geçersiz olduğuyla ilgili bir hata alırsanız, güncelleştirilmiş [sertifikaları yüklemeniz gerekir.](install-certificates-for-visual-studio-offline.md) Çevrimdışı önbelleğinizin Sertifikalar klasörünü açın. Sertifika dosyalarının her biri için çift tıklayın ve ardından Sertifika Yöneticisi sihirbazına tıklayın. Parola istenirse boş bırakın.

::: moniker range=">=vs-2019"
> [!TIP]
> Çevrimdışı yüklemeler için "Aşağıdaki parametrelerle eşleşen bir ürün bulunamadı" hata iletisini alırsanız, 16.3.5 veya sonraki bir sürüme sahip anahtarı kullanırkenn `--noweb` emin olun.

::: moniker-end

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

- [Visual Studio ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
