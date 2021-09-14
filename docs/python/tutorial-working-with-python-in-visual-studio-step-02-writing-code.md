---
title: Python in Visual Studio öğreticisi 2. adım, kod yazma ve çalıştırma
titleSuffix: ''
description: Kod düzenleme ve proje çalıştırma dahil olmak üzere Visual Studio Python özelliklerine temel bir kılavuz olan 2. adım.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3198ed207c09c593e6e2bc0444499556c16ae206
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628274"
---
# <a name="step-2-write-and-run-code"></a>2. Adım: Kod yazma ve çalıştırma

**Önceki adım: [Yeni bir Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Bu **Çözüm Gezgini** proje dosyalarını yönetebilirsiniz ancak  düzenleyici penceresi genellikle kaynak  kod gibi dosyaların içeriğiyle birlikte çalışmanız gereken yerdir. Düzenleyici, programlama dili (dosya uzantısını temel alarak) dahil olmak üzere düzenlemekte olduğunu dosya türünü bağlamsal olarak biliyor ve IntelliSense kullanarak söz dizimi renklendirme ve otomatik tamamlama gibi bu dile uygun özellikler sunar.

1. Yeni bir "Python Uygulaması" projesi oluşturdukta, PythonApplication1.py adlı *varsayılan boş* dosya Visual Studio açılır.

1. Düzenleyicide yazmaya başlayın ve `print("Hello, Visual Studio")` IntelliSense'in Visual Studio tamamlama seçeneklerini nasıl görüntüleye dikkat edin. Açılan listede özetlenen seçenek, Sekme tuşuna bassanız kullanılan varsayılan **tamamlamadır.** Daha uzun deyimler veya tanımlayıcılar söz konusu olduğunda tamamlamalar en çok yararlıdır.

    ![IntelliSense otomatik tamamlama açılır menüsü](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense kullandığınız deyime, çağıran işlevine vb. bağlı olarak farklı bilgiler gösterir. `print`işleviyle, bir işlev `(` `print` çağrısını belirtmek için sonra yazarak bu işleve ilişkin tam kullanım bilgilerini görüntüler. IntelliSense açılır menüsünde geçerli bağımsız değişken kalın (burada gösterildiği gibi **değer)** gösterilir:

    ![bir işlev için IntelliSense otomatik tamamlama açılır menüsü](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Aşağıdakiyle eşleşmesi için deyimini tamamlama:

    ```python
    print("Hello, Visual Studio")
    ```

1. deyimini bağımsız değişkenden ayıran söz dizimi `print` renklendirmesi dikkat. `"Hello Visual Studio"` Ayrıca, dizede son dizeyi geçici olarak silin ve Visual Studio hataları içeren kod için kırmızı bir alt `"` çizginin nasıl olduğunu fark edin. Ardından kodunu düzeltmek `"` için yerine değiştirin.

    ![IntelliSense söz dizimi renklendirme ve hata vurgulama](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Bir geliştirme ortamı çok kişisel bir konu olduğundan, Visual Studio görünümü ve davranışı üzerinde Visual Studio tam denetim sağlar. Araçlar Seçenekler  >  **menü komutunu** seçin ve Ortam ve Metin Düzenleyici **sekmeleri** altındaki ayarları **keşfedin.** Varsayılan olarak yalnızca sınırlı sayıda seçenek vardır; Her programlama dilinin her seçeneğini görmek için iletişim **kutusunun alt** kısmından Tüm ayarları göster'i seçin.

1. **Ctrl** F5 tuşlarına basarak veya Hata Ayıklama Olmadan Başlat menü öğesini seçerek bu +    >  **noktaya yazarak** kodu çalıştırın. Visual Studio hala hata varsa sizi uyarabilir.

1. Programı çalıştırarak, komut satırına sahip bir Python yorumlayıcı çalıştırmış gibi sonuçları *görüntüleyen bir PythonApplication1.py* penceresi görüntülenir. Pencereyi kapatmak ve düzenleyiciye geri dönmek için Visual Studio basın.

    ![Programın ilk çalıştırması için çıkış](media/vs-getting-started-python-07-output.png)

1. IntelliSense, deyimler ve işlevler için tamamlamalara ek olarak Python ve deyimler `import` için `from` tamamlamalar sağlar. Bu tamamlamalar, ortamınız için hangi modüllerin ve bu modüllerin üyelerinin kullanılabilir olduğunu kolayca keşfetmenize yardımcı olur. Düzenleyicide, satırı silin `print` ve yazmaya `import` başlayın. Alanı yazarak modüllerin listesi görüntülenir:

    ![İçeri aktarma deyimi için kullanılabilir modülleri gösteren IntellSense](media/vs-getting-started-python-08-import1.png)

1. yazarak veya seçerek satırı `sys` tamamlar.

1. Sonraki satırda, modül `from` listesini görmek için yazın:

    ![bir from deyimi için kullanılabilir modülleri gösteren IntellSense](media/vs-getting-started-python-09-import2.png)

1. öğesini seçin veya `math` yazın, ardından modül üyelerini görüntüleyen bir `import` boşluk ve ile yazmaya devam edin:

    ![Modül üyelerini gösteren IntellSense](media/vs-getting-started-python-10-import3.png)

1. , ve üyelerini `sin` `cos` içeri `radians` aktararak, her biri için kullanılabilen otomatik tamamlamaları noterek işlemi bitirin. Bitirin ve kodunuzun aşağıdaki gibi görünmesi gerekir:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Tamamlamalar siz yazarak, sözcüklerin parçalarını, sözcüklerin başındaki harfleri ve hatta atlanan karakterleri eşleştirerek alt dizelerle çalışır. Ayrıntılar [için bkz. Kodu düzenleme -](editing-python-code-in-visual-studio.md#completions) Tamamlamalar.

1. 360 derecelik kosinüs değerlerini yazdırmak için biraz daha kod ekleyin:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. **Ctrl** F5 veya Hata Ayıklama Olmadan Başlat ile +  programı   >  **yeniden çalıştırın.** Bitirin ve çıkış penceresini kapatın.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Kodu düzenleme](editing-python-code-in-visual-studio.md)
- [Kodu biçimlendirme](formatting-python-code.md)
- [Kodu yeniden düzenleme](refactoring-python-code.md)
- [PyLint kullanma](linting-python-code.md)
