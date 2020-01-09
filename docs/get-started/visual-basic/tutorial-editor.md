---
title: Visual Basic geliştiricileri için düzenlemelere giriş
description: Visual Studio 'da kod düzenleyicisine bu 10 dakikalık bir giriş, Visual Studio 'Nun Visual Basic kodu yazma, gezinme ve anlama işlemlerini daha kolay hale getiren bazı yolları gösterir.
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584614"
---
# <a name="learn-to-use-the-code-editor"></a>Kod Düzenleyicisi'ni kullanmayı öğrenin

Visual Studio Kod düzenleyicisinde 10 dakikalık giriş, Visual Studio yazma, gezinme ve kodu daha kolay anlama yapar yollarından bazıları aramak için bir dosya için kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

Bu makalede, Visual Basic zaten bildiğiniz varsayılmaktadır. Bu durumda, ilk olarak [Visual Studio 'da Visual Basic kullanmaya başlama](../../get-started/visual-basic/tutorial-console.md) gibi bir öğreticiye bakmanız önerilir.

> [!TIP]
> Bu makaleyle birlikte izlemek için, Visual Studio için Visual Basic ayarlarını seçtiğinizden emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında daha fazla bilgi için bkz. [ortam ayarlarını seçme](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluşturma

Yeni bir dosya oluşturarak ve bazı kodlar eklemeden başlatın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Geliştirme ortamını açmak için **ESC** tuşuna basın veya başlangıç penceresinde **kod olmadan devam et** ' e tıklayın.

::: moniker-end

2. Menü çubuğundaki **Dosya** menüsünde **yeni dosya**' yı seçin.

3. **Yeni dosya** iletişim kutusunda, **genel** kategori altında **Visual Basic sınıf**' ı seçin ve sonra **Aç**' ı seçin.

   Düzenleyicide Visual Basic sınıfının iskeçiyle yeni bir dosya açılır. (Sözdizimi vurgulama gibi kod düzenleyicisinin sunduğu avantajlardan bazılarını kazanmak için tam bir Visual Studio projesi oluşturmanız gerekmediğine zaten dikkat edebilirsiniz. Tüm ihtiyacınız olan bir kod dosyasıdır!)

   ![Visual Studio 'da kod dosyası Visual Basic](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio sağlar yararlı *kod parçacıkları* kod bloklarında kullanılan yaygın olarak hızla ve kolayca oluşturmak için kullanabilirsiniz. [Kod parçacıkları](../../ide/code-snippets.md) Visual Basic, C#ve C++gibi farklı programlama dilleri için kullanılabilir. Visual Basic **alt** kod parçacığını dosyanıza ekleyelim.

1. İmlecinizi, `End Class`belirten çizginin üzerine yerleştirin ve **Sub**yazın.

   `Sub` anahtar sözcüğü ve **alt** kod parçacığını ekleme hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir.

   ![Visual Studio'da kod parçacığı için IntelliSense](media/tutorial-intellisense-snippet.png)

1. Tuşuna **sekmesini** iki kez kod parçacığını eklemek için.

   `MySub()` Sub yordamının ana hattı dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dili için farklılık gösterir. Visual Basic için kullanılabilir kod parçacıklarına **bakabilirsiniz > ** **IntelliSense** > **kod parçacığı Ekle** ' yi seçerek (veya **CTRL**+**K**, **CTRL**+**X**tuşlarına basın). Visual Basic için, kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Kod parçacığı listesini Visual Basic](media/tutorial-code-snippet-list.png)

Bilgisayarda bir dosyanın var olup olmadığını belirlemek, bir metin dosyasına yazmak, bir kayıt defteri değeri okumak, SQL sorgusu yürütmek, her biri Için bir oluşturmak için kod parçacıkları vardır.. [. Sonraki bildiri](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)ve çok daha fazlası.

## <a name="comment-out-code"></a>Kodu açıklama

Visual Studio menü çubuğunda altında düğmelerden araç çubuğunda, kodu daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilir, bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak ayarlayabilirsiniz. ([IntelliSense](../../ide/using-intellisense.md) , farklı şeyler arasından eşleşen yöntemlerin bir listesini görüntüleyen bir kodlama yardımıdır.) Bu bölümde, bazı kodları açıklayacağız.

![Düzenleyici araç çubuğu düğmeleri](media/tutorial-editor-toolbar.png)

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

1. `morewords` dizisini kullanmıyoruz, ancak bunu daha sonra tamamen silmek istemediğimiz için kullanabiliriz. Bunun yerine, şimdi bu satırları açıklama satırı yapar. Kapanış küme ayracı `morewords` tüm tanımını seçin ve ardından araç çubuğunda **Seçili satırlar** düğmesini seçin. Klavyeyi kullanmak isterseniz, basın **Ctrl**+**K**, **Ctrl**+**C**.

   ![Açıklama düğmesi](media/tutorial-comment-out.png)

   Visual Basic açıklama karakteri `'`, kodu açıklama eklemek için seçili her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloğu Daralt

Yalnızca ilginizi çeken parçalara odaklanmak için kod bölümlerini daraltabilirsiniz. Pratikte `_words` dizisini tek bir kod satırına darallayalım. `Dim _words = New String() {`belirten satırın kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin. Ya da bir klavye kullanıcısı kullanıyorsanız, imleci dizi tanımında herhangi bir yere yerleştirin ve **ctrl**+**m**, **CTRL**+**m**tuşlarına basın.

![Anahat oluşturma Daralt düğmesi](media/tutorial-collapse.png)

Üç nokta ve ardından yalnızca ilk satırı, kod bloğu daraltır (`...`). Kod bloğunu tekrar artırmak için artık bir artı işareti veya tuşuna basın aynı gri kutusunda tıklayın **Ctrl**+**M**, **Ctrl**+**M**  yeniden. Bu özelliğin adı [anahat](../../ide/outlining.md) ve uzun yöntemleri veya tüm sınıflar daraltma özellikle yararlı olur.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüleme

Visual Studio Düzenleyicisi bir tür, yöntem vb. tanımlamayı incelemenizi kolaylaştırır. Tek bir yol, tanımı içeren dosyaya gitmeniz, örneğin simgenin başvurduğu her yerde **Tanıma Git** ' i seçerek. İçinde çalışmakta olduğunuz odağınızı uzağa dosya hareket etmediği bir bile daha hızlı yolu [Özet tanım](../../ide/go-to-and-peek-definition.md#peek-definition). Şimdi tanımda Özet `String` türü.

1. `String` sözcüğe sağ tıklayın ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Veya basın **Alt**+**F12**.

   Tanımını bir açılır pencere görünür `String` sınıfı. Açılır pencere veya hatta göz at peeked kodun başka bir tür tanımı içinde gezinebilirsiniz.

   ![Özet tanım penceresi](media/tutorial-peek-definition.png)

1. Açılır pencerenin sağ üst köşedeki "x" işareti olan küçük kutusunu seçerek baktı tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlamak için IntelliSense kullanma

[IntelliSense](../../ide/using-intellisense.md) , kodlamaya, her bir kaynaktır. Bu, kullanılabilir üyeler bir türü veya farklı bir yöntem aşırı yüklemeleri için parametre ayrıntıları hakkında bilgi gösterebilirsiniz. IntelliSense, bunu ayırt etmek için yeterli sayıda karakter girdikten sonra bir sözcük tamamlamak için de kullanabilirsiniz. Bir Git programının çıktısı için standart yerdir konsol penceresine sıralı dizeler yazdırmak için kod satırı ekleyelim.

1. Aşağıda `query` aşağıdaki kod yazarak değişken Başlat:

   ```vb
   For Each str In qu
   ```

   IntelliSense, Göster gördüğünüz **hızlı bilgi** hakkında `query` simgesi.

   ![Visual Studio IntelliSense Sözcük tamamlama](media/tutorial-intellisense-completion-list.png)

1. Word geri kalanını eklemek için `query` IntelliSense'nın sözcük tamamlama işlevlerini kullanarak basın **sekmesini**.

1. Şu kod gibi aramak için kod bloğunu kapatmak tamamlayın.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleyin

Hiç kimse ilk kez kod sağ alır ve bir değişkeni veya yöntemin adını değiştirmeniz gerekebilir şeyleri biridir. Visual Studio'nun deneyelim [yeniden düzenleme](../../ide/refactoring-in-visual-studio.md) yeniden adlandırmak için işlevselliği `_words` değişkenini `words`.

1. İmlecinizi `_words` değişkeninin tanımına yerleştirin ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin.

   Bir açılır pencere **Yeniden Adlandır** iletişim kutusunun en üstünde görünür sağında Düzenleyici.

1. Değişken `_words` hala seçiliyse, istenen **sözcüklerin**adını yazın. Dikkat başvuru `words` sorguda da otomatik olarak yeniden adlandırıldı. **ENTER** tuşuna bastıktan veya **Uygula**' ya tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](media/tutorial-rename.png)

1. **ENTER** tuşuna basın veya **Uygula**' ya tıklayın.

   `words` tekrarlarının her ikisi de yeniden adlandırılır ve kod açıklamasında `words` başvurusudur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../../ide/code-snippets.md)
- [Kod gidin](../../ide/navigating-code.md)
- [Anahat Oluşturma](../../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
