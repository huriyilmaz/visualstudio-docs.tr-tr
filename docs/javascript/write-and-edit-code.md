---
title: JavaScript geliştiricileri için düzenlemeye giriş
description: Visual Studio'daki kod düzenleyicisine yapılan bu giriş, Visual Studio'nun JavaScript kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştırdığı bazı yollardan bazılarını gösterir.
ms.date: 12/13/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 111100038817d16d4655271f648aeb076bf1e9af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840852"
---
# <a name="learn-to-use-the-code-editor"></a>Kod düzenleyicisini kullanmayı öğrenin

Visual Studio'daki kod düzenleyicisine kısa bir giriş te, Visual Studio'nun kodu yazmayı, gezinmeyi ve anlamayı kolaylaştırdığı bazı yollara bakacağız.

> [!TIP]
> Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin. Yaptığınız uygulama geliştirme türüne bağlı olarak, Visual Studio ile **Düğüm.js geliştirme iş yükünü** yüklemeniz gerekebilir.

Bu makalede, JavaScript geliştirme aşina olduğunuzu varsayar. Eğer değilseniz, önce [Bir Düğüm Oluştur ve Express uygulaması](../javascript/tutorial-nodejs.md) gibi bir öğreticiye bakmanızı öneririz.

## <a name="add-a-new-project-file"></a>Yeni bir proje dosyası ekleme

Projenize yeni dosyalar eklemek için IDE'yi kullanabilirsiniz.

1. Projeniz Visual Studio'da açıkken, Solution Explorer'daki bir klasöre veya proje düğümünüze sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. **Genel** kategori altında **yeni dosya** iletişim kutusunda, **JavaScript Dosyası**gibi eklemek istediğiniz dosya türünü seçin ve sonra **Aç'ı**seçin.

    Yeni dosya projenize eklenir ve düzenleyicide açılır.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlamak için IntelliSense'i kullanın

IntelliSense, kodlama yaparken paha biçilmez bir kaynaktır. Bir yöntemin farklı aşırı yükleri için bir türün kullanılabilir üyeleri veya parametre ayrıntıları hakkında bilgi gösterebilir. Aşağıdaki kodda, yazarken, `Router()`geçebileceğiniz bağımsız değişken türlerini görürsünüz. Buna imza yardımı denir.

![IntelliSense kullanma](../javascript/media/write-code-signature-checking.png)

Ayrıca, bir sözcüğü ayrıştırmak için yeterli karakter yazdıktan sonra bir sözcüğü tamamlamak için De IntelliSense'i kullanabilirsiniz. İmlecinizi aşağıdaki kod `data` ve yazıdaki `get`dizeden sonra koyarsanız, IntelliSense size kodda daha önce tanımlanan veya projenize eklediğiniz bir üçüncü taraf kitaplığında tanımlanan işlevleri gösterir.

![IntelliSense kullanma](../javascript/media/write-code-intellisense.png)

IntelliSense, programlama öğelerinin üzerinde gezinirken türler hakkında da bilgi gösterebilir.

IntelliSense bilgilerini sağlamak için, dil hizmeti TypeScript *d.ts* dosyalarını ve JSDoc yorumlarını kullanabilir. En yaygın JavaScript kitaplıkları *için, d.ts* dosyaları otomatik olarak elde edilir. IntelliSense bilgilerinin nasıl elde edilen hakkında daha fazla bilgi için [JavaScript IntelliSense'e](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json) bakın

## <a name="check-syntax"></a>Sözdizimini denetleme

Dil hizmeti sözdizimi denetimi ve linting sağlamak için ESLint kullanır. Düzenleyicide sözdizimi denetimi için seçenekler ayarlamanız gerekiyorsa, **Araçlar** > **Seçenekleri** > **JavaScript/TypeScript** > **Linting'i**seçin. Linting seçenekleri sizi genel ESLint yapılandırma dosyasına yönlendirer.

Aşağıdaki kodda, ifadede yeşil sözdizimi vurgulama (yeşil dalgalı) görürsünüz. Sözdizimi vurgulama üzerinde gezinmek.

![Sözdizimi hatasini görüntüleme](../javascript/media/write-code-syntax-checking.png)

Bu iletinin son satırı, dil hizmetinin virgül`,`beklediğini söyler ( ). Yeşil dalgalı bir uyarı gösterir. Kırmızı dalgalı bir hata olduğunu gösterir.

Alt bölmede, dosya adı ve satır numarasıyla birlikte uyarı ve açıklamayı görmek için **Hata Listesi** sekmesini tıklatabilirsiniz.

![Hata listesini görüntüleme](../javascript/media/write-code-error-list.png)

Virgül ( )`,`eklenerek bu `"data"`kodu düzeltebilirsiniz.

## <a name="comment-out-code"></a>Yorum kodu

Visual Studio'daki menü çubuğunun altındaki düğme satırı olan araç çubuğu, kodladığınız da daha üretken hale getirmenize yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu geçiştirebilirsiniz[(IntelliSense,](../ide/using-intellisense.md) diğer şeylerin yanı sıra eşleşen yöntemlerin listesini görüntüleyen), bir satır girintisini artıran veya azaltan veya derlemek istemediğiniz kodu oluşturan bir kodlama yardımıdır. Bu bölümde, bazı kod lar hakkında yorum yapacağız.

Düzenleyicide bir veya daha fazla kod satırı seçin ve ardından ![araç](../javascript/media/write-code-comment-out.png) **çubuğundaki seçili satırlar** düğmesine yorum yapın düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl**+**K**, **Ctrl**+**C**tuşuna basın.

JavaScript yorum karakterleri, `//` kodu açıklama yapmak için seçilen her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daraltma

Bazı kod bölgelerinin görünümünü zedelemeniz gerekiyorsa, bunu daraltabilirsiniz. Bir işlevin ilk satırının kenar boşluğunda eksi işareti bulunan küçük gri kutuyu seçin. Veya, klavye kullanıcısıysanız, imleci oluşturucu kodun herhangi bir yerine yerleştirin ve **Ctrl**+M , **Ctrl**+**M****M**tuşlarına basın.

![Daraltma düğmesini anahat oluşturma](../javascript/media/write-code-collapse-code.png)

Kod bloğu sadece ilk satıra çöker, ardından bir`...`elips ( ). Kod bloğunu yeniden genişletmek için, içinde artı işareti olan aynı gri kutuyu tıklatın veya **Ctrl**+**M**, **Ctrl**+**M** tuşlarına tekrar basın. Bu özellik [Anahat lama](../ide/outlining.md) olarak adlandırılır ve özellikle uzun işlevleri veya tüm sınıfları daraltırken kullanışlıdır.

## <a name="view-definitions"></a>Tanımları görüntüleme

Visual Studio editörü, bir tür, işlev, vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, örneğin programlama öğesinin başvuruldettiği her yerde **Tanıma Git'i** seçerek tanımı içeren dosyaya gitmektir. Odak noktanızı çalıştığınız dosyadan uzağa taşımayan daha hızlı bir yol [Peek Definition'ı](../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Aşağıdaki örnekte yöntemin tanımına `render` bakalım.

İçerik menüsünden `render` **Peek Tanımı'na** sağ tıklayın ve seçeneğini belirleyin. Veya, **Alt**+**F12 tuşuna**basın.

   `render` Metnin tanımıyla birlikte açılır pencere görüntülenir. Açılır pencere içinde gezinebilir, hatta gözetlenen koddan başka bir türün tanımına göz atabilirsiniz.

   ![Peek tanım penceresi](../javascript/media/write-code-peek-definition.png)

Açılan pencerenin sağ üst kısmında "x" yazan küçük kutuyu seçerek gözetlenen tanım penceresini kapatın.

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [JavaScript](../ide/code-snippets.md) de dahil olmak üzere farklı programlama dilleri için kod parçacıkları kullanılabilir. Kod dosyanıza `for` bir döngü ekleyelim.

İmlecinizi snippet'i eklemek istediğiniz yere yerleştirin, sağ tıklatın ve **Snippet** > **Ekle Snippet'i**seçin.

![Visual Studio'da Kod parçacığı](../javascript/media/write-code-insert-snippet.png)

Editörde Bir **Ekle Snippet** kutusu görünür. **Genel'i** seçin ve ardından listedeki **öğe için** çift tıklatın.

![Visual Studio'da for döngüsü için kod snippet](../javascript/media/write-code-insert-snippet-for-loop.png)

Bu, `for` döngü snippet'ini kodunuza ekler:

```javascript
for (var i = 0; i < length; i++) {

}
```

**IntelliSense** > **Insert Snippet'i** **edit'i** > seçip dilinizin klasörünü seçerek diliniz için kullanılabilir kod parçacıklarına bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [Kodda gezinme](../ide/navigating-code.md)
- [Anahat](../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
