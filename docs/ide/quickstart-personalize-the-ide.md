---
title: Kümesi renk teması ve yazı tipleri
ms.date: 11/20/2017
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11cd73574f42fffb7bcfcda5ab47496fe92565c7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596950"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Visual Studio IDE ve düzenleyicisini kişiselleştirin

Bu 5-10 dakikalık öğreticide, koyu temayı seçerek Visual Studio Color temasını özelleştireceğiz. Biz de iki farklı türde metin düzenleyicisinde metin renklerini özelleştireceksiniz.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

## <a name="set-the-color-theme"></a>Renk teması ayarlayabilir

Visual Studio 'nun Kullanıcı arabirimine yönelik varsayılan renk teması **mavi**olarak adlandırılır. Kendisine değiştirelim **koyu**.

1. Menü çubuğunda, olan menüleri satırının gibi **dosya** ve **Düzenle**, seçin **Araçları** > **seçenekleri**.

1. Üzerinde **ortam** > **genel** seçenekler sayfası, değişiklik **renk teması** seçimi **koyu**seçin **Tamam**.

   Tüm Visual Studio geliştirme ortamı (IDE) için renk teması **koyu**olarak değişir.

   ::: moniker range="vs-2017"

   ![Koyu temalı Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Koyu temalı Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

> [!TIP]
> [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) **Visual Studio Color teması düzenleyicisini** yükleyerek önceden tanımlanmış ek temalar yükleyebilirsiniz. Bu aracı yükledikten sonra ek renk temaları görünür **renk teması** aşağı açılan listesi.

## <a name="change-text-color"></a>Metin rengini değiştirme

Şimdi biz düzenleyici için bazı metin renklerini özelleştireceksiniz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturalım.

1. Menü çubuğundan seçin **dosya** > **yeni** > **dosya**.

1. İçinde **yeni dosya** iletişim kutusunun **genel** kategorisi seçin **XML dosyası**ve ardından **açık**.

1. Aşağıdaki XML içeren satırın altına yapıştırın `<?xml version="1.0" encoding="utf-8"?>`.

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

   Satır numaralarını Turkuaz-mavi renk ve XML özniteliklerini olduğuna dikkat edin (gibi `id="bk101"`) bir açık mavi renk kodludur. Bu öğeler için metin rengini değiştirmek için ekleyeceğiz.

   ![XML dosyası yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. Açmak için **seçenekleri** iletişim kutusunda **Araçları** > **seçenekleri** menü çubuğundan.

1. Altında **ortam**, seçin **yazı tipleri ve renkler** kategorisi.

   Dikkat altındaki metin **ayarlarını göster** diyor **metin düzenleyici**&mdash;istediğimiz budur. Yalnızca yerleri burada yazı tipleri ve metin rengini özelleştirebilirsiniz kapsamlı bir listesini görmek için açılan listeyi genişletin.

1. Satır numaraları metnin rengini değiştirmek için **görüntü öğeleri** listesinde **satır numarası**. İçinde **öğe ön plan** kutusunda **Zeytin**.

   ![Seçenekler iletişim kutusu, yazı tipleri ve renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı diller, kendi özel yazı tipleri ve renkler ayarları vardır. C++ geliştiricisisiniz ve işlevleri için kullanılan rengi değiştirmek istediğinizde, örneğin, arayabileceğiniz **C++ işlevlerini** içinde **görüntü öğeleri** listesi.

1. Biz iletişim kutusu dışına çıkmadan önce de XML öznitelikleri rengini değiştirelim. İçinde **görüntü öğeleri** listesinde, aşağı kaydırarak **XML özniteliği** ve bu seçeneği belirleyin. İçinde **öğe ön plan** kutusunda **Küf**. Seçin **Tamam** bizim seçimlerini kaydetmek ve iletişim kutusunu kapatın.

   Satır numaraları artık Zeytin bir renk ve XML öznitelikleri, parlak Küf Yeşili. Bir C++ ya da C# kod dosyası gibi başka bir dosya türünü açarsanız, satır numaralarını Zeytin renkte göründüğünü göreceksiniz.

   ![Yeni yazı tipi renkleri olan XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Biz, Visual Studio'daki renkler özelleştirme yalnızca birkaç yolu incelediniz. Diğer özelleştirme seçeneklerinin hakkında bilgi edineceksiniz umuyoruz **seçenekleri** iletişim kutusu, gerçek anlamda Visual Studio kendi yapma.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi özelleştirme](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE’ye Genel Bakış](../get-started/visual-studio-ide.md)
