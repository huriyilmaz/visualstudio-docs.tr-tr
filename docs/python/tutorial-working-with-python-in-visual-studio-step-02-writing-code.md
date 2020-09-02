---
title: Visual Studio 'da Python öğreticisi 2. adım, kodu yazma ve çalıştırma
titleSuffix: ''
description: Visual Studio 'da kod ekleme ve proje çalıştırma dahil olmak üzere Python özelliklerine yönelik temel bir izlenecek adım 2.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fda68b9e5bffbd1afab3389a0d8d624312a8de3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430070"
---
# <a name="step-2-write-and-run-code"></a>2. Adım: kodu yazma ve çalıştırma

**Önceki adım: [Yeni bir Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Proje dosyalarını yönettiğiniz **Çözüm Gezgini** , genellikle, kaynak kodu gibi dosyaların *içeriğiyle* çalıştığınız yerde *Düzenleyici* pencere olur. Düzenleyici, programlama dili de dahil olmak üzere düzenlemekte olduğunuz dosya türünün bağlamsal olarak farkındadır ve IntelliSense kullanarak söz dizimi renklendirme ve otomatik tamamlama gibi özellikler sunar.

1. Yeni bir "Python uygulaması" projesi oluşturduktan sonra, Visual Studio düzenleyicisinde *PythonApplication1.py* adlı varsayılan bir boş dosya açıktır.

1. Düzenleyicide yazmaya başlayın `print("Hello, Visual Studio")` ve Visual Studio IntelliSense 'in bu şekilde otomatik tamamlama seçeneklerini nasıl görüntülediğini fark edin. Açılan listede, **sekme** tuşuna bastığınızda kullanılan varsayılan tamamlama, açılan listedeki ana hatlarıyla gösterilmiştir. Daha uzun deyimler veya tanımlayıcılar dahil edildiğinde tamamlamalar en çok yararlı olur.

    ![IntelliSense otomatik tamamlama açılan penceresi](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense, kullanmakta olduğunuz ifadeye, aradığınız işleve ve benzeri olarak farklı bilgiler gösterir. İşlevi ile `print` , `(` `print` bir işlev çağrısını belirten yazdıktan sonra bu işlev için tam kullanım bilgilerini görüntüler. IntelliSense açılır penceresi ayrıca kalın yazı (burada gösterilen**değer** ) ile geçerli bağımsız değişkeni gösterir:

    ![Bir işlev için IntelliSense otomatik tamamlama açılan penceresi](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Şu şekilde eşleşen ifadeyi doldurun:

    ```python
    print("Hello, Visual Studio")
    ```

1. Bağımsız değişkenden bildirimi ayıran söz dizimi renkine dikkat edin `print` `"Hello Visual Studio"` . Ayrıca, en son dizeyi geçici olarak silin `"` ve Visual Studio 'nun sözdizimi hataları içeren kod için kırmızı alt çizgiyi nasıl gösterdiğini görürsünüz. Sonra `"` kodu düzeltmek için öğesini değiştirin.

    ![IntelliSense sözdizimi renklendirme ve hata vurgulama](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Tek bir geliştirme ortamı çok kişisel olduğundan Visual Studio, Visual Studio 'nun görünümü ve davranışı üzerinde tamamen denetim sağlar. **Araçlar**  >  **Seçenekler** menü komutunu seçin ve **ortam** ve **metin Düzenleyicisi** sekmeleri altındaki ayarları araştırın. Varsayılan olarak yalnızca sınırlı sayıda seçenek görürsünüz. Her programlama diline yönelik her bir seçeneği görmek için iletişim kutusunun altındaki **tüm ayarları göster** ' i seçin.

1. **CTRL** + **F5** tuşuna basarak veya hata ayıklama menüsü öğesi olmadan **Hata Ayıkla**  >  **Başlat** ' ı seçerek bu noktaya yazdığınız kodu çalıştırın. Kodunuzda hatalar varsa, Visual Studio sizi uyarır.

1. Programı çalıştırdığınızda, komut satırından *PythonApplication1.py* Ile bir Python yorumlayıcı çalıştırdığınız gibi, sonuçları görüntüleyen bir konsol penceresi görüntülenir. Pencereyi kapatmak ve Visual Studio düzenleyicisine dönmek için bir tuşa basın.

    ![Programın ilk çalışması için çıkış](media/vs-getting-started-python-07-output.png)

1. Deyim ve işlevlerin tamamlarına ek olarak IntelliSense, Python ve deyimler için tamamlama `import` sağlar `from` . Bu tamamlamalar, ortamınızda hangi modüllerin kullanılabildiğini ve bu modüllerin üyelerini kolayca keşfetmenize yardımcı olur. Düzenleyicide `print` satırı silin ve yazmaya başlayın `import` . Bir modül listesi, alanı yazdığınızda görüntülenir:

    ![İçeri aktarma bildiriminde kullanılabilen modülleri gösteren ıntellsense](media/vs-getting-started-python-08-import1.png)

1. Yazarak veya seçerek satırı doldurun `sys` .

1. Bir sonraki satırda, `from` bir modül listesi görmek için yazın:

    ![From deyimindeki kullanılabilir modülleri gösteren ıntellsense](media/vs-getting-started-python-09-import2.png)

1. ' İ seçin veya yazın `math` , sonra da `import` Modül üyelerini görüntüleyen bir boşluk ile yazmaya devam edin:

    ![Modül üyelerini gösteren ıntellsense](media/vs-getting-started-python-10-import3.png)

1. `sin`, `cos` , Ve üyelerini içeri aktararak, `radians` her biri için kullanılabilir otomatik tamamlamayı yaşıyorsanız. İşiniz bittiğinde, kodunuzun aşağıdaki gibi görünmesi gerekir:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Siz yazarken alt dizelerdeki çalışmayı, sözcüklerin parçalarını eşleştirmeyi, sözcüklerin başındaki harfleri ve hatta Atlanan karakterleri tamamlama. Ayrıntılar için bkz. [kodu düzenleme-tamamlama](editing-python-code-in-visual-studio.md#completions) .

1. 360 derecenin kosinüs değerlerini yazdırmak için biraz daha fazla kod ekleyin:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Programı, **Ctrl** + **F5** **Debug**  >  **hata ayıklama olmadan**CTRL F5 veya Debug Start ile yeniden çalıştırın. Bitirdiğinizde çıkış penceresini kapatın.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Daha derin git

- [Kodu Düzenle](editing-python-code-in-visual-studio.md)
- [Kodu biçimlendirme](formatting-python-code.md)
- [Kodu yeniden düzenleme](refactoring-python-code.md)
- [PyLint kullanma](linting-python-code.md)
