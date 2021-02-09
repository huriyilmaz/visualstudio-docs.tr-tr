---
title: C# geliştiricileri için düzenlemelere giriş
description: Visual Studio 'da kod düzenleyicisine bu 10 dakikalık bir giriş, Visual Studio 'Nun C# kodunu yazma, gezinme ve anlamayı kolaylaştıran bazı yolları gösterir.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8724fcb717953f3897bab092eb3895e228e10c60
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909227"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>C ile kod düzenleyicisini kullanmayı öğrenin\#

Visual Studio 'daki kod düzenleyicisine bu 10 dakikalık bir giriş için, Visual Studio 'Nun C# kodunu yazma, gezinme ve anlamayı kolaylaştıran bazı yöntemlere bakmak için bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bu makalede, C# hakkında zaten bilgi sahibi olduğunuz varsayılır. Değilseniz, önce [C# ile çalışmaya başlama ve Visual Studio 'da ASP.NET Core](tutorial-aspnet-core.md) gibi bir öğreticiye bakmanız önerilir.

> [!TIP]
> Bu makaleyle birlikte izlemek için, Visual Studio için C# ayarlarının seçili olduğundan emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında daha fazla bilgi için bkz. [ortam ayarlarını seçme](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluştur

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **ESC** tuşuna basın veya başlangıç penceresinde **kod olmadan devam et** ' e tıklayın.

::: moniker-end

2. Menü çubuğundaki **Dosya** menüsünde **Yeni**  >  **Dosya**' yı seçin veya **CTRL** + **N** tuşuna basın.

3. **Yeni dosya** iletişim kutusunda, **genel** kategori altında, **Visual C# sınıfı**' nı seçin ve sonra **Aç**' ı seçin.

   Yeni bir dosya, bir C# sınıfının iskelet ile düzenleyicide açılır. (Kod düzenleyicisinin sunduğu avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmak zorunda olmadığınızdan emin olun; tüm ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio 'da C# kod dosyası](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../../ide/code-snippets.md) , C#, Visual Basic ve C++ gibi farklı programlama dilleri için kullanılabilir. Şimdi de C# `void Main` kod parçacığını dosyanıza ekleyelim.

1. İmlecinizi, dosyadaki son kapanış ayracı üzerine yerleştirin **}** ve karakterleri yazın `svm` ( `static void Main` &mdash; ne anlama geldiğini bilmiyorsanız çok fazla endişelenmeyin).

   Kod parçacığı hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir `svm` .

   ![Visual Studio 'da kod parçacığı için IntelliSense](../media/tutorial-intellisense-snippet.png)

1. Kod parçacığını eklemek için **sekme** tuşuna iki kez basın.

   `static void Main()`Dosyanın imzasını dosyaya eklendiğini görürsünüz. [Main ()](/dotnet/csharp/programming-guide/main-and-command-args/) yöntemi C# uygulamalarının giriş noktasıdır.

Kullanılabilir kod parçacıkları farklı programlama dilleri için farklılık gösterir. Dil için kullanılabilir kod parçacıklarını,   >  **IntelliSense**  >  **ekleme kod parçacığı** seçerek veya **CTRL** + **K**, **CTRL** + **X** tuşlarına basarak ve sonra dilin klasörünü seçerek görebilirsiniz. C# için liste şöyle görünür:

![C# kod parçacığı listesi](../media/tutorial-code-snippet-list.png)

Liste, bir [sınıf](/dotnet/csharp/programming-guide/classes-and-structs/classes), [Oluşturucu](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [for](/dotnet/csharp/language-reference/keywords/for) döngüsü, bir [if](/dotnet/csharp/language-reference/keywords/if-else) veya [Switch](/dotnet/csharp/language-reference/keywords/switch) ifadesini ve daha fazlasını oluşturmaya yönelik kod parçacıklarını içerir.

## <a name="comment-out-code"></a>Kodu dışarı açıklama

Visual Studio 'daki menü çubuğu altındaki düğmelerin satırı olan araç çubuğu, kod olarak daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilirsiniz ([IntelliSense](../../ide/using-intellisense.md) , eşleşen yöntemlerin bir listesini, diğer şeyleri arasından görüntüleyen bir kodlama yardımıdır), bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak değiştirir. Bu bölümde, bazı kodları açıklayacağız.

![Düzenleyici araç çubuğu](../media/tutorial-editor-toolbar.png)

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

1. Bu değişkeni kullanmıyoruz `morewords` , ancak bunu daha sonra tamamen silmek istemdiğimiz için kullanabiliriz. Bunun yerine, bu satırları açıklamaya bakalım. Tüm tanımlamayı `morewords` sağ noktalı virgülle seçin ve ardından araç çubuğundaki **Seçili çizgiler** düğmesini seçin. Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C** tuşlarına basın.

   ![Açıklama dışarı düğmesi](../media/tutorial-comment-out.png)

   C# Açıklama karakterleri, `//` kodu açıklama eklemek için seçili her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını Daralt

Oluşturulan boş [oluşturucuyu](/dotnet/csharp/programming-guide/classes-and-structs/constructors) görmek istemiyorum `Class1` , bu nedenle kodun görünümümüzü kaldırmak için bunu daralm. Oluşturucunun ilk satırının kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin. Ya da bir klavye kullanıcısı kullanıyorsanız, imleci Oluşturucu kodunda herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m** tuşlarına basın.

![Anahat Daralt düğmesi](../media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi bir artı işaretine sahip olan gri kutuya tıklayın veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltdığınızda yararlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüle

Visual Studio Düzenleyicisi bir tür, yöntem vb. tanımlamayı incelemenizi kolaylaştırır. Bir yol, tanımı içeren dosyaya gitmeniz, örneğin **Tanıma Git** ' i seçerek veya sembolün başvurduğu her yerde **F12** tuşuna basarak. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türün tanımına göz atalım `string` .

1. Herhangi bir oluşumuna sağ tıklayın `string` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif olarak, **alt** + **F12** tuşuna basın.

   Sınıfının tanımına sahip bir açılır pencere görüntülenir `String` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   ![Tanım penceresi Özeti](../media/tutorial-peek-definition.png)

1. Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek atılamıyor tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlaması için IntelliSense kullanma

Kodlamadan [IntelliSense](../../ide/using-intellisense.md) , değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. Düzenli dizeleri konsol penceresine yazdırmak için bir kod satırı ekleyelim, bu da programdan git 'in çıkış için standart yer.

1. Değişkenin altında `query` aşağıdaki kodu yazmaya başlayın:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense, sembol hakkında **hızlı bilgi** gösterir `query` .

   ![Visual Studio 'da IntelliSense kelime tamamlama](../media/tutorial-intellisense-completion-list.png)

1. `query`IntelliSense 'in kelime tamamlama işlevini kullanarak sözcüğün geri kalanını eklemek Için **Tab** tuşuna basın.

1. Aşağıdaki kod gibi görmek için kod bloğunu sona erdirin. Kodu `cw` oluşturmak için iki kez **Tab** tuşuna basarak ve sonra da kod parçacıklarını yeniden kullanarak da alıştırma yapabilirsiniz `Console.WriteLine` .

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

Hiç kimse ilk kez kod alır ve değiştirmeniz gerekebilecek işlemlerden biri bir değişkenin veya yöntemin adıdır. Değişkeni olarak yeniden adlandırmak için Visual Studio 'nun yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim `_words` `words` .

1. İmlecinizi değişkeninin tanımına yerleştirin `_words` ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin veya **CTRL** + **r**, **CTRL** + **r** tuşlarına basın.

   Düzenleyicinin sağ üst köşesinde bir açılır pencere **yeniden adlandırma** iletişim kutusu görüntülenir.

1. İstenen ad **sözcüklerini** girin. `words`Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **ENTER** tuşuna tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](../media/tutorial-rename.png)

1.  **Enter** tuşuna basın.

   Her iki tekrarın her ikisi de `words` yeniden adlandırıldı ve `words` kod açıklamasında başvurusu.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Koda git](../../ide/navigating-code.md)
- [Anahat Oluşturma](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
