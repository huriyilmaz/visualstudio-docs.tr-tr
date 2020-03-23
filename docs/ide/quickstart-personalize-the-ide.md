---
title: Renk teonu ve yazı tiplerini ayarlama
ms.date: 11/20/2017
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11cd73574f42fffb7bcfcda5ab47496fe92565c7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75596950"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Visual Studio IDE ve Editörü Kişiselleştirin

Bu 5-10 dakikalık eğitimde, görsel stüdyo renk teonu koyu tema seçerek özelleştireceğiz. Ayrıca metin düzenleyicisindeki iki farklı metin türü için renkleri özelleştireceğiz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="set-the-color-theme"></a>Renk tesini ayarlama

Visual Studio kullanıcı arabirimi için varsayılan renk teması **Mavi**denir. **Hadi bunu Karanlık**olarak değiştirelim.

1. **Dosya** ve **Edit**gibi menüler satırı olan menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

1. **Çevre** > **Genel** seçenekleri sayfasında, **Renk teması** seçimini **Koyu**olarak değiştirin ve ardından **Tamam'ı**seçin.

   Tüm Visual Studio geliştirme ortamı (IDE) için renk teması **Dark**değiştirir.

   ::: moniker range="vs-2017"

   ![Karanlık temada Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Karanlık temada Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

> [!TIP]
> Visual **Studio Color Theme Editor'u** [Visual Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)yükleyerek önceden tanımlanmış ek temalar yükleyebilirsiniz. Bu aracı yükledikten sonra, Renk **teması** açılır listesinde ek renk temaları görünür.

## <a name="change-text-color"></a>Metin rengini değiştirme

Şimdi editör için bazı metin renklerini özelleştireceğiz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturalım.

1. Menü çubuğundan > **Yeni** > Dosya **yı**seçin.**File**

1. Genel **kategori** altında **Yeni Dosya** iletişim kutusunda, **XML Dosyası'nı**seçin ve sonra **Aç'ı**seçin.

1. Aşağıdaki XML'i içeren `<?xml version="1.0" encoding="utf-8"?>`satırın altına yapıştırın.

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

   Satır numaralarının turkuaz-mavi renk, XML özniteliklerinin (örneğin) `id="bk101"`açık mavi renk olduğuna dikkat edin. Bu öğelerin metin rengini değiştireceğiz.

   ![XML dosya yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. **Seçenekler** iletişim kutusunu açmak için menü çubuğundan **Araçlar** > **Seçenekleri'ni** seçin.

1. **Çevre** **altında, Yazı Tipleri ve Renkler** kategorisini seçin.

   **Metin Düzenleyicisi**&mdash; **için Göster ayarları** altındaki metnin istediğimizin bu olduğunu söylediğine dikkat edin. Yazı tiplerini ve metin rengini özelleştirebileceğiniz yerlerin geniş listesini görmek için açılır listeyi genişletin.

1. Satır numaraları metninin rengini değiştirmek için, **Görüntü öğeleri** listesinde **Satır Numarası'nı**seçin. Öğe **ön planda** kutusunda, **Olive**seçin.

   ![Seçenekler iletişim kutusu, Yazı Tipleri ve Renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı dillerin kendi özel yazı tipleri ve renk ayarları vardır. Bir C++ geliştiricisiyseniz ve örneğin işlevler için kullanılan rengi değiştirmek istiyorsanız, Görüntü **öğeleri** listesinde **C++ Işlevlerini** alabilirsiniz.

1. İletişim kutusundan çıkmadan önce XML özniteliklerinin rengini de değiştirelim. Görüntü **öğeleri** listesinde, **XML Özniteliği'ne** gidin ve seçin. Öğe **ön plan** kutusunda, **Lime**seçin. Seçimlerimizi kaydetmek ve iletişim kutusunu kapatmak için **Tamam'ı** seçin.

   Çizgi numaraları artık bir zeytin rengi ve XML öznitelikleri parlak, kireç yeşili. C++ veya C# kodu dosyası gibi başka bir dosya türünü açarsanız, satır numaralarının da zeytin renginde göründüğünü görürsünüz.

   ![Yeni yazı tipi renkleri ile XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Visual Studio'da renkleri özelleştirmenin sadece birkaç yolunu araştırdık. Visual Studio'yu gerçekten kendi iletişim kutunuz haline getirmek için **Seçenekler** iletişim kutusundaki diğer özelleştirme seçeneklerini keşfedeceğinizi umuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE’ye Genel Bakış](../get-started/visual-studio-ide.md)
