---
title: Geliştiriciler için düzenlemeye Visual Basic giriş
description: Visual Studio'da kod düzenleyicisine 10 dakikalık giriş, Visual Studio kodu yazmayı, gezinmeyi ve anlamayı kolaylaştıran Visual Basic gösterir.
ms.custom:
- vs-acquisition
- get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cad5a842a0a5da29cde8df75869677e406f17414
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970626"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Kod düzenleyicisini Visual Basic

Visual Studio'daki kod düzenleyicisine bu 10 dakikalık girişte, Visual Studio'nin kod yazmayı, gezinmeyi ve kodu daha kolay anlamanıza nasıl Visual Basic ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

Bu makalede, kaynaklarla ilgili bilgi sahibi Visual Basic. Yoksa, önce Kullanmaya başlayın'de Visual Basic [ile](../../get-started/visual-basic/tutorial-console.md) Visual Studio öneririz.

> [!TIP]
> Bu makaleyi takip etmek için, uygulama ayarları için Visual Basic emin Visual Studio. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz. Ortam ayarlarını seçme.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni kod dosyası oluşturma

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.
 
1. Menü **çubuğundaki** Dosya menüsünden Yeni **Dosya'ya tıklayın.**

1. Yeni Dosya **iletişim kutusunda,** Genel kategorisi **altında** Sınıf **Visual Basic'ı ve** ardından Aç'ı **seçin.**

   Düzenleyicide yeni bir dosya açılır ve bu dosya bir Visual Basic olur. (Kod düzenleyicisinin sunduğu bazı avantajlardan (söz dizimi vurgulama gibi) kazanmak için tam Visual Studio proje oluşturmanız gerek olmadığını fark etme. Tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Basic kod dosyasını Visual Studio](media/tutorial-editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak **için Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'a tıklayın.

1. Menü **çubuğundaki** Dosya menüsünden Yeni **Dosya'ya tıklayın.**

1. Yeni Dosya **iletişim kutusunda,** Genel kategorisi **altında** Sınıf **Visual Basic'ı ve** ardından Aç'ı **seçin.**

   Düzenleyicide yeni bir dosya açılır ve bu dosya bir Visual Basic olur. (Kod düzenleyicisinin sunduğu bazı avantajlardan (söz dizimi vurgulama gibi) kazanmak için tam Visual Studio proje oluşturmanız gerek olmadığını fark etme. Tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Kod düzenleyicisinde yeni Visual Basic sınıf dosyasını Visual Studio ekran görüntüsü.](media/tutorial-editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak **için Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'ı seçin.

1. Menü **çubuğundaki** Dosya menüsünden Yeni **Dosya'ya** > **tıklayın.**

1. Yeni Dosya **iletişim kutusunda,** Genel kategorisi **altında** Sınıf **Visual Basic'ı ve** ardından Aç'ı **seçin.**

   Düzenleyicide yeni bir dosya açılır ve bu dosya bir Visual Basic olur. (Kod düzenleyicisinin sunduğu bazı avantajlardan (söz dizimi vurgulama gibi) kazanmak için tam Visual Studio proje oluşturmanız gerek olmadığını fark etme. Tek ihtiyacınız olan bir kod dosyasıdır!)

   :::image type="content" source="media/vs-2022/tutorial-editor.png" alt-text="Kod düzenleyicisinde yeni Visual Basic sınıf dosyasını Visual Studio ekran görüntüsü.":::

::: moniker-end

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın *olarak kullanılan kod* bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı kod parçacıkları sağlar. [Kod parçacıkları Visual Basic,](../../ide/code-snippets.md) C# ve C++ gibi farklı programlama dilleri için kullanılabilir. Şimdi Visual Basic **Sub kod parçacığını** dosyamıza ekleriz.

::: moniker range="<=vs-2019"

1. İmlecinizi , ve yazarak sub olan `End Class` satırın üzerine **yazın.**

   anahtar sözcüğü ve Alt kod parçacığının nasıl eklendiğinden `Sub` emin olmak için bir **açılır** iletişim kutusu görüntülenir.

   ![Kod parçacığında 'Sub' kod parçacığı için IntelliSense'i gösteren Visual Studio.](media/tutorial-intellisense-snippet.png)

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Alt yordamın `MySub()` ana hatları dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir. IntelliSense Insert Snippet'ı Düzenle'yi seçerek Visual Basic kod parçacıklarına bakabilirsiniz  >    >   **(veya Ctrl** + **K**, Ctrl X **tuşlarına** + **basın).** Daha Visual Basic kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Kod parçacıkları içeren kategori klasörlerinin listesini içeren Kod Parçacığı Ekle penceresini Visual Basic ekran görüntüsü.](media/tutorial-code-snippet-list.png)

Bilgisayarda bir dosya olup olmadığını belirlemek, bir metin dosyasına yazmak, kayıt defteri değerini okumak, bir kayıt defteri SQL yürütmek veya [For Each... Sonraki deyimi](/dotnet/visual-basic/language-reference/statements/for-each-next-statement), ve çok daha fazlası.

::: moniker-end

::: moniker range=">=vs-2022"

1. İmlecinizi , ve yazarak sub olan `End Class` satırın üzerine **yazın.**

   anahtar sözcüğü ve Alt kod parçacığının nasıl eklendiğinden `Sub` emin olmak için bir **açılır** iletişim kutusu görüntülenir.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-snippet.png" alt-text="Kod parçacığında 'Sub' kod parçacığı için IntelliSense'i gösteren Visual Studio.":::

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Alt yordamın `MySub()` ana hatları dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir. Kod düzenleyicisinde sağ tıklamayı veya bağlam menüsünü Visual Basic Kod Parçacığı Ekleme'yi seçerek   >   (veya **Ctrl** + **K**, **Ctrl** X tuşlarına basarak) Visual Basic için kullanılabilir kod parçacıklarına + **bakabilirsiniz.** Daha Visual Basic kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

:::image type="content" source="media/vs-2022/tutorial-code-snippet-list.png" alt-text="Kod parçacıkları içeren kategori klasörlerinin listesini içeren Kod Parçacığı Ekle penceresini Visual Basic ekran görüntüsü.":::

::: moniker-end

## <a name="comment-out-code"></a>Kodu açıklamaya alma

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç çubuğu Visual Studio kodlarken daha üretken çalışmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu açıp, satır girintisini artırabilir veya azaltabilir ya da derlemek istemeyebilirsiniz. ([IntelliSense,](../../ide/using-intellisense.md) eşleşen yöntemlerin listesini ve diğer öğeleri görüntüleyen bir kodlama yardımıdır.) Bu bölümde bazı kodlara açıklama olarak yer veserden bakabilirsiniz.

::: moniker range="<=vs-2019"

![Kod açıklamalarını ekleme veya Visual Studio düğmeleri içeren araç çubuğunu gösteren ekran görüntüsü.](media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu yordam `MySub()` gövdesine yapıştırın.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. dizisini kullanmaz ancak daha sonra bunu kullanarak diziyi tamamen `morewords` silmek istemeyebilirsiniz. Bunun yerine, bu satırları açıklama satırına bakalım. öğesinin kapanış küme ayracı tanımının tamamını seçin ve ardından araç çubuğunda seçili satırları `morewords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl** + **K**, Ctrl C  + **tuşlarına basın.**

   ![Kırmızı renkle vurgulanmış kodu açıklama ekleme düğmesinin yer alan araç çubuğunu gösteren ekran görüntüsü.](media/tutorial-comment-out.png)

   Kod Visual Basic açıklama satırı karakteri, seçilen `'` her satırın başına eklenir.

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-editor-toolbar.png" alt-text="Kod açıklamalarını ekleme veya Visual Studio düğmeleri içeren araç çubuğunu gösteren ekran görüntüsü.":::

1. Aşağıdaki kodu yordam `MySub()` gövdesine yapıştırın.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. dizisini kullanmaz ancak daha sonra bunu kullanarak diziyi tamamen `morewords` silmek istemeyebilirsiniz. Bunun yerine, bu satırları açıklama satırına bakalım. öğesinin kapanış küme ayracı tanımının tamamını seçin ve ardından araç çubuğunda seçili satırları `morewords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl** + **K**, Ctrl C  + **tuşlarına basın.**

   :::image type="content" source="media/vs-2022/tutorial-comment-out.png" alt-text="Kırmızı renkle vurgulanmış kodu açıklama ekleme düğmesinin yer alan araç çubuğunu gösteren ekran görüntüsü.":::

   Kod Visual Basic açıklama satırı karakteri, seçilen `'` her satırın başına eklenir.

::: moniker-end

## <a name="collapse-code-blocks"></a>Kod bloklarını daralt

::: moniker range="<=vs-2019"

Yalnızca ilgini gereken bölümlere odaklanmak için kod bölümlerini daraltabilirsiniz. Alıştırma yapmak için diziyi tek `_words` kod satırına daraltabilirsiniz. içinde eksi işareti bulunan ve satırın kenar boşluğunda bulunan küçük gri kutuyu `Dim _words = New String() {` seçin. Veya klavye kullanıcısıysanız imleci dizi tanımında herhangi bir yere yerleştirerek Ctrl M , **Ctrl** + **M** **tuşlarına** + **basın.**

![Kırmızı renkle Visual Studio Code bölümünün ana hatlarını daraltma denetimiyle birlikte yeni düzenleyiciyi gösteren ekran görüntüsü.](media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta `...` ( ). Kod bloğuna yeniden genişletmek için, artık artı işareti olan gri kutuya tıklayın veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

Yalnızca ilgini gereken bölümlere odaklanmak için kod bölümlerini daraltabilirsiniz. Alıştırma yapmak için diziyi tek `_words` kod satırına daraltabilirsiniz. içinde eksi işareti bulunan ve satırın kenar boşluğunda bulunan küçük gri kutuyu `Dim _words = New String() {` seçin. Veya klavye kullanıcısıysanız imleci dizi tanımında herhangi bir yere yerleştirerek Ctrl M , **Ctrl** + **M** **tuşlarına** + **basın.**

:::image type="content" source="media/vs-2022/tutorial-collapse.png" alt-text="Kırmızı renkle Visual Studio Code bölümünün ana hatlarını daraltma denetimiyle birlikte yeni düzenleyiciyi gösteren ekran görüntüsü.":::

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta `...` ( ). Kod bloğu yeniden genişletmek için, artık artı işareti olan gri kutuyu seçin veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

::: moniker-end
## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

::: moniker range="<=vs-2019"

Bu Visual Studio, bir türün, yöntemin vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir;  örneğin sembole başvurulan her yerde Tanıma Git'i seçerek. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Tanıma Göz At [kullanmakdır.](../../ide/go-to-and-peek-definition.md#peek-definition) Türün tanımına göz `String` atalım.

1. Söze sağ tıklayın ve `String` içerik **menüsünden Tanıma Göz** At'ı seçin. Alternatif olarak, **alt** + **F12** tuşuna basın.

   Sınıfının tanımına sahip bir açılır pencere görüntülenir `String` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   ![' String ' sınıfının tanımını içeren bir Özet Tanım açılır penceresini gösteren ekran görüntüsü.](media/tutorial-peek-definition.png)

1. Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek atılamıyor tanım penceresini kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio düzenleyicisi, bir tür veya sınıf üyesinin tanımını incelemeyi kolaylaştırır. Tek bir yol, tanımı içeren dosyaya gitmeniz, örneğin simgenin başvurduğu her yerde **Tanıma Git** ' i seçerek. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türün tanımına göz atalım `String` .

1. Sözcüğe sağ tıklayın `String` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif olarak, **alt** + **F12** tuşuna basın.

   Sınıfının tanımına sahip bir açılır pencere görüntülenir `String` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   :::image type="content" source="media/vs-2022/tutorial-peek-definition.png" alt-text="' String ' sınıfının tanımını içeren bir Özet Tanım açılır penceresini gösteren ekran görüntüsü.":::

1. Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek Özet Tanım penceresini kapatın.

::: moniker-end

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlaması için IntelliSense kullanma

::: moniker range="<=vs-2019"

Kodlamadan [IntelliSense](../../ide/using-intellisense.md) , değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. Düzenli dizeleri konsol penceresine yazdırmak için bir kod satırı ekleyelim, bu da programdan git 'in çıkış için standart yer.

1. Değişkenin altında `query` aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense, sembol hakkında **hızlı bilgi** gösterir `query` .

   ![Visual Studio kod düzenleyicisinde ' query ' kelimesinin ıntellisense sözcük tamamlama penceresini gösteren ekran görüntüsü.](media/tutorial-intellisense-completion-list.png)

1. `query`IntelliSense 'in kelime tamamlama işlevini kullanarak sözcüğün geri kalanını eklemek Için **Tab** tuşuna basın.

1. Aşağıdaki kod gibi görmek için kod bloğunu sona erdirin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

::: moniker-end

::: moniker range=">=vs-2022"

Kodlamadan [IntelliSense](../../ide/using-intellisense.md) , değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. Düzenli dizeleri konsol penceresine yazdırmak için bir kod satırı ekleyelim, bu da programdan git 'in çıkış için standart yer.

1. Değişkenin altında `query` aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense, sembol hakkında **hızlı bilgi** gösterir `query` .

   :::image type="content" source="media/vs-2022/tutorial-intellisense-completion-list.png" alt-text="Visual Studio kod düzenleyicisinde ' query ' kelimesinin ıntellisense sözcük tamamlama penceresini gösteren ekran görüntüsü.":::

1. `query`IntelliSense 'in kelime tamamlama işlevini kullanarak sözcüğün geri kalanını eklemek Için **Tab** tuşuna basın.

1. Aşağıdaki kod gibi görmek için kod bloğunu sona erdirin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

::: moniker-end
## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

::: moniker range="<=vs-2019"

Hiç kimse ilk kez kod alır ve değiştirmeniz gerekebilecek işlemlerden biri bir değişkenin veya yöntemin adıdır. değişkenin yeniden adlandırılması için Visual Studio yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim `_words` `words` .

1. İmlecinizi değişkeninin tanımına yerleştirin `_words` ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin.

   Düzenleyicinin sağ üst köşesinde bir açılır pencere **yeniden adlandırma** iletişim kutusu görüntülenir.

1. Değişken seçili durumdayken `_words` , istenen **sözcüklerin** adını yazın. `words`Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **ENTER** tuşuna bastıktan veya **Uygula**' ya tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   ![' _Words ' değişkeni için yeniden adlandır iletişim kutusunu gösteren ekran görüntüsü, ' ekleme açıklamaları ' seçeneği işaretlendi.](media/tutorial-rename.png)

1. **ENTER** tuşuna basın veya **Uygula**' ya tıklayın.

   Her iki tekrarın her ikisi de `words` yeniden adlandırılır ve `words` kod açıklamasında başvurusu.

::: moniker-end

::: moniker range=">=vs-2022"

Hiç kimse ilk kez kod alır ve değiştirmeniz gerekebilecek işlemlerden biri bir değişkenin veya yöntemin adıdır. değişkenin yeniden adlandırılması için Visual Studio yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim `_words` `words` .

1. İmlecinizi değişkeninin tanımına yerleştirin `_words` ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin.

   Düzenleyicinin sağ üst köşesinde bir açılır pencere **yeniden adlandırma** iletişim kutusu görüntülenir.

1. Değişken seçili durumdayken `_words` , istenen **sözcüklerin** adını yazın. `words`Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **ENTER** veya **Uygula**'Ya tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   :::image type="content" source="media/vs-2022/tutorial-rename.png" alt-text="' _Words ' değişkeni için yeniden adlandır iletişim kutusunu gösteren ekran görüntüsü, ' ekleme açıklamaları ' seçeneği işaretlendi.":::

1. **ENTER** tuşuna basın veya **Uygula**' yı seçin.

   Her iki tekrarın her ikisi de `words` yeniden adlandırılır ve `words` kod açıklamasında başvurusu.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Koda git](../../ide/navigating-code.md)
- [Anahat Oluşturma](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
