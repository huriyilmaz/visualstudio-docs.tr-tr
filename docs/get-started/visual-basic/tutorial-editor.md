---
title: Visual Basic geliştiricileri için düzenlemeye giriş
description: Visual Studio'daki kod düzenleyicisine yapılan bu 10 dakikalık giriş, Visual Studio'nun Visual Basic kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştırdığı bazı yolları gösterir.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 695b1600aedb30a9e75a7829af4bac400f069922
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75584614"
---
# <a name="learn-to-use-the-code-editor"></a>Kod düzenleyicisini kullanmayı öğrenin

Visual Studio'daki kod düzenleyicisine bu 10 dakikalık girişte, Visual Studio'nun kodu yazmayı, gezinmeyi ve anlamayı kolaylaştırdığı bazı yollara bakmak için bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

Bu makalede, Visual Basic'e zaten aşina olduğunuzu varsayar. Eğer değilseniz, size Visual Studio Visual [Basic ile ilk başlayın](../../get-started/visual-basic/tutorial-console.md) gibi bir öğretici bakmak öneririz.

> [!TIP]
> Bu makaleyi takip etmek için Visual Studio için Visual Basic ayarlarını seçtiğinizden emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluşturma

Yeni bir dosya oluşturup bazı kodlar ekleyerek başlayın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **Esc** tuşuna basın veya başlat penceresinde **kodsuz Devam'ı** tıklatın.

::: moniker-end

2. Menü çubuğundaki **Dosya** menüsünden **Yeni Dosya'yı**seçin.

3. Genel **kategori** altında **Yeni Dosya** iletişim kutusunda **Visual Basic Class'ı**seçin ve ardından **Aç'ı**seçin.

   Visual Basic sınıfının iskeletiyle birlikte editörde yeni bir dosya açılır. (Kod düzenleyicisinin sözdizimi vurgulama gibi sunduğu avantajlardan bazılarını elde etmek için tam bir Visual Studio projesi oluşturmanız gerekmeyeni zaten fark edebilirsiniz. İhtiyacınız olan tek şey bir kod dosyası!)

   ![Visual Studio Visual Basic kod dosyası](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../../ide/code-snippets.md) Visual Basic, C#ve C++ gibi farklı programlama dilleri için kullanılabilir. Visual Basic **Sub** snippet'i dosyamıza ekleyelim.

1. İmlecinizi `End Class`yazan çizginin üzerine yerleştirin ve **alt**yazın.

   Açılır pencere iletişim `Sub` kutusu, anahtar kelime ve **Alt** kod snippet'inin nasıl eklendiğini niçin içeren bilgilerle birlikte görüntülenir.

   ![Visual Studio kod parçacığı için IntelliSense](media/tutorial-intellisense-snippet.png)

1. Kod parçacıkını eklemek için **Sekme'ye** iki kez basın.

   Alt yordamın `MySub()` anahattı dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dilleri için değişir. Visual Basic için kullanılabilir kod parçacıklarına**IntelliSense** > **Insert Snippet'i** (veya Ctrl**K**, **Ctrl**+ **Ctrl**+**X**tuşuna basarak) seçerek **Edit** > bakabilirsiniz. Visual Basic için kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Visual Basic kod snippet listesi](media/tutorial-code-snippet-list.png)

Bilgisayarda bir dosya olup olmadığını belirlemek, metin dosyasına yazmak, kayıt defteri değerini okumak, SQL sorgusu yürütmek, Her biri için bir dosya oluşturmak için parçacıklar [vardır... Sonraki ifade](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)ve daha birçok.

## <a name="comment-out-code"></a>Yorum kodu

Visual Studio'daki menü çubuğunun altındaki düğme satırı olan araç çubuğu, kodladığınız da daha üretken hale getirmenize yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu geçiş yapabilir, bir satır girintisini artırabilir veya azaltabilir veya derlemek istemediğiniz kodu yorumlayabilirsiniz. [(IntelliSense](../../ide/using-intellisense.md) diğer şeylerin yanı sıra eşleşen yöntemlerin bir listesini görüntüleyen bir kodlama yardımıdır.) Bu bölümde, bazı kod lar hakkında yorum yapacağız.

![Düzenleyici araç çubuğu düğmeleri](media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu yordam gövdesine yapıştırın. `MySub()`

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

1. Diziyi `morewords` kullanmıyoruz, ancak daha sonra kullanabiliriz, bu yüzden tamamen silmek istemeyiz. Bunun yerine, şu satırları yorumlayalım. Kapatma kıvırcık `morewords` ayracının tüm tanımını seçin ve ardından araç **çubuğundaki seçili satırlar** düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl**+**K**, **Ctrl**+**C**tuşuna basın.

   ![Açıklama düğmesi](media/tutorial-comment-out.png)

   Visual Basic yorum `'` karakteri, kodu oluşturmak için seçilen her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daraltma

Yalnızca ilginizi çeken bölümlere odaklanmak için kod bölümlerini daraltabilirsiniz. Alıştırma yapmak için, diziyi `_words` bir kod satırına daraltalım. Eksi işareti olan küçük gri kutuyu seçin. `Dim _words = New String() {` Veya klavye kullanıcısıysanız, imleci dizi tanımının herhangi bir yerine yerleştirin ve **Ctrl**+M , **Ctrl**+**M****M**tuşlarına basın.

![Daraltma düğmesini anahat oluşturma](media/tutorial-collapse.png)

Kod bloğu sadece ilk satıra çöker, ardından bir`...`elips ( ). Kod bloğunu yeniden genişletmek için, içinde artı işareti olan aynı gri kutuyu tıklatın veya **Ctrl**+**M**, **Ctrl**+**M** tuşlarına tekrar basın. Bu özellik [Anahat lama](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltırken kullanışlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

Visual Studio editörü, bir tür, yöntem, vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir, örneğin simgenin başvuruldİğİ her yerde **Tanıma Git'i** seçerek. Odak noktanızı çalıştığınız dosyadan uzağa taşımayan daha hızlı bir yol [Peek Definition'ı](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türünün tanımına `String` bakalım.

1. Kelimeye `String` sağ tıklayın ve içerik menüsünden **Peek Tanımı'nı** seçin. Veya, **Alt**+**F12 tuşuna**basın.

   `String` Sınıfın tanımıyla birlikte açılır pencere görüntülenir. Açılır pencere içinde gezinebilir, hatta gözetlenen koddan başka bir türün tanımına göz atabilirsiniz.

   ![Peek tanım penceresi](media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" yazan küçük kutuyu seçerek gözetlenen tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlamak için IntelliSense'i kullanın

[IntelliSense,](../../ide/using-intellisense.md) kodlama yaparken paha biçilmez bir kaynaktır. Bir yöntemin farklı aşırı yükleri için bir türün kullanılabilir üyeleri veya parametre ayrıntıları hakkında bilgi gösterebilir. Ayrıca, bir sözcüğü ayrıştırmak için yeterli karakter yazdıktan sonra bir sözcüğü tamamlamak için De IntelliSense'i kullanabilirsiniz. Programdan çıktı için standart bir yer olan konsol penceresine sıralanmış dizeleri yazdırmak için bir kod satırı ekleyelim.

1. Değişkenin `query` altında, aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense'in size sembol hakkında Hızlı Bilgi gösterdiğini görüyorsunuz. **Quick Info** `query`

   ![Visual Studio IntelliSense kelime tamamlama](media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün `query` geri kalanını eklemek için **Sekme'ye**basın.

1. Aşağıdaki kodgibi görünmek için kod bloğunu kapatın.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

İlk seferinde kimse kodu doğru şekilde kullanmaz ve değiştirmeniz gereken şeylerden biri de bir değişkenin veya yöntemin adıdır. Değişkeni `words`yeniden adlandırmak için Visual Studio'nun [yeniden düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim. `_words`

1. İmlecinizi `_words` değişkenin tanımının üzerine yerleştirin ve sağ tıklatma veya bağlam menüsünden **Yeniden Adlandır'ı** seçin.

   Editörün sağ üst kısmında açılır yeniden **adlandırma** iletişim kutusu görüntülenir.

1. Değişken `_words` hala seçiliyken, istenilen **sözcük**adını yazın. `words` Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **Enter** tuşuna basmadan veya **Uygula'ya**tıklamadan önce, **Yeniden Adlandır** açılır kutusuna **yorum ekle** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](media/tutorial-rename.png)

1. **Enter** tuşuna basın veya **Uygula'ya**tıklayın.

   Her iki `words` olay da kod `words` yorumunda başvurunun yanı sıra yeniden adlandırılır.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Kodda gezinme](../../ide/navigating-code.md)
- [Anahat](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
