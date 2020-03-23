---
title: Hata ayıklama ASP.NET Çekirdek
description: Visual Studio hata ayıklama kullanarak ASP.NET Core hata ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75847882"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Quickstart: Visual Studio hata ayıklama ile ASP.NET Core hata ayıklama

Visual Studio hata ayıklama, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **asp.net**yazın, **Şablonlar'ı**seçin, ardından **Yeni ASP.NET Oluştur'u seçin.** Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **Web'i**seçin ve sonra orta bölmede Çekirdek Web **Uygulaması ASP.NET**seçin. **MyDbgApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.

    Görünen iletişim kutusunda, orta bölmede **Web Uygulaması'nı** seçin ve ardından **Tamam'ı**tıklatın.

    ![Bir Web uygulaması seçin](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Core Web Application proje **şablonuna ASP.NET** görmüyorsanız, Visual Studio Yükleyici'yi açan **Araçlar** > **Araçları ve Özellikleri Al...** adresine gidin. ASP.NET **ve web geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

    Visual Studio projeyi oluşturur.

1. Solution Explorer'da About.cshtml.cs açın (Pages/About.cshtml altında) ve aşağıdaki kodu değiştirin

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    bu kod ile:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

*Kesme noktası,* Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösteren bir işaretçidir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktasını ayarlamak `doWork` için, işlevin solundaki olukta tıklayın (veya kod çizgisini seçin ve **F9**tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Kesme noktası, açılış ayracının solunda ayarlanır (`{`).

1. Şimdi **F5** tuşuna basın (veya **Hata Ayıklama > Hata Ayıklama'yı başlat'ı**seçin).

1. Web sayfası yüklendiğinde, web sayfasının üst kısmındaki **Hakkında** bağlantısını tıklatın.

    Hata ayıklama, kesme noktasını ayarladığınız yerde duraklar. Hata ayıklama ve uygulama yürütmenin duraklattığı deyim sarı okla gösterilir. İşlev bildiriminden sonra`{`açılan ayracı olan satır ( ) henüz yürütülmedi. `doWork`

    ![Bir kesme noktasına çarptım](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Bir döngü veya özyinelemede bir kesme noktanız varsa veya sık sık adım attığınız çok sayıda kesme noktanız varsa, yalnızca belirli koşullar karşılandığında kodunuzun askıya aldığından emin olmak için [koşullu](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) bir kesme noktası kullanın. Bu, zamandan tasarruf sağlar ve yeniden oluşturulması zor olan sorunları ayıklamayı da kolaylaştırabilir.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıkıcıya devam etmesini emretmek için farklı komutlar vardır. Visual Studio 2017'den itibaren kullanılabilen kullanışlı bir kod navigasyon komutu gösteriyoruz.

Kesme noktasında duraklatılırken, yeşil `return c2` **Çalıştır'dan Tıklatdüğmesine** ![](../debugger/media/dbg-tour-run-to-click.png) tıklayın düğmesine kadar deyimin üzerine basın ve ardından **Tıklatmak için Çalıştır düğmesine basın.**

![Tıklatmak için çalıştırın](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Uygulama yürütmeye devam eder ve düğmeyi tıklattığınız kod satırında duraklar.

Koda basmak için kullanılan yaygın klavye komutları **F10** ve **F11'i**içerir. Daha ayrıntılı talimatlar için [hata ayıklama bölümüne ilk bakışta](../debugger/debugger-feature-tour.md)bakın.

## <a name="inspect-variables-in-a-datatip"></a>Veri ucundaki değişkenleri inceleyin

1. Geçerli kod satırında (sarı yürütme işaretçisi ile `c2` işaretlenmiş), bir veri ipucu göstermek için fareniz ile nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Veri ipucu, `c2` değişkenin geçerli değerini gösterir ve değişkenin özelliklerini incelemenize olanak tanır. Hata ayıklama yaparken, beklemediğiniz bir değer görürseniz, büyük olasılıkla önceki veya kod satırlarını çağıran bir hatanız vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için `c2` veri ucunu genişletin.

3. Kod `c2` yürütürken değerini görmeye devam etmek için veri ucunu sabitlemek istiyorsanız, küçük pin simgesini tıklatın. (Sabitlenmiş veri ucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunuzda sınamak istediğiniz bir değişikliği tanımlarsanız, bunu da yapabilirsiniz.

1. `OnGet` Yöntemde, ikinci örneğini `result.First.Value` tıklatın `result.First.Value` ve `result.Last.Value`değiştirin.

1. Hata ayıklayıcıyı ilerletmek ve düzenlenen kodu yürütmek için **F10** (veya **Hata Ayıklama > Adım At)** tuşuna birkaç kez basın.

    ![Edin ve devam edin](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Edin ve devam edin")

    **F10** hata ayıklayıcıyı bir defada bir ifadeyi ilerletir, ancak bunlara adım atmak yerine işlevlerin üzerine adım atar (atladığınız kod hala yürütülür).

Edit-and-continue ve özellik sınırlamaları hakkında daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatmayı, koda nasıl basabileceğinizi ve değişkenleri nasıl inceleyincenizi öğrendiniz. Hata ayıklama özelliklerine daha fazla bilgi bağlantılarıyla birlikte üst düzey bir görünüm elde etmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
