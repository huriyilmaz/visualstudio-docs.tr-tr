---
title: Tür tanımlarını görüntüleme
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d78614966a33421aac707f370f2b18e62e4b3d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603539"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiricilerin genellikle kendi kodlarında kullandıkları türler veya sınıf üyeleri için kaynak kodu tanımlarını görüntülemesi gerekir. Visual Studio 'da, tanım ve Özet **tanım** özelliklerine **Git** özelliği, bir tür veya üyenin tanımını kolayca görüntülemenizi sağlar. Kaynak kodu yoksa, bunun yerine meta veriler görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** özelliği bir tür veya üyenin kaynağına gider ve sonucu yeni bir sekmede açar. Bir klavye kullanıcısı kullanıyorsanız, metin imlecinizi bir yere sembol adının içine yerleştirin ve **F12**tuşuna basın. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Tanıma Git** ' i seçin veya aşağıdaki bölümde açıklanan **CTRL-tıklama** işlevini kullanın.

### <a name="ctrl-click-go-to-definition"></a>CTRL-tanıma git ' e tıklayın

**Ctrl** + **,** fare kullanıcılarına hızlı erişim için bir kısayoldur ve **Tanıma Git**. **CTRL** tuşuna bastığınızda ve türün ya da üyenin üzerine geldiğinizde semboller tıklatılabilir hale gelir. Bir simgenin tanımına hızlıca gitmek için **CTRL** tuşuna basın ve ardından üzerine tıklayın. Bu kadar kolay!

![Fare tıklaması tanım animasyonuna git](../ide/media/click_gotodef.gif)

Fare tıklaması için değiştirici tuşunu değiştirebilirsiniz. **araçlar**  > **seçenekler**  > **metin  >  Düzenleyicisi** ' ne giderek**genel**' **i veya** **CTRL** 0 alt ' i seçerek **Tanıma Git** ' e tıklayın. **değiştirici anahtarını kullan** açılır listesinden. Fare **tıklamasını** devre dışı bırakmak için fare tıklamasını **Etkinleştir** onay kutusunun işaretini kaldırın.

![Fare tıklamasını etkinleştirme tanıma git](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Açıklama Özeti

Özet **tanım** özelliği, bir türün tanımını düzenleyicide geçerli konumundan çıkmadan önizlemenizi sağlar. Bir klavye kullanıcısı kullanıyorsanız, metin imlecinizi bir yere tür veya üye adının içine yerleştirin ve **alt + F12**tuşlarına basın. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Açıklama tanımı** ' nı seçebilirsiniz.

**Ctrl** + etkinleştirmek için işlevler **' e tıklayın** , **Araçlar**  > **Seçenekler**  > **metin Düzenleyicisi** **genel** >  ' a gidin. **Göz atma görünümü ' nde tanımı aç** seçeneğini belirleyin ve **Seçenekler** Iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

![Fare tıklaması tanım seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

Ardından, **CTRL** tuşuna basın (veya **Seçenekler**'de herhangi bir değiştirici tuşu seçilidir) ve türe veya üyeye tıklayın.

![Tanım animasyonuna göz atma](../ide/media/peek_definition.gif)

Açılan pencereden başka bir tanıma göz alıyorsa, açılan pencerede görüntülenen daireleri ve okları kullanarak gezinebileceğiniz bir içerik haritası yolu başlatabilirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: Açıklama tanımı kullanarak kodu görüntüleme ve düzenleme (alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Meta verileri kaynak kodu olarak görüntüleC#()

Kaynak kodu kullanılamayan C# türlerin veya üyelerin tanımını görüntülediğinizde, onun meta verileri görüntülenir. Türlerin ve üyelerin bildirimlerini görebilirsiniz, ancak uygulamalarını görüntüleyebilirsiniz.

Kaynak kodu kullanılamayan bir öğe için **Tanıma Git** veya **Açıklama Özeti** komutunu çalıştırdığınızda, kod Düzenleyicisi 'nde, kaynak kodu olarak gösterilen öğenin meta verilerinin bir görünümünü içeren sekmeli bir belge görüntülenir. Türün adı, ardından **gelen [meta verilerden]** belge sekmesinde görünür.

Örneğin, <xref:System.Console> için **Tanıma Git** komutunu çalıştırırsanız, <xref:System.Console> meta verileri kod düzenleyicisinde kaynak kodu olarak C# görünür. Kod bildirimine benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> İç olarak işaretlenmiş türler veya Üyeler için **Tanıma Git** veya **Açıklama Özeti** komutunu çalıştırmayı denediğinizde, başvuran derlemenin arkadaş olup olmamasına bakılmaksızın Visual Studio meta verilerini kaynak kodu olarak görüntülemez.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Meta veri (C#) yerine ayrıştırılmış kaynak tanımlarını görüntüle

Kaynak kodu kullanılamayan bir C# türün veya üyenin tanımını görüntülediğinizde, ayrıştırılmış kaynak kodunu görmek için bir seçenek belirleyebilirsiniz. Bu özelliği etkinleştirmek için menü çubuğundan **araçlar**  > **Seçenekler** ' i seçin. Sonra,  > **gelişmiş** > **C#** **metin düzenleyici** ' yi genişletin ve **derlenmiş kaynaklara gezinmeyi etkinleştir**' i seçin.

![Ayrıştırılmış bir tanımı görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio ılspy dederlemesini kullanarak Yöntem gövdelerini yeniden oluşturur. Bu özelliğe ilk kez eriştiğinizde, yazılım lisanslama ve telif hakkı ve ticari marka yasaları ile ilgili yasal bir vazgeçme belgesi kabul etmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Koda git](../ide/navigating-code.md)
- [Nasıl yapılır: Özet tanımı 'nı kullanarak kodu görüntüleme ve düzenleme (alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)