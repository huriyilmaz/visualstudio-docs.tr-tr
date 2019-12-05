---
title: 'Öğretici: hata C# ayıklama kodu'
description: Kodu adımlayın Visual Studio hata ayıklayıcısını başlatın ve veri İnceleme hakkında bilgi edinin.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c7237d8d8bf66273078049a41a3193af0026792
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830019"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: hata ayıklamayı öğrenin C# kullanarak Visual Studio code

Bu makalede, Visual Studio hata ayıklayıcı adım adım kılavuzda özelliklerini tanıtır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md). Olduğunda, *uygulamanızda hata ayıklama*, hata ayıklayıcısı ekli, uygulamanızın çalıştığını genellikle anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı, kodunuzun ne yaptığını görmek için birçok yol sağlar. çalışırken. Kodunuzda adım adım ve değişkenlerinde depolanan değerleri bakmak, gözcüler ayarlayabilirsiniz değerleri değiştiğinde görmek için değişkenlerini kodunuzun yürütme yolunu inceleyin, bir dal kod çalıştırma, vb. olup olmadığını. Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [yeni başlayanlar için hata ayıklama](../../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.

Tanıtım uygulamasını olmasına rağmen C#, özelliklerin çoğunu Visual Basic, C++ için uygun F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer dillerde (F# Düzenle ve devam et desteklemez. F#ve JavaScript desteği **Otolar** pencere). Ekran görüntüleri C# ' de var.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktaları isabet.
> * Hata ayıklayıcı kodda adım adım için komutları öğrenin
> * Veri ipuçları ve hata ayıklayıcı pencereleri değişkenler inceleyin
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"

Visual Studio 2019 yüklü ve **.net masaüstü geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 yüklü olması gerekir ve **.NET Masaüstü geliştirmesinden** iş yükü.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** iş yükü, ardından **Değiştir**.

## <a name="create-a-project"></a>Proje oluştur

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **konsolu**yazın, **Şablonlar**' ı seçin, sonra **Yeni konsol uygulaması oluştur (.NET Core) projesi** veya **Yeni konsol uygulaması (.NET Framework) projesi**seçin. Görüntülenen iletişim kutusunda, **Get-Started-hata ayıklama**gibi bir ad yazın ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. Ardından, **Get-Started-hata ayıklama** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması (.NET Framework)** proje şablonunu görmüyorsanız, **Araçlar** ' a gidin > **Araçlar ve Özellikler al...** ' a giderek Visual Studio yükleyicisi açılır. Seçin **.NET masaüstü geliştirme** iş yükü, ardından **Değiştir**.

    Visual Studio projesi oluşturur.

1. *Program.cs*' de, varsayılan kodun tümünü değiştirin

    ```csharp
    using System;
    // ...

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    Bu kod ile:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }

        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
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

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata**Ayıkla > Başlat**) ![veya hata](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

     **F5** başladığında hata ayıklayıcının uygulamayla uygulamaya bağlı işlem ancak biz kodunu incelemek için özel bir şey yapmadınız hemen. Bu nedenle yalnızca uygulamayı yükler ve konsol çıktısı görürsünüz.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Bu öğreticide, biz hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından göz atın ve hata ayıklayıcı göz özelliklerini elde etmek.

2. Kırmızı durma ![hata ayıklamayı](../../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") Durdur düğmesine basarak hata ayıklayıcıyı durdurun.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklayıcıyı başlatın

1. İçinde `foreach` , döngü `Main` işlev, aşağıdaki kod satırının sol kenar boşluğunu tıklayarak kesme noktası ayarlayın:

    `shape.Draw()`

    Kesme noktasının ayarlandığı kırmızı bir daire görünür.

    Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Ayarlayın ve bir kesme noktası isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, aynı zamanda aynı noktayı (Bu bildirimi henüz çalıştırılmadı) uygulama yürütmeyi askıya alır, hata ayıklayıcı durduruldu, deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durur. Aksi takdirde, **F5** uygulamayı sonraki kesme noktasına kadar çalışmaya devam eder.

    Kod satırının veya ayrıntılı olarak incelemek istediğiniz kod bölümünün bildiğiniz durumlarda kesme noktaları yararlı bir özelliktir.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Kod adım komutları kullanarak hata ayıklayıcısında gidin

Almak için en iyi yolu olduğundan bu çoğunlukla, klavye kısayollarını Burada, kullandığımız hata ayıklayıcı (komutları parantez içinde gösterilen eşdeğer komutları menüsü gibi) uygulamanız çalıştırma sırasında hızlı.

1. İçinde duraklatıldığı sırada `shape.Draw` yöntem çağrısı `Main` yöntemi, basın **F11** (veya tercih **hata ayıklama > içine adımla**) için koda ilerlemek için `Rectangle` sınıfı.

     ![Koda geçmek için F11 kullanın](../csharp/media/get-started-f11.png "F11 step INTO")

     F11 olan **içine adımla** komut ve aynı anda uygulama yürütme bir deyim ilerler. F11 çoğu ayrıntılı yürütme akışı incelemek için iyi bir yoludur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

2. Basın **F10** (veya tercih **hata ayıklama > Step Over**) hata ayıklayıcı birkaç kez durur kadar `base.Draw` yöntem çağrısının yazıp ENTER tuşuna **F10** bir kez daha.

     ![Kod üzerinde adımla F10 kullanın](../csharp/media/get-started-step-over.png "F10 adımla")

     Hata ayıklayıcı içine girmez şu bildirim `Draw` temel sınıf yöntemini (`Shape`). **F10** işlevleri veya yöntemleri (kod hala çalışır), uygulama kodunuzda içine Adımlama olmadan, hata ayıklayıcı ilerler. `base.Draw` Yöntem çağrısında **F10** tuşuna basarak ( **F11**yerine), `base.Draw` için uygulama kodu atlandık (Bu, şu anda ilgilentik olabilir).

## <a name="navigate-code-using-run-to-click"></a>Tıkla Çalıştır'ı kullanarak kod gidin

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak `Triangle` sınıfında `Console.WriteLine` yönteminin üzerine gelin ve sol tarafta görüntülenen düğmesine ![tıklamak](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") üzere **düğme** Çalıştır düğmesine tıklayın. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklanan satıra kadar Çalıştır** düğmesidir yeni [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Yeşil ok düğmesini görmüyorsanız kullanın **F11** Bu örnekte bunun yerine hata ayıklayıcı doğru yere ilerlemek için.

2. **Tıklama düğmesine tıklayarak** ![' ye tıklayın.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Bu düğmeyi kullanarak geçici bir kesme noktası ayarlayarak benzer. **Tıklanan satıra kadar Çalıştır** (herhangi bir açık dosyayı tıklayabilirsiniz) uygulama kodu görünür bir bölge içinde hızla dolaşma için kullanışlıdır.

    Hata ayıklayıcı ilerler `Console.WriteLine` yöntem uygulaması için `Triangle` sınıfı. (Hata ayıklayıcı daha önce ayarladığınız kesme noktasında ilk olarak durakladığında, `Console.WriteLine`hata ayıklayıcıyı ilerletmek için **Çalıştır ' ı** kullanın.)

    Duraklatıldığı sırada bir yazım yanlışı dikkat edin! "Bir trangle çizim" çıkış yanlış yazılmıştır. Biz burada Hata Ayıklayıcısı'nda uygulama çalıştırılırken düzeltebilirsiniz.

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

1. İçine tıklayın "bir trangle çizim" ve "trangle" değiştirme "üçgene", bir düzeltme yazın.

1. Tuşuna **F11** bir kez ve bkz hata ayıklayıcıyı yeniden ilerler.

    > [!NOTE]
    > Ne tür kod hata ayıklayıcıda düzenleme bağlı olarak, bir uyarı iletisi görebilirsiniz. Bazı senaryolarda, kod devam edebilmek derlemeniz gerekir.

## <a name="step-out"></a>Dışına adımla

İşiniz olduğunu düşünelim İnceleme `Draw` yönteminde `Triangle` sınıfı ve istediğiniz get işlevi dışında ancak hata ayıklayıcıda haberdar olun. Bunu kullanarak yapabilirsiniz **Step Out** komutu.

1. Tuşuna **Shift** + **F11** (veya **hata ayıklama > dışarı adımla**).

     Bu komut, uygulama yürütmeyi devam ettirir (ve hata ayıklayıcı ilerler) geçerli işlev dönene kadar.

     Geri olmalıdır `foreach` içinde döngü `Main` yöntemi. Aksi takdirde, **shıft** + **F11** tuşuna basın.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlı bir şekilde yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

Bastığınızda **yeniden**, uygulama durdurup hata ayıklayıcı yerine zaman kaydeder. İlk kesme noktasına isabet kodu yürüterek, hata ayıklayıcı duraklatır.

Hata ayıklayıcıyı yeniden üzerinde sizin ayarladığınız kesme noktasında durur `shape.Draw()` yöntemi.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları değişkenlerle inceleyin

Değişkenleri incelemek özellik hata ayıklayıcının en kullanışlı özellikler biridir ve bunu yapmanın farklı yolu vardır. Genellikle, hata ayıklama bir sorun açmayı denediğinde, belirli bir zamanda sahip olmalarını beklediğiniz değerleri değişkenleri olup depoladığını kullanıma bulmak çalışıyorsunuz.

1. Üzerinde duraklatıldığı sırada `shape.Draw()` yöntemi, kutucuğun üzerine gelip `shape` nesneyi ve nesne türü varsayılan özellik değeri görmek `Rectangle`.

1. Genişletin `shape` gibi özellikleri görmek için nesne `Height` özelliğini 0 değerine sahiptir.

1. Tuşuna **F10** (veya **hata ayıklama** > **Step Over**) birkaç kez kez yinelemek için `foreach` döngü, üzerinde yeniden duraklatma `shape.Draw()`.

1. Şekil nesnesi yeniden ve bu süre türü ile yeni bir nesne olduğunu gördüğünüz gelin `Triangle`.

     ![Veri ipucunu görüntüleme](../csharp/media/get-started-data-tip.gif "Veri Ipucunu görüntüleme")

    Genellikle, hata ayıklama sırasında istediğiniz değişkenlerde depolamak için bunları beklediğiniz değerleri depolamak olup olmadığını görmek için özellik değerlerini denetlemek için hızlı bir yol ve veri ipuçları yapmak için iyi bir yoludur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenlerle inceleyin

1. Bakmak **Otolar** altındaki kod düzenleyicisi penceresi.

    Kapalıysa, hata ayıklayıcıda seçerek duraklatıldığı sırada açmak **hata ayıklama** > **Windows** > **Otolar**.

1. Genişletin `shapes` nesne.

     ![Oto penceresindeki değişkenleri İncele](../csharp/media/get-started-autos-window.png "Oto penceresi")

    İçinde **Otolar** penceresi değişkenleri ve bunların geçerli değerini görürsünüz. **Otolar** penceresi, geçerli veya önceki satırındaki (dile özgü davranışı için belgeleri denetleyin) kullanılan tüm değişkenleri gösterir.

1. Ardından, bakmak **Yereller** penceresinde ileri bir sekmeye **Otolar** penceresi.

    **Yereller** penceresi gösterir, geçerli olan değişkenlere [kapsam](https://www.wikipedia.org/wiki/Scope_(computer_science)), diğer bir deyişle, geçerli yürütme bağlamı.

## <a name="set-a-watch"></a>Bir izleme ayarlayın

1. Ana Kod Düzenleyicisi'ni penceresinde sağ `shapes` seçin ve nesne **Gözcü Ekle**.

    **Watch** Kod Düzenleyicisi sayfanın en penceresi açılır. Kullanabileceğiniz bir **Watch** penceresinin bir değişken (veya bir ifade) takip etmek istediğinizi belirtin.

    Artık, bir izleme ayarlayın sahipsiniz `shapes` nesne ve hata ayıklayıcı geçerken değiştirme değeri görebilirsiniz. Diğer değişken pencerelerini aksine **Watch** penceresi her zaman, izlerken değişkenleri gösterir (bunlar zaman kapsam dışına renkte).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. İçinde duraklatıldığı sırada `foreach` döngüsünde, tıklayın **çağrı yığını** varsayılan alt sağ bölmede açık olarak penceresinde.

    Kapalıysa, hata ayıklayıcıda seçerek duraklatıldığı sırada açmak **hata ayıklama** > **Windows** > **çağrı yığını**.

2. Tıklayın **F11** birkaç kez duraklatmak, hata ayıklayıcı görene kadar `Base.Draw` yöntemi `Triangle` Kod düzenleyicisinde sınıfı. Bakmak **çağrı yığını** penceresi.

    ![Çağrı yığınını inceleyin](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    **Çağrı yığını** penceresi, yöntemleri ve işlevleri çağrılır sırasını gösterir. Geçerli işlev en üst satırına gösterir ( `Triangle.Draw` bu uygulamada yöntemi). İkinci satır gösteren `Triangle.Draw` çağırıldığı `Main` yöntemi ve benzeri.

   > [!NOTE]
   > **Çağrı yığını** penceresi benzer hata ayıklama perspektifi için Eclipse gibi bazı IDE içinde.

    Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

    Bir satır kod, kaynak koda bakmaktır gitmek için çift tıklayın ve hata ayıklayıcı tarafından denetlenmekte olan geçerli kapsamını da değişiklikler. Bu eylem, hata ayıklayıcı ilerleyin değil.

    Sağ tıklama menülerden kullanabilirsiniz **çağrı yığını** başka şeyler için pencere. Örneğin, belirtilen işlevlere kesme noktaları ekleme, hata ayıklayıcıyı kullanarak ilerleyin **imlece kadar Çalıştır**ve kaynak kodunu inceleyin. Daha fazla bilgi için [nasıl yapılır: çağrı yığını inceleyin](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

1. İçinde hata ayıklayıcısı ile duraklatıldı `Circle.Draw` yöntemi çağrısı, sol taraftaki sarı ok (yürütme işaretçisi) almak için fareyi kullanın ve sarı ok için bir satır yukarı taşı `Console.WriteLine` yöntem çağrısı.

1. Tuşuna **F11**.

    Hata ayıklayıcıyı yeniden çalıştırır `Console.WriteLine` yöntemi (bunu görmeniz konsol penceresi çıktısı).

    Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

    > [!WARNING]
    > Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

1. Tuşuna **F5** uygulamayı çalıştırmaya devam etmek için.

    Bu öğreticiyi tamamlamak Tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
