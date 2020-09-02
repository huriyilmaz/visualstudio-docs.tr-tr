---
title: Microsoft Dil Arabirimi Paketleri (LIP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 503f97d1530f8d22184f42a2452046782a997c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814330"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Microsoft Dil Arabirim Paketleri (LIP'ler) ve Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Windows dil arabirimi paketi (LıP) kullanarak Windows 'un bir dil sürümünü yükleyebilir ve sonra çeşitli kullanıcı arabirimi dil paketlerini yükleyebilirsiniz. Kullanıcı Arabirimi dil paketleri, işletim sistemi için yerelleştirilmiş bir kullanıcı arabirimi (UI) sağlar. Örneğin, Windows 'un Ingilizce bir sürümünün üzerine bir Japonca dil arabirimi paketi yükleyebilir ve sonra Windows Kullanıcı arabirimi dilini Japonca ve Ingilizce arasında geçirebilirsiniz. LIP 'Leri kullanarak, tek bir bilgisayarda Windows 'un birden çok dil sürümüne sahip olabilirsiniz.

 Visual Studio 'nun LIP 'Leri ve birden çok dil sürümüne sahip bilgisayarlarda, Windows görüntüleme dili ayarlarını değiştirmek, eşleşen dil paketleri yüklenirken hem Windows hem de Visual Studio 'Yu ayarlar.

## <a name="limitations-of-multi-language-installations"></a>Çoklu dil yüklemelerinin sınırlamaları
 Visual Studio 'nun farklı dil sürümlerini aynı bilgisayara yüklediğinizde, yalnızca eşleşen sürümler arasında diller arasında geçiş yapabilirsiniz. Örneğin, yüklü bir Ingilizce Express Edition yüklüyse, Almanca Express sürümü yüklüyse ve Professional sürümü yüklüyse, profesyonel sürüm için değil yalnızca Express sürümleri için diller geçirebilirsiniz.

 Visual Studio Birleşik bir dil paketi kullanır. Bu ürünlerin birden fazla dil sürümünü yüklemek için, önce tam dil ürünü yüklemeniz ve sonra bir veya daha fazla dil paketi yüklemeniz gerekir.

> [!NOTE]
> Visual Studio, tam dil ürününün aynı bilgisayara birden çok dil sürümünün yüklenmesini desteklemez. Bir tam dil ürünü yükledikten sonra dil paketleri kullanarak dil sürümlerini eklemeniz gerekir. Aynı bilgisayara Express sürümlerinin birden çok tam dil ürününü yüklemeye devam edebilirsiniz.

### <a name="support-for-code-pages"></a>Kod sayfaları için destek
 Bazı Visual Studio Araçları, metin geçerli kod sayfasında olmayan karakterler içerdiğinde metni doğru görüntülemez. Bunun yerine, soru işaretleri görünür veya metin bozuk olur. Aşağıdaki araçlar veya bölgeler etkilenir:

- FTP kullanılarak dağıtılan siteler.

- Bazı denetimlerde ASCII olmayan bilgisayar adları.

- Visual Studio dışında çalışan komut satırı araçları.

- Visual Basic Geçiş Sihirbazı.

- ActiveX denetimi test kapsayıcısı.

- OLE/COM nesne Görüntüleyici.

- ISAPI Web hata ayıklama aracı.

- HTML Yardımı içeriğine sahip MFC uygulama projeleri.

- Uyumsuz bir kod sayfası olduğunda Visual SourceSafe/SCCı UI, Ingilizce 'ye geri döner.

- Visual SourceSafe Unicode dosya adlarını desteklemez.

- Son Kullanıcı tanımlı karakterler (özel kullanım bölgesi) belirteç/tanımlayıcı olarak kullanılamaz.

- Windows kod sayfası Doğu Asya diline ayarlandığında Latin genişletilmiş-B karakterleri bazı Visual Studio araç pencereleri içinde görüntülenemez.

- Birden çok dil betiğinin karakterlerinden oluşan metin çalıştırmaları, bazı karakterler için varsayılan glifi gösterebilir.

- Karmaşık betik dizelerini genel denetimlere kopyalamak ve yapıştırmak, karakter şekillendirmeye neden olabilir. Bunun yerine, metin girmek için ilgili dil klavyesini kullanın.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Geçerli kod sayfasına dahil olmayan karakterleri doğru şekilde göstermek için

1. **Başlat**' a tıklayın, **Denetim Masası**' na tıklayın, sonra **bölge ve dil seçeneklerini** (veya içinde **bölgesi** [!INCLUDE[win8](../includes/win8-md.md)] ) açın.

    > [!NOTE]
    > Bu adımları izlemek için bilgisayarda bir yönetici olmanız gerekir.

2. **Gelişmiş** sekmesine tıklayın.

3. Kullanmak istediğiniz **Unicode olmayan programların dil sürümüyle eşleşecek bir dil seçin** listesinde, kullanmakta olduğunuz dili seçin.

4. **Tamam**’a tıklayın.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Visual Studio 'da Kullanıcı arabirimi metni için kullanılan dili değiştirme
 Aynı bilgisayara birden çok dil sürümü yüklediğinizde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabirimi varsayılan **olarak Microsoft Windows ile aynı**olur. Bu ayar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabirimi metnini işletim sisteminin görüntüleme dili olarak belirtilen dilde gösterecek şekilde gösterir.

> [!NOTE]
> Visual Studio, **Microsoft Windows Ile aynı**kullanmak üzere ayarlandıysa ve eşleşen Visual Studio dil paketi yüklü değilse, Visual Studio Ilk Visual Studio yüklemesinin dilini kullanır.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Visual Studio 'da Kullanıcı arabirimi metni için kullanılan dili ayarlamak için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Seçenekler** Iletişim kutusunda **ortam** ' ı genişletin ve ardından **Uluslararası ayarlar**' a tıklayın.

3. **Dil** listesinde, Kullanıcı arabirimi metninin geliştirme ortamında görüntüleneceği dili seçin.

    IDE 'deki Kullanıcı arabirimi metninin işletim sistemi görüntüleme dili ayarıyla eşleşmesini sağlamak için **Microsoft Windows Ile aynı**' ı seçin.

   UI için kullanılan dili ayarlamak için devenv komutunu da kullanabilirsiniz. Daha fazla bilgi için bkz. [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Uluslararası Ayarlar, Ortam, Seçenekler İletişim Kutusu](../ide/reference/international-settings-environment-options-dialog-box.md)