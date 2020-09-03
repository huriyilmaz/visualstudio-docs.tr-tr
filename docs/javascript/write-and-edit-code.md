---
title: JavaScript geliştiricileri için düzenlemelere giriş
description: Visual Studio 'da kod düzenleyicisine giriş, Visual Studio 'Nun JavaScript kodunu yazma, gezinme ve anlamayı kolaylaştıran bazı yolları gösterir.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a033c0fe1fd80edc7959c5f49993714982ecc805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238186"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>JavaScript için kod düzenleyicisini kullanmayı öğrenin

Visual Studio 'daki kod düzenleyicisine bu kısa giriş bölümünde, Visual Studio 'Nun kodu yazma, gezinme ve daha kolay hale getirmeye yönelik bazı yöntemlere bakacağız.

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleme yapın. Yaptığınız uygulama geliştirme türüne bağlı olarak, Visual Studio ile **Node.js geliştirme iş yükünü** yüklemeniz gerekebilir. TypeScript için dil hizmetini alma hakkında daha fazla bilgi için bkz. [TypeScript desteği](../javascript/javascript-in-vs-2019.md#typescript-support).

Bu makalede, JavaScript geliştirme konusunda zaten bilgi sahibi olduğunuz varsayılır. Değilseniz, önce [Node.js ve hızlı uygulama oluşturma](../javascript/tutorial-nodejs.md) gibi bir öğreticiye bakmanız önerilir.

## <a name="add-a-new-project-file"></a>Yeni bir proje dosyası Ekle

Projenize yeni dosyalar eklemek için IDE 'yi kullanabilirsiniz.

1. Projeniz Visual Studio 'da açıkken, Çözüm Gezgini (sağ bölme) ' de bir klasöre veya proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **Yeni dosya** iletişim kutusunda, **genel** kategori altında, eklemek istediğiniz dosya türünü seçin ( **JavaScript dosyası**gibi) ve sonra **Aç**' ı seçin.

    Yeni dosya projenize eklenir ve düzenleyicide açılır.

## <a name="use-intellisense-to-complete-words"></a>Sözcükleri tamamlaması için IntelliSense kullanma

Kodlamadan IntelliSense, değerli bir kaynaktır. Bir türün kullanılabilir üyeleri hakkında bilgi veya bir yöntemin farklı aşırı yüklemeleri için parametre ayrıntıları gösterebilir. Aşağıdaki kodda, yazdığınızda `Router()` , geçirebilmeniz için bağımsız değişken türlerini görürsünüz. Bu, imza yardımı olarak adlandırılır.

![IntelliSense kullanma](../javascript/media/write-code-signature-checking.png)

IntelliSense 'i, ayırt etmek için yeterince karakter yazdıktan sonra bir sözcüğü yazarak tamamlamayı de kullanabilirsiniz. `data`Aşağıdaki kod ve türden dizeden sonra imlecinizi yerleştirirseniz `get` , IntelliSense kodda daha önce tanımlanan veya projenize eklediğiniz bir üçüncü taraf kitaplığında tanımlanan işlevleri gösterir.

![IntelliSense kullanma](../javascript/media/write-code-intellisense.png)

IntelliSense, programlama öğelerinin üzerine geldiğinizde, türler hakkındaki bilgileri de gösterebilir.

IntelliSense bilgilerini sağlamak için dil hizmeti TypeScript *d. TS* dosyalarını ve JSDoc açıklamalarını kullanabilir. En yaygın JavaScript kitaplıkları için *d. TS* dosyaları otomatik olarak alınır. IntelliSense bilgilerinin nasıl alındığı hakkında daha fazla ayrıntı için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Sözdizimini denetle

Dil hizmeti, sözdizimi denetimi ve kullanımı sağlamak için ESLint kullanır. Düzenleyicide sözdizimi denetimi için seçenekler ayarlamanız gerekiyorsa, **Araçlar**  >  **Seçenekler**  >  **JavaScript/TypeScript**  >  **Linting**' i seçin. Bu seçenekler, genel Eslınt yapılandırma dosyasına sizi işaret edersiniz.

Aşağıdaki kodda, ifadede yeşil sözdizimi vurgulaması (yeşil dalgalı çizgiler) görürsünüz. Söz dizimi vurgulamanın üzerine gelin.

![Sözdizimi görüntüleme hatası](../javascript/media/write-code-syntax-checking.png)

Bu iletinin son satırı, dil hizmetinin bir virgül () beklediğine bildirir `,` . Yeşil dalgalı çizgi bir uyarı gösterir. Red dalgalı çizgiler bir hata gösterir.

Alt bölmede, dosya adı ve satır numarası ile birlikte uyarı ve açıklama ' yı görmek için **hata listesi** sekmesine tıklayabilirsiniz.

![Hata listesini görüntüle](../javascript/media/write-code-error-list.png)

Daha önce virgül () ekleyerek bu kodu giderebilirsiniz `,` `"data"` .

Daha fazla bilgi için [bkz. nasıl](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md)yapılır.

## <a name="comment-out-code"></a>Kodu dışarı açıklama

Visual Studio 'daki menü çubuğu altındaki düğmelerin satırı olan araç çubuğu, kod olarak daha üretken olmanıza yardımcı olabilir. Örneğin, IntelliSense tamamlama modunu değiştirebilirsiniz ([IntelliSense](../ide/using-intellisense.md) , eşleşen yöntemlerin bir listesini, diğer şeyleri arasından görüntüleyen bir kodlama yardımıdır), bir satır girintisini artırabilir veya azaltabilir ya da derlemek istemediğiniz kodu açıklama olarak değiştirir. Bu bölümde, bazı kodları açıklayacağız.

Düzenleyicide bir veya daha fazla kod satırı seçin ve ardından araç çubuğundaki **Seçili satırlar** düğmesine Açıklama ![ çıkar düğmesini seçin ](../javascript/media/write-code-comment-out.png) . Klavyeyi kullanmayı tercih ediyorsanız **CTRL** + **K**, **CTRL** + **C**tuşlarına basın.

JavaScript Açıklama karakterleri, `//` kodu açıklama eklemek için seçili her satırın başına eklenir.

## <a name="collapse-code-blocks"></a>Kod bloklarını Daralt

Bazı kod bölgelerinde görünümün kalabalıklığını ortadan kaldırmak istiyorsanız, daraltabilirsiniz. Bir işlevin ilk satırının kenar boşluğunda eksi işareti olan küçük gri kutusunu seçin. Ya da bir klavye kullanıcısı kullanıyorsanız, imleci Oluşturucu kodunda herhangi bir yere yerleştirin ve **CTRL** + **m**, **CTRL** + **m**tuşlarına basın.

![Anahat Daralt düğmesi](../javascript/media/write-code-collapse-code.png)

Kod bloğu yalnızca ilk satırı ve ardından üç nokta () ile daraltır `...` . Kod bloğunu yeniden genişletmek için, şimdi bir artı işaretine sahip olan gri kutuya tıklayın veya **CTRL** + **e**, **CTRL** + **e** tuşlarına basın. Bu özellik, ana [hat](../ide/outlining.md) olarak adlandırılır ve özellikle uzun işlevleri veya bütün sınıfları daraltdığınızda yararlıdır.

## <a name="view-definitions"></a>Tanımları görüntüle

Visual Studio Düzenleyicisi bir tür, işlev, vb. tanımlamayı incelemenizi kolaylaştırır. Bir yol, tanımı içeren dosyaya gitmenin yanı, örneğin, programlama öğesinin başvurduğu her yerde **Tanıma Git** ' i seçerek. Odağı, üzerinde çalıştığınız dosyadan uzağa taşımayın, [göz atma tanımını](../ide/go-to-and-peek-definition.md#peek-definition)kullanmaktır. `render`Aşağıdaki örnekteki yöntemin tanımına göz atalım.

Öğesine sağ tıklayın `render` ve içerik menüsünden **Açıklama Özeti** ' ni seçin. Alternatif olarak, **alt** + **F12**tuşuna basın.

   Yöntemin tanımına sahip bir açılır pencere görüntülenir `render` . Açılır pencere içinde kaydırma yapabilir veya atılamıyor kodundan başka bir türün tanımına de göz atın.

   ![Tanım penceresi Özeti](../javascript/media/write-code-peek-definition.png)

Açılır pencerenin sağ üst köşesinde bulunan bir "x" ile küçük kutuyu seçerek atılamıyor tanım penceresini kapatın.

## <a name="use-code-snippets"></a>Kod parçacıkları kullanma

Visual Studio, yaygın olarak kullanılan kod bloklarını hızlı ve kolay bir şekilde oluşturmak için kullanabileceğiniz yararlı *kod parçacıkları* sağlar. [Kod parçacıkları](../ide/code-snippets.md) JavaScript dahil farklı programlama dilleri için kullanılabilir. `for`Kod dosyanıza bir döngü ekleyelim.

Parçacığınızı eklemek istediğiniz yere yerleştirin, sağ tıklayın ve **kod**parçacığı  >  **ekleme kod parçacığı**' nu seçin.

![Visual Studio 'da kod parçacığı](../javascript/media/write-code-insert-snippet.png)

Düzenleyicide bir **kod parçacığı Ekle** kutusu görünür. **Genel** ' i seçin ve ardından **listedeki öğeye çift** tıklayın.

![Visual Studio 'da for döngüsü için kod parçacığı](../javascript/media/write-code-insert-snippet-for-loop.png)

Bu, `for` döngü kod parçacığını kodunuza ekler:

```javascript
for (var i = 0; i < length; i++) {

}
```

**Edit**  >  **IntelliSense**  >  **ekleme kod parçacığını**Düzenle ' yi ve ardından Dilinizin klasörünü seçerek diliniz için kullanılabilir kod parçacıkları bölümüne bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [Koda git](../ide/navigating-code.md)
- [Anahat Oluşturma](../ide/outlining.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Yeniden Düzenle](../ide/refactoring-in-visual-studio.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
