---
title: Kod düzenleyicisinde düzenleme için giriş
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a0c8122bd08e4eb9af68a0aa70f06cfb18e51469
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595273"
---
# <a name="learn-to-use-the-code-editor"></a>Kod düzenleyicisini kullanmayı öğrenin

Visual Studio 'da kod düzenleyicisine bu 10 dakikalık bir giriş yaptığınızda, Visual Studio 'Nun kodu yazma, gezinme ve anlama işlemlerini daha kolay hale getiren bazı yöntemlere bakmak için bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bu makalede, bir programlama diliyle zaten bilgi sahibi olduğunuz varsayılır. Aksi takdirde, [Python](../ide/quickstart-python.md) veya [C#](../get-started/csharp/tutorial-aspnet-core.md)ile bir web uygulaması oluşturma veya [Visual Basic](../ide/quickstart-visual-basic-console.md) ya da [C++](/cpp/get-started/tutorial-console-cpp)ile bir konsol uygulaması oluşturma gibi öncelikle programlama hızlı başlangıçlarından birine bakmanız önerilir.

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluştur

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **ESC** tuşuna basın veya başlangıç penceresinde **kod olmadan devam et** ' e tıklayın.

::: moniker-end

2. Menü çubuğundaki **Dosya** menüsünde **Yeni**  >  **Dosya**' yı seçin.

3. **Yeni dosya** iletişim kutusunda, **genel** kategori altında, **Visual C# sınıfı**' nı seçin ve sonra **Aç**' ı seçin.

   Yeni bir dosya, bir C# sınıfının iskelet ile düzenleyicide açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmak zorunda olmadığınızdan emin olun; tüm ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio 'da C# kod dosyası](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../ide/code-snippets.md) , C#, Visual Basic ve C++ gibi farklı programlama dilleri için kullanılabilir. Şimdi de C# `void Main` kod parçacığını dosyanıza ekleyelim.

1. İmlecinizi, dosyadaki son **Kapanış küme ayracı** üzerine yerleştirin ve karakterleri yazın `svm` . ( `svm` için temsil eder `static void Main` ; [Main ()](/dotnet/csharp/programming-guide/main-and-command-args/) yöntemi C# uygulamalarının giriş noktasıdır.)

   Kod parçacığı hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir `svm` .

   ![Visual Studio 'da kod parçacığı için IntelliSense](media/tutorial-intellisense-snippet.png)

1. Kod parçacığını eklemek için **sekme** tuşuna iki kez basın.

   `static void Main()`Dosyanın imzasını dosyaya eklendiğini görürsünüz.

Kullanılabilir kod parçacıkları farklı programlama dilleri için farklılık gösterir. **Edit**  >  **IntelliSense**  >  **ekleme kod parçacığını**Düzenle ' yi ve ardından Dilinizin klasörünü seçerek diliniz için kullanılabilir kod parçacıkları bölümüne bakabilirsiniz. C# için liste şöyle görünür:

![C# kod parçacığı listesi](media/tutorial-code-snippet-list.png)

Liste, bir [sınıf](/dotnet/csharp/programming-guide/classes-and-structs/classes), [Oluşturucu](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [for](/dotnet/csharp/language-reference/keywords/for) döngüsü, bir [if](/dotnet/csharp/language-reference/keywords/if-else) veya [Switch](/dotnet/csharp/language-reference/keywords/switch) ifadesini ve daha fazlasını oluşturmaya yönelik kod parçacıklarını içerir.

## <a name="comment-out-code"></a>Kodu dışarı açıklama

Visual Studio 'daki menü çubuğu altındaki düğmelerin satırı olan araç çubuğu, kod olarak daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilirsiniz ([IntelliSense](../ide/using-intellisense.md) , eşleşen yöntemlerin bir listesini, diğer şeyleri arasından görüntüleyen bir kodlama yardımıdır), bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak değiştirir. Bu bölümde, bazı kodları açıklayacağız.

![Düzenleyici araç çubuğu](media/tutorial-editor-toolbar.png)

1. Aşağıdaki kodu `Main()` yöntem gövdesine yapıştırın.

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

1. Bu değişkeni kullanmıyoruz `morewords` , ancak bunu daha sonra tamamen silmek istemdiğimiz için kullanabiliriz. Bunun yerine, bu satırları açıklamaya bakalım. Tüm tanımlamayı `morewords` sağ noktalı virgülle seçin ve ardından araç çubuğundaki **Seçili çizgiler** düğmesini seçin. Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C**tuşlarına basın.

   ![Açıklama dışarı düğmesi](media/tutorial-comment-out.png)

   C# Açıklama karakterleri, `//` kodu açıklama eklemek için seçili her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını Daralt

Oluşturulan boş [oluşturucuyu](/dotnet/csharp/programming-guide/classes-and-structs/constructors) görmek istemiyorum `Class1` , bu nedenle kodun görünümümüzü kaldırmak için bunu daralm. Oluşturucunun ilk satırının kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin. Ya da bir klavye kullanıcısı kullanıyorsanız, imleci Oluşturucu kodunda herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m**tuşlarına basın.

![Anahat Daralt düğmesi](media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi bir artı işaretine sahip olan gri kutuya tıklayın veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltdığınızda yararlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüle

Visual Studio Düzenleyicisi bir tür, yöntem vb. tanımlamayı incelemenizi kolaylaştırır. Tek bir yol, tanımı içeren dosyaya gitmeniz, örneğin simgenin başvurduğu her yerde **Tanıma Git** ' i seçerek. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türün tanımına göz atalım `string` .

1. Herhangi bir oluşumuna sağ tıklayın `string` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif olarak, **alt** + **F12**tuşuna basın.

   Sınıfının tanımına sahip bir açılır pencere görüntülenir `String` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   ![Tanım penceresi Özeti](media/tutorial-peek-definition.png)

1. Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek atılamıyor tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlaması için IntelliSense kullanma

Kodlamadan [IntelliSense](../ide/using-intellisense.md) , değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. Düzenli dizeleri konsol penceresine yazdırmak için bir kod satırı ekleyelim, bu da programdan git 'in çıkış için standart yer.

1. Değişkenin altında `query` aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense, sembol hakkında **hızlı bilgi** gösterir `query` .

   ![Visual Studio 'da IntelliSense kelime tamamlama](media/tutorial-intellisense-completion-list.png)

1. `query`IntelliSense 'in kelime tamamlama işlevini kullanarak sözcüğün geri kalanını eklemek Için **Tab**tuşuna basın.

1. Aşağıdaki kod gibi görmek için kod bloğunu sona erdirin. Kodu `cw` oluşturmak için iki kez **Tab** tuşuna basarak ve sonra da kod parçacıklarını yeniden kullanarak da alıştırma yapabilirsiniz `Console.WriteLine` .

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

Hiç kimse ilk kez kod alır ve değiştirmeniz gerekebilecek işlemlerden biri bir değişkenin veya yöntemin adıdır. Değişkeni olarak yeniden adlandırmak için Visual Studio 'nun yeniden [düzenleme](../ide/refactoring-in-visual-studio.md) işlevini deneyelim `_words` `words` .

1. İmlecinizi değişkeninin tanımına yerleştirin `_words` ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin veya **CTRL** + **r**, **CTRL** + **r**tuşlarına basın.

   Düzenleyicinin sağ üst köşesinde bir açılır pencere **yeniden adlandırma** iletişim kutusu görüntülenir.

1. İstenen ad **sözcüklerini**girin. `words`Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **ENTER**tuşuna tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](media/tutorial-rename.png)

1.  **Enter** tuşuna basın.

   Her iki tekrarın her ikisi de `words` yeniden adlandırıldı ve `words` kod açıklamasında başvurusu.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [Koda git](../ide/navigating-code.md)
- [Anahat Oluşturma](../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
