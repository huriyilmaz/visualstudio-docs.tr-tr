---
title: Python Visual Studio öğretici adım 2, kod yazmak ve çalıştırmak
titleSuffix: ''
description: Visual Studio'da kod düzenleme ve proje çalıştırma dahil olmak üzere Python yeteneklerinin temel bir walkthrough'unun 2.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430070"
---
# <a name="step-2-write-and-run-code"></a>Adım 2: Kod yazma ve çalıştırma

**Önceki adım: [Yeni bir Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

**Çözüm Gezgini** proje dosyalarını yönettiğiniz yer olsa da, *düzenleyici* penceresi genellikle kaynak kodu gibi dosyaların *içeriğiyle* çalıştığınız yerdir. Düzenleyici, programlama dili (dosya uzantısına dayalı olarak) dahil olmak üzere düzenlediğiniz dosya nın türünü bağlamsal olarak farkındadır ve IntelliSense kullanarak sözdizimi boyama ve otomatik tamamlama gibi bu dile uygun özellikler sunar.

1. Yeni bir "Python Uygulaması" projesi oluşturduktan sonra Visual Studio düzenleyicisinde *PythonApplication1.py* adlı varsayılan boş bir dosya açılır.

1. Editörde yazmaya başlayın `print("Hello, Visual Studio")` ve Visual Studio IntelliSense'in yol boyunca otomatik tamamlama seçeneklerini nasıl görüntülenebildiğini fark edin. Açılan listede özetlenen seçenek, **Sekme** tuşuna bastığınızda kullanılan varsayılan tamamlamadır. Daha uzun ifadeler veya tanımlayıcılar söz konusu olduğunda tamamlamalar en yararlı dır.

    ![IntelliSense otomatik tamamlama açılır](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense, kullandığınız ifadeye, aradığınız işleve ve benzeri bilgilere bağlı olarak farklı bilgiler gösterir. İşlev ile, `(` `print` bir işlev çağrısı nı belirtmek için sonra yazarak bu işlev için tam kullanım bilgilerini görüntüler. `print` IntelliSense açılır da boldface geçerli argüman gösterir (burada gösterildiği gibi**değer):**

    ![Bir fonksiyon için IntelliSense otomatik tamamlama açılır](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Aşağıdakiyle eşleşin diye ifadeyi tamamlayın:

    ```python
    print("Hello, Visual Studio")
    ```

1. İfadeyi `print` bağımsız değişkenden `"Hello Visual Studio"`ayıran sözdizimi renklendirmesine dikkat edin. Ayrıca, dizedeki `"` sonuncuyu geçici olarak silin ve Visual Studio'nun sözdizimi hataları içeren kod için nasıl kırmızı bir alt çizgi çizdiğini fark edin. Ardından kodu `"` düzeltmek için değiştirin.

    ![IntelliSense sözdizimi boyama ve hata vurgulama](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Kişinin geliştirme ortamı çok kişisel bir konu olduğundan, Visual Studio Visual Studio görünüm ve davranış üzerinde tam kontrol sağlar. **Araçlar** > **Seçenekleri** menüsü komutunu seçin ve **Çevre** ve **Metin Düzenleyicisi** sekmelerinin altındaki ayarları keşfedin. Varsayılan olarak yalnızca sınırlı sayıda seçenek görürsünüz; her programlama dili için her seçeneği görmek için iletişim kutusunun altındaki **tüm ayarları göster'i** seçin.

1. **Ctrl**+**F5** tuşuna basarak veya hata ayıklama menüsü **öğesini** > hata ayıklama dan seçerek bu noktaya yazdığınız kodu**çalıştırın.** Visual Studio, kodunuzda hala hatalar varsa sizi uyarır.

1. Programı çalıştırdığınızda, komut satırından *PythonApplication1.py* olan bir Python yorumlayıcısı çalıştırıyormuşsunuz gibi sonuçları gösteren bir konsol penceresi görüntülenir. Pencereyi kapatmak ve Visual Studio editörüne dönmek için bir tuşa basın.

    ![Programın ilk çalışması için çıktı](media/vs-getting-started-python-07-output.png)

1. IntelliSense, deyimler ve işlevler için tamamlamalara `import` ek `from` olarak Python ve deyimler için tamamlamasağlar. Bu tamamlamalar, ortamınızda hangi modüllerin mevcut olduğunu ve bu modüllerin üyelerini kolayca keşfetmenize yardımcı olur. `print` Düzenleyicide, satırı silin ve `import`yazmaya başlayın. Alanı yazdığınızda modüllerin listesi görüntülenir:

    ![IntellSense bir ithalat deyimi için kullanılabilir modülleri gösteren](media/vs-getting-started-python-08-import1.png)

1. Yazarak veya seçerek `sys`satırı tamamlayın.

1. Bir sonraki satırda, modüllerin listesini tekrar görmek için yazın: `from`

    ![IntellSense bir açıklama için kullanılabilir modülleri gösteren](media/vs-getting-started-python-09-import2.png)

1. Seçin veya `math`yazın, sonra bir `import`boşlukla yazmaya devam edin ve modül üyelerini görüntüler:

    ![IntellSense modül üyelerini gösteriyor](media/vs-getting-started-python-10-import3.png)

1. Her biri için `sin` `cos`kullanılabilir `radians` otomatik tamamlamaları fark, , ve üyeleri alarak bitirmek. İşinizi bitirdiğinizde, kodunuz aşağıdaki gibi görünmelidir:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Tamamlamalar, siz yazarken, sözcüklerin bölümlerini, sözcüklerin başındaki harfleri ve hatta atlanan karakterleri eşleştirerken alt dizeleri ile çalışır. Bkz. Kodu Edit - Ayrıntılar için [tamamlamalar.](editing-python-code-in-visual-studio.md#completions)

1. 360 derece için kosinüs değerlerini yazdırmak için biraz daha kod ekleyin:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Programı **Ctrl**+**F5** veya **Hata Ayıklama** > Başlangıç ile hata ayıklama olmadan yeniden**çalıştırın.** Bittiğinde çıkış penceresini kapatın.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Daha derine inin

- [Kodu edin](editing-python-code-in-visual-studio.md)
- [Kodu biçimlendirme](formatting-python-code.md)
- [Kodu yeniden düzenleme](refactoring-python-code.md)
- [PyLint kullanma](linting-python-code.md)
