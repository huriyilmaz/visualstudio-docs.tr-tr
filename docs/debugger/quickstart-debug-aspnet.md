---
title: Hata ayıklama ASP.NET Core
description: Visual Studio ASP.NET Core hata ayıklayıcısını kullanarak Visual Studio ayıklama
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 18d108b61e047151daf197832c81836b2e33b38a
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972589"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Hızlı Başlangıç: ASP.NET Core hata ayıklayıcısıyla Visual Studio ayıklama

Bu Visual Studio hata ayıklayıcısı, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, temel özelliklerden bazıları hakkında bilgi edinmek için hızlı bir yol sağlar.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, **asp.net** yazın, Şablonlar'ı seçin ve ardından Web **Uygulaması'ASP.NET Core oluştur'a tıklayın.**  Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında **Web'i** seçin ve orta bölmede Web **Uygulaması'ASP.NET Core seçin.** **MyDbgApp** gibi bir ad yazın ve Tamam'a **tıklayın.**

    Görüntülenen iletişim kutusunda orta bölmede **Web Uygulaması'yı** seçin ve ardından Tamam'a **tıklayın.**

    ![Web uygulaması seçme](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    **ASP.NET Core Web Uygulaması** proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**

    Visual Studio projeyi oluşturur.

1. Bu Çözüm Gezgini About.cshtml.cs dosyasını açın (Sayfalar/About.cshtml altında) ve aşağıdaki kodu değiştirin

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    yerine şu kodu yazın:

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

Kesme *noktası,* değişkenlerin değerlerine Visual Studio veya bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktası ayarlamak için işlevin sol tarafından sol tarafta yer alan oluklu maddeye tıklayın (veya kod satırına tıklayın ve `doWork` **F9 tuşuna basın).**

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Kesme noktası, açma ayracı ( ) sol tarafından `{` ayarlanır.

1. Şimdi **F5 tuşuna basın** (veya Hata **Ayıklamayı Başlat >'yi seçin).**

1. Web sayfası yüklenirken, web **sayfasının** üst kısmında yer alan Hakkında bağlantısına tıklayın.

    Hata ayıklayıcısı kesme noktası ayarlayıcıyı duraklatıyor. Hata ayıklayıcısı ve uygulama yürütmenin duraklatılmış olduğu deyim sarı okla işaret ediyor. İşlev bildirimi henüz yürütülmedikten `{` sonra açılış ayracı ( ) `doWork` olan satır.

    ![Kesme noktası isabeti](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Döngüde veya yeniden çalışmada kesme noktanız varsa veya sık sık adım attığınız çok sayıda [](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) kesme noktanız varsa, kodunuzun YALNIZCA belirli koşullar karşılandı olduğunda askıya alındıktan emin olmak için koşullu kesme noktası kullanın. Bu, zamandan tasarruf sağlar ve yeniden üretile zor olan sorunlarda hata ayıklamayı da kolaylaştırır.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıklayıcıya devam etme talimatı için farklı komutlar vardır. 2017'den itibaren kullanılabilen yararlı bir kod gezinti Visual Studio gösteriyoruz.

Kesme noktası duraklatılırken, yeşil renkli Çalıştır düğmesine tıklar gibi görünene kadar deyimin üzerine gelin ve ardından `return c2`  ![ ](../debugger/media/dbg-tour-run-to-click.png) **Çalıştır'a tıklayarak düğmesine** basın.

![Tıklamak için çalıştır](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Uygulama yürütmeye devam eder ve düğmeye tıklamış olduğunuz kod satırı üzerinde duraklatılır.

Kodda adım adım gezinmek için kullanılan yaygın klavye komutları **F10** ve **F11'tir.** Daha ayrıntılı yönergeler için bkz. [Hata ayıklayıcıya ilk bakış.](../debugger/debugger-feature-tour.md)

## <a name="inspect-variables-in-a-datatip"></a>Veri ipucunda değişkenleri inceleme

1. Geçerli kod satırı (sarı yürütme işaretçisi ile işaretlenmiş) farenizin olduğu nesnenin üzerine gelerek `c2` bir veri ipucu gösterir.

    ![Veri ipucu görüntüleme](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Veri ipucu değişkenin geçerli değerini `c2` gösterir ve özelliklerini incelemeye olanak sağlar. Hata ayıklama sırasında, beklemeyebilirsiniz bir değer görüyorsanız, büyük olasılıkla önceki veya çağıran kod satırlarında bir hata vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için veri ipucuna `c2` bakın.

3. Kod yürütürken değerini görmeye devam etmek için veri ipucuna sabitlemek için küçük pin `c2` simgesine tıklayın. (Sabitlenmiş veri ipucunı uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunda test etmek istediğiniz bir değişikliği tespit ediyorsanız, bunu da kullanabilirsiniz.

1. `OnGet`yönteminde, öğesinin ikinci örneğine tıklayın `result.First.Value` ve olarak `result.First.Value` `result.Last.Value` değişir.

1. Hata ayıklayıcıyı ilerletin ve **düzenlenen kodu yürütmek >** **F10** 'a (veya Hata Ayıkla veya AdımLa) birkaç kez basın.

    ![Düzenle ve devam](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Düzenle ve devam")

    **F10,** hata ayıklayıcıyı tek tek bir deyime ilerletmektedir, ancak işlevlere adımlarını atlar (atlayıp atlayılan kod yine de yürütülür).

Düzenle ve devam edin özelliğini kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. Düzenle [ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
