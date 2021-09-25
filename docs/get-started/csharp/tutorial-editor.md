---
title: 'Öğretici: C# geliştiricileri için düzenleme'
description: Visual Studio'da kod düzenleyicisine 10 dakikalık bir giriş, C# Visual Studio yazmayı, gezinmeyi ve anlamayı kolaylaştıran bazı yöntemleri gösterir.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c75a5e83ebdabd814e37f601979e0e8b5e808cec
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431377"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>C ile kod düzenleyicisini kullanmayı öğrenin\#

Visual Studio'daki kod düzenleyicisine bu 10 dakikalık girişte, Visual Studio'nin C# kodu yazmayı, gezinmeyi ve anlamayı kolaylaştıran bazı yollara bakmak için bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

Bu makalede, C# hakkında zaten bilgi sahibi olduğunuz varsaylanmıştır. Yoksa, C# ile Kullanmaya başlayın gibi bir [öğreticiye](tutorial-aspnet-core.md) bakmanızı ve ASP.NET Core Visual Studio öneririz.

> [!TIP]
> Bu makaleyi takip etmek için C# ayarlarının seçili olduğundan emin Visual Studio. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz. Ortam ayarlarını seçme.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni kod dosyası oluşturma

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü **çubuğundaki** Dosya menüsünde Yeni  Dosya'ya tıklayın > **veya** Ctrl N **tuşlarına** + **basın.**

1. Yeni Dosya **iletişim kutusundaki** Genel  kategorisi altında **Visual C#** Sınıfı'na ve ardından Aç'ı **seçin.**

   Düzenleyicide C# sınıfının iskeletiyle yeni bir dosya açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazıları elde etmek için tam Visual Studio projesini oluşturmamız gerek olmadığını, tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio'daki C# kod dosyasının ekran görüntüsü.](../media/tutorial-editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak **için Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'a tıklayın.

1. Menü **çubuğundaki** Dosya menüsünde Yeni  Dosya'ya tıklayın > **veya** Ctrl N **tuşlarına** + **basın.**

1. Yeni Dosya **iletişim kutusundaki** Genel  kategorisi altında **Visual C#** Sınıfı'na ve ardından Aç'ı **seçin.**

   Düzenleyicide C# sınıfının iskeletiyle yeni bir dosya açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazıları elde etmek için tam Visual Studio projesini oluşturmamız gerek olmadığını, tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio'daki C# kod dosyasının ekran görüntüsü.](../media/tutorial-editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak için **Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'ı seçin.

1. Menü **çubuğundaki** Dosya menüsünde Yeni  Dosya'ya tıklayın > **veya** Ctrl N **tuşlarına** + **basın.**

1. Yeni Dosya **iletişim kutusundaki** Genel  kategorisi altında **Visual C#** Sınıfı'na ve ardından Aç'ı **seçin.**

   Düzenleyicide C# sınıfının iskeletiyle yeni bir dosya açılır. Kod düzenleyicisinin tek ihtiyacınız olan bir kod dosyası Visual Studio bir proje oluşturmak zorunda &mdash; değil.

   :::image type="content" source="media/vs-2022/tutorial-editor.png" alt-text="Visual Studio 2022'de C# kod dosyasının ekran görüntüsü.":::

::: moniker-end

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın *olarak kullanılan kod* bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı kod parçacıkları sağlar. [Kod parçacıkları](../../ide/code-snippets.md) C#, Visual Basic ve C++ gibi farklı programlama dilleri için kullanılabilir.

Şimdi C# kod parçacığını `void Main` dosyamıza ek o zaman.

::: moniker range="<=vs-2019"

1. İmlecinizi dosyaya son kapanış ayracı **}** üzerine yerleştirerek karakterleri yazın (bunun ne anlama geldiğini bilmiyorsanız çok fazla `svm` `static void Main` &mdash; endişelenmeyin anlamına gelir).

   Kod parçacığıyla ilgili bilgilerle birlikte bir açılır `svm` iletişim kutusu görüntülenir.

   ![Visual Studio'de kod parçacığı için IntelliSense açılan Visual Studio.](../media/tutorial-intellisense-snippet.png)

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Yöntem `static void Main()` imzasının dosyaya ekli olduğunu görüyorsunuz. [Main() yöntemi,](/dotnet/csharp/programming-guide/main-and-command-args/) C# uygulamaları için giriş noktasıdır.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir.   >  **IntelliSense** Insert  >  **Snippet'ı** Düzenle'yi seçerek veya **Ctrl** K , Ctrl X tuşlarına basarak ve ardından dilinizin klasörünü seçerek diliniz için kullanılabilir kod +   + parçacıklarına bakabilirsiniz. C# için liste şöyle görünür:

![C# kod parçacığı listesi için IntelliSense açılan listesinin ekran görüntüsü.](../media/tutorial-code-snippet-list.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. İmlecinizi dosyada son kapanış **`}`** ayracı'nın hemen üzerine yerleştirerek karakterlerini `svm` yazın. `svm`henüz bunun ne anlama geldiğini bilmiyorsanız endişelenmeyin `static void Main` &mdash; anlamına gelir.

   Kod parçacığıyla ilgili bilgilerle birlikte bir açılır `svm` iletişim kutusu görüntülenir.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-snippet.png" alt-text="Visual Studio 2022'de bir kod parçacığı için IntelliSense açılır pencere ekran görüntüsü.":::

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Yöntem imzasının `static void Main()` dosyaya ekli olduğunu görüyorsunuz. [Main() yöntemi,](/dotnet/csharp/programming-guide/main-and-command-args/) C# uygulamaları için giriş noktasıdır.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir. IntelliSense Insert Snippet'ı Düzenle'yi seçerek veya  >    >   Ctrl K , **Ctrl** X tuşlarına basarak ve ardından programlama diliniz için klasörü seçerek diliniz için kullanılabilir kod +   + parçacıklarına bakabilirsiniz. C# için kod parçacığı listesi şöyle görünür:

:::image type="content" source="media/vs-2022/tutorial-code-snippet-list.png" alt-text="C# kod parçacığı listesi için IntelliSense açılan listesinin ekran görüntüsü.":::

::: moniker-end

Listede sınıf, [oluşturucu,](/dotnet/csharp/fundamentals/types/classes)for [döngüsü,](/dotnet/csharp/programming-guide/classes-and-structs/constructors)if [](/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement) veya switch deyimi ve [daha](/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement) fazlası oluşturmak için [kod](/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement) parçacıkları yer almaktadır.

## <a name="comment-out-code"></a>Kodu açıklamaya alma

::: moniker range="<=vs-2019"

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç çubuğu Visual Studio kodlarken daha üretken çalışmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu[(IntelliSense,](../../ide/using-intellisense.md) eşleşen yöntemlerin listesini görüntüleyen bir kodlama yardımıdır), satır girintisini artırabilir veya azaltabilir veya derlemek istemeyebilirsiniz kodu açıklama satırı olarak ekleyebilirsiniz. Bu bölümde bazı kodlara açıklama olarak yer veserden bakabilirsiniz.

![Visual Studio'daki Düzenleyici araç çubuğunun ekran görüntüsü.](../media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu yöntem `Main()` gövdesine yapıştırın.

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

1. değişkenlerini kullanacağız ancak daha sonra tamamen silmek `morewords` istemeyeceğiz. Bunun yerine, bu satırları açıklama satırına bakalım. öğesinin tanımının tamamını kapatma noktalı virgülle seçin ve ardından araç çubuğunda seçili satırları `morewords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz Ctrl K , **Ctrl** + C  + **tuşlarına basın.**

   ![Visual Studio'daki Düzenleyici araç çubuğundaki Açıklama dışarı Visual Studio.](../media/tutorial-comment-out.png)

   C# açıklama `//` karakterleri, kodu açıklama satırı yapmak için seçilen her satırın başına eklenir.

::: moniker-end

::: moniker range=">=vs-2022"

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç çubuğu Visual Studio kodlarken daha üretken çalışmanıza yardımcı olur. Örneğin, [IntelliSense](../../ide/using-intellisense.md) tamamlama modunu açıp satır girintisini azaltabilir veya derlemek istemeyebilirsiniz.

:::image type="content" source="media/vs-2022/tutorial-editor-toolbar.png" alt-text="Visual Studio 2022'de Metin Düzenleyici araç çubuğunun ekran görüntüsü.":::

Bazı kodlara açıklama olarak bakalım.

1. Aşağıdaki kodu yöntem `Main()` gövdesine yapıştırın.

    ```csharp
    // someWords is a string array.
    string[] someWords = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] moreWords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    // Alphabetically sort the words.
    IEnumerable<string> query = from word in someWords
                                orderby word
                                select word;
    ```

1. değişkenlerini kullanacağız ancak daha sonra bu değişkeni silmek `moreWords` istemeyeceğiz. Bunun yerine, bu satırları açıklama satırı olarak kullanıruz. Kapalı olan noktalı virgül tanımının tamamını seçin ve ardından araç çubuğunda seçili satırları `moreWords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl** + **E**, Ctrl C  + **tuşlarına basın.**

   :::image type="content" source="media/vs-2022/tutorial-comment-out.png" alt-text="2022'de Metin Düzenleyici araç çubuğundaki Açıklama Visual Studio ekran görüntüsü.":::

   C# açıklama `//` karakterleri, kodu açıklama satırı yapmak için seçilen her satırın başına eklenir.

::: moniker-end

## <a name="collapse-code-blocks"></a>Kod bloklarını daralt

için oluşturulan boş oluşturucu görmek [](/dotnet/csharp/programming-guide/classes-and-structs/constructors) istemiyoruz, bu nedenle kodun görünümünü `Class1` daraltın. Oluşturucuda ilk satırın kenar boşluğunda eksi işareti bulunan küçük gri kutuyu seçin. Veya klavyeyi kullanmayı tercih ederseniz imleci oluşturucu kodunun herhangi bir yerine yerleştirerek **Ctrl** + M , Ctrl **M**  + **tuşlarına basın.**

::: moniker range="<=vs-2019"

![Metin Düzenleyici araç çubuğundaki Genel Görünüm daralt düğmesinin ekran Visual Studio.](../media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta ( ) `...` alır. Kod bloğuna yeniden genişletmek için, artık artı işareti olan aynı gri kutuya tıklayın veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-collapse.png" alt-text="2022'de Metin Düzenleyici araç çubuğundaki Satır Visual Studio düğmesinin ekran görüntüsü.":::

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta ( ) `...` alır. Kod bloğu yeniden genişletmek için, artık artı işareti olan gri kutuyu seçin veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

::: moniker-end

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

::: moniker range="<=vs-2019"

Bu Visual Studio, bir türün, yöntemin vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir.  Örneğin Tanıma Git'i seçerek veya simgeye başvurulan her yerde **F12** tuşuna basabilirsiniz. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Peek [Definition kullanmakdır.](../../ide/go-to-and-peek-definition.md#peek-definition) Türün tanımına göz `string` atalım.

1. herhangi bir oluşuma sağ tıklayın ve `string` içerik **menüsünden Tanıma** Göz At'ı seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   ![Visual Studio'da Bir Tanıma Göz At penceresinin ekran görüntüsü.](../media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek göz atarak tanım penceresini kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

Bu Visual Studio türün, yöntemin veya değişkenin tanımını incelemeyi kolaylaştırır. Bunun bir yolu Tanıma Git'i seçerek veya  bir sembole başvurulan herhangi bir yerde **F12** tuşuna basarak tanıma gitmektir. Odağınızı üzerinde çalışmakta olduğunu koddan uzak olmayan daha da hızlı bir yol, Peek [Definition kullanmaktır.](../../ide/go-to-and-peek-definition.md#peek-definition)

Türün tanımına göz `string` atalım.

1. herhangi bir oluşuma sağ tıklayın ve `string` içerik **menüsünden Tanıma** Göz At'ı seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   :::image type="content" source="media/vs-2022/tutorial-peek-definition.png" alt-text="Visual Studio 2022'de Tanıma göz at penceresinin ekran görüntüsü.":::

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek tanımlama penceresine göz at penceresini kapatın.

::: moniker-end

## <a name="use-intellisense-to-complete-words"></a>IntelliSense kullanarak sözcükleri tamamlama

::: moniker range="<=vs-2019"

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne kadar karakter yazarak daha anlaşılır olduğunu da anlayana kadar kullanabilirsiniz. Şimdi konsol penceresine sipariş edilen dizeleri yazdırmak için bir kod satırı ekliyiz. Bu, programın çıkışının standart olduğu yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense'in simge hakkında **Hızlı Bilgi** göster olduğunu `query` görürsünüz.

   ![Visual Studio'da IntelliSense sözcük tamamlama açılan Visual Studio.](../media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün geri `query` kalanını eklemek için Tab tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin. Hatta kodu oluşturmak için Sekme tuşuna iki kez basarak kod parçacıklarını tekrar `cw` kullanmayı da  `Console.WriteLine` ekleyebilirsiniz.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

::: moniker-end

::: moniker range=">=vs-2022"

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne kadar karakter yazarak daha anlaşılır olduğunu da anlayana kadar kullanabilirsiniz.

Şimdi konsol penceresine sipariş edilen dizeleri yazdırmak için bir kod satırı ekliyiz. Bu, programın çıkışının standart olduğu yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   Simgesi hakkında bilgi olan bir IntelliSense açılır pencere `query` görürsünüz.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-completion-list.png" alt-text="Visual Studio 2022'de IntelliSense sözcük tamamlama açılan ekran görüntüsü.":::

1. IntelliSense sözcük tamamlama kullanarak sözcüğün geri `query` kalanını eklemek için Sekme tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin. deyimini oluşturmak için Sekme tuşuna iki kez basarak kod `cw` parçacıklarıyla daha fazla  `Console.WriteLine` alıştırmalar yapın.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

::: moniker-end

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

::: moniker range="<=vs-2019"

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio yeniden [düzenleme işlevini](../../ide/refactoring-in-visual-studio.md) `_words` `words` deneyelim.

1. İmlecinizi değişkenin tanımının üzerine yerleştirerek sağ tıklama veya bağlam menüsünden Yeniden Adlandır'ı seçin veya `_words` **Ctrl** R ,  + Ctrl R **tuşlarına** + **basın.**

   Düzenleyicinin sağ **üst kısmında** bir açılan Yeniden Adlandırma iletişim kutusu görüntülenir.

1. İstediğiniz ad sözcüklerini **girin.** Sorguda başvurusunun `words` da otomatik olarak yeniden adlandırıldıklarından emin oluruz. Enter tuşuna **basmadan** önce **Yeniden adlandır** açılır kutusunda Açıklama **dahil edin** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusunun ekran görüntüsü Visual Studio.](../media/tutorial-rename.png)

1.  **Enter** tuşuna basın.

   Hem `words` oluşumları yeniden adlandırılmıştır hem de kod `words` açıklamasındaki başvurusudur.

::: moniker-end

::: moniker range=">=vs-2022"

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio yeniden [düzenleme işlevini](../../ide/refactoring-in-visual-studio.md) `someWords` `unsortedWords` deneyelim.

1. İmlecinizi değişkenin tanımının üzerine yerleştirerek sağ tıklama veya bağlam menüsünden Yeniden `someWords` Adlandır'ı seçin veya **F2 tuşuna basın.** 

   **Düzenleyicinin** sağ üst kısmında Yeniden Adlandır iletişim kutusu görüntülenir.

   :::image type="content" source="media/vs-2022/tutorial-rename-start.png" alt-text="Visual Studio 2022'nin düzenleyicisinde Bulunan Yeniden Adlandır açılır kutusunun ekran görüntüsü.":::

1. İstenen **unsortedWords adını girin.** Atama deyiminde başvurusun da `unsortedWords` otomatik `query` olarak yeniden adlandırıldı olduğunu görüyorsunuz. Enter tuşuna **basmadan** önce **Yeniden adlandır** açılır kutusunda Açıklama **dahil edin** onay kutusunu seçin.

   :::image type="content" source="media/vs-2022/tutorial-rename.png" alt-text="Visual Studio 2022'de Yeniden Adlandır açılır kutusunun ekran görüntüsü.":::

1. **Enter tuşuna** basın veya **Yeniden Adlandır** iletişim kutusunda **Uygula'ya** tıklayın.

   Kodundaki her `someWords` iki oluşum da yeniden adlandırılmıştır ve kod `someWords` açıklamanıza metinleri de eklemez.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Kodda gezinme](../../ide/navigating-code.md)
- [Anahat Oluşturma](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
