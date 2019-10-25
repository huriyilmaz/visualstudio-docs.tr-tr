---
title: Çevrimdışı yükleme oluşturma
description: Güvenilir olmayan bir internet bağlantınız veya düşük bant genişliğiniz olduğunda Visual Studio 'Yu çevrimdışı yüklemeyi öğrenin.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c8b59ce38657bab157b966a25e0cd27109510215
ms.sourcegitcommit: 58000baf528da220fdf7a999d8c407a4e86c1278
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72789992"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun çevrimdışı yüklemesini oluşturma

::: moniker range="vs-2017"

Visual Studio 2017 ' i çeşitli ağ ve bilgisayar yapılandırmalarında iyi bir şekilde çalışacak şekilde tasarlıyoruz. [Visual Studio web yükleyicisini](https://visualstudio.microsoft.com/vs/older-downloads) &mdash;which küçük bir dosya olduğundan, en son düzeltmeler ve özelliklerle güncel kalacağınızı ve &mdash;we anlayacağınızı anlamanız önerilir.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 ' i çeşitli ağ ve bilgisayar yapılandırmalarında iyi bir şekilde çalışacak şekilde tasarlıyoruz. [Visual Studio web yükleyicisini](https://visualstudio.microsoft.com/downloads) &mdash;which küçük bir dosya olduğundan, en son düzeltmeler ve özelliklerle güncel kalacağınızı ve &mdash;we anlayacağınızı anlamanız önerilir.

::: moniker-end

Örneğin, güvenilir olmayan bir internet bağlantınız veya düşük bant genişliğine sahip olabilirsiniz. Bu durumda, birkaç seçeneğiniz vardır: yüklemeden önce dosyaları indirmek için yeni "tümünü Indir, sonra Yükle" özelliğini kullanabilir veya dosyaların yerel bir önbelleğini oluşturmak için komut satırını kullanabilirsiniz.

> [!NOTE]
> Internet 'ten güvenlik duvarlı bir istemci iş istasyonu ağına Visual Studio dağıtımı gerçekleştirmek isteyen bir kuruluş yöneticisiyseniz, bkz. [Visual Studio 'nun ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md) ve [sertifika yükleme Visual Studio çevrimdışı yükleme sayfaları için gereklidir](../install/install-certificates-for-visual-studio-offline.md) .

## <a name="use-the-download-all-then-install-feature"></a>"Tümünü Indir, sonra Yükle" özelliğini kullanın

::: moniker range="vs-2017"

[**Sürüm 15,8 ' deki yenilikler**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): web yükleyicisini indirdikten sonra, Visual Studio yükleyicisi yeni **Tümünü İndir '** i seçin ve sonra yükleyin. Ardından, yüklemenize devam edin.

   !["Tümünü Indir, sonra Yükle" seçeneği](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Web yükleyicisini indirdikten sonra, yeni **Tümünü İndir '** i seçin ve sonra Visual Studio yükleyicisi seçeneğini yükleyin. Ardından, yüklemenize devam edin.

   !["Tümünü Indir, sonra Yükle" seçeneği](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Visual Studio 'Yu indirdiğiniz aynı bilgisayar için tek bir yükleme olarak indirebilmeniz için "tümünü Indir ve Yükle" özelliğini tasarladık. Bu şekilde, Visual Studio 'Yu yüklemeden önce Web ile güvenli bir şekilde bağlantıyı kesebilirsiniz.

> [!IMPORTANT]
> Başka bir bilgisayara aktarmayı planladığınız çevrimdışı bir önbellek oluşturmak için "tümünü Indir ve Yükle" özelliğini kullanmayın. Bu şekilde çalışacak şekilde tasarlanmamıştır. <br><br>Visual Studio 'Yu başka bir bilgisayara yüklemek üzere çevrimdışı bir önbellek oluşturmak istiyorsanız, yerel bir önbellek oluşturma veya görsel ağ yüklemesi oluşturma hakkında bilgi için bu sayfanın [Yerel önbellek oluşturmak için komut satırını kullanma](#use-the-command-line-to-create-a-local-cache) bölümüne bakın. [ ](../install/create-a-network-installation-of-visual-studio.md)Bir ağ önbelleğinin nasıl oluşturulacağı hakkında bilgi için bkz.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Yerel önbellek oluşturmak için komut satırını kullanın

Küçük bir önyükleyici indirdikten sonra, yerel bir önbellek oluşturmak için komut satırını kullanın. Ardından, Visual Studio 'Yu yüklemek için yerel önbelleği kullanın. (Bu işlem önceki sürümler için kullanılabilir olan ISO dosyalarının yerini alır.)

İşte.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Adım 1-Visual Studio önyükleyici 'yi Indirin

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

Kurulum çalıştırılabilir dosyanız daha belirli bir şekilde &mdash;or, önyükleyici dosyası &mdash;should eşleşiyor veya aşağıdakilerden birine benzer.

| Sürüm | Kısaltın |
|-------------|-----------------------|
|Visual Studio Community | vs_community. exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise. exe |
|Visual Studio Derleme Araçları   | vs_buildtools. exe |

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'nun seçili sürümü için Visual Studio önyükleyici indirerek başlayın. Kurulum dosyanız &mdash;or önyükleyici &mdash;will eşleşiyor veya aşağıdakilerden birine benzer.

| Sürüm                    | Dosya                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vS_professional. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Derleme Araçları   | [vs_buildtools. exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfası.

### <a name="step-2---create-a-local-install-cache"></a>2\. adım-yerel bir yüklemesi önbelleği oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

> [!IMPORTANT]
> Visual Studio Community yüklerseniz, yüklemeyi 30 gün içinde etkinleştirmeniz gerekir. Bu, internet bağlantısı gerektirir.

Bir komut istemi açın ve aşağıdaki örneklerde komutlardan birini kullanın. Burada listelenen örneklerde, Visual Studio 'nun Community sürümünü kullandığınızı varsayılmaktadır; komutu sürümünüz için uygun şekilde ayarlayın.

> [!TIP]
> Bir hatayı engellemek için, tam yükleme yolunuz 80 karakterden az olduğundan emin olun.

- .NET Web ve .NET masaüstü geliştirme için şunu çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- .NET masaüstü ve Office geliştirme için şunu çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Masaüstü C++ geliştirme için şunu çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Tüm özelliklerle tam bir yerel düzen oluşturmak için (&mdash;we _çok_ sayıda özelliği olması uzun zaman alır!), şunu çalıştırın:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Tamamen Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs/). Yalnızca yüklemek istediğiniz bileşenleri içeren bir düzen oluşturma hakkında bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Tamamen Visual Studio düzeni en az 35 GB disk alanı gerektirir. Daha fazla bilgi için bkz. [sistem gereksinimleri](/visualstudio/releases/2019/system-requirements/). Yalnızca yüklemek istediğiniz bileşenleri içeren bir düzen oluşturma hakkında bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Ingilizce dışında bir dil yüklemek isterseniz, [dil yerel ayarları listesinden](#list-of-language-locales)`en-US` ' ı değiştirin. Daha sonra, yükleme önbelleğinizi daha fazla özelleştirmek için kullanabileceğiniz [bileşenlerin ve iş yüklerinin listesini](workload-and-component-ids.md) kullanın.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>3\. adım-yerel önbellekten Visual Studio 'Yu yükler

> [!TIP]
> Yerel yükleme önbelleğinden çalıştırdığınızda, kurulum bu dosyaların her birinin yerel sürümlerini kullanır. Ancak, yükleme sırasında önbellekte olmayan bileşenler ' i seçerseniz, kurulum bunları internet 'ten indirmeyi dener.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için, "aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" adlı bir hata mesajı alırsanız, 16.3.5 veya sonraki bir sürümüyle `--noweb` anahtarını kullandığınızdan emin olun.
>
::: moniker-end

Yalnızca daha önce indirdiğiniz dosyaları yüklediğinizden emin olmak için, düzen önbelleğini oluşturmak için kullandığınız komut satırı seçeneklerini kullanın. Örneğin, aşağıdaki komutla bir düzen önbelleği oluşturduysanız:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Yüklemeyi çalıştırmak için bu komutu kullanın:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

[Komut satırı parametrelerinin](use-command-line-parameters-to-install-visual-studio.md)nasıl kullanılacağına ilişkin daha fazla örnek için bkz. [Visual Studio için komut satırı parametresi örnekleri yükleme](command-line-parameter-examples.md) sayfası. 

> [!NOTE]
> İmzanın geçersiz olduğunu belirten bir hata alırsanız, güncelleştirilmiş sertifikaları yüklemelisiniz. Çevrimdışı önbelleğinizin Sertifikalar klasörünü açın. Sertifika dosyalarının her birine çift tıklayın ve ardından Sertifika Yöneticisi Sihirbazı ' na tıklayın. Parola istenirse boş bırakın.

### <a name="list-of-language-locales"></a>Dil yerel ayarları listesi

| **Dil yerel ayarı** | **Dil** |
| ----------------------- | --------------- |
| CS-CZ | Çekçe |
| de-DE | Almanca |
| en-US | İngilizce |
| ES-ES | İspanyolca |
| fr-FR | Fransızca |
| BT BT | İtalyanca |
| ja-JP | Japonca |
| ko-KR | Korece |
| PL-PL | Lehçe |
| PT-BR | Portekizce - Brezilya |
| ru-RU | Rusça |
| tr-TR | Türkçe |
| zh-CN | Çince-Basitleştirilmiş |
| zh-TW | Çince-Geleneksel |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'nun ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
