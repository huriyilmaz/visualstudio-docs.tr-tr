---
title: Tür tanımlarını görüntüleme
description: Bir türün veya üyenin tanımını kolayca görüntülemenizi sağlayan tanıma git ve açıklama tanıma özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a0cd8fe13af8f60d90b8c4b0e29a442d5e70a498f55368d4f87cfb8d8e47caca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413233"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiricilerin genellikle kendi kodlarında kullandıkları türler veya sınıf üyeleri için kaynak kodu tanımlarını görüntülemesi gerekir. Visual Studio, tanım ve özet **tanım** özelliklerine **git** özelliği, bir tür veya üyenin tanımını kolayca görüntülemenizi sağlar. Kaynak kodu yoksa, bunun yerine meta veriler görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** özelliği bir tür veya üyenin kaynağına gider ve sonucu yeni bir sekmede açar. Bir klavye kullanıcısı kullanıyorsanız, metin imlecinizi bir yere sembol adının içine yerleştirin ve **F12** tuşuna basın. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Tanıma Git** ' i seçin veya aşağıdaki bölümde açıklanan **CTRL-tıklama** işlevini kullanın.

### <a name="ctrl-click-go-to-definition"></a>CTRL-tanıma git ' e tıklayın

**CTRL** + hızlı **erişim için fare kullanıcıları için bir** kısayoldur **seçeneğine tıklayın** . **CTRL** tuşuna bastığınızda ve türün ya da üyenin üzerine geldiğinizde semboller tıklatılabilir hale gelir. Bir simgenin tanımına hızlıca gitmek için **CTRL** tuşuna basın ve ardından üzerine tıklayın. Bu kadar kolay!

![Fare tıklaması tanım animasyonuna git](../ide/media/click_gotodef.gif)

Fare tıklaması için değiştirici anahtarını değiştirebilirsiniz. **Araçlar**   >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **genel**'e giderek ve   + **değiştirici tuşu kullan** açılır listesinden alt ya da CTRL **alt** ' i seçerek tanıma git ' i seçin. Fare **tıklamasını** devre dışı bırakmak için fare tıklamasını **Etkinleştir** onay kutusunun işaretini kaldırın.

![Fare tıklamasını etkinleştirme tanıma git](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Tanıma Göz At

Özet **tanım** özelliği, bir türün tanımını düzenleyicide geçerli konumundan çıkmadan önizlemenizi sağlar. Bir klavye kullanıcısı kullanıyorsanız, metin imlecinizi bir yere tür veya üye adının içine yerleştirin ve **alt + F12** tuşlarına basın. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Açıklama tanımı** ' nı seçebilirsiniz.

**CTRL** + **tıklama** işlevselliğini etkinleştirmek için **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **genel**' e gidin. **Göz atma görünümü ' nde tanımı aç** seçeneğini belirleyin ve **Seçenekler** Iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

![Fare tıklaması tanım seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

Ardından, **CTRL** tuşuna basın (veya **Seçenekler**'de herhangi bir değiştirici tuşu seçilidir) ve türe veya üyeye tıklayın.

![Tanım animasyonuna göz atma](../ide/media/peek_definition.gif)

Açılan pencereden başka bir tanıma göz alıyorsa, açılan pencerede görüntülenen daireleri ve okları kullanarak gezinebileceğiniz bir içerik haritası yolu başlatabilirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: Açıklama tanımı kullanarak kodu görüntüleme ve düzenleme (alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Meta verileri kaynak kodu olarak görüntüle (C#)

C# türlerinin veya kaynak kodu kullanılamayan üyelerin tanımını görüntülediğinizde bunun yerine meta verileri görüntülenir. Türlerin ve üyelerin bildirimlerini görebilirsiniz, ancak uygulamalarını görüntüleyebilirsiniz.

Kaynak kodu kullanılamayan bir öğe için **Tanıma Git** veya **Açıklama Özeti** komutunu çalıştırdığınızda, kod Düzenleyicisi 'nde, kaynak kodu olarak gösterilen öğenin meta verilerinin bir görünümünü içeren sekmeli bir belge görüntülenir. Türün adı, ardından **gelen [meta verilerden]** belge sekmesinde görünür.

Örneğin, için **tanımına git** komutunu çalıştırırsanız <xref:System.Console> , meta veriler <xref:System.Console> kod düzenleyicisinde C# kaynak kodu olarak görünür. Kod bildirimine benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> iç olarak işaretlenen türler veya üyeler için **tanıma git** veya **göz atma** komutunu çalıştırmayı denediğinizde, başvuran derlemenin arkadaş olup olmamasına bakılmaksızın meta verilerini kaynak kodu olarak görüntülemez Visual Studio.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Meta veriler yerine ayrıştırılmış kaynak tanımlarını görüntüleme (C#)

Kaynak kodu kullanılamayan bir C# türünün veya üyenin tanımını görüntülediğinizde, ayrıştırılmış kaynak kodunu görmek için bir seçenek belirleyebilirsiniz. Bu özelliği etkinleştirmek için menü çubuğundan **Araçlar**  >  **Seçenekler** ' i seçin. Ardından, **metin düzenleyici**  >  **C#**  >  **Gelişmiş**' i genişletin ve **derlenen kaynaklar için gezintiyi etkinleştir**' i seçin.

![Ayrıştırılmış bir tanımı görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio ılspy dederlemesini kullanarak yöntem gövdelerini yeniden oluşturur. Bu özelliğe ilk kez eriştiğinizde, yazılım lisanslama ve telif hakkı ve ticari marka yasaları ile ilgili yasal bir vazgeçme belgesi kabul etmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Koda git](../ide/navigating-code.md)
- [Nasıl yapılır: Özet tanımı 'nı kullanarak kodu görüntüleme ve düzenleme (alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
