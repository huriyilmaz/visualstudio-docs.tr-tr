---
title: Visual Basic geliştiricileri için düzenlemelere giriş
description: Visual Studio kod düzenleyicisine bu 10 dakikalık giriş, Visual Studio Visual Basic kodu yazma, gezinme ve anlama işlemlerini daha kolay hale getiren bazı yolları gösterir.
ms.custom:
- vs-acquisition
- seodec18
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
ms.openlocfilehash: efc84a54a866082791f3c367bbf1fe08d52ae91f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431076"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Kod düzenleyicisini Visual Basic ile kullanmayı öğrenin

Visual Studio kod düzenleyicisine bu 10 dakikalık bir giriş için, Visual Studio Visual Basic kodu yazma, gezinme ve anlama işlemlerini daha kolay hale getiren bazı yöntemlere bakmak için bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

Bu makalede, Visual Basic zaten bildiğiniz varsayılmaktadır. değilseniz, önce [Visual Studio Visual Basic kullanmaya başlama](../../get-started/visual-basic/tutorial-console.md) gibi bir öğreticiye bakmanız önerilir.

> [!TIP]
> bu makaleyle birlikte izlemek için, Visual Studio için Visual Basic ayarların seçili olduğundan emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında daha fazla bilgi için bkz. [ortam ayarlarını seçme](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluştur

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.
 
1. Menü çubuğundaki **Dosya** menüsünde **yeni dosya**' yı seçin.

1. **yeni dosya** iletişim kutusunda, **genel** kategori altında **Visual Basic sınıf**' ı seçin ve sonra **aç**' ı seçin.

   düzenleyicide Visual Basic sınıfının iskeçiyle yeni bir dosya açılır. (sözdizimi vurgulama gibi kod düzenleyicisinin sağladığı avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmanız gerekmediğine zaten fark edebilirsiniz. Tüm ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio Visual Basic kod dosyası](media/tutorial-editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **ESC** tuşuna basın veya başlangıç penceresinde **kod olmadan devam et** ' e tıklayın.

1. Menü çubuğundaki **Dosya** menüsünde **yeni dosya**' yı seçin.

1. **yeni dosya** iletişim kutusunda, **genel** kategori altında **Visual Basic sınıf**' ı seçin ve sonra **aç**' ı seçin.

   düzenleyicide Visual Basic sınıfının iskeçiyle yeni bir dosya açılır. (sözdizimi vurgulama gibi kod düzenleyicisinin sağladığı avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmanız gerekmediğine zaten fark edebilirsiniz. Tüm ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio kod düzenleyicisinde yeni bir Visual Basic sınıf dosyası gösteren ekran görüntüsü.](media/tutorial-editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **ESC** tuşuna basın veya başlangıç penceresinde **kod olmadan devam et** ' i seçin.

1. Menü çubuğundaki **Dosya** menüsünde **Yeni** > **Dosya**' yı seçin.

1. **yeni dosya** iletişim kutusunda, **genel** kategori altında **Visual Basic sınıf**' ı seçin ve sonra **aç**' ı seçin.

   düzenleyicide Visual Basic sınıfının iskeçiyle yeni bir dosya açılır. (sözdizimi vurgulama gibi kod düzenleyicisinin sağladığı avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmanız gerekmediğine zaten fark edebilirsiniz. Tüm ihtiyacınız olan bir kod dosyasıdır!)

   :::image type="content" source="media/vs-2022/tutorial-editor.png" alt-text="Visual Studio kod düzenleyicisinde yeni bir Visual Basic sınıf dosyası gösteren ekran görüntüsü.":::

::: moniker-end

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [kod parçacıkları](../../ide/code-snippets.md) Visual Basic, C# ve C++ gibi farklı programlama dilleri için kullanılabilir. Visual Basic **alt** kod parçacığını dosyanıza ekleyelim.

::: moniker range="<=vs-2019"

1. İmlecinizi, belirten çizginin üzerine getirin `End Class` ve **Sub** yazın.

   `Sub`Anahtar sözcüğü ve **alt** kod parçacığını ekleme hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir.

   ![Visual Studio ' Sub ' kod parçacığı için IntelliSense 'i gösteren ekran görüntüsü.](media/tutorial-intellisense-snippet.png)

1. Kod parçacığını eklemek için **sekme** tuşuna iki kez basın.

   Alt yordamın ana hattı `MySub()` dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dilleri için farklılık gösterir. ıntellisense ekleme kod parçacığını **düzenle**' yi seçerek Visual Basic için kullanılabilir kod parçacıklarına bakabilirsiniz  >    >   (veya **ctrl** + **K**, **ctrl** + **X** tuşlarına basın). Visual Basic için, kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Visual Basic kod parçacıkları içeren kategori klasörlerinin listesini içeren kod parçacığı ekle penceresini gösteren ekran görüntüsü.](media/tutorial-code-snippet-list.png)

bilgisayarda bir dosyanın var olup olmadığını belirlemek, bir metin dosyasına yazmak, kayıt defteri değerini okumak, SQL sorgusu çalıştırmak veya her biri için bir oluşturmak için kod parçacıkları vardır.. [. Sonraki bildiri](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)ve çok daha fazlası.

::: moniker-end

::: moniker range=">=vs-2022"

1. İmlecinizi, belirten çizginin üzerine getirin `End Class` ve **Sub** yazın.

   `Sub`Anahtar sözcüğü ve **alt** kod parçacığını ekleme hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-snippet.png" alt-text="Visual Studio ' Sub ' kod parçacığı için IntelliSense 'i gösteren ekran görüntüsü.":::

1. Kod parçacığını eklemek için **sekme** tuşuna iki kez basın.

   Alt yordamın ana hattı `MySub()` dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dilleri için farklılık gösterir. kod düzenleyicisinde sağ tıklama veya bağlam menüsünü açıp kod **parçacığı**  >  **ekle kod parçacığı** ' nı seçerek Visual Basic için kullanılabilir kod parçacıklarına bakabilirsiniz (veya **ctrl** + **K**, **ctrl** + **X** tuşlarına basın). Visual Basic için, kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

:::image type="content" source="media/vs-2022/tutorial-code-snippet-list.png" alt-text="Visual Basic kod parçacıkları içeren kategori klasörlerinin listesini içeren kod parçacığı ekle penceresini gösteren ekran görüntüsü.":::

::: moniker-end

## <a name="comment-out-code"></a>Kodu dışarı açıklama

Visual Studio ' de menü çubuğu altındaki düğmelerin satırı olan araç çubuğu, kod olarak daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilir, bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak ayarlayabilirsiniz. ([IntelliSense](../../ide/using-intellisense.md) , farklı şeyler arasından eşleşen yöntemlerin bir listesini görüntüleyen bir kodlama yardımıdır.) Bu bölümde, bazı kodları açıklayacağız.

::: moniker range="<=vs-2019"

![kod açıklamaları ekleme veya kaldırma için düğmeler içeren Visual Studio araç çubuğunu gösteren ekran görüntüsü.](media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu `MySub()` yordam gövdesine yapıştırın.

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

1. Diziyi kullanmıyoruz `morewords` , ancak bunu daha sonra tamamen silmek istemdiğimiz için kullanabiliriz. Bunun yerine, bu satırları açıklamaya bakalım. `morewords`Kapanış küme ayracı için tüm tanımı seçin ve ardından araç çubuğundaki **Seçili çizgiler** düğmesini seçin. Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C** tuşlarına basın.

   ![Kırmızı renkle vurgulanmış kodu açıklama eklemek için düğme ile araç çubuğunu gösteren ekran görüntüsü.](media/tutorial-comment-out.png)

   Visual Basic açıklama karakteri, `'` kodu açıklama eklemek için seçili her satırın başına eklenir.

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-editor-toolbar.png" alt-text="kod açıklamaları ekleme veya kaldırma için düğmeler içeren Visual Studio araç çubuğunu gösteren ekran görüntüsü.":::

1. Aşağıdaki kodu `MySub()` yordam gövdesine yapıştırın.

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

1. Diziyi kullanmıyoruz `morewords` , ancak bunu daha sonra tamamen silmek istemdiğimiz için kullanabiliriz. Bunun yerine, bu satırları açıklamaya bakalım. `morewords`Kapanış küme ayracı için tüm tanımı seçin ve ardından araç çubuğundaki **Seçili çizgiler** düğmesini seçin. Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C** tuşlarına basın.

   :::image type="content" source="media/vs-2022/tutorial-comment-out.png" alt-text="Kırmızı renkle vurgulanmış kodu açıklama eklemek için düğme ile araç çubuğunu gösteren ekran görüntüsü.":::

   Visual Basic açıklama karakteri, `'` kodu açıklama eklemek için seçili her satırın başına eklenir.

::: moniker-end

## <a name="collapse-code-blocks"></a>Kod bloklarını Daralt

::: moniker range="<=vs-2019"

Yalnızca ilginizi çeken parçalara odaklanmak için kod bölümlerini daraltabilirsiniz. Pratikte, `_words` diziyi tek bir kod satırına darallayalım. Görüntülenen satırın kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin `Dim _words = New String() {` . Ya da bir klavye kullanıcısı kullanıyorsanız, imleci dizi tanımında herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m** tuşlarına basın.

![Visual Studio Code düzenleyicisini gösteren ve kırmızı renkle vurgulanmış bir kod bölümünün ana hattını daraltma denetimiyle ilgili ekran görüntüsü.](media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi bir artı işaretine sahip olan gri kutuya tıklayın veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltdığınızda yararlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

Yalnızca ilginizi çeken parçalara odaklanmak için kod bölümlerini daraltabilirsiniz. Pratikte, `_words` diziyi tek bir kod satırına darallayalım. Görüntülenen satırın kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin `Dim _words = New String() {` . Ya da bir klavye kullanıcısı kullanıyorsanız, imleci dizi tanımında herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m** tuşlarına basın.

:::image type="content" source="media/vs-2022/tutorial-collapse.png" alt-text="Visual Studio Code düzenleyicisini gösteren ve kırmızı renkle vurgulanmış bir kod bölümünün ana hattını daraltma denetimiyle ilgili ekran görüntüsü.":::

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi de bir artı işaretine sahip olan gri kutuyu seçin veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltdığınızda yararlıdır.

::: moniker-end
## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüle

::: moniker range="<=vs-2019"

Visual Studio düzenleyicisi, bir tür, yöntem vb. tanımlamayı incelemeyi kolaylaştırır. Tek bir yol, tanımı içeren dosyaya gitmeniz, örneğin simgenin başvurduğu her yerde **Tanıma Git** ' i seçerek. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türün tanımına göz atalım `String` .

1. Sözcüğe sağ tıklayın `String` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   !['String' sınıfının tanımını içeren Bir Tanıma Göz At açılır penceresini gösteren ekran görüntüsü.](media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek göz atarak tanım penceresini kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio düzenleyicisi, bir tür veya sınıf üyesinin tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir;  örneğin sembole başvurulan her yerde Tanıma Git'i seçerek. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Peek [Definition kullanmakdır.](../../ide/go-to-and-peek-definition.md#peek-definition) Türün tanımına göz `String` atalım.

1. Söze sağ tıklayın ve `String` içerik **menüsünden Tanıma Göz** At'ı seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   :::image type="content" source="media/vs-2022/tutorial-peek-definition.png" alt-text="'String' sınıfının tanımını içeren Bir Tanıma Göz At açılır penceresini gösteren ekran görüntüsü.":::

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek tanımlama penceresine göz at penceresini kapatın.

::: moniker-end

## <a name="use-intellisense-to-complete-words"></a>IntelliSense kullanarak sözcükleri tamamlama

::: moniker range="<=vs-2019"

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne kadar karakter yazarak daha anlaşılır olduğunu da anlayana kadar kullanabilirsiniz. Şimdi konsol penceresine sipariş edilen dizeleri yazdırmak için bir kod satırı ekliyiz. Bu, programın çıkışının standart olduğu yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense'in simge hakkında **Hızlı Bilgi** göster olduğunu `query` görürsünüz.

   ![Kod düzenleyicisinde 'query' sözcüğü için IntelliSense sözcük tamamlama penceresini Visual Studio ekran görüntüsü.](media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün geri `query` kalanını eklemek için Tab tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

::: moniker-end

::: moniker range=">=vs-2022"

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne kadar karakter yazarak daha anlaşılır olduğunu da anlayana kadar kullanabilirsiniz. Şimdi konsol penceresine sipariş edilen dizeleri yazdırmak için bir kod satırı ekliyiz. Bu, programın çıkışının standart olduğu yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense'in simge hakkında **Hızlı Bilgi** göster olduğunu `query` görürsünüz.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-completion-list.png" alt-text="Kod düzenleyicisinde 'query' sözcüğü için IntelliSense sözcük tamamlama penceresini Visual Studio ekran görüntüsü.":::

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün geri `query` kalanını eklemek için Tab tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

::: moniker-end
## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

::: moniker range="<=vs-2019"

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio [yeniden düzenleme işlevini](../../ide/refactoring-in-visual-studio.md) `_words` `words` deneyelim.

1. İmlecinizi değişkenin tanımının `_words` üzerine yerleştirerek sağ tıklama **veya** bağlam menüsünden Yeniden Adlandır'ı seçin.

   Düzenleyicinin sağ **üst kısmında** bir açılan Yeniden Adlandırma iletişim kutusu görüntülenir.

1. değişkeni `_words` seçiliyken, sözcüklerin istenen adını **yazın.** Sorguda başvurusunun `words` da otomatik olarak yeniden adlandırıldıklarından emin oluruz. Enter tuşuna **basmadan** veya  **Uygula'ya** tıklamadan önce, Yeniden Adlandır açılan kutusunda **Açıklama** ekle onay kutusunu seçin.

   !['Açıklama ekle' seçeneğinin işaretli olduğu '_words' değişkeni için Yeniden Adlandır iletişim kutusunu gösteren ekran görüntüsü.](media/tutorial-rename.png)

1. **Enter tuşuna** basın veya Uygula'ya **tıklayın.**

   Hem `words` oluşumları yeniden adlandırılır hem de kod `words` açıklamasındaki başvurusu.

::: moniker-end

::: moniker range=">=vs-2022"

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio [yeniden düzenleme işlevini](../../ide/refactoring-in-visual-studio.md) `_words` `words` deneyelim.

1. İmlecinizi değişkenin tanımının `_words` üzerine yerleştirerek sağ tıklama **veya** bağlam menüsünden Yeniden Adlandır'ı seçin.

   Düzenleyicinin sağ **üst kısmında** bir açılan Yeniden Adlandırma iletişim kutusu görüntülenir.

1. değişkeni `_words` seçiliyken, sözcüklerin istenen adını **yazın.** Sorguda başvurusunun `words` da otomatik olarak yeniden adlandırıldıklarından emin oluruz. **Enter** veya **Uygula'ya basmadan** **önce, Yeniden adlandır** açılır kutusunda Açıklama dahil **edin** onay kutusunu seçin.

   :::image type="content" source="media/vs-2022/tutorial-rename.png" alt-text="'Açıklama ekle' seçeneğinin işaretli olduğu '_words' değişkeni için Yeniden Adlandır iletişim kutusunu gösteren ekran görüntüsü.":::

1. **Enter tuşuna basın** veya Uygula'ya **basın.**

   Hem `words` oluşumları yeniden adlandırılır hem de kod `words` açıklamasındaki başvurusu.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Kodda gezinme](../../ide/navigating-code.md)
- [Anahat Oluşturma](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
