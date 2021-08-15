---
title: C# IntelliSense
description: C# projenizi kodlarken kullanabileceğiniz bazı IntelliSense özellikleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 92717a55fb25c8a4d5662cb544eeb61d42fdce6b5d1356709b4b0f4d4d86b60b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121289237"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense, düzenleyicide kod kodlarken ve Anında mod komut penceresinde hata [ayıklarken](../ide/reference/immediate-window.md) kullanılabilir.

## <a name="completion-lists"></a>Tamamlama listeleri

C# içinde IntelliSense tamamlama listeleri Liste Üyeleri, Tam Sözcük ve daha fazlasının belirteçlerini içerir. Aşağıdakilere hızlı erişim sağlar:

- Bir türün veya ad alanının üyeleri

- Değişkenler, komutlar ve işlev adları

- Kod parçacıkları

- Dil anahtar sözcükleri

- Genişletme yöntemleri

C# içinde tamamlama listesi ayrıca ilgisiz belirteçleri filtreleye ve bağlama göre bir belirteci önceden seçecek kadar akıllıdır. Daha fazla bilgi için [bkz. Filtrelenmiş tamamlama listeleri.](#filtered-completion-lists)

### <a name="code-snippets-in-completion-lists"></a>Tamamlama listelerinde kod parçacıkları

C# içinde tamamlama listesi, önceden tanımlanmış kod gövdelerini programınıza kolayca eklemenize yardımcı olacak kod parçacıkları içerir. Kod parçacıkları tamamlama listesinde kod parçacığının kısayol metni [olarak görünür.](../ide/code-snippets-schema-reference.md#shortcut-element) Varsayılan olarak C# ile kullanılabilen kod parçacıkları hakkında daha fazla bilgi için bkz. [C# kod parçacıkları.](../ide/visual-csharp-code-snippets.md)

### <a name="language-keywords-in-completion-lists"></a>Tamamlama listelerinde dil anahtar sözcükleri

C# dilinde tamamlama listesi dil anahtar sözcüklerini de içerir. C# dili anahtar sözcükleri hakkında daha fazla bilgi için bkz. [C# anahtar sözcükleri.](/dotnet/csharp/language-reference/keywords/index)

### <a name="extension-methods-in-completion-lists"></a>Tamamlama listelerinde uzantı yöntemleri

C# içinde tamamlama listesi kapsamda olan uzantı yöntemlerini içerir.

> [!NOTE]
> Tamamlama listesi, nesneler için tüm uzantı yöntemlerini <xref:System.String> görüntülemez.

Uzantı yöntemleri, örnek yöntemlerden farklı bir simge kullanır. Liste simgesi başvuru kılavuzu için bkz. [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri.](../ide/class-view-and-object-browser-icons.md) Aynı adla bir örnek yöntemi ve genişletme yöntemi kapsamda olduğunda, tamamlama listesi uzantı yöntemi simgesini görüntüler.

### <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlama listeleri

IntelliSense, filtreleri kullanarak gereksiz üyeleri tamamlama listesinden kaldırır. C# bu öğeler için görünen tamamlama listelerini filtreler:

- **Arabirimler ve temel sınıflar:** IntelliSense, hem sınıf bildirimi temel listelerinde hem de arabirim listelerinde ve kısıtlama listelerinde öğeleri arabirim ve temel sınıf tamamlama listelerinden otomatik olarak kaldırır. Örneğin, enum'lar temel sınıflar için kullanılamaz, çünkü temel sınıflar için tamamlama listesinde enum'lar görünmez. Temel sınıfların tamamlanma listesi yalnızca arabirimleri ve ad alanlarını içerir. Listeden bir öğe seçer ve ardından virgül yazmazsanız, C# birden çok devralmayı desteklemez, çünkü IntelliSense temel sınıfları tamamlama listesinden kaldırır. Kısıtlama yan tümceleri için de aynı davranış oluşur.

- **Öznitelikler:** Bir türe öznitelik uygulayan tamamlama listesi, listenin yalnızca gibi bu türleri içeren ad alanlarından azalan türleri içermesi için filtrelenmiş <xref:System.Attribute> olur.

- **Catch yan tümceleri**

- **Nesne başlatıcılar:** Yalnızca başlatılmış üyeler tamamlama listesinde görünür.

- **new anahtar** sözcüğü: `new` Yazarak Boşluk tuşuna **basıyorsanız** bir tamamlama listesi görüntülenir. Kod içeriğinizin bağlamına bağlı olarak listede otomatik olarak bir öğe seçilir. Örneğin, yöntemlerdeki bildirim ve dönüş deyimleri için tamamlama listesinde öğeler otomatik olarak seçilir.

- **enum anahtar** sözcüğü: Bir enum **ataması için** eşit işaretin ardından Boşluk tuşuna basıldıktan sonra bir tamamlama listesi görüntülenir. Kod içeriğinizin bağlamına bağlı olarak listede otomatik olarak bir öğe seçilir. Örneğin, anahtar sözcük dönüş yazınca ve bir bildirim ekleyebilirsiniz.

- **ve işleçleri:** veya anahtar sözcüğünü yazdikten sonra **Boşluk** tuşuna basarak filtrelenmiş tamamlama listesi otomatik `as` olarak `is` görüntülenir.

- **Olaylar:** anahtar sözcüğünü yazarak `event` tamamlama listesi yalnızca temsilci türlerini içerir.

- **Parametre yardımı,** siz girdikleri zaman parametrelerle eşleşen ilk yöntem aşırı yüklemesi için otomatik olarak sıralamaya yardımcı olur. Birden çok yöntem aşırı yüklemesi varsa, listede bir sonraki olası aşırı yüklemeye gitmek için yukarı ve aşağı okları kullanabilirsiniz.

### <a name="most-recently-used-members"></a>En son kullanılan üyeler

IntelliSense, otomatik nesne adı tamamlama için açılan Liste Üyeleri kutusunda [son](../ide/using-intellisense.md) seçtiğiniz üyeleri anımsar. Üye Listesi'nin **bir sonraki kullanımında** en son kullanılan üyeler en üstte gösterilir. En son kullanılan üyelerin geçmişi, her oturum Visual Studio temiz.

### <a name="override"></a>override

Geçersiz kılmaya [ve](/dotnet/csharp/language-reference/keywords/override) ardından **Boşluk'a** basıyorsanız, IntelliSense bir açılır liste kutusunda geçersiz kılabilirsiniz geçerli tüm temel sınıf üyelerini görüntüler. Sonrasında yönteminin dönüş türünü yazmak, `override` IntelliSense'den yalnızca aynı türün dönüş yöntemini göstermelerini istenir. IntelliSense herhangi bir eşleşme bulamazsa, tüm temel sınıf üyelerini görüntüler.

### <a name="ai-enhanced-intellisense"></a>AI ile geliştirilmiş IntelliSense

[Visual Studio IntelliCode,](/visualstudio/intellicode/intellicode-visual-studio) yapay zeka destekli IntelliSense tamamlama listeleri sağlar. IntelliCode, yalnızca alfabetik bir üye listesi sunmak yerine kullanmak için en doğru API'yi tahmin ediyor. Dinamik listeyi sağlamak için geçerli kod bağlamınızı ve desenlerinizi kullanır.

## <a name="automatic-code-generation"></a>Otomatik kod oluşturma

### <a name="add-using"></a>using Ekle

IntelliSense **kullanarak** ekle işlemi, kod dosyanıza `using` gerekli yönergeyi otomatik olarak ekler. Bu özellik, odağınızı kodun başka bir parçasına kaydırmanızı gerektirmek yerine, yazmakta olduğu koda odaklanmanızı sağlar.

Add **using işlemi başlatmak** için imleci çözümlenemez bir tür başvurusu üzerine getirin. Örneğin, bir konsol uygulaması oluşturdukta ve ardından yönteminin gövdesine eklerken, tür başvurusu çözümlenemedik diye bu kod satırına kırmızı bir `XmlReader` `Main` geçiş görünür. Ardından Hızlı Eylemler aracılığıyla **Kullanarak Ekle'yi** **çağırabilirsiniz.** Hızlı **Eylemler** yalnızca imleç, gelen türe yerleştirilene kadar görünür.

![Kullanarak ekleme, hızlı eylem genişletilmiş görüntü](../ide/media/addusing-quickaction.png)

Hata ampulü simgesine tıklayın ve ardından using yönergesi **System.Xml;** öğesini seçin.

### <a name="add-missing-using-directives-on-paste"></a>Yapıştırma sırasında eksik using yönergelerini ekle

Kod dosyanıza bir tür yapıştırırsanız IntelliSense, `using` kodunuz için eksik yönergeleri otomatik olarak ekleyebilir. Bu özellik, bir tür bir dosyaya yapıştırırken eksik using yönergeleri ekleme görevini otomatik olarak otomatik olarak size zaman kazandırır. Araçlar Seçenekler Metin **Düzenleyici** C# veya Temel Gelişmiş'te bu özelliği etkinleştirin ve yapıştırmak için Eksik  >    >    >   using   >   **yönergeleri ekle'yi seçin.**

### <a name="remove-and-sort-usings"></a>Kullanarak kaldırma ve sıralama

Kullanmaları **Kaldır ve Sırala seçeneği,** kaynak kodun davranışını değiştirmeden ve `using` `extern` bildirimlerini sıralar ve kaldırır. Zaman içinde, gereksiz ve düzensiz yönergeler nedeniyle kaynak dosyalar şişirilmiş ve okunma `using` zor hale gelir. Kullanmaları **Kaldır ve Sırala** seçeneği, kullanılmayan yönergeleri kaldırarak kaynak kodu sıkıştırarak `using` okunabilirliği artırır. Düzenle menüsünde **IntelliSense'i ve ardından** Kullanımı **Düzenle'yi seçin.** 

### <a name="implement-interface"></a>Arabirim uygulama

IntelliSense, kod düzenleyicisinde çalışırken arabirim [uygulamanıza](/dotnet/csharp/language-reference/keywords/interface) yardımcı olacak bir seçenek sağlar. Normalde, bir arabirimi düzgün uygulamak için, sınıfınıza arabirimin her üyesi için bir yöntem bildirimi oluşturmanız gerekir. IntelliSense'i kullanarak, bir sınıf bildiriminde arabirimin adını yazdikten sonra bir **Hızlı Eylemler** ampulü görüntülenir. Ampul, açık veya örtülü adlandırma kullanarak arabirimi otomatik olarak uygulama seçeneği sunar. Açık adlandırma altında yöntem bildirimleri arabirimin adını taşır. Örtülü adlandırmanın altında, yöntem bildirimleri ait olduğu arabirimi gösterir. Açıkça adlandırılmış bir arabirim yöntemine yalnızca bir arabirim örneği üzerinden erişilebilir, sınıf örneği üzerinden erişilemez. Daha fazla bilgi için [bkz. Açık arabirim uygulaması.](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)

Arabirimi Uygulama, arabirimi karşılamak için gereken en az sayıda yöntem saplamaları üretir. Bir temel sınıf arabirimin bölümlerini uygulayıyorsa, bu saplamalar yeniden üretillenmez.

### <a name="implement-abstract-base-class"></a>Soyut temel sınıf uygulama

IntelliSense, kod düzenleyicisinde çalışırken soyut bir temel sınıfın üyelerini otomatik olarak uygulamanıza yardımcı olacak bir seçenek sağlar. Normalde, soyut bir temel sınıfın üyelerini uygulamak için türetilmiş sınıfınıza soyut temel sınıfın her yöntemi için yeni bir yöntem tanımı oluşturulması gerekir. IntelliSense'i kullanarak, bir sınıf bildiriminde soyut bir temel sınıfın adını yazarak bir **Hızlı Eylemler** ampulü görüntülenir. Ampul, temel sınıf yöntemlerini otomatik olarak uygulama seçeneği sağlar.

Soyut Temel Sınıf Uygulama özelliği  tarafından oluşturulan yöntem saplamaları, *MethodStub.snippet* dosyasında tanımlanan kod parçacığı tarafından model oluşturulur. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için [bkz. Adım adım kılavuz: Kod parçacığı oluşturma.](../ide/walkthrough-creating-a-code-snippet.md)

### <a name="generate-from-usage"></a>Kullanımdan oluşturma

Kullanımdan **Oluştur özelliği,** sınıfları ve üyeleri tanımlamadan önce kullanmana olanak sağlar. Kullanmak istediğiniz ancak henüz tanımlamamış herhangi bir sınıf, Oluşturucu, yöntem, özellik, alan veya Enum için bir saplama oluşturabilirsiniz. Geçerli konumunuzu kodda bırakmadan yeni türler ve Üyeler oluşturabilirsiniz. Bu, iş akışınız için kesintiye en aza indirir.

Her tanımsız tanımlayıcı altında kırmızı dalgalı alt çizgi görünür. Fare işaretçisini tanımlayıcıda bıraktığınızda, araç ipucunda bir hata iletisi görüntülenir. Uygun seçenekleri göstermek için aşağıdaki yordamlardan birini kullanabilirsiniz:

- Tanımsız tanımlayıcıya tıklayın. Tanımlayıcının altında **hızlı bir eylem** hatası ampulü görünür. Ampul hatası ' na tıklayın.

- Tanımsız tanımlayıcıya tıklayın ve ardından CTRL tuşuna basın  + **.** (**CTRL** + nokta).

- Tanımsız tanımlayıcıya sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**' e tıklayın.

Görüntülenen seçenekler şunları içerebilir:

- **Özellik Oluştur**

- **Alan oluştur**

- **Metot oluşturma**

- **Sınıf üret**

- **Yeni tür oluşturma** (bir sınıf, yapı, arabirim veya sabit listesi için)

## <a name="generate-event-handlers"></a>Olay işleyicileri oluştur

IntelliSense, kod Düzenleyicisi 'nde Yöntemler (olay işleyicileri) ile olay alanlarını almanıza yardımcı olabilir.

`+=`Bir *. cs* dosyasındaki bir olay alanından sonra Işleci yazdığınızda, IntelliSense **sekme** tuşuna basarak bu seçeneği girmenizi ister. Bu, olayı işleme yöntemine işaret eden bir temsilcinin yeni bir örneğini ekler.

![Düğme otomatik kancası](../ide/media/vxautohookup.gif)

**Sekme** tuşuna basarsanız, IntelliSense sizin için ifadeyi otomatik olarak tamamlar ve olay işleyicisi başvurusunu kod düzenleyicisinde seçili metin olarak görüntüler. Otomatik olay kancaini tamamlayabilmeniz için, IntelliSense, olay işleyicisi için boş bir saplama oluşturmak üzere **Tab** tuşuna tekrar basmanız istenir.

![Olay Işleyicisi oluştur](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> IntelliSense tarafından oluşturulan yeni bir temsilci var olan bir olay işleyicisine başvuruyorsa, IntelliSense bu bilgileri araç ipucunda iletişim kurar. Bu başvuruyu daha sonra değiştirebilirsiniz; metin, kod düzenleyicisinde zaten seçilidir. Aksi takdirde, bu noktada otomatik olay kancau tamamlanmıştır.

**Sekme** tuşuna basarsanız, IntelliSense doğru imzaya sahip bir yöntemi dışarı yerleştirir ve imleci olay işleyicinizin gövdesine koyar.

> [!NOTE]
>  Olay kancası bildirimine geri dönmek için Görünüm menüsündeki **geri git** komutunu (Ctrl + **-** ) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
