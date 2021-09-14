---
title: koyu Visual Studio temasını ayarlama ve metin renklerini değiştirme
description: varsayılan Visual Studio color temasını koyu moda değiştirme ve kod düzenleyicisinde yazı tipi renklerini değiştirme hakkında bilgi edinin.
ms.date: 08/19/2021
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8dd4e56ececf68b9bd53b5530f8ccfe0c906a975
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635966"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>nasıl yapılır: Visual Studio ıde ve düzenleyiciyi kişiselleştirme

bu nasıl yapılır makalesinde, varsayılan mavi temadan koyu temaya Visual Studio color temasını özelleştireceğiz. Daha sonra, kod düzenleyicisinde iki farklı metin türünün renklerini özelleştireceğiz.

> [!NOTE]
> [Visual Studio 2022 Preview](/visualstudio/releases/2022/release-notes-preview)sürümünde, renk temaları işlevini Windows ayarlarınızdaki bir şekilde kullanıma sunduk. daha fazla bilgi için bkz. [**Visual Studio blog gönderisi için esnek tema özellikleri**](https://devblogs.microsoft.com/visualstudio/flexible-theming-visual-studio/) .

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>IDE için renk temasını ayarlama

Visual Studio kullanıcı arabirimine yönelik varsayılan renk teması **mavi** olarak adlandırılır. **Koyu** olarak değiştirelim.

1. **Dosya** ve **düzenleme** gibi menülerin bir satırı olan menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

1. **Ortam**  >  **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   tüm Visual Studio geliştirme ortamı (ıde) için renk teması **koyu** olarak değişir.

   ::: moniker range="vs-2017"

   ![koyu temada Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![koyu temada Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> [Visual Studio market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)'ten **Visual Studio Color Theme düzenleyicisini** yükleyerek, önceden tanımlanmış ek temalar yükleyebilirsiniz. Bu aracı yükledikten sonra, **renk teması** açılan listesinde ek renk temaları görüntülenir.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> [Visual Studio marketi](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)'nden **Visual Studio Color teması tasarımcısını** yükleyerek kendi temalarınızı oluşturabilirsiniz.

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Düzenleyicideki metin renklerini değiştirme

Artık düzenleyicinin bazı metin renklerini özelleştireceğiz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturalım.

1. Menü çubuğundan **Dosya**  >  **Yeni**  >  **Dosya**' yı seçin.

1. **Yeni dosya** iletişim kutusunda, **genel** kategori altında **XML dosyası**' nı seçin ve **Aç**' ı seçin.

1. Aşağıdaki XML 'i içeren satırın altına yapıştırın `<?xml version="1.0" encoding="utf-8"?>` .

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Satır numaralarının turkuaz mavi renkli olduğunu ve XML özniteliklerinin (gibi `id="bk101"` ) açık mavi renkli olduğunu unutmayın. Bu öğelerin metin rengini değiştireceğiz.

   ![XML dosyası yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. **Seçenekler** iletişim kutusunu açmak için menü çubuğundan **Araçlar**  >  **Seçenekler** ' i seçin.

1. **Ortam** altında **yazı tipleri ve renkler** kategorisini seçin.

   **Ayarları göster** ' in altındaki metin bir **metin Düzenleyicisi** olduğunu söyler &mdash; . Yazı tiplerini ve metin rengini özelleştirebileceğiniz yerlerin kapsamlı listesini görmek için açılan listeyi genişletin.

1. Satır numaraları metninin rengini değiştirmek için, **görüntüleme öğeleri** listesinde **satır numarası**' nı seçin. **Öğe ön planı** kutusunda, **zeytin**' ı seçin.

   ![Seçenekler iletişim kutusu, yazı tipleri ve renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı dillerin kendilerine özgü yazı tipleri ve renkler ayarları vardır. C++ geliştiricisiyseniz ve işlevler için kullanılan rengi değiştirmek istiyorsanız, **görüntüleme öğeleri** listesinde **C++ işlevlerine** bakabilirsiniz.

1. İletişim kutusundan çıkmadan önce, XML özniteliklerinin rengini de değiştirelim. **Öğeleri görüntüle** listesinde, **XML özniteliği** ' ne gidin ve bunu seçin. **Öğe ön planı** kutusunda, **limon sarısı**' ı seçin. Seçimlerinizi kaydetmek ve iletişim kutusunu kapatmak için **Tamam** ' ı seçin.

   Satır numaraları artık bir zeytin rengi ve XML öznitelikleri parlak, limon yeşili. C++ veya C# kod dosyası gibi başka bir dosya türünü açarsanız, satır numaralarının de zeytin rengi içinde göründüğünü görürsünüz.

   ![Yeni yazı tipi renkleriyle XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Visual Studio renkleri özelleştirmenin yalnızca birkaç yolunu araştırtık. [**seçenekler**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) iletişim kutusundaki diğer özelleştirme seçeneklerini, gerçekten Visual Studio sahip olmak için araştırmanızı umuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Studio yazı tiplerini, renkleri ve temaları değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Nasıl yapılır: düzenleyicide metin durumunu değiştirme](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
