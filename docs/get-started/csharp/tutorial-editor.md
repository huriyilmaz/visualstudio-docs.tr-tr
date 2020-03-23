---
title: C# geliştiricileri için düzenlemeye giriş
description: Visual Studio'daki kod düzenleyicisine yapılan bu 10 dakikalık giriş, Visual Studio'nun C# kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştırdığı bazı yolları gösterir.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0cacd56ff6b3b3510505ca2752404b55a2771429
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75590442"
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

Bu makalede, C#'a zaten aşina olduğunuzu varsayar. Eğer değilseniz, önce [C# ve ASP.NET Core](tutorial-aspnet-core.md) in Visual Studio ile başlama gibi bir öğreticiye bakmanızı öneririz.

> [!TIP]
> Bu makaleyi takip etmek için Visual Studio için C# ayarlarını seçtiğinizden emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluşturma

Yeni bir dosya oluşturup bazı kodlar ekleyerek başlayın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **Esc** tuşuna basın veya başlat penceresinde **kodsuz Devam'ı** tıklatın.

::: moniker-end

2. Menü çubuğundaki **Dosya** menüsünden **Yeni** > **Dosya'yı**seçin veya **Ctrl**+**N**tuşuna basın.

3. Genel **kategori** altında **Yeni Dosya** iletişim kutusunda **Visual C# Class'ı**seçin ve ardından **Aç'ı**seçin.

   Editörde C# sınıfının iskeletini içeren yeni bir dosya açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazılarını elde etmek için tam bir Visual Studio projesi oluşturmak zorunda olmadığımıza dikkat edin; tek ihtiyacınız olan bir kod dosyası!)

   ![Visual Studio'da C# kod dosyası](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../../ide/code-snippets.md) C#, Visual Basic ve C++gibi farklı programlama dilleri için kullanılabilir. C# `void Main` snippet'i dosyamıza ekleyelim.

1. İmlecinizi son kapanış ayracı **}** hemen üzerine dosyaya `svm` yerleştirin ve `static void Main` &mdash;karakterleri yazın (bunun ne anlama geldiğini bilmiyorsanız çok fazla endişelenmeyin).

   `svm` Kod snippet hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir.

   ![Visual Studio kod parçacığı için IntelliSense](../media/tutorial-intellisense-snippet.png)

1. Kod parçacıkını eklemek için **Sekme'ye** iki kez basın.

   Yöntem imzasının `static void Main()` dosyaya eklenmesini görüyorsunuz. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) yöntemi C# uygulamalarının giriş noktasıdır.

Kullanılabilir kod parçacıkları farklı programlama dilleri için değişir. **IntelliSense** > **Insert Snippet'i** **Edit'i** > seçerek veya **Ctrl**+**K**, **Ctrl**+**X**tuşuna basarak ve ardından dilinizin klasörünü seçerek dilinizin kullanılabilir kod parçacıklarına bakabilirsiniz. C# için liste şuna benzer:

![C# kod snippet listesi](../media/tutorial-code-snippet-list.png)

Liste, bir [sınıf,](/dotnet/csharp/programming-guide/classes-and-structs/classes)bir [oluşturucu,](/dotnet/csharp/programming-guide/classes-and-structs/constructors)bir [for](/dotnet/csharp/language-reference/keywords/for) loop, [if](/dotnet/csharp/language-reference/keywords/if-else) veya [switch](/dotnet/csharp/language-reference/keywords/switch) deyimi ve daha fazlası oluşturmak için parçacıklar içerir.

## <a name="comment-out-code"></a>Yorum kodu

Visual Studio'daki menü çubuğunun altındaki düğme satırı olan araç çubuğu, kodladığınız da daha üretken hale getirmenize yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu geçiştirebilirsiniz[(IntelliSense,](../../ide/using-intellisense.md) diğer şeylerin yanı sıra eşleşen yöntemlerin listesini görüntüleyen), bir satır girintisini artıran veya azaltan veya derlemek istemediğiniz kodu oluşturan bir kodlama yardımıdır. Bu bölümde, bazı kod lar hakkında yorum yapacağız.

![Düzenleyici araç çubuğu](../media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu yöntem gövdesine yapıştırın. `Main()`

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Değişkeni `morewords` kullanmıyoruz, ancak daha sonra kullanabiliriz, bu yüzden tamamen silmek istemeyiz. Bunun yerine, şu satırları yorumlayalım. Kapatma yarı-iki `morewords` nokta için tüm tanımı seçin ve sonra araç **çubuğunda seçili satırları dışarı Yorum** seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl**+**K**, **Ctrl**+**C**tuşuna basın.

   ![Açıklama düğmesi](../media/tutorial-comment-out.png)

   C# yorum karakterleri, `//` kodu açıklama yapmak için seçilen her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daraltma

Bunun için `Class1` boş [yapıcının](/dotnet/csharp/programming-guide/classes-and-structs/constructors) oluşturulduğunu görmek istemiyoruz, bu yüzden koda bakışımızı çözmek için, onu daraltalım. Oluşturucunun ilk satırının kenar boşluğunda eksi işareti olan küçük gri kutuyu seçin. Veya, klavye kullanıcısıysanız, imleci oluşturucu kodun herhangi bir yerine yerleştirin ve **Ctrl**+M , **Ctrl**+**M****M**tuşlarına basın.

![Daraltma düğmesini anahat oluşturma](../media/tutorial-collapse.png)

Kod bloğu sadece ilk satıra çöker, ardından bir`...`elips ( ). Kod bloğunu yeniden genişletmek için, içinde artı işareti olan aynı gri kutuyu tıklatın veya **Ctrl**+**M**, **Ctrl**+**M** tuşlarına tekrar basın. Bu özellik [Anahat lama](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltırken kullanışlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

Visual Studio editörü, bir tür, yöntem, vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir, örneğin **Tanıma Git'i** seçerek veya sembolün başvuruldİğİ her yerde **F12** tuşuna basarak. Odak noktanızı çalıştığınız dosyadan uzağa taşımayan daha hızlı bir yol [Peek Definition'ı](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türünün tanımına `string` bakalım.

1. Herhangi bir olay üzerine `string` sağ tıklayın ve içerik menüsünden **Peek Tanımı'nı** seçin. Veya, **Alt**+**F12 tuşuna**basın.

   `String` Sınıfın tanımıyla birlikte açılır pencere görüntülenir. Açılır pencere içinde gezinebilir, hatta gözetlenen koddan başka bir türün tanımına göz atabilirsiniz.

   ![Peek tanım penceresi](../media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" yazan küçük kutuyu seçerek gözetlenen tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlamak için IntelliSense'i kullanın

[IntelliSense,](../../ide/using-intellisense.md) kodlama yaparken paha biçilmez bir kaynaktır. Bir yöntemin farklı aşırı yükleri için bir türün kullanılabilir üyeleri veya parametre ayrıntıları hakkında bilgi gösterebilir. Ayrıca, bir sözcüğü ayrıştırmak için yeterli karakter yazdıktan sonra bir sözcüğü tamamlamak için De IntelliSense'i kullanabilirsiniz. Programdan çıktı için standart bir yer olan konsol penceresine sıralanmış dizeleri yazdırmak için bir kod satırı ekleyelim.

1. Değişkenin `query` altında, aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense'in size sembol hakkında Hızlı Bilgi gösterdiğini görüyorsunuz. **Quick Info** `query`

   ![Visual Studio IntelliSense kelime tamamlama](../media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün `query` geri kalanını eklemek için **Sekme'ye**basın.

1. Aşağıdaki kodgibi görünmek için kod bloğunu kapatın. Kodu oluşturmak `Console.WriteLine` için **Sekme'ye** iki kez `cw` basarak ve sonra tekrar kod parçacıkları kullanarak pratik yapabilirsiniz.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

İlk seferinde kimse kodu doğru şekilde kullanmaz ve değiştirmeniz gereken şeylerden biri de bir değişkenin veya yöntemin adıdır. Değişkeni `words`yeniden adlandırmak için Visual Studio'nun [yeniden düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim. `_words`

1. `_words` İmlecinizi değişkenin tanımının üzerine yerleştirin ve sağ tıklatma veya bağlam menüsünden **Yeniden Adlandır'ı** seçin veya Ctrl**R**, **Ctrl**+ **Ctrl**+**R**tuşuna basın.

   Editörün sağ üst kısmında açılır yeniden **adlandırma** iletişim kutusu görüntülenir.

1. İstenilen ad **sözcükleri**girin. `words` Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **Enter**tuşuna basmadan önce, Yeniden **Adlandır** açılır kutusuna **yorum ekle** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](../media/tutorial-rename.png)

1. **Enter**'a basın.

   Her iki `words` olay da kod `words` yorumunda atıfta bulunularak yeniden adlandırıldı.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Kodda gezinme](../../ide/navigating-code.md)
- [Anahat](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
