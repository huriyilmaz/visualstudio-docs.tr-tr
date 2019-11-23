---
title: C++ Visual Studio hata ayıklayıcısını kullanarak hata ayıklamayı öğrenin
description: Kodu adımlayın Visual Studio hata ayıklayıcısını başlatın ve veri İnceleme hakkında bilgi edinin.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 070cbcc79a79aea16e37f17ea775ce7838b41d59
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179813"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: C++ kodunuzu Visual Studio kullanarak hata ayıklamayı öğrenin

Bu makalede, Visual Studio hata ayıklayıcı adım adım kılavuzda özelliklerini tanıtır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Olduğunda, *uygulamanızda hata ayıklama*, hata ayıklayıcısı ekli, uygulamanızın çalıştığını genellikle anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı, kodunuzun ne yaptığını görmek için birçok yol sağlar. çalışırken. Kodunuzda adım adım ve değişkenlerinde depolanan değerleri bakmak, gözcüler ayarlayabilirsiniz değerleri değiştiğinde görmek için değişkenlerini kodunuzun yürütme yolunu inceleyin, bir dal kod çalıştırma, vb. olup olmadığını. Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktaları isabet.
> * Hata ayıklayıcı kodda adım adım için komutları öğrenin
> * Veri ipuçları ve hata ayıklayıcı pencereleri değişkenler inceleyin
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

Visual Studio 2019 ' nin yüklü olması ve iş yüküyle **Masaüstü C++ geliştirmesi** olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 yüklü olması gerekir ve **C++ ile masaüstü geliştirme** iş yükü.

::: moniker-end

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Visual Studio Yükleyicisi'ni başlatır. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir**.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **C++** yazın, **Şablonlar**' ı seçin ve **Yeni konsol uygulaması projesi oluştur**' u seçin. Görüntülenen iletişim kutusunda, **Get-Started-hata ayıklama**gibi bir ad yazın ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C++** altında **Windows Masaüstü**' nün ardından orta bölmedeki **Windows konsol uygulaması**' nı seçin. Ardından, **Mydbgapp** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Windows konsol uygulaması** proje şablonunu görmüyorsanız **Araçlar** **ve Özellikler al** > ' a gidin ve Visual Studio yükleyicisi açılır. Visual Studio Yükleyicisi'ni başlatır. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir**.

    Visual Studio projesi oluşturur.

1. İçinde *get çalışmaya debugging.cpp*, aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kod ile:

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatın!

1. Tuşuna **F5** (**hata ayıklama > hata ayıklamayı Başlat**) veya **hata ayıklamayı Başlat** düğmesi ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat ") hata ayıklama araç çubuğu.

     **F5** başladığında hata ayıklayıcının uygulamayla uygulamaya bağlı işlem ancak biz kodunu incelemek için özel bir şey yapmadınız hemen. Bu nedenle yalnızca uygulamayı yükler ve konsol çıktısı görürsünüz.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Bu öğreticide, biz hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından göz atın ve hata ayıklayıcı göz özelliklerini elde etmek.

2. Kırmızı Durdur tuşuna basarak hata ayıklayıcıyı ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "hata ayıklamayı Durdur") düğmesi.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklayıcıyı başlatın

1. İçinde `for` , döngü `main` işlev, aşağıdaki kod satırının sol kenar boşluğunu tıklayarak kesme noktası ayarlayın:

    `shape->Draw()`

    Kesme noktasının ayarlandığı kırmızı bir daire görünür.

    Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

2. Tuşuna **F5** veya **hata ayıklamayı Başlat** düğmesi! [ Hata Ayıklamayı Başlat] (.. "Hata ayıklamayı Başlat", uygulamanın /Debugger/Media/dbg-Tour-Start-Debugging.PNG başlar ve hata ayıklayıcı, Kesme noktasının ayarlandığı kod satırına çalıştırır.

    ![Ayarlayın ve bir kesme noktası isabet](../debugger/media/get-started-set-breakpoint-cpp.gif)

    Sarı ok, aynı zamanda aynı noktayı (Bu bildirimi henüz çalıştırılmadı) uygulama yürütmeyi askıya alır, hata ayıklayıcı durduruldu, deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durur. Aksi takdirde, **F5** uygulamayı sonraki kesme noktasına kadar çalışmaya devam eder.

    Kod satırının veya ayrıntılı olarak incelemek istediğiniz kod bölümünün bildiğiniz durumlarda kesme noktaları yararlı bir özelliktir.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Kod adım komutları kullanarak hata ayıklayıcısında gidin

Almak için en iyi yolu olduğundan bu çoğunlukla, klavye kısayollarını Burada, kullandığımız hata ayıklayıcı (komutları parantez içinde gösterilen eşdeğer komutları menüsü gibi) uygulamanız çalıştırma sırasında hızlı.

1. İçinde duraklatıldığı sırada `shape->Draw` yöntem çağrısı `main` işlev, basın **F11** (veya tercih **hata ayıklama > içine adımla**) için koda ilerlemek için `Rectangle` sınıfı.

     ![İçine adımla kodu F11 kullanın](../debugger/media/get-started-f11-cpp.png "F11 adımla")

     F11 olan **içine adımla** komut ve aynı anda uygulama yürütme bir deyim ilerler. F11 çoğu ayrıntılı yürütme akışı incelemek için iyi bir yoludur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

2. Basın **F10** (veya tercih **hata ayıklama > Step Over**) hata ayıklayıcı birkaç kez durur kadar `Shape::Draw` yöntem çağrısının yazıp ENTER tuşuna **F10** bir kez daha.

     ![Step Over kodu F10 kullanın](../debugger/media/get-started-step-over-cpp.png "F10 adımla")

     Hata ayıklayıcı içine girmez şu bildirim `Draw` temel sınıf yöntemini (`Shape`). **F10** işlevleri veya yöntemleri (kod hala çalışır), uygulama kodunuzda içine Adımlama olmadan, hata ayıklayıcı ilerler. F10 tuşlarına basarak `Shape::Draw` yöntem çağrısının (yerine **F11**), biz uygulama kodunu üzerinden atlandı `Draw` (hangi maybe değiliz ilginizi şu anda) temel sınıf.

## <a name="navigate-code-using-run-to-click"></a>Tıkla Çalıştır'ı kullanarak kod gidin

1. Kod Düzenleyicisi'nde, ekranı aşağı kaydırın ve üzerine `std::cout` içinde `Triangle` sınıfı yeşil kadar **tıklanan satıra kadar Çalıştır** düğmesi ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png "RunToClick") Soldaki bölmede görünür.

     ![Tıkla Çalıştır kullanın özellik](../debugger/media/get-started-run-to-click-cpp.png "tıklanan satıra kadar Çalıştır")

   > [!NOTE]
   > **Tıklama Için Çalıştır** düğmesi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]başlayarak kullanılabilir. Yeşil ok düğmesini görmüyorsanız kullanın **F11** Bu örnekte bunun yerine hata ayıklayıcı doğru yere ilerlemek için.

2. Tıklayın **tıklanan satıra kadar Çalıştır** düğmesi ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Bu düğmeyi kullanarak geçici bir kesme noktası ayarlayarak benzer. **Tıklanan satıra kadar Çalıştır** (herhangi bir açık dosyayı tıklayabilirsiniz) uygulama kodu görünür bir bölge içinde hızla dolaşma için kullanışlıdır.

    Hata ayıklayıcı ilerler `std::cout` yöntem uygulaması için `Triangle` sınıfı.

    Duraklatıldığı sırada bir yazım yanlışı dikkat edin! "Bir trangle çizim" çıkış yanlış yazılmıştır. Biz burada Hata Ayıklayıcısı'nda uygulama çalıştırılırken düzeltebilirsiniz.

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

1. İçine tıklayın "bir trangle çizim" ve "trangle" değiştirme "üçgene", bir düzeltme yazın.

1. Tuşuna **F11** bir kez kod bir ileti yeniden derlemeden ve ardından hata ayıklayıcıyı yeniden ilerler görürsünüz.

    > [!NOTE]
    > Ne tür kod hata ayıklayıcıda düzenleme bağlı olarak, bir uyarı iletisi görebilirsiniz. Bazı senaryolarda, kod devam edebilmek derlemeniz gerekir.

## <a name="step-out"></a>Dışına adımla

İşiniz olduğunu düşünelim İnceleme `Draw` yönteminde `Triangle` sınıfı ve istediğiniz get işlevi dışında ancak hata ayıklayıcıda haberdar olun. Bunu kullanarak yapabilirsiniz **Step Out** komutu.

1. Tuşuna **Shift** + **F11** (veya **hata ayıklama > dışarı adımla**).

     Bu komut, uygulama yürütmeyi devam ettirir (ve hata ayıklayıcı ilerler) geçerli işlev dönene kadar.

     Geri olmalıdır `for` içinde döngü `main` yöntemi.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlı bir şekilde yeniden başlatın

Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**).

Bastığınızda **yeniden**, uygulama durdurup hata ayıklayıcı yerine zaman kaydeder. İlk kesme noktasına isabet kodu yürüterek, hata ayıklayıcı duraklatır.

Hata ayıklayıcıyı yeniden üzerinde sizin ayarladığınız kesme noktasında durur `shape->Draw()` yöntemi.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları değişkenlerle inceleyin

Değişkenleri incelemek özellik hata ayıklayıcının en kullanışlı özellikler biridir ve bunu yapmanın farklı yolu vardır. Genellikle, hata ayıklama bir sorun açmayı denediğinde, belirli bir zamanda sahip olmalarını beklediğiniz değerleri değişkenleri olup depoladığını kullanıma bulmak çalışıyorsunuz.

1. Üzerinde duraklatıldığı sırada `shape->Draw()` yöntemi, kutucuğun üzerine gelip `shapes` kapsayıcı (vektör nesnesi) ve bkz varsayılan özellik değerine `size` gösteren özelliği `size=3`.

1. Genişletin `shapes` tüm özelliklerini, dizinin ilk dizini gibi görmek için nesne `[0]`, bir bellek adresi vardır.

    Nesnelerin özelliklerini görüntülemek için daha da genişletebilirsiniz.

1. İlk dizinini genişletin `[0]` görmek için `privateHeight` dikdörtgeninin özelliği.

     ![Bir veri ipucunda görüntülemek](../debugger/media/get-started-data-tip-cpp.png "bir veri ipucunda görüntüleyin")

     Genellikle, hata ayıklama sırasında istediğiniz nesnelerin özellik değerlerini denetlemek için hızlı bir yol ve veri ipuçları yapmak için iyi bir yoludur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenlerle inceleyin

1. Bakmak **Otolar** altındaki kod düzenleyicisi penceresi.

     ![Otomatik değişkenler penceresi değişkenleri İnceleme](../debugger/media/get-started-autos-window-cpp.png "otomatik değişkenler penceresi")

    İçinde **Otolar** penceresi değişkenleri ve bunların geçerli değerini görürsünüz. C++ için **Otolar** penceresi değişkenleri kod üç önceki satırlarını gösterir.

2. Ardından, bakmak **Yereller** penceresinde ileri bir sekmeye **Otolar** penceresi.

    **Yereller** penceresi gösterir, geçerli olan değişkenlere [kapsam](https://www.wikipedia.org/wiki/Scope_(computer_science)), diğer bir deyişle, geçerli kod yürütme bağlamı.

## <a name="set-a-watch"></a>Bir izleme ayarlayın

1. Ana Kod Düzenleyicisi'ni penceresinde sağ `shapes` seçin ve nesne **Gözcü Ekle**.

    **Watch** Kod Düzenleyicisi sayfanın en penceresi açılır. Kullanabileceğiniz bir **Watch** penceresinin bir değişken (veya bir ifade) takip etmek istediğinizi belirtin.

    Artık, bir izleme ayarlayın sahipsiniz `shapes` nesne ve hata ayıklayıcı geçerken değiştirme değeri görebilirsiniz. Diğer değişken pencerelerini aksine **Watch** penceresi her zaman, izlerken değişkenleri gösterir (bunlar zaman kapsam dışına renkte).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. İçinde duraklatıldığı sırada `for` döngüsünde, tıklayın **çağrı yığını** varsayılan alt sağ bölmede açık olarak penceresinde.

2. Tıklayın **F11** birkaç kez duraklatmak, hata ayıklayıcı görene kadar `Shape::Draw` yöntemi `Rectangle` Kod düzenleyicisinde sınıfı. Bakmak **çağrı yığını** penceresi.

    ![Çağrı yığınını incelemek](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    **Çağrı yığını** penceresi, yöntemleri ve işlevleri çağrılır sırasını gösterir. Geçerli işlev en üst satırına gösterir ( `Rectangle::Draw` Bu örnekte yöntemi). İkinci satır gösteren `Rectangle::Draw` çağırıldığı `main` işlevi ve benzeri.

   > [!NOTE]
   > **Çağrı yığını** penceresi benzer hata ayıklama perspektifi için Eclipse gibi bazı IDE içinde.

    Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

    Bir satır kod, kaynak koda bakmaktır gitmek için çift tıklayın ve hata ayıklayıcı tarafından denetlenmekte olan geçerli kapsamını da değişiklikler. Bu eylem, hata ayıklayıcı ilerleyin değil.

    Sağ tıklama menülerden kullanabilirsiniz **çağrı yığını** başka şeyler için pencere. Örneğin, belirtilen işlevlere kesme noktaları ekleme, hata ayıklayıcıyı kullanarak ilerleyin **imlece kadar Çalıştır**ve kaynak kodunu inceleyin. Daha fazla bilgi için [nasıl yapılır: çağrı yığını inceleyin](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

1. İçinde hata ayıklayıcısı ile duraklatıldı `Shape::Draw` yöntemi çağrısı, sol taraftaki sarı ok (yürütme işaretçisi) almak için fareyi kullanın ve sarı ok için bir satır yukarı taşı `std::cout` yöntem çağrısı.

1. Tuşuna **F11**.

    Hata ayıklayıcıyı yeniden çalıştırır `std::cout` yöntemi (bunu görmeniz konsol penceresi çıktısı).

    Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

    > [!WARNING]
    > Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

1. Tuşuna **F5** uygulamayı çalıştırmaya devam etmek için.

    Bu öğreticiyi tamamlamak Tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
