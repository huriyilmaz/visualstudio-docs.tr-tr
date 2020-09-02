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
ms.openlocfilehash: c46120c369fa130e83620549ca0bc084a5075f7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235153"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Kod düzenleyicisini Visual Basic ile kullanmayı öğrenin

Visual Studio 'daki kod düzenleyicisine bu 10 dakikalık bir giriş için, Visual Studio 'Nun Visual Basic kodu daha kolay yazma, gezinme ve anlama yöntemlerinin bazılarına bakmak üzere bir dosyaya kod ekleyeceğiz.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bu makalede, Visual Basic zaten bildiğiniz varsayılmaktadır. Bu durumda, ilk olarak [Visual Studio 'da Visual Basic kullanmaya başlama](../../get-started/visual-basic/tutorial-console.md) gibi bir öğreticiye bakmanız önerilir.

> [!TIP]
> Bu makaleyle birlikte izlemek için, Visual Studio için Visual Basic ayarlarını seçtiğinizden emin olun. Tümleşik geliştirme ortamı (IDE) için ayarları seçme hakkında daha fazla bilgi için bkz. [ortam ayarlarını seçme](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Yeni bir kod dosyası oluştur

Yeni bir dosya oluşturarak ve buna kod ekleyerek başlayın.

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

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../../ide/code-snippets.md) Visual Basic, C# ve C++ gibi farklı programlama dilleri için kullanılabilir. Visual Basic **alt** kod parçacığını dosyanıza ekleyelim.

1. İmlecinizi, belirten çizginin üzerine getirin `End Class` ve **Sub**yazın.

   `Sub`Anahtar sözcüğü ve **alt** kod parçacığını ekleme hakkında bilgi içeren bir açılır iletişim kutusu görüntülenir.

   ![Visual Studio 'da kod parçacığı için IntelliSense](media/tutorial-intellisense-snippet.png)

1. Kod parçacığını eklemek için **sekme** tuşuna iki kez basın.

   Alt yordamın ana hattı `MySub()` dosyaya eklenir.

Kullanılabilir kod parçacıkları farklı programlama dilleri için farklılık gösterir. IntelliSense ekleme kod parçacığını **Düzenle**' yi seçerek Visual Basic için kullanılabilir kod parçacıklarına bakabilirsiniz  >  **IntelliSense**  >  **Insert Snippet** (veya **CTRL** + **K**, **CTRL** + **X**tuşlarına basın). Visual Basic için, kod parçacıkları aşağıdaki kategoriler için kullanılabilir:

![Kod parçacığı listesini Visual Basic](media/tutorial-code-snippet-list.png)

Bilgisayarda bir dosyanın var olup olmadığını belirlemek, bir metin dosyasına yazmak, bir kayıt defteri değeri okumak, SQL sorgusu yürütmek, her biri Için bir oluşturmak için kod parçacıkları vardır.. [. Sonraki bildiri](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)ve çok daha fazlası.

## <a name="comment-out-code"></a>Kodu dışarı açıklama

Visual Studio 'daki menü çubuğu altındaki düğmelerin satırı olan araç çubuğu, kod olarak daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilir, bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak ayarlayabilirsiniz. ([IntelliSense](../../ide/using-intellisense.md) , farklı şeyler arasından eşleşen yöntemlerin bir listesini görüntüleyen bir kodlama yardımıdır.) Bu bölümde, bazı kodları açıklayacağız.

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

1. Diziyi kullanmıyoruz `morewords` , ancak bunu daha sonra tamamen silmek istemdiğimiz için kullanabiliriz. Bunun yerine, bu satırları açıklamaya bakalım. `morewords`Kapanış küme ayracı için tüm tanımı seçin ve ardından araç çubuğundaki **Seçili çizgiler** düğmesini seçin. Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C**tuşlarına basın.

   ![Açıklama dışarı düğmesi](media/tutorial-comment-out.png)

   Visual Basic açıklama karakteri, `'` kodu açıklama eklemek için seçili her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını Daralt

Yalnızca ilginizi çeken parçalara odaklanmak için kod bölümlerini daraltabilirsiniz. Pratikte, `_words` diziyi tek bir kod satırına darallayalım. Görüntülenen satırın kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin `Dim _words = New String() {` . Ya da bir klavye kullanıcısı kullanıyorsanız, imleci dizi tanımında herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m**tuşlarına basın.

![Anahat Daralt düğmesi](media/tutorial-collapse.png)

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi bir artı işaretine sahip olan gri kutuya tıklayın veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../../ide/outlining.md) olarak adlandırılır ve özellikle uzun yöntemleri veya tüm sınıfları daraltdığınızda yararlıdır.

## <a name="view-symbol-definitions"></a>Sembol tanımlarını görüntüle

Visual Studio Düzenleyicisi bir tür, yöntem vb. tanımlamayı incelemenizi kolaylaştırır. Tek bir yol, tanımı içeren dosyaya gitmeniz, örneğin simgenin başvurduğu her yerde **Tanıma Git** ' i seçerek. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. Türün tanımına göz atalım `String` .

1. Sözcüğe sağ tıklayın `String` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif olarak, **alt** + **F12**tuşuna basın.

   Sınıfının tanımına sahip bir açılır pencere görüntülenir `String` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   ![Tanım penceresi Özeti](media/tutorial-peek-definition.png)

1. Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek atılamıyor tanım penceresini kapatın.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlaması için IntelliSense kullanma

Kodlamadan [IntelliSense](../../ide/using-intellisense.md) , değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. Düzenli dizeleri konsol penceresine yazdırmak için bir kod satırı ekleyelim, bu da programdan git 'in çıkış için standart yer.

1. Değişkenin altında `query` aşağıdaki kodu yazmaya başlayın:

   ```vb
   For Each str In qu
   ```

   IntelliSense, sembol hakkında **hızlı bilgi** gösterir `query` .

   ![Visual Studio 'da IntelliSense kelime tamamlama](media/tutorial-intellisense-completion-list.png)

1. `query`IntelliSense 'in kelime tamamlama işlevini kullanarak sözcüğün geri kalanını eklemek Için **Tab**tuşuna basın.

1. Aşağıdaki kod gibi görmek için kod bloğunu sona erdirin.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Bir adı yeniden düzenleme

Hiç kimse ilk kez kod alır ve değiştirmeniz gerekebilecek işlemlerden biri bir değişkenin veya yöntemin adıdır. Değişkeni olarak yeniden adlandırmak için Visual Studio 'nun yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) işlevini deneyelim `_words` `words` .

1. İmlecinizi değişkeninin tanımına yerleştirin `_words` ve sağ tıklama ya da bağlam menüsünden **Yeniden Adlandır** ' ı seçin.

   Düzenleyicinin sağ üst köşesinde bir açılır pencere **yeniden adlandırma** iletişim kutusu görüntülenir.

1. Değişken seçili durumdayken `_words` , istenen **sözcüklerin**adını yazın. `words`Sorgudaki başvurunun da otomatik olarak yeniden adlandırıldığına dikkat edin. **ENTER** tuşuna bastıktan veya **Uygula**' ya tıklamadan önce, **Yeniden Adlandır** açılan kutusunda **açıklamaları dahil et** onay kutusunu seçin.

   ![Yeniden Adlandır iletişim kutusu](media/tutorial-rename.png)

1. **ENTER** tuşuna basın veya **Uygula**' ya tıklayın.

   Her iki tekrarın her ikisi de `words` yeniden adlandırılır ve `words` kod açıklamasında başvurusu.

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
