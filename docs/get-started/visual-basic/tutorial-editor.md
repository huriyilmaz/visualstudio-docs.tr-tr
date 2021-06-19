---
title: Geliştiriciler için düzenlemeye Visual Basic giriş
description: Visual Studio'de kod düzenleyicisine 10 dakikalık bir giriş, Visual Studio kodu yazmayı, gezinmeyi ve kodu daha kolay Visual Basic gösterir.
ms.custom:
- vs-acquisition
- seodec18
- get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: fe411074c95db15fde4819ffb07eca39a05e844d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390170"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Kod düzenleyicisini Visual Basic

Visual Studio'daki kod düzenleyicisine bu 10 dakikalık girişte, Visual Studio'nin kod yazmayı, gezinmeyi ve kodu daha kolay anlamanıza nasıl Visual Basic bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Henüz Visual Studio Preview [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidip ücretsiz olarak yükleyin.

::: moniker-end

Bu makalede, kaynaklarla ilgili bilgi sahibi Visual Basic. Yoksa, önce Visual Basic ile birlikte Kullanmaya başlayın gibi [bir Visual Studio](../../get-started/visual-basic/tutorial-console.md) öneririz.

> [!TIP]
> Bu makaleyi takip etmek için, uygulama ayarları için Visual Basic emin Visual Studio. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında bilgi için [bkz. Ortam ayarlarını seçme.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Yeni kod dosyası oluşturma

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme **ortamını** açmak **için Esc tuşuna** basın veya başlangıç penceresinde Kod olmadan devam'a tıklayın.

::: moniker-end

2. Menü **çubuğundaki** Dosya menüsünden Yeni **Dosya'ya tıklayın.**

3. Yeni Dosya **iletişim kutusunda,** Genel kategorisi **altında** Sınıf **Visual Basic'ı ve** ardından Aç'ı **seçin.**

   Düzenleyicide yeni bir dosya açılır ve bu dosya bir Visual Basic olur. (Kod düzenleyicisinin sunduğu bazı avantajlardan (söz dizimi vurgulama gibi) kazanmak için tam Visual Studio proje oluşturmanız gerek olmadığını fark etme. Tek ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Basic kod dosyasını Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın *olarak kullanılan kod* bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı kod parçacıkları sağlar. [Kod parçacıkları Visual Basic,](../../ide/code-snippets.md) C# ve C++ gibi farklı programlama dilleri için kullanılabilir. Şimdi Visual Basic Sub kod **parçacığını** dosyamıza ekleriz.

1. İmlecinizi , ve yazarak sub olan `End Class` satırın üzerine **yerleştirebilirsiniz.**

   anahtar sözcüğü ve Alt kod parçacığının nasıl eklendiğinden `Sub` emin olmak için bir **açılır** iletişim kutusu görüntülenir.

   ![Visual Studio'de kod parçacığı için IntelliSense](media/tutorial-intellisense-snippet.png)

1. Kod **parçacığını** eklemek için Sekme tuşuna iki kez basın.

   Alt yordamın ana `MySub()` hatları dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dillerinde değişiklik gösterir. IntelliSense Insert Snippet'ı Düzenle'yi seçerek Visual Basic kod parçacıklarına bakabilirsiniz  >    >   **(veya Ctrl** + **K**, Ctrl X **tuşlarına** + **basın).** Daha Visual Basic kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Visual Basic kod parçacığı listesi](media/tutorial-code-snippet-list.png)

Bilgisayarda bir dosya olup olmadığını belirlemek, bir metin dosyasına yazmak, kayıt defteri değerini okumak, SQL sorgusu yürütmek, Her biri için bir oluşturmak için kod parçacıkları [vardır. Sonraki deyimi](/dotnet/visual-basic/language-reference/statements/for-each-next-statement), ve çok daha fazlası.

## <a name="comment-out-code"></a>Kodu açıklamaya alma

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç Visual Studio kodlarken daha üretken çalışmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu açıp açıp, satır girintisini artırabilir veya azaltabilir ya da derlemek istemeyebilirsiniz. ([IntelliSense,](../../ide/using-intellisense.md) eşleşen yöntemlerin listesini ve diğer öğeleri görüntüleyen bir kodlama yardımıdır.) Bu bölümde bazı kodlara açıklama olarak yer veserden bakabilirsiniz.

![Düzenleyici araç çubuğu düğmeleri](media/tutorial-editor-toolbar.png)

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

1. dizisini kullanmaz, ancak daha sonra bu diziyi kullanarak diziyi tamamen `morewords` silmek istemeyebilirsiniz. Bunun yerine, bu satırları açıklama satırına bakalım. öğesinin kapanış küme ayracı tanımının tamamını seçin ve ardından araç çubuğunda seçili satırları `morewords` **açıklama satırı** yap düğmesini seçin. Klavyeyi kullanmayı tercih ederseniz Ctrl K , **Ctrl** + C  + **tuşlarına basın.**

   ![Açıklama düğmesi](media/tutorial-comment-out.png)

   Visual Basic açıklama `'` karakteri, kodu açıklama satırı yapmak için seçilen her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daralt

Yalnızca ilgini gereken bölümlere odaklanmak için kod bölümlerini daraltabilirsiniz. Alıştırma yapmak için diziyi tek `_words` kod satırına daraltabilirsiniz. içinde eksi işareti bulunan ve satırın kenar boşluğunda bulunan küçük gri kutuyu `Dim _words = New String() {` seçin. Veya klavye kullanıcısıysanız imleci dizi tanımında herhangi bir yere yerleştirerek Ctrl M , **Ctrl** + **M** **tuşlarına** + **basın.**

![Daralt düğmesinin altı çizili](media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta `...` ( ). Kod bloğuna yeniden genişletmek için, artık artı işareti olan gri kutuya tıklayın veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../../ide/outlining.md) adlandırılan ve özellikle uzun yöntemleri veya sınıfların tamamını daraltıyorken yararlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

Visual Studio düzenleyicisi, bir türün, yöntemin vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, tanımı içeren dosyaya gitmektir;  örneğin sembole başvurulan her yerde Tanıma Git'i seçerek. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Peek [Definition kullanmakdır.](../../ide/go-to-and-peek-definition.md#peek-definition) Türün tanımına göz `String` atalım.

1. Söze sağ tıklayın ve `String` içerik **menüsünden Tanıma Göz** At'ı seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   Sınıfının tanımıyla birlikte bir açılır pencere `String` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   ![Tanıma göz atma penceresi](media/tutorial-peek-definition.png)

1. Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek göz atmış tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense kullanarak sözcükleri tamamlama

[IntelliSense,](../../ide/using-intellisense.md) kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne olduğunu tam olarak anlayan yeterli karakter kullanabilirsiniz. Şimdi konsol penceresine sipariş edilen dizeleri yazdırmak için bir kod satırı ek o zaman programdan çıkış için standart bir yerdir.

1. değişkeninin `query` altına aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense'in simge hakkında **Hızlı Bilgi** göster olduğunu `query` görürsünüz.

   ![Visual Studio'de IntelliSense sözcük tamamlama](media/tutorial-intellisense-completion-list.png)

1. IntelliSense'in sözcük tamamlama işlevini kullanarak sözcüğün geri kalanını `query` eklemek için Tab tuşuna **basın.**

1. Kod bloğu aşağıdaki koda benzer şekilde bitsin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

Hiç kimse kodu ilk kez doğru şekilde alamiyor ve değiştirmek zorunda olabileceğiniz şeylerden biri değişkenin veya yöntemin adıdır. Şimdi değişkeni olarak Visual Studio [yeniden düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini `_words` `words` deneyelim.

1. İmlecinizi değişkenin tanımının `_words` üzerine yerleştirerek sağ tıklama **veya** bağlam menüsünden Yeniden Adlandır'ı seçin.

   Düzenleyicinin sağ **üst kısmında** bir açılan Yeniden Adlandırma iletişim kutusu görüntülenir.

1. değişkeni `_words` seçiliyken, sözcüklerin istenen adını **yazın.** Sorguda başvurusunun `words` da otomatik olarak yeniden adlandırıldıklarından emin oluruz. Enter tuşuna **basmadan** veya  **Uygula'ya** tıklamadan önce, Yeniden Adlandır açılan kutusunda **Açıklama** ekle onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](media/tutorial-rename.png)

1. **Enter tuşuna** basın veya Uygula'ya **tıklayın.**

   Hem `words` oluşumları yeniden adlandırılır hem de kod `words` açıklamasındaki başvurusu.

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
