---
title: JavaScript geliştiricileri için düzenlemeye giriş
description: Visual Studio'da kod düzenleyicisine giriş Visual Studio JavaScript kodunu yazmayı, gezinmeyi ve anlamayı kolaylaştıran yöntemlerden bazıları gösterir.
ms.date: 03/25/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f84c9483da176a67d4636dd22a6cadee062e826eb82f06d561b6384aa17ad794
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231905"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>JavaScript için kod düzenleyicisini kullanmayı öğrenin

Visual Studio'de kod düzenleyicisine bu kısa girişte, Visual Studio yazma, gezinme ve kodu anlamayı kolaylaştıran yöntemlere göz ateceğiz.

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin. Uygulama geliştirmenin türüne bağlı olarak, uygulama geliştirme iş yükünüNode.js **yüklemeniz** Visual Studio. TypeScript dil hizmetini alma hakkında daha fazla bilgi için bkz. [TypeScript desteği.](../javascript/javascript-in-vs-2019.md#typescript-support)

Bu makalede JavaScript geliştirmeyle ilgili bilgi sahibi olduğunuz varsaylanmıştır. Yoksa, önce Create a Node.js ve Express app gibi [bir öğreticiye bakmanızı](../javascript/tutorial-nodejs.md) öneririz.

## <a name="add-a-new-project-file"></a>Yeni proje dosyası ekleme

Projenize yeni dosyalar eklemek için IDE'yi kullanabilirsiniz.

1. Projeniz Visual Studio açıkken, Çözüm Gezgini (sağ bölme) içinde bir klasöre veya proje düğüme sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

1. Yeni **Dosya iletişim** kutusunda,  Genel kategorisi altında, eklemek istediğiniz dosya türünü **(JavaScript** Dosyası gibi) seçin ve ardından Aç'ı **seçin.**

    Yeni dosya projenize eklenir ve düzenleyicide açılır.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense kullanarak sözcükleri tamamlama

IntelliSense, kod yazmanız durumunda çok değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntılarını gösterebilir. Aşağıdaki kodda, `Router()` yazarak, geçebilirsiniz bağımsız değişken türlerini görüyorsunuz. Bu, imza yardımı olarak adlandırılan bir durum.

![JavaScript kodunun Visual Studio kod penceresinin ekran görüntüsü. Router() işlevi için IntelliSense bilgileri gösterilir.](../javascript/media/write-code-signature-checking.png)

Ayrıca IntelliSense'i kullanarak bir sözcüğün tam olarak ne olduğunu tam olarak anlayan yeterli karakter kullanabilirsiniz. İmlecinizi aşağıdaki kodda dizenin altına yerleştirdikten sonra yazın. `data` IntelliSense, kodda daha önce tanımlanmış veya projenize ekley istediğiniz üçüncü taraf kitaplığında tanımlanmış işlevleri `get` gösterir.

!['get' Visual Studio kod penceresinin ekran görüntüsü. 'Get' ile başlayan tüm işlevler için IntelliSense bilgileri gösterilir.](../javascript/media/write-code-intellisense.png)

IntelliSense, programlama öğelerinin üzerine gelindiğinde türler hakkında bilgi de gösterebilir.

IntelliSense bilgilerini sağlamak için dil hizmeti TypeScript *d.ts* dosyalarını ve JSDoc açıklamalarını kullanabilir. En yaygın JavaScript kitaplıkları için *d.ts* dosyaları otomatik olarak alınacaktır. IntelliSense bilgilerini edinme hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json). Visual Studio'de AngularJS programlamayla ilgileniyorsanız, IntelliSense'i almak için [angularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) dil Visual Studio uzantısını kullanabilirsiniz.

## <a name="check-syntax"></a>Söz dizimlerini denetleme

Dil hizmeti söz dizimi denetimi ve lint sağlamak için ESLint kullanır. Düzenleyicide söz dizimi denetimi için seçenekleri ayarlamanız gerekirse Araçlar Seçenekler  >    >  **JavaScript/TypeScript**  >  **Linting seçeneğini belirleyin.** Lint seçenekleri sizi genel ESLint yapılandırma dosyasına işaret ediyor.

Aşağıdaki kodda, ifadede yeşil söz dizimi vurgulaması (yeşil geçişler) görüyorsunuz. Söz dizimi vurgulamanın üzerine gelin.

![Söz dizimi hatasını görüntüleme](../javascript/media/write-code-syntax-checking.png)

Bu iletinin son satırı, dil hizmetinin virgül () beklendiğini size `,` söyler. Yeşil iki durumlu düğme bir uyarı gösterir. Kırmızı geçişler bir hata olduğunu gösterir.

Alt bölmede, uyarıyı ve **açıklamayı** dosya adı ve satır numarasıyla birlikte görmek için Hata Listesi sekmesine tıklarsınız.

![Hata listesini görüntüleme](../javascript/media/write-code-error-list.png)

önce virgül ( ) ekleyerek bu kodu `,` `"data"` düzeltebilirsiniz.

Lint hakkında daha fazla bilgi için bkz. [Linting](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Kodu açıklamaya alma

Araç çubuğundaki menü çubuğunun altındaki düğmelerin satırı olan araç Visual Studio kodlarken daha üretken çalışmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu[(IntelliSense,](../ide/using-intellisense.md) eşleşen yöntemlerin listesini görüntüleyen bir kodlama yardımıdır), satır girintisini artırabilir veya azaltabilir veya derlemek istemeyebilirsiniz kodu açıklama satırı olarak ekleyebilirsiniz. Bu bölümde bazı kodlara açıklama olarak yer veserden bakabilirsiniz.

Düzenleyicide bir veya daha fazla kod satırı  seçin ve ardından araç çubuğundaki Seçili satırları açıklama satırı yap ![ düğmesini Açıklama satırı düğmesi ](../javascript/media/write-code-comment-out.png) seçin. Klavyeyi kullanmayı tercih ederseniz Ctrl K , **Ctrl** + C  + **tuşlarına basın.**

Kodu açıklama satırı yapmak için seçilen her satırın başına JavaScript `//` açıklama karakterleri eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını daralt

Bazı kod bölgelerine bakış açınızı daraltırsanız daraltabilirsiniz. İşlevin ilk satırı kenar boşluğunda eksi işareti bulunan küçük gri kutuyu seçin. Veya klavye kullanıcısıysanız imleci oluşturucu kodunun herhangi bir yerine yerleştirerek Ctrl M , **Ctrl** + **M** **tuşlarına** + **basın.**

![Daralt düğmesinin altı çizili](../javascript/media/write-code-collapse-code.png)

Kod bloğu yalnızca ilk satıra daraltır ve ardından üç nokta ( ) `...` alır. Kod bloğuna yeniden genişletmek için, artık artı işareti olan gri kutuya tıklayın veya **Ctrl** + **M**, **Ctrl** + **M tuşlarına tekrar** basın. Bu özellik, [Outlining olarak](../ide/outlining.md) adlandırılan ve özellikle uzun işlevleri veya sınıfların tamamını daraltıyorken yararlıdır.

## <a name="view-definitions"></a>Tanımları görüntüleme

Visual Studio düzenleyicisi, bir türün, işlevin vb. tanımını incelemeyi kolaylaştırır. Bunun bir yolu, örneğin programlama öğesine başvurulan her yerde Tanıma **Git'i** seçerek tanımı içeren dosyaya gitmektir. Odağınızı üzerinde çalışmakta olduğunu dosyadan başka bir yere taşımanın daha da hızlı bir yolu, Peek [Definition kullanmakdır.](../ide/go-to-and-peek-definition.md#peek-definition) Aşağıdaki örnekte yönteminin `render` tanımına göz atalım.

Sağ tıklayın ve `render` içerik **menüsünden Tanıma Göz** At'ı seçin. Alternatif **olarak, Alt** + **F12 tuşuna basın.**

   yönteminin tanımıyla birlikte bir açılır pencere `render` görüntülenir. Açılan pencerede kaydırabilir, hatta göz atmış koddan başka bir türün tanımına göz atabilirsiniz.

   ![Tanıma göz atma penceresi](../javascript/media/write-code-peek-definition.png)

Açılan pencerenin sağ üst kısmında "x" olan küçük kutuyu seçerek göz atarak tanım penceresini kapatın.

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın *olarak kullanılan kod* bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı kod parçacıkları sağlar. [Kod parçacıkları](../ide/code-snippets.md) JavaScript dahil olmak üzere farklı programlama dilleri için kullanılabilir. Şimdi kod `for` dosyanıza bir döngü ekleriz.

İmlecinizi kod parçacığını eklemek istediğiniz yere yerleştirerek sağ tıklayın ve Kod Parçacığı Ekleme **Kod Parçacığı**  >  **'yı seçin.**

![Visual Studio'de kod parçacığı](../javascript/media/write-code-insert-snippet.png)

Düzenleyicide **bir** Kod Parçacığı Ekle kutusu görüntülenir. **Genel'i** seçin ve ardından listede **öğe** için çift tıklayın.

![Visual Studio'de for döngüsü için kod Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Bu, döngü `for` parçacığını kodunuza ekler:

```javascript
for (var i = 0; i < length; i++) {

}
```

  >  **IntelliSense** Insert  >  **Snippet'ı** Düzenle'yi ve ardından dilinizin klasörünü seçerek dilinize uygun kod parçacıklarına bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [Kodda gezinme](../ide/navigating-code.md)
- [Anahat Oluşturma](../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
