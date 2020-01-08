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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592080"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiriciler genellikle kendi kodlarında türler veya sınıf üyeleri kullandıkları için kaynak kod tanımlarını görüntülemek gerekir. Visual Studio'da **tanıma** ve **Özet tanım** özelliklerini kolayca tür veya üyenin tanımı görüntülemek etkinleştirin. Meta veri, kaynak kodu kullanılabilir durumda değilse, bunun yerine görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** özelliği bir tür veya üyenin kaynağına gider ve sonucu yeni bir sekmede açar. Bir klavye kullanıcısı kullanıyorsanız, metin imlecinizi bir yere sembol adının içine yerleştirin ve **F12**tuşuna basın. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Tanıma Git** ' i seçin veya aşağıdaki bölümde açıklanan **CTRL-tıklama** işlevini kullanın.

### <a name="ctrl-click-go-to-definition"></a>CTRL tuşunu tanımına Git

**Ctrl**+ **,** fare kullanıcılarına hızlı erişim için bir kısayoldur ve **Tanıma Git**. Semboller hale tıklanabilir bastığınızda **Ctrl** ve türe veya üyeye üzerine gelin. Sembol tanımını hızlıca gezinmek için basın **Ctrl** anahtar ve üzerine tıklayın. Bu kadar kolay!

![Fare tıklatın tanımı animasyon Git](../ide/media/click_gotodef.gif)

Fare tıklaması için değiştirici tuşunu değiştirebilirsiniz. **araçlar** > **seçenekler** > **metin > Düzenleyicisi** ' ne giderek, **genel**' i seçin ve **değiştirici tuşu kullan** açılır **listesinden alt veya** **CTRL**+**alt** ' i seçerek **Tanıma Git** ' i seçebilirsiniz. Fare tıklatın de devre dışı bırakabilirsiniz **tanıma** kaldırarak **tanıma gerçekleştirmek için fare tıklamasını etkinleştir** onay kutusu.

![Fare tıklatın etkinleştirme tanımına Git](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Tanıma göz at

**Özet tanım** özellik Düzenleyicisi'nde geçerli konumunuzu çıkmadan bir tür tanımı Önizleme olanak sağlar. Klavye kullanıcısıysanız yere tuşuna basın ve tür veya üye adı içindeki metin imleci yerleştirmeniz **Alt + F12**. Fare kullanıcısı kullanıyorsanız, sağ tıklama menüsünden **Açıklama tanımı** ' nı seçebilirsiniz.

**Ctrl**+etkinleştirmek için işlevler **' e tıklayın** , **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** **genel** > ' a gidin. Seçeneğini **tanımı Özet Görünümü'nde açın** tıklatıp **Tamam** kapatmak için **seçenekleri** iletişim kutusu.

![Fare tıklatın gözlem tanım seçeneği ayarlama](../ide/media/editor_options_peek_view.png)

Daha sonra basın **Ctrl** (veya hangi değiştirici tuşa seçili olduğundan **seçenekleri**), türe veya üyeye tıklayın.

![Özet tanım animasyon](../ide/media/peek_definition.gif)

Açılan pencereden başka bir tanıma göz alıyorsa, açılan pencerede görüntülenen daireleri ve okları kullanarak gezinebileceğiniz bir içerik haritası yolu başlatabilirsiniz.

Daha fazla bilgi için [nasıl yapılır: Özet tanım (Alt + F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Kaynak kodu olarak meta verileri görüntüleme (C#)

Tanımı görüntülediğinizde C# türleri veya üyeleri kaynak kodu kullanılabilir değil, meta veriler görüntüleniyor. Türleri ve üyeleri, ancak kendi uygulamalarını bildirimlerini görebilirsiniz.

Çalıştırdığınızda **tanıma** veya **Özet tanım** kaynak kodu kullanılamıyor, bir öğenin bu öğeye ait meta verilerin, kaynak kodu görüntülenen bir görünüm içeren sekmeli belge komutu Kod Düzenleyicisi'nde görünür. Türün adını ve ardından **[meta verilerden]** , belgenin sekmesinde görünür.

Örneğin çalıştırırsanız, **tanıma** komutunu <xref:System.Console>, meta verileri <xref:System.Console> Kod Düzenleyicisi görünür C# kaynak kodu. Kod bildiriminden benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> Çalıştırılacak çalıştığınızda **tanıma** veya **Özet tanım** komut türleri veya iç olarak işaretlenmiş üyeleri için Visual Studio görüntülemez meta verilerinin bağımsız olarak, kaynak kodu başvuru bütünleştirilmiş kod veya arkadaş olur.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Kaynak koda dönüştürülmüş kaynak tanımları yerine meta verileri görüntüleme (C#)

Kaynak kodu kullanılamayan bir C# türün veya üyenin tanımını görüntülediğinizde, ayrıştırılmış kaynak kodunu görmek için bir seçenek belirleyebilirsiniz. Bu özelliği etkinleştirmek için seçin **Araçları** > **seçenekleri** menü çubuğundan. Ardından, **metin düzenleyici** > **C#**  > **Gelişmiş**seçip **kaynak koda dönüştürülmüş kaynaklara gezintiyi etkinleştir** .

![Kaynak koda dönüştürülmüş tanımını görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio metot gövdeleri yetenek ılspy kullanarak yeniden oluşturur. Bu özellik, erişim ilk kez ticari marka yasaları ve yazılım lisans ve telif hakkı ile ilgili yasal Sorumluluklar kabul gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod gidin](../ide/navigating-code.md)
- [Nasıl yapılır: Özet tanım (Alt + F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
