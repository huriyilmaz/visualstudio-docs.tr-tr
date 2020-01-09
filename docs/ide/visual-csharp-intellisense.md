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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594181"
---
# <a name="c-intellisense"></a>C# IntelliSense

C#IntelliSense, düzenleyicide kodlarken ve [anında mod](../ide/reference/immediate-window.md) komut penceresinde hata ayıklarken kullanılabilir.

## <a name="completion-lists"></a>Tamamlanma listeleri

İçindeki C# IntelliSense tamamlanma listeleri, liste üyelerinden belirteçleri, tüm sözcüğü ve daha fazlasını içerir. Öğesine hızlı erişim sağlar:

- Bir türün veya ad alanının üyeleri

- Değişkenler, komutlar ve işlev adları

- Kod parçacıkları

- Dil anahtar sözcükleri

- Uzantı yöntemleri

' De C# tamamlanma listesi, ilgisiz belirteçleri filtreleyecek ve bağlam temelinde bir belirteci önceden seçecek kadar akıllı bir değer sağlar. Daha fazla bilgi için bkz. [filtrelenmiş tamamlanma listeleri](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Tamamlanma listelerindeki kod parçacıkları

' C#De, tamamlama listesi, önceden tanımlanmış kod gövdelerini programınıza kolayca ekleyebilmeniz için kod parçacıklarını içerir. Kod parçacıkları, parçacık [kısayol metni](../ide/code-snippets-schema-reference.md#shortcut-element)olarak tamamlama listesinde görünür. ' De C# varsayılan olarak bulunan kod parçacıkları hakkında daha fazla bilgi için bkz [ C# . kod parçacıkları](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Tamamlanma listelerinde dil anahtar sözcükleri

' C#De, tamamlanma listesi dil anahtar sözcüklerini de içerir. Dil anahtar sözcükleri hakkında C# daha fazla bilgi için bkz [ C# . anahtar sözcükler](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Tamamlanma listelerindeki genişletme yöntemleri

' C#De, tamamlanma listesi kapsamdaki genişletme yöntemlerini içerir.

> [!NOTE]
> Tamamlanma listesi <xref:System.String> nesneleri için tüm genişletme yöntemlerini görüntülemez.

Uzantı yöntemleri örnek metotlardan farklı bir simge kullanır. Liste simgesi başvuru kılavuzu için, bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Aynı ada sahip bir örnek yöntemi ve genişletme yöntemi her ikisi de kapsam içinde olduğunda, tamamlanma listesi uzantı yöntemi simgesini görüntüler.

### <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlanma listeleri

IntelliSense, filtre kullanarak gereksiz üyeleri tamamlama listesinden kaldırır. C#Bu öğeler için görüntülenen tamamlanma listelerine filtre uygular:

- **Arabirimler ve temel sınıflar**: IntelliSense hem sınıf bildirim tabanında hem de arabirim listelerinde ve kısıtlama listelerinde bulunan öğeleri arabirim ve temel sınıf tamamlama listelerinden otomatik olarak kaldırır. Örneğin, numaralandırmalar taban sınıflar için kullanılamadığından numaralandırmalar, temel sınıfların tamamlanma listesinde görünmez. Temel sınıfların tamamlanma listesi yalnızca arabirimler ve ad alanları içerir. Listeden bir öğe seçer ve sonra bir virgül yazarsanız, IntelliSense, birden fazla devralmayı desteklemediği için, temel sınıfları tamamlama listesinden C# kaldırır. Aynı davranış de kısıtlama yan tümceleri için oluşur.

- **Öznitelikler**: bir türe bir öznitelik uyguladığınızda, listenin yalnızca bu türleri içeren ad alanlarından (<xref:System.Attribute>gibi) ilgili türleri içermesi için tamamlama listesi filtrelenir.

- **Catch yan tümceleri**

- **Nesne başlatıcıları**: yalnızca başlatılmış Üyeler tamamlama listesinde görünür.

- **Yeni anahtar sözcük**: `new` yazdığınızda ve sonra **alana**bastığınızda bir tamamlama listesi görüntülenir. Kodunuzda bağlam temelinde, listede otomatik olarak bir öğe seçilir. Örneğin, öğeler için tamamlama listesinde ve metotlarda Return deyimlerinin öğeleri otomatik olarak seçilir.

- **enum anahtar sözcüğü**: bir Enum ataması için eşittir Işaretinden sonra **boşluğa** bastığınızda bir tamamlama listesi görüntülenir. Kodunuzda bağlam temelinde, listede otomatik olarak bir öğe seçilir. Örneğin, Return anahtar sözcüğünü yazdıktan sonra ve bir bildirim yaptığınızda öğeler tamamlama listesinde otomatik olarak seçilir.

- **as ve in işleçleri**: `as` veya `is` anahtar sözcüğünü yazdıktan sonra **alana** bastığınızda filtrelenmiş bir tamamlanma listesi otomatik olarak görüntülenir.

- **Olaylar**: `event`anahtar sözcüğünü yazdığınızda, tamamlanma listesi yalnızca temsilci türlerini içerir.

- **Parametre yardımı** , parametreleri girdiğiniz parametrelerle eşleşen ilk yöntem aşırı yüklemesini otomatik olarak sıralar. Birden çok yöntem aşırı yüklemesi varsa, listede bir sonraki olası aşırı yüklemeye gitmek için yukarı ve aşağı okları kullanabilirsiniz.

### <a name="most-recently-used-members"></a>En son kullanılan Üyeler

IntelliSense, otomatik nesne adı tamamlamada açılan [liste üyeleri](../ide/using-intellisense.md) kutusunda en son seçtiğiniz üyeleri anımsar. **Üye listesini**bir dahaki sefer kullandığınızda en son kullanılan Üyeler en üstte gösterilir. En son kullanılan üyelerin geçmişi her bir Visual Studio oturumu arasında temizlenir.

### <a name="override"></a>geçersiz kılma

[Geçersiz kılma](/dotnet/csharp/language-reference/keywords/override) yazın ve ardından **boşluk**tuşuna bastığınızda IntelliSense, bir açılır liste kutusunda geçersiz kılabileceğiniz geçerli temel sınıf üyelerini görüntüler. `override` sonra yöntemin dönüş türünü yazmak, IntelliSense 'in yalnızca aynı türü döndüren yöntemleri göstermesini ister. IntelliSense herhangi bir eşleşme bulamadığınızda, tüm temel sınıf üyelerini görüntüler.

### <a name="ai-enhanced-intellisense"></a>AI ile geliştirilmiş IntelliSense

[Visual Studio ıntellicode](/visualstudio/intellicode/intellicode-visual-studio) yapay zeka gelişmiş IntelliSense tamamlanma listeleri sağlar. Intellicode, yalnızca alfabetik bir üye listesini sunmak yerine, kullanmak için en olası doğru API 'YI tahmin eder. Dinamik listeyi sağlamak için geçerli kod bağlamını ve desenlerinizi kullanır.

## <a name="automatic-code-generation"></a>Otomatik kod oluşturma

### <a name="add-using"></a>using Ekle

IntelliSense **kullanarak Ekle** işlemi, gerekli `using` yönergesini kod dosyanıza otomatik olarak ekler. Bu özellik, odağınızı kodun başka bir bölümüne kaydırabilmeniz yerine, yazmakta olduğunuz koda odaklanmanızı sağlar.

**Using using** işlemini başlatmak için imleci çözümlenemeyen bir tür başvurusu üzerine konumlandırın. Örneğin, bir konsol uygulaması oluşturup `Main` yönteminin gövdesine `XmlReader` eklediğinizde, tür başvurusu çözümlenemediği için bu kod satırında kırmızı bir dalgalı çizgi görünür. Daha sonra **hızlı eylemler**aracılığıyla **ekleme komutunu** çağırabilirsiniz. **Hızlı eylemler** yalnızca imleç ilişkisiz türde konumlandırıldığında görünür.

![Kullanarak, hızlı eylem genişletilmiş görüntüsünü ekleyin](../ide/media/addusing-quickaction.png)

Hata ampulü simgesine tıklayın ve ardından using yönergesini otomatik olarak eklemek için **System. xml kullanarak** öğesini seçin.

### <a name="remove-and-sort-usings"></a>Using deyimlerini kaldırma ve sıralama

**Kaldırma ve sıralama** kullanımları seçeneği, kaynak kodu davranışını değiştirmeden `using` ve `extern` bildirimlerini sıralar ve kaldırır. Zaman içinde, kaynak dosyalar gereksiz ve düzensiz `using` yönergeleri nedeniyle okunabilir ve okunabilir hale gelebilir. **Kaldırma ve sıralama** kullanımları seçeneği, kullanılmayan `using` yönergelerini kaldırarak kaynak kodu sıkıştırır ve bunları sıralayarak okunabilirliği geliştirir. **Düzenle** menüsünde **IntelliSense**' i seçin ve ardından kullanımları **Düzenle**' yi seçin.

### <a name="implement-interface"></a>Arabirim uygulama

IntelliSense, kod Düzenleyicisi 'nde çalışırken bir [arabirimi](/dotnet/csharp/language-reference/keywords/interface) uygulamanıza yardımcı olacak bir seçenek sunar. Normalde, bir arabirimi düzgün bir şekilde uygulamak için sınıfınıza arabirimin her üyesi için bir yöntem bildirimi oluşturmanız gerekir. IntelliSense kullanarak bir sınıf bildiriminde bir arabirimin adını yazdıktan sonra **hızlı bir eylem** ampul görüntülenir. Ampul, açıkça veya örtük adlandırma kullanarak arabirimi otomatik olarak uygulama seçeneği sunar. Açık adlandırma altında yöntem bildirimleri arabirimin adını taşır. Örtük adlandırma altında yöntem bildirimleri ait oldukları arabirimi göstermez. Açıkça adlandırılmış bir arabirim yöntemine, bir sınıf örneği aracılığıyla değil, yalnızca bir arabirim örneği üzerinden erişilebilir. Daha fazla bilgi için bkz. [Açık arabirim uygulama](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Uygulama arabirimini sağlamak için gereken en az Yöntem saplamaları sayısını oluşturur. Bir temel sınıf arabirimin parçalarını uygularsa, bu saplamalar yeniden oluşturulmaz.

### <a name="implement-abstract-base-class"></a>Soyut temel sınıf Uygula

IntelliSense, kod Düzenleyicisi 'nde çalışırken soyut bir temel sınıfın üyelerini otomatik olarak uygulamanıza yardımcı olacak bir seçenek sunar. Normalde, soyut bir temel sınıfın üyelerini uygulamak için, türetilmiş sınıfınızdaki soyut temel sınıfın her bir yöntemi için yeni bir yöntem tanımı oluşturulmasını gerektirir. IntelliSense kullanarak bir sınıf bildiriminde soyut bir temel sınıfın adını yazdıktan sonra **hızlı bir eylem** ışığı görüntülenir. Ampul, size temel sınıf yöntemlerini otomatik olarak uygulama seçeneği sunar.

**Soyut temel sınıf Uygula** özelliği tarafından oluşturulan Yöntem saplamaları, *MethodStub. parçacığında*dosyasında tanımlanan kod parçacığına göre modellenir. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için bkz. [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Kullanımdan oluştur

**Kullanımdan oluştur** özelliği, sınıfları ve üyeleri tanımladıktan önce kullanmanıza olanak sağlar. Kullanmak istediğiniz ancak henüz tanımlamamış herhangi bir sınıf, Oluşturucu, yöntem, özellik, alan veya Enum için bir saplama oluşturabilirsiniz. Geçerli konumunuzu kodda bırakmadan yeni türler ve Üyeler oluşturabilirsiniz. Bu, iş akışınız için kesintiye en aza indirir.

Her tanımsız tanımlayıcı altında kırmızı dalgalı alt çizgi görünür. Fare işaretçisini tanımlayıcıda bıraktığınızda, araç ipucunda bir hata iletisi görüntülenir. Uygun seçenekleri göstermek için aşağıdaki yordamlardan birini kullanabilirsiniz:

- Tanımsız tanımlayıcıya tıklayın. Tanımlayıcının altında **hızlı bir eylem** hatası ampulü görünür. Ampul hatası ' na tıklayın.

- Tanımsız tanımlayıcıya ve ardından **Ctrl**+' a basın **.** (**CTRL** + nokta).

- Tanımsız tanımlayıcıya sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**' e tıklayın.

Görüntülenen seçenekler şunları içerebilir:

- **Özellik Oluştur**

- **Alan oluştur**

- **Metot oluşturma**

- **Sınıf üret**

- **Yeni tür oluşturma** (bir sınıf, yapı, arabirim veya sabit listesi için)

## <a name="generate-event-handlers"></a>Olay işleyicileri oluştur

IntelliSense, kod Düzenleyicisi 'nde Yöntemler (olay işleyicileri) ile olay alanlarını almanıza yardımcı olabilir.

Bir *. cs* dosyasındaki bir olay alanından sonra `+=` işlecini yazdığınızda, IntelliSense, **sekme** tuşuna basarak bu seçeneği girmenizi ister. Bu, olayı işleme yöntemine işaret eden bir temsilcinin yeni bir örneğini ekler.

![Düğme otomatik kancası](../ide/media/vxautohookup.gif)

**Sekme**tuşuna basarsanız, IntelliSense sizin için ifadeyi otomatik olarak tamamlar ve olay işleyicisi başvurusunu kod düzenleyicisinde seçili metin olarak görüntüler. Otomatik olay kancaini tamamlayabilmeniz için, IntelliSense, olay işleyicisi için boş bir saplama oluşturmak üzere **Tab** tuşuna tekrar basmanız istenir.

![Olay Işleyicisi oluştur](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> IntelliSense tarafından oluşturulan yeni bir temsilci var olan bir olay işleyicisine başvuruyorsa, IntelliSense bu bilgileri araç ipucunda iletişim kurar. Bu başvuruyu daha sonra değiştirebilirsiniz; metin, kod düzenleyicisinde zaten seçilidir. Aksi takdirde, bu noktada otomatik olay kancau tamamlanmıştır.

**Sekme**tuşuna basarsanız, IntelliSense doğru imzaya sahip bir yöntemi dışarı yerleştirir ve imleci olay işleyicinizin gövdesine koyar.

> [!NOTE]
> Olay kancası bildirimine geri dönmek için **Görünüm** menüsündeki **geri git** komutunu (**CTRL**+ **-** ) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
