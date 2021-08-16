---
title: 'Öğretici: C# geliştiricileri için düzenleme'
description: Visual Studio'da kod düzenleyicisine 10 dakikalık giriş, Visual Studio C# kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştıran bazı yöntemleri gösterir.
ms.custom: vs-acquisition, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 43608336cb6c2a07f5cf788661fadd25b8986aadbb7c4467020481bff8e42250
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374122"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>C ile kod düzenleyicisini kullanmayı öğrenin\#

Visual Studio'daki kod düzenleyicisine bu 10 dakikalık girişte, Visual Studio'nin C# kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştıran bazı yöntemlere göz atacak bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio yüklemediyebilirsiniz. [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

Bu makalede, C# hakkında zaten bilgi sahibi olduğunuz varsaylanmıştır. Yoksa, C# ile Kullanmaya başlayın gibi bir [öğreticiye](tutorial-aspnet-core.md) bakmanızı ve ASP.NET Core Visual Studio öneririz.

> [!TIP]
> Bu makaleyi takip etmek için C# ayarlarının seçili olduğundan emin Visual Studio. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz. Ortam ayarlarını seçme.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni kod dosyası oluşturma

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak **için Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'a tıklayın.

::: moniker-end

2. Menü **çubuğundaki** Dosya menüsünde Yeni Dosya'ya tıklayın  >  **veya** Ctrl N **tuşlarına** + **basın.**

3. Yeni Dosya **iletişim kutusundaki** Genel  kategorisi altında **Visual C#** Sınıfı'na ve ardından Aç'ı **seçin.**

   Düzenleyicide C# sınıfının iskeletiyle yeni bir dosya açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazıları elde etmek için tam Visual Studio projesini oluşturmamız gerek olmadığını, tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio'de C# kod Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın *olarak kullanılan kod* bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı kod parçacıkları sağlar. [Kod parçacıkları](../../ide/code-snippets.md) C#, Visual Basic ve C++ gibi farklı programlama dilleri için kullanılabilir. Şimdi C# kod parçacığını `void Main` dosyamıza ek o zaman.

1. İmlecinizi dosyaya son kapanış ayracı **}** üzerine yerleştirerek karakterleri yazın (bunun ne anlama geldiğini bilmiyorsanız çok fazla `svm` `static void Main` &mdash; endişelenmeyin anlamına gelir).

   Kod parçacığıyla ilgili bilgilerle birlikte bir açılır `svm` iletişim kutusu görüntülenir.

   ![Visual Studio'de kod parçacığı için IntelliSense](../media/tutorial-intellisense-snippet.png)

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Yöntem `static void Main()` imzasının dosyaya ekli olduğunu görüyorsunuz. [Main() yöntemi,](/dotnet/csharp/programming-guide/main-and-command-args/) C# uygulamaları için giriş noktasıdır.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir.   >  **IntelliSense** Insert  >  **Snippet'ı** Düzenle'yi seçerek veya **Ctrl** K , Ctrl X tuşlarına basarak ve ardından dilinizin klasörünü seçerek diliniz için kullanılabilir kod +   + parçacıklarına bakabilirsiniz. C# için liste şöyle görünür:

![C# kod parçacığı listesi](../media/tutorial-code-snippet-list.png)

Listede sınıf, [oluşturucu,](/dotnet/csharp/programming-guide/classes-and-structs/classes)for [döngüsü,](/dotnet/csharp/programming-guide/classes-and-structs/constructors)if [](/dotnet/csharp/language-reference/keywords/for) veya switch deyimi ve [daha](/dotnet/csharp/language-reference/keywords/if-else) fazlası oluşturmak için [kod](/dotnet/csharp/language-reference/keywords/switch) parçacıkları yer almaktadır.

## <a name="comment-out-code"></a>Kodu açıklamaya alma

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç çubuğu Visual Studio kodlarken daha üretken çalışmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu[(IntelliSense,](../../ide/using-intellisense.md) diğer şeylerin dışında eşleşen yöntemlerin listesini görüntüleyen bir kodlama yardımıdır), satır girintisini artırabilir veya azaltabilir veya derlemek istemeyebilirsiniz kodu açıklama satırı olarak ekleyebilirsiniz. Bu bölümde bazı kodlara açıklama olarak yer veserden bakabilirsiniz.

![Düzenleyici araç çubuğu](../media/tutorial-editor-toolbar.png)

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

1. değişkenlerini kullanmaz ancak daha sonra bunu kullanarak tamamen silmek `morewords` istemeyebilirsiniz. Bunun yerine, bu satırları açıklama satırına bakalım. öğesinin tanımının tamamını kapanış noktalı virgül olarak seçin ve ardından araç çubuğunda seçili satırları `morewords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz **Ctrl** + **K**, Ctrl C  + **tuşlarına basın.**

   ![Açıklama düğmesi](../media/tutorial-comment-out.png)

   C# açıklama `//` karakterleri, kodu açıklama satırı yapmak için seçilen her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daralt

Oluşturulan için boş oluşturucu görmek [](/dotnet/csharp/programming-guide/classes-and-structs/constructors) istemiyoruz, bu nedenle kodun görünümünü `Class1` daraltın. Oluşturucusu ilk satırın kenar boşluğunda eksi işareti bulunan küçük gri kutuyu seçin. Veya klavye kullanıcısıysanız imleci oluşturucu kodunun herhangi bir yerine yerleştirerek Ctrl M , **Ctrl** + **M** **tuşlarına** + **basın.**

![Daralt düğmesinin altı çizili](../media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta ( ) `...` alır. Kod bloğuna yeniden genişletmek için, artık artı işareti olan aynı gri kutuya tıklayın veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

Bu Visual Studio, bir türün, yöntemin vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir.  Örneğin Tanıma Git'i seçerek veya simgeye başvurulan her yerde **F12** tuşuna basabilirsiniz. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Peek [Definition kullanmakdır.](../../ide/go-to-and-peek-definition.md#peek-definition) Türün tanımına göz `string` atalım.

1. herhangi bir oluşuma sağ tıklayın ve `string` içerik **menüsünden Tanıma** Göz At'ı seçin. Alternatif olarak, **Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   ![Tanıma göz atma penceresi](../media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek göz atarak tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense kullanarak sözcükleri tamamlama

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne olduğunu tam olarak anlayan yeterli karakter kullanabilirsiniz. Şimdi sipariş edilen dizeleri konsol penceresine yazdırmak için bir kod satırı ek o zaman. Bu, programın çıkışının standart olduğu yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense'in simge hakkında **Hızlı Bilgi** göster olduğunu `query` görürsünüz.

   ![Visual Studio'de IntelliSense sözcük Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün geri kalanını `query` eklemek için Tab tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin. Hatta kodu oluşturmak için Sekme tuşuna iki kez basarak kod parçacıklarını tekrar `cw` kullanmayı da  `Console.WriteLine` ekleyebilirsiniz.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini `_words` `words` deneyelim.

1. İmlecinizi değişkenin tanımının üzerine yerleştirerek sağ tıklama veya bağlam menüsünden Yeniden Adlandır'ı seçin veya `_words` Ctrl R , **Ctrl** R  +   + **tuşlarına basın.**

   Düzenleyicinin sağ **üst kısmında** bir açılan Yeniden Adlandırma iletişim kutusu görüntülenir.

1. İstediğiniz ad sözcüklerini **girin.** Sorguda başvurusunun `words` da otomatik olarak yeniden adlandırıldıklarından emin oluruz. Enter tuşuna **basmadan** **önce Yeniden adlandır** açılır kutusunda Açıklama dahil **edin** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](../media/tutorial-rename.png)

1.  **Enter** tuşuna basın.

   Hem oluşumları yeniden adlandırılmıştır hem de kod `words` `words` açıklamasındaki başvurusudur.

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
