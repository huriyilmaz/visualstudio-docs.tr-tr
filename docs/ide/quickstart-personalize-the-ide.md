---
title: Renk temasını ve yazı tiplerini ayarlama
ms.date: 11/20/2017
ms.topic: quickstart
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039e48dec17ce902932e2d0df26ebb336c396985
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667796"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Visual Studio IDE ve düzenleyicisini kişiselleştirin

Bu 5-10 dakikalık öğreticide, koyu temayı seçerek Visual Studio Color temasını özelleştireceğiz. Ayrıca, metin düzenleyicisinde iki farklı metin türünün renklerini de özelleştireceğiz.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="set-the-color-theme"></a>Renk temasını ayarlama

Visual Studio 'nun Kullanıcı arabirimine yönelik varsayılan renk teması **mavi**olarak adlandırılır. **Koyu**olarak değiştirelim.

1. **Dosya** ve **düzenleme**gibi menülerin bir satırı olan menü çubuğunda **Araçlar**  > **Seçenekler**' i seçin.

1. **Ortam**  > **genel** Seçenekler sayfasında, **renk teması** seçimini **koyu**olarak değiştirin ve ardından **Tamam**' ı seçin.

   Tüm Visual Studio geliştirme ortamı (IDE) için renk teması **koyu**olarak değişir.

   ::: moniker range="vs-2017"

   ![Koyu temalı Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Koyu temalı Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

> [!TIP]
> [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) **Visual Studio Color teması düzenleyicisini** yükleyerek önceden tanımlanmış ek temalar yükleyebilirsiniz. Bu aracı yükledikten sonra, **renk teması** açılan listesinde ek renk temaları görüntülenir.

## <a name="change-text-color"></a>Metin rengini değiştir

Artık düzenleyicinin bazı metin renklerini özelleştireceğiz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturalım.

1. Menü çubuğundan **dosya**  > **Yeni**  > **dosyası**' nı seçin.

1. **Yeni dosya** iletişim kutusunda, **genel** kategori altında **XML dosyası**' nı seçin ve **Aç**' ı seçin.

1. Aşağıdaki XML 'i `<?xml version="1.0" encoding="utf-8"?>` içeren satırın altına yapıştırın.

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

   Satır numaralarının turkuaz mavi renkli olduğunu ve XML özniteliklerinin (örneğin `id="bk101"`) açık mavi renkli olduğunu unutmayın. Bu öğelerin metin rengini değiştireceğiz.

   ![XML dosyası yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. **Seçenekler** iletişim kutusunu açmak için, menü çubuğundan **Araçlar**  > **Seçenekler** ' i seçin.

1. **Ortam**altında **yazı tipleri ve renkler** kategorisini seçin.

   **Ayarları göster** ' in altındaki metin **metin Düzenleyicisi** &mdash;this istediğimizi unutmayın. Yazı tiplerini ve metin rengini özelleştirebileceğiniz yerlerin kapsamlı listesini görmek için açılan listeyi genişletin.

1. Satır numaraları metninin rengini değiştirmek için, **görüntüleme öğeleri** listesinde **satır numarası**' nı seçin. **Öğe ön planı** kutusunda, **zeytin**' ı seçin.

   ![Seçenekler iletişim kutusu, yazı tipleri ve renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı dillerin kendilerine özgü yazı tipleri ve renkler ayarları vardır. Bir C++ geliştiricisiyseniz ve işlevler için kullanılan rengi değiştirmek istiyorsanız, **görüntüleme öğeleri** listesindeki  **C++ işlevleri** arayabilirsiniz.

1. İletişim kutusundan çıkmadan önce, XML özniteliklerinin rengini de değiştirelim. **Öğeleri görüntüle** listesinde, **XML özniteliği** ' ne gidin ve bunu seçin. **Öğe ön planı** kutusunda, **limon sarısı**' ı seçin. Seçimlerinizi kaydetmek ve iletişim kutusunu kapatmak için **Tamam** ' ı seçin.

   Satır numaraları artık bir zeytin rengi ve XML öznitelikleri parlak, limon yeşili. C++ Ya C# da kod dosyası gibi başka bir dosya türünü açarsanız, satır numaralarının de zeytin rengi içinde göründüğünü görürsünüz.

   ![Yeni yazı tipi renkleriyle XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Visual Studio 'da renkleri özelleştirmenin yalnızca birkaç yolunu araştırtık. Visual Studio 'Yu gerçek anlamda yapmak için **Seçenekler** iletişim kutusundaki diğer özelleştirme seçeneklerini araştırmanızı umuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE’ye Genel Bakış](../get-started/visual-studio-ide.md)