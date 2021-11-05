---
title: Koyu Visual Studio ve metin renklerini değiştirme
description: Varsayılan renk temasını koyu Visual Studio ve kod düzenleyicisinde yazı tipi renklerini değiştirme hakkında bilgi edinin.
ms.date: 11/04/2021
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 42f5282df5e31473fe7dd00e5a9ad57ceee243f3
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662813"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Nasılürür: Visual Studio IDE'leri ve düzenleyiciyi kişiselleştirme

Bu nasıl yapılan makalesinde, mavi temadan koyu Visual Studio renk temasını özelleştirdik. Ardından, kod düzenleyicisinde iki farklı metin türü için renkleri özelleştirin.

> [!NOTE]
> [2022'Visual Studio'da,](/visualstudio/releases/2022/release-notes-preview)renk temaları işlevselliğini kendi tema ayarlarınıza göre Windows. Daha fazla bilgi edinmek için [**bkz. Esnek Visual Studio**](https://devblogs.microsoft.com/visualstudio/flexible-theming-visual-studio/) özellikleri.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>IDE için renk temasını ayarlama

Visual Studio kullanıcı arabirimi için varsayılan renk teması Mavi olarak **adlandırılan bir temadır.** Şimdi bunu Koyu olarak **değiştir bakalım.**

1. Dosya ve Düzenle gibi menülerin satırı olan menü çubuğunda **Araçlar** **Seçenekleri'ne**   >  **tıklayın.**

1. Ortam Genel **seçenekleri**  >  **sayfasında** Renk teması seçimini  **Koyu olarak** ve ardından Tamam'ı **seçin.**

   Geliştirme ortamının (IDE) Visual Studio renk teması Koyu olarak **değişir.**

   ::: moniker range="vs-2017"

   ![Visual Studio 2017'de koyu tema](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019'da koyu tema](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio Market'te Visual Studio **Tema** Düzenleyicisi'ni [yükleyerek önceden tanımlanmış Visual Studio yükleyebilirsiniz.](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) Bu aracı yükledikten sonra, Renk teması açılan **listesinde ek renk** temaları görünür.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio Market'te Visual Studio **Tema Tasarımcısı'Visual Studio** [oluşturabilirsiniz.](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Daha fazla tema seçmek ister misiniz? Visual Studio Market'te çok çeşitli [**özel temalara göz atabilirsiniz.**](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Themes&sortBy=Installs) VS Code tabanlı yeni Visual Studio 2022 özel temalarının örneklerini görmek için Yeni Visual Studio temaları koleksiyonuna tanıtma blog [**gönderisi'ne**](https://devblogs.microsoft.com/visualstudio/custom-themes/) göz atabilirsiniz.

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Düzenleyicide metin renklerini değiştirme

Şimdi düzenleyici için bazı metin renklerini özelleştirebilirsiniz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturabilirsiniz.

1. Menü çubuğundan Dosya Yeni **Dosya'ya**  >    >  **tıklayın.**

1. Yeni Dosya **iletişim kutusunda,** Genel kategorisi **altında** XML Dosyası'na ve **ardından** Aç'ı **seçin.**

1. Aşağıdaki XML dosyasını içeren satırın altına `<?xml version="1.0" encoding="utf-8"?>` yapıştırın.

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

   Satır numaralarının turququua-blue renk, XML özniteliklerinin ise (örneğin) açık `id="bk101"` mavi bir renk olduğunu farkedin. Bu öğelerin metin rengini değiştirmeyeceksiniz.

   ![XML dosyası yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. Seçenekler iletişim **kutusunu açmak** için menü   >  **çubuğundan Araçlar** Seçenekler'i seçin.

1. Ortam **altında** Yazı Tipleri **ve Renkler kategorisini** seçin.

   Ayarlarını göster altındaki **metinde Metin** **Düzenleyici'nin şu** &mdash; şekilde olduğunu fark edebilirsiniz. Yazı tiplerini ve metin rengini özelleştirebileceğiniz yerlerin kapsamlı listesini görmek için açılan listeyi genişletin.

1. Satır numaraları metninin rengini değiştirmek için Öğeleri görüntüle **listesinde Satır** Numarası'ı **seçin.** Öğe ön **plan kutusunda, Yeşil'i** **seçin.**

   ![Seçenekler iletişim kutusu, Yazı Tipleri ve Renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı dillerin kendi özel yazı tipleri ve renk ayarları vardır. C++ geliştiricisiyseniz ve örneğin, işlevler için kullanılan rengi değiştirmek istiyorsanız, Öğeleri görüntüle listesinde **C++** **İşlevleri'ne bakabilirsiniz.**

1. İletişim kutusundan çıkmadan önce XML özniteliklerinin rengini de değiştirebilirsiniz. Öğeleri **görüntüle listesinde aşağı** kaydırarak **XML Özniteliği'ne kaydırın** ve seçin. Öğe ön **plan kutusunda Yer'i** **seçin.** **Seçimlerimizi** kaydetmek ve iletişim kutusunu kapatmak için Tamam'ı seçin.

   Çizgi numaraları artık yeşil renklidir ve XML öznitelikleri parlak, yeşil yeşil renktedir. C++ veya C# kod dosyası gibi başka bir dosya türü açarsanız, satır numaralarının da yeşil renkte olduğunu görüyorsunuz.

   ![Yeni yazı tipi renkleri ile XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Visual Studio'de renkleri özelleştirmenin yalnızca birkaç Visual Studio. Seçenekleri gerçekten kendi özelleştirmenizi yapmak için [](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) Seçenekler iletişim kutusundaki diğer özelleştirme seçeneklerini Visual Studio umuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapabilirsiniz: Visual Studio'da yazı tiplerini, renkleri ve temaları değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Nasıl olur: Düzenleyicide metin büyük/yeni harf değiştirme](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
