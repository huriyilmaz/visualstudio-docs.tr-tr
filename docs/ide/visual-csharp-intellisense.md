---
title: C# IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2ed5d86599fa99b9c1360b414b37ef95ab59082d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303031"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense, editörde kodlama yaparken ve [Anında mod](../ide/reference/immediate-window.md) komut penceresinde hata ayıklama yaparken kullanılabilir.

## <a name="completion-lists"></a>Tamamlama listeleri

C#'daki IntelliSense tamamlama listeleri Liste Üyeleri, Komple Word ve daha fazlasının belirteçlerini içerir. Hızlı erişim sağlar:

- Bir türün veya ad alanının üyeleri

- Değişkenler, komutlar ve işlev adları

- Kod parçacıkları

- Dil anahtar kelimeleri

- Uzatma yöntemleri

C#'daki tamamlanma listesi, alakasız belirteçleri filtreleyecek ve içeriğe dayalı bir belirteç önceden seçecek kadar da akıllıdır. Daha fazla bilgi için [filtreuygulanmış tamamlama listelerine](#filtered-completion-lists)bakın.

### <a name="code-snippets-in-completion-lists"></a>Tamamlama listelerindeki kod parçacıkları

C#'da, tamamlanma listesi, programınıza önceden tanımlanmış kod gövdelerini kolayca eklemenize yardımcı olacak kod parçacıkları içerir. Kod parçacıkları tamamlanma listesinde snippet'in [kısayol metni](../ide/code-snippets-schema-reference.md#shortcut-element)olarak görünür. Varsayılan olarak C# olarak kullanılabilen kod parçacıkları hakkında daha fazla bilgi için [C# kod parçacıklarına](../ide/visual-csharp-code-snippets.md)bakın.

### <a name="language-keywords-in-completion-lists"></a>Tamamlama listelerindeki dil anahtar kelimeleri

C#'da, tamamlama listesi dil anahtar kelimelerini de içerir. C# dil anahtar kelimeleri hakkında daha fazla bilgi için [C# anahtar kelimelerine](/dotnet/csharp/language-reference/keywords/index)bakın.

### <a name="extension-methods-in-completion-lists"></a>Tamamlama listelerindeki uzantı yöntemleri

C#'da, tamamlama listesi kapsamda olan uzantı yöntemlerini içerir.

> [!NOTE]
> Tamamlama listesi nesneler için <xref:System.String> tüm uzantı yöntemlerini görüntülemez.

Uzantı yöntemleri, örnek yöntemlerinden farklı bir simge kullanır. Liste simgesi başvuru kılavuzu için [Sınıf Görünümü ve Nesne Tarayıcı simgelerine](../ide/class-view-and-object-browser-icons.md)bakın. Aynı ada sahip bir örnek yöntemi ve uzantı yöntemi her ikisi de kapsam içinde olduğunda, tamamlama listesi uzantı yöntemi simgesini görüntüler.

### <a name="filtered-completion-lists"></a>Filtreuygulanmış tamamlama listeleri

IntelliSense, gereksiz üyeleri filtreler kullanarak tamamlama listesinden kaldırır. C# bu öğeler için görünen tamamlanma listelerini filtreler:

- **Arabirimler ve temel sınıflar**: IntelliSense, hem sınıf bildirim tabanı hem de arabirim listelerinde ve kısıtlama listelerinde öğeleri arabirim ve taban sınıf tamamlama listelerinden otomatik olarak kaldırır. Örneğin, enums temel sınıflar için kullanılabilir olduğundan, temel sınıflar için tamamlanma listesinde görünmez. Temel sınıfların tamamlanma listesi yalnızca arabirimler ve ad alanları içerir. Listede bir öğe seçip virgül yazarsanız, C# birden çok kalıtım desteklemediği için IntelliSense temel sınıfları tamamlama listesinden kaldırır. Aynı davranış kısıtlama yan tümceleri için de oluşur.

- **Öznitelikler**: Bir türe öznitelik uyguladığınız zaman, tamamlanma listesi yalnızca bu türleri içeren ad alanlarından gelen türleri <xref:System.Attribute>içerecek şekilde filtrelenir.

- **Yan tümceleri yakalama**

- **Nesne baş harfleri**: Yalnızca başlangıç yapılabilir üyeler tamamlanma listesinde görünür.

- **yeni anahtar kelime**: `new` **Boşluk**yazıp sonra tuşuna bastığında, bir tamamlama listesi görüntülenir. Bir öğe, kodunuzdaki içeriğe bağlı olarak listede otomatik olarak seçilir. Örneğin, maddeler otomatik olarak bildirimler ve yöntemlerdeki iade deyimleri için tamamlanma listesinde seçilir.

- **enum anahtar kelime**: Bir enum atamaiçin eşit bir işaret ten sonra **Boşluk** tuşuna bastığınızda, bir tamamlama listesi görüntülenir. Bir öğe, kodunuzdaki içeriğe bağlı olarak listede otomatik olarak seçilir. Örneğin, anahtar kelime iadesini yazdıktan sonra ve bir bildirim yaptığınızda öğeler tamamlanma listesinde otomatik olarak seçilir.

- **gibi ve olduğu gibi**: Filtreuygulanmış bir tamamlama listesi, boşluk `as` veya `is` anahtar kelimeyazdıktan sonra **Boşluk** tuşuna bastığında otomatik olarak görüntülenir.

- **Etkinlikler**: Anahtar kelimeyi `event`yazdığınızda, tamamlanma listesi yalnızca temsilci türlerini içerir.

- **Parametre,** siz girerken parametrelerle eşleşen ilk yöntemaşırı yüklemesine otomatik olarak sıralar. Birden çok yöntem aşırı yüklemesi varsa, listedeki bir sonraki olası aşırı yüklemeye gitmek için yukarı ve aşağı okları kullanabilirsiniz.

### <a name="most-recently-used-members"></a>En son kullanılan üyeler

IntelliSense, otomatik nesne adı tamamlama için açılan [liste üyeleri](../ide/using-intellisense.md) kutusunda yakın zamanda seçtiğiniz üyeleri hatırlar. **Üye Listesini**bir sonraki kez kullandığınızda, en son kullanılan üyeler en üstte gösterilir. En son kullanılan üyelerin geçmişi her Visual Studio oturumu arasında temizlenir.

### <a name="override"></a>override

[Geçersiz kılma](/dotnet/csharp/language-reference/keywords/override) yazıp **Boşluk tuşuna**bastığınızda, IntelliSense açılır liste kutusunda geçersiz kılabileceğiniz tüm geçerli taban sınıf üyelerini görüntüler. Yöntemin dönüş türünü, `override` IntelliSense'in yalnızca aynı türü döndüren yöntemleri göstermesini istedimkten sonra yazmak. IntelliSense eşleşme bulamadığında, tüm taban sınıf üyelerini görüntüler.

### <a name="ai-enhanced-intellisense"></a>AI-geliştirilmiş IntelliSense

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) yapay zeka ile geliştirilmiş IntelliSense tamamlama listeleri sağlar. IntelliCode, alfabetik bir üye listesi sunmak yerine kullanılacak en olası doğru API'yi tahmin eder. Dinamik listeyi sağlamak için geçerli kod bağlamınızı ve desenlerinizi kullanır.

## <a name="automatic-code-generation"></a>Otomatik kod oluşturma

### <a name="add-using"></a>using Ekle

IntelliSense işlemini **kullanarak Ekle** işlemi, kod dosyanıza gerekli `using` yönergeyi otomatik olarak ekler. Bu özellik, odağınızı kodun başka bir bölümüne kaydırmanızı gerektirmek yerine yazdığınız koda odaklanmanızı sağlar.

**Ekle işlemini başlatmak** için imleci çözülemeyen bir tür referansına yerleştirin. Örneğin, bir konsol uygulaması oluşturup `XmlReader` `Main` yöntemin gövdesine eklediğinizde, tür başvurusu çözülemediğinden bu kod satırında kırmızı bir dalgalı lık görüntülenir. Daha sonra **Hızlı Eylemler**aracılığıyla **Add'i arayabilirsiniz.** **Hızlı Eylemler** yalnızca imleç bağlanmamış türe yerleştirildiğinde görünür.

![Kullanarak ekleme, hızlı eylem genişletilmiş görüntü](../ide/media/addusing-quickaction.png)

Hata ampulü simgesini tıklatın ve ardından **System.Xml'i kullanmayı seçin;**

### <a name="remove-and-sort-usings"></a>Kullanımı kaldırma ve sıralama

**Usings'i Kaldır ve Sırala** seçeneği, kaynak kodun davranışını değiştirmeden sıralar `using` ve kaldırır ve `extern` bildirimleri sunar. Zaman içinde, kaynak dosyaları şişirilmiş ve gereksiz ve düzensiz `using` yönergeler nedeniyle okunması zor olabilir. **Kullanve Kaldır** seçeneği, kullanılmayan `using` yönergeleri kaldırarak kaynak kodunu sıkıştırAr ve bunları sıralayarak okunabilirliği artırır. **Düzenle** menüsünde **IntelliSense'i**seçin ve ardından **Kullanımı Düzenle'yi**seçin.

### <a name="implement-interface"></a>Arabirim uygulama

IntelliSense, kod düzenleyicisinde çalışırken bir [arabirim](/dotnet/csharp/language-reference/keywords/interface) uygulamanıza yardımcı olacak bir seçenek sunar. Normalde, bir arabirimi düzgün bir şekilde uygulamak için, sınıfınızdaki arabirimin her üyesi için bir yöntem bildirimi oluşturmanız gerekir. IntelliSense kullanarak, bir sınıf bildiriminde bir arabirimin adını yazdıktan sonra, **Hızlı Eylemler** ampulgörüntülenir. Ampul, açık veya örtülü adlandırma kullanarak arabirimi otomatik olarak uygulama seçeneği sunar. Açık adlandırma altında, yöntem bildirimleri arabirimin adını taşır. Örtülü adlandırma altında, yöntem bildirimleri ait oldukları arabirimi göstermez. Açıkça adlandırılmış arabirim yöntemine yalnızca bir arabirim örneği üzerinden erişilebilir, sınıf örneği üzerinden değil. Daha fazla bilgi için açık [arabirim uygulamasına](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)bakın.

Arabirimi Uygula, arabirimi karşılamak için gereken en az sayıda yöntem saplaması oluşturur. Bir taban sınıf arabirimin bölümlerini uygularsa, bu saplamalar yeniden oluşturulmaz.

### <a name="implement-abstract-base-class"></a>Soyut taban sınıf uygulama

IntelliSense, kod düzenleyicisinde çalışırken soyut bir taban sınıfın üyelerini otomatik olarak uygulamanıza yardımcı olacak bir seçenek sunar. Normalde, soyut bir taban sınıfının üyelerini uygulamak için türemiş sınıfınızdaki soyut taban sınıfın her yöntemi için yeni bir yöntem tanımı oluşturulması nı gerektirir. IntelliSense kullanılarak, bir sınıf bildiriminde soyut bir taban sınıfın adını yazdıktan sonra, **Hızlı Eylemler** ampulü görüntülenir. Ampul, taban sınıf yöntemlerini otomatik olarak uygulama seçeneği sunar.

**Soyut Taban Sınıf Uygula** özelliği tarafından oluşturulan yöntem saplamaları, *MethodStub.snippet*dosyasında tanımlanan kod parçacığı ile modellenir. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için [Bkz. Walkthrough: Kod parçacığı oluşturun.](../ide/walkthrough-creating-a-code-snippet.md)

### <a name="generate-from-usage"></a>Kullanımdan üretin

**Kullanımdan Oluştur** özelliği, sınıfı ve üyeleri tanımlamadan önce kullanmanıza olanak tanır. Kullanmak istediğiniz ancak henüz tanımlanmamış herhangi bir sınıf, oluşturucu, yöntem, özellik, alan veya enum için bir saplama oluşturabilirsiniz. Geçerli konumunuzu kodda bırakmadan yeni türler ve üyeler oluşturabilirsiniz. Bu, iş akışınızın kesintiye uğramasını en aza indirir.

Tanımlanmamış her tanımlayıcının altında kırmızı dalgalı bir alt çizgi görünür. Fare işaretçisini tanımlayıcıya dayandırken, bir araç ipucunda bir hata iletisi görüntülenir. Uygun seçenekleri görüntülemek için aşağıdaki yordamlardan birini kullanabilirsiniz:

- Tanımlanmamış tanımlayıcıyı tıklatın. **Hızlı Eylemler** hata ampul tanımlayıcıaltında görünür. Hata ampulü tıklatın.

- Tanımlanmamış tanımlayıcıyı tıklatın ve ardından **Ctrl**+**tuşuna basın.** (**Ctrl** + dönem).

- Tanımlanmamış tanımlayıcıyı sağ tıklatın ve ardından **Hızlı Eylemler ve Yeniden Düzenleme'yi**tıklatın.

Görünen seçenekler aşağıdakileri içerebilir:

- **Özellik oluşturma**

- **Alan oluşturma**

- **Metot oluşturma**

- **Sınıf oluşturma**

- **Yeni tür oluşturma** (sınıf, yapı, arayüz veya enum için)

## <a name="generate-event-handlers"></a>Olay işleyicileri oluşturma

Kod düzenleyicisinde, IntelliSense yöntem (olay işleyicileri) olay alanlarına bağlamanıza yardımcı olabilir.

Bir `+=` *.cs* dosyasına bir olay alanından sonra işleci yazdığınızda, IntelliSense **sekme** tuşuna basma seçeneğini sorar. Bu, olayı işleme yöntemine işaret eden yeni bir temsilci örneği ekler.

![Düğme Otomatik Kanca](../ide/media/vxautohookup.gif)

**Sekme**tuşuna baslarsanız, IntelliSense deyimi otomatik olarak sizin için tamamlar ve olay işleyicisi referansını kod düzenleyicisinde seçili metin olarak görüntüler. Otomatik olay bağlantısını tamamlamak için, IntelliSense olay işleyicisi için boş bir saplama oluşturmak için **Sekme** tuşuna yeniden basmanızı ister.

![Olay Işleyicisi Oluştur](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> IntelliSense tarafından oluşturulan yeni bir temsilci varolan bir olay işleyicisine başvuruyorsa, IntelliSense bu bilgileri araç ipucunda iletir. Daha sonra bu başvurudeğiştirebilirsiniz; metin zaten kod düzenleyicisinde seçilir. Aksi takdirde, otomatik olay bağlantısı bu noktada tamamlanır.

**Sekme**tuşuna basarsanız, IntelliSense doğru imzayla bir yöntem çıkarır ve imleci olay işleyicinizin gövdesine koyar.

> [!NOTE]
> Olay bağlantı deyimine geri dönmek için **Görünüm** menüsünde **(Ctrl)**+**-** **Geriye Git** komutunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Görsel Stüdyo IDE](../get-started/visual-studio-ide.md)
