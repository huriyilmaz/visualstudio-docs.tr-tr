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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592080"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiricilerin genellikle kodlarında kullandıkları türler veya sınıf üyeleri için kaynak kodu tanımlarını görüntülemeleri gerekir. Visual Studio'da, **Tanıma Git** ve **Peek Tanımı** özellikleri, bir türün veya üyenin tanımını kolayca görüntülemenizi sağlar. Kaynak kodu kullanılamıyorsa, bunun yerine meta veriler görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** özelliği bir türün veya üyenin kaynağına gider ve sonucu yeni bir sekmeyle açar. Klavye kullanıcısıysanız, metin imlecinizi sembol adının içinde bir yere yerleştirin ve **F12 tuşuna**basın. Fare kullanıcısıysanız, sağ tıklama menüsünden **Tanıma Git'i** seçin veya aşağıdaki bölümde açıklanan **Ctrl tıklama** işlevini kullanın.

### <a name="ctrl-click-go-to-definition"></a>Ctrl-click Tanımına Git

**Ctrl**+**tıklaması,** fare kullanıcılarının **Tanıma Git'e**hızla erişmeleri için bir kısayol. **Ctrl** tuşuna bastığınızda ve türünün veya üyenin üzerine geldiğinizde semboller tıklanabilir hale gelir. Bir sembolün tanımına hızla gitmek için **Ctrl** tuşuna basın ve üzerine tıklayın. Bu kadar kolay!

![Fare tıklaması tanım animasyongit](../ide/media/click_gotodef.gif)

 >  **Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi Genel'e**giderek ve **Kullan değiştirici anahtarı** açılır bırak'dan **Alt** veya **Ctrl**+**Alt'ı** seçerek fareyi tıklatın Tanıma **Git** tuşunu değiştirebilirsiniz.**Text Editor** Ayrıca, Tanıma Git onay kutusunu gerçekleştirmek için **Fareyi Etkinleştir düğmesini** işaretleyerek **Fareyi** Tanıma Git'e tıklayın' seçeneğini devre dışı bırakabilirsiniz.

![Fare tıklatma tanıma gitme etkinleştirme](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Tanıma Göz At

**Peek Tanımı** özelliği, geçerli konumunuzu düzenleyicide bırakmadan bir türün tanımını önizlemenize olanak tanır. Klavye kullanıcısıysanız, metin imlecinizi yazının veya üye adının içinde bir yere yerleştirin ve **Alt + F12**tuşuna basın. Fare kullanıcısıysanız, sağ tıklama menüsünden **Peek Tanımı'nı** seçebilirsiniz.

**Ctrl**+**tıklatma** işlevini etkinleştirmek için **Araçlar** > **Seçenekleri** > Metin Genel**Yayın** > **Yönetmeni'ne**gidin. **Peek görünümünde tanımı aç** seçeneğini seçin ve **Seçenekler** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.

![Fare tıklaması peek tanımı seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

Ardından **Ctrl'ye** (veya **Seçenekler'de**hangi değiştirici tuşu seçilirse seçiliyse) tuşuna basın ve türe veya üyeye tıklayın.

![Peek tanımı animasyonu](../ide/media/peek_definition.gif)

Açılır pencereden başka bir tanıma bakarsanız, açılır pencerenin üzerinde görünen daireleri ve okları kullanarak gezinebileceğiniz bir kırıntı yolu başlatın.

Daha fazla bilgi için [bkz: Peek Definition (Alt+F12) kullanarak kodu görüntüleme ve düzenleme.](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

## <a name="view-metadata-as-source-code-c"></a>Meta verileri kaynak kodu olarak görüntüleme (C#)

C# türlerinin veya kaynak kodu kullanılamayan üyelerin tanımını görüntülediğinizde, bunun yerine meta verileri görüntülenir. Türlerin ve üyelerin bildirimlerini görebilirsiniz, ancak uygulamalarını göremezsiniz.

Kaynak kodu kullanılamayan bir öğe için **Tanım alete git** veya **Peek Tanımı** komutunu çalıştırdığınızda, kod düzenleyicisinde kaynak kodu olarak görüntülenen öğenin meta verilerinin görünümünü içeren sekmeli bir belge görüntülenir. [meta **verilerden]** ardından türün adı, belgenin sekmesinde görünür.

Örneğin, için **Tanıma Git** komutunu <xref:System.Console>çalıştırırsanız, kod düzenleyicisinde C# kaynak kodu olarak <xref:System.Console> görünür. Kod bildirimine benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> Dahili olarak işaretlenmiş türler veya üyeler için **Tanıma Git** veya **Peek Tanımı** komutunu çalıştırmaya çalıştığınızda, Visual Studio başvuru derlemesinin arkadaş olup olmadığına bakılmaksızın meta verilerini kaynak kodu olarak görüntülemez.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Meta veri yerine derlenmiş kaynak tanımlarını görüntüleme (C#)

C# türü veya kaynak kodu kullanılamayan üyenin tanımını görüntülediğinizde derlenmiş kaynak kodunu görmek için bir seçenek ayarlayabilirsiniz. Bu özelliği açmak için menü çubuğundan **Araçlar** > **Seçenekleri'ni** seçin. Ardından, **Metin Düzenleyicisi** > **C#** > **Advanced'i**genişletin ve **derlenmiş kaynaklara gezinmeyi etkinleştir'i**seçin.

![Derlenmiş bir tanımı görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio, ILSpy decompilation kullanarak yöntem gövdelerini yeniden yapılandırmaya devam eder. Bu özelliğe ilk kez eriştiğınızda, yazılım lisanslama, telif hakkı ve ticari marka yasalarıyla ilgili yasal bir feragatnameyi kabul etmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
- [Nasıl yapılır: Peek Definition (Alt+F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
