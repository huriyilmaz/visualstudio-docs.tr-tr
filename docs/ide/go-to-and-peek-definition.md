---
title: Tür tanımlarını görüntüleme
description: Bir tür veya üyenin tanımını kolayca görüntülemenizi sağlayan Tanıma Git ve Tanıma Göz At özelliklerini öğrenin.
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
ms.openlocfilehash: 8c09aad63a8d61de1b7d6289a5a49befb221728c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078342"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiricilerin genellikle kodlarında kullanmakta olduğu türler veya sınıf üyeleri için kaynak kod tanımlarını görüntülemesi gerekir. Bu Visual Studio Tanıma **Git** ve Tanıma Göz At **özellikleri,** bir tür veya üyenin tanımını kolayca görüntülemenizi sağlar. Kaynak kodu kullanılamıyorsa meta veriler görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

Tanıma **Git özelliği,** türün veya üyenin kaynağına gider ve sonucu yeni bir sekmede açar. Klavye kullanıcısıysanız metin imlecinizi sembol adının içine yerleştirerek **F12 tuşuna basın.** Fare kullanıcısıysanız sağ tıklama  menüsünde Tanıma Git'i seçin veya aşağıdaki bölümde açıklanan **Ctrl** tuşunu basılı tutarak tıklama işlevini kullanın.

### <a name="ctrl-click-go-to-definition"></a>Tanıma Git'e Ctrl tuşunu basılı tutarak tıklayın

**Ctrl tuşunu basılı tutarak** + **tıklama,** fare kullanıcılarının Tanıma Git'e hızlıca erişmesi **için bir kısayol sağlar.** Ctrl tuşuna basarak tür veya **üyenin üzerine** gelindiğinde simgeler tıklanabilir hale geldi. Bir sembolün tanımına hızla gitmek için **Ctrl tuşuna basın** ve simgeye tıklayın. Bu kadar kolay!

![Fare tıklaması tanıma animasyona git](../ide/media/click_gotodef.gif)

Araçlar Seçenekler Metin Düzenleyici Genel'e  gidip Değiştiriciyi kullan açılan menüsünden Alt veya Ctrl Alt tuşlarını seçerek fareyle tanıma git'e yönelik değiştirici tuşunu  >    >    >     +  değiştirebilirsiniz.  Tanıma Git gerçekleştirmek için fare **tıklamasını** etkinleştir onay kutusunun işaretini kaldırarak da fareyle tanıma **git'i devre dışı** abilirsiniz.

![Fare tıklamayı etkinleştirme tanıma git](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Tanıma Göz At

Tanıma **Göz At** özelliği, geçerli konumunuz düzenleyicide bırakmadan bir türün tanımının önizlemesini oluşturmanızı sağlar. Klavye kullanıcısıysanız metin imlecinizi tür veya üye adının içine yerleştirerek **Alt + F12 tuşlarına basın.** Fare kullanıcısıysanız sağ tıklama **menüsünden Tanıma** Göz At'ı seçebilirsiniz.

**Ctrl tıklama işlevini** + **etkinleştirmek** için Araçlar Seçenekler Metin **Düzenleyici**  >    >  **Genel'e**  >  **gidin.** Tanımı göz atma **görünümünde aç seçeneğini belirleyin ve** Seçenekler iletişim **kutusunu** kapatmak için **Tamam'a** tıklayın.

![Fareyle tıklamayla tanıma göz atma seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

Ardından **Ctrl tuşuna** basın (veya Seçenekler'de hangi değiştirici tuş seçiliyse) ve türe veya üyeye tıklayın.

![Tanıma göz atma animasyonu](../ide/media/peek_definition.gif)

Açılan penceredeki başka bir tanıma göz atarak açılan pencerenin üzerinde görünen daireleri ve okları kullanarak gezinebilirsiniz.

Daha fazla bilgi için, [bkz. How to: View and edit code by using Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Meta verileri kaynak kod olarak görüntüleme (C#)

Kaynak kodu kullanılabilir olmayan C# türlerinin veya üyelerin tanımını görüntülendiğinde, bunların meta verileri görüntülenir. Türlerin ve üyelerin bildirimlerini görebilir, ancak bunların uygulamalarına bakamayyrı.

Kaynak kodu **kullanılamayan** bir  öğe için Tanıma Git veya Tanıma Göz At komutunu çalıştırarak kod düzenleyicisinde bu öğenin meta verilerine ait görünümü içeren ve kaynak kod olarak görüntülenen sekmeli bir belge görüntülenir. Türün adı ve ardından **[meta verilerden]**, belgenin sekmesinde görünür.

Örneğin, için Tanıma **Git** komutunu çalıştırmanız, için <xref:System.Console> meta verileri <xref:System.Console> C# kaynak kodu olarak kod düzenleyicisinde görünür. Kod bildirimine benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> İç olarak işaretlenmiş  türler veya  üyeler için Tanıma Git veya Tanıma Göz At komutunu çalıştırmaya çalışabilirsiniz. Visual Studio, başvuran derlemenin arkadaş olup olmadığı ne olursa olsun meta verilerini kaynak kod olarak görüntülemez.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Meta veriler yerine kaynak tanımlarını görüntüleme (C#)

Kaynak kodu kullanılamayan bir C# türünün veya üyesinin tanımını görüntüleseniz, kaynak kodunu görmek için bir seçenek ayarlayın. Bu özelliği açmak için menü  >  **çubuğundan Araçlar** Seçenekler'i seçin. Ardından Metin Düzenleyici  >  **C# Gelişmiş'i**  >  **genişletin** ve Kaynaklarda **gezinmeyi etkinleştir'i seçin.**

![Compiled tanımını görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio ILSpy decompilation kullanarak yöntem gövdelerini yeniden yapılandırıyor. Bu özelle ilk kez erişin, yazılım lisanslama ve telif hakkı ve ticari marka yasalarıyla ilgili yasal bir sorumluluk reddini kabul edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
- [Nasıllı: Tanıma Göz At (Alt+F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
