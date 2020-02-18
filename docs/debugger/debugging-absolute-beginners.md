---
title: Mutlak yeni başlayanlar için hata ayıklama kodu
description: İlk kez hata ayıklaması yapıyorsanız, uygulamanızı Visual Studio ile hata ayıklama modunda çalıştırmanıza yardımcı olacak birkaç ilke öğrenin
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c3cf9d5e4d72ed316344d1bda930d0416e9efe5
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416404"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Mutlak yeni başlayanlar için hata ayıklama

Hata olmadan, yazılım geliştiricileri olarak yazdığımız kod, her zaman bunu yapması Beklendiğimiz şeyi yapmaz. Bazen tamamen farklı bir şey yapar! Bu durumda, bir sonraki görev nedenini anlamak ve yalnızca kodumuza saat için bir hata ayıklama işlemi yapmak istememize rağmen bir hata ayıklayıcı aracı ya da hata ayıklayıcının kullanılması çok daha kolay ve verimlidir.

Ne yazık ki hata ayıklayıcı, tüm sorunları veya kodlarımızda "hataları" açığa çıkarılabilecek bir şey değildir. *Hata ayıklama* , bir programlama hatası yaptığınız kesin noktayı bulmak Için Visual Studio gibi bir hata ayıklama aracında kod adım adım adımları çalıştırmanın anlamına gelir. Kodunuzda yapmanız gereken düzeltmeleri öğreniyor ve hata ayıklama araçları, programı çalıştırmaya devam edebilmeniz için genellikle geçici değişiklikler yapmanıza olanak sağlar.

Bir hata ayıklayıcının kullanılması, her yazılım geliştiricisi için son olarak temel bir görev olan öğrenirken zaman alan bir yetenuygulamadır. Bu makalede, hata ayıklamanın temel ilkelerini tanıttık ve başlamanıza yönelik ipuçları sunarız.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Doğru soruları isteyerek sorunu açıklığa kavuşturun

Sorunu gidermeyi denemeden önce, çalıştırdığınız sorunu açıklığa kavuşturmanıza yardımcı olur. Kodunuzda bir sorunla karşılaşmanızı bekledik, aksi takdirde hata ayıklamayı nasıl saptayacağınızı düşünüyorsunuz! Bu nedenle, hata ayıklamaya başlamadan önce, çözmeye çalıştığınız sorunu belirttiğinizden emin olun:

* Kodunuzun ne yapması beklensin?

* Bunun yerine ne oldu?

    Uygulamanızı çalıştırırken bir hata (özel durum) çalıştırdıysanız, bu iyi bir şey olabilir! Özel durum, kod çalıştırılırken karşılaşılan beklenmeyen bir olaydır ve genellikle bir tür hata oluşur. Hata ayıklama aracı sizi, özel durumun oluştuğu ve olası düzeltmeleri araştırmanıza yardımcı olabilecek kodunuzda tam konuma götürebilir.

    Başka bir şey meydana gelirse, sorunun belirtisi nedir? Bu sorunun kodunuzda oluştuğu yerde zaten şüpheli mı? Örneğin, kodunuz bazı metinleri görüntülüyorsa, ancak metin yanlış ise, verilerinizin hatalı olduğunu veya görüntü metnini ayarlamış olan kodun bir tür hataya sahip olduğunu bilirsiniz. Bir hata ayıklayıcıdaki kodu düzenleyerek, değişkeninizdeki her değişikliği ve hatalı değerleri ne zaman ve nasıl atandığını fark edebilirsiniz.

## <a name="examine-your-assumptions"></a>Varsayımlarınızı inceleyin

Bir hatayı veya hatayı araştırmadan önce, belirli bir sonucu beklediğinizi düşünün. Gizli veya bilinmeyen varsayımlar, bir hata ayıklayıcıda sorun nedenlerini doğrudan ararken bile bir sorunu tanımlama yoluyla alabilir. Olası varsayımlara yönelik uzun bir listeniz olabilir! Aşağıda, varsayımlarınızı zorluk duymasını istemek için birkaç soru verilmiştir.

* Doğru API 'yi (yani, doğru nesne, işlev, yöntem veya özellik) kullanıyorsunuz musunuz? Kullandığınız bir API, ne olduğunu düşündüklerini yapamayabilir. (Hata ayıklayıcıda API çağrısını inceleyerek, doğru API 'yi belirlemesine yardımcı olmak için belgelere seyahat gerektirebilir.)

* API 'YI doğru bir şekilde kullanıyor musunuz? Doğru API 'YI kullanmış olabilirsiniz ancak doğru şekilde kullanmadınız.

* Kodunuz herhangi bir yazım hatası içeriyor mu? Bir değişken adının basit bir yanlış yazım hatası gibi bazı yazım hataları, özellikle, kullanılmadan önce değişkenlerin bildirilmesini gerektirmeyen dillerle birlikte çalışırken görülmesi zor olabilir.

* Kodunuzda bir değişiklik yaptınız ve gördüğünüz sorunla ilgili ilgisiz olduğunu varsaydınız mı?

* Gerçekten ne olduğunu belirten bir nesne veya değişkenin belirli bir değeri (veya belirli bir değer türünü) içermesini beklediğiniz istiyor muydunuz?

* Kodun amacını tanıyor musunuz? Başka birinin kodunun hata ayıklaması genellikle daha zordur. Kodunuz yoksa, etkin bir şekilde Hata ayıklayabilmeniz için öncelikle kodun ne yaptığını tam olarak öğreniyor olmanız gerekebilir.

    > [!TIP]
    > Kod yazarken, küçük bir başlangıç yapın ve çalıştıran kodla başlayın! (İyi örnek kod burada yararlı olur.) Bazen, elde etmek istediğiniz temel görevi gösteren küçük bir kod parçasıyla başlayarak büyük veya karmaşık bir kod kümesinin düzeltilmesi daha kolaydır. Ardından, her bir noktada hata için test etme, her bir noktada kod değiştirebilir veya test edebilirsiniz.

Varsayımlarınızı sorgarak kodunuzda bir sorun bulmak için geçen süreyi azaltabilirsiniz. Ayrıca bir sorunu çözmek için geçen süreyi de azaltabilirsiniz.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Sorunun nerede oluştuğunu bulmak için kodunuzda hata ayıklama moduna geçin

Bir uygulamayı normalde çalıştırdığınızda, yalnızca kod çalıştıktan sonra hatalar ve hatalı sonuçlar görürsünüz. Ayrıca, bir program neden sizi bildirmeden beklenmedik şekilde sonlandırılabilir.

Hata ayıklayıcı içinde, *hata ayıklama modu*olarak da adlandırılan bir uygulama çalıştırmak, hata ayıklayıcının program çalışırken meydana gelen her şeyi etkin bir şekilde izlediği anlamına gelir. Ayrıca, durumu incelemek için uygulamayı dilediğiniz zaman duraklatıp, ardından her ayrıntıyı olduğu gibi izlemek için kod satırlarınızın satıra göre ilerleyebileceğiniz bir işlem yapabilirsiniz.

Visual ![Studio 'da,](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") hata ayıklama moduna **F5** (veya Debug > **Start** **Debug** Menu komutunu veya Debug araç çubuğunda **hata ayıklamayı Başlat düğmesine basın** ) yazın. Herhangi bir özel durum oluşursa, Visual Studio 'nun özel durum Yardımcısı sizi özel durumun gerçekleştiği kesin noktaya götürür ve diğer yararlı bilgileri sağlar. Kodunuzda özel durumların nasıl işleneceği hakkında daha fazla bilgi için bkz. [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md).

Bir özel durum almadıysanız, büyük olasılıkla kodunuzda sorunu nerede aramanız gerektiği konusunda iyi bir fikir sahibi olabilirsiniz. Bu, kendinize kodunuzu daha dikkatli bir şekilde incelemenize olanak tanımak için hata ayıklayıcı ile *kesme noktaları* kullanırsınız. Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu duraklatıp, değişkenlerin değerlerine veya bellek davranışına ya da kodun çalıştığı diziye göz atabilmenizi sağlayacak şekilde belirtir.

Visual Studio 'da, bir kod satırının yanındaki sol kenar boşluğuna tıklayarak hızlı bir kesme noktası ayarlayabilirsiniz. Ya da imleci bir satıra yerleştirip **F9**tuşuna basın.

Bu kavramları göstermeye yardımcı olmak için, daha önce birkaç hata içeren bazı örnek kodlar aracılığıyla sizi ele aldık. Kullanıyoruz C#, ancak hata ayıklama özellikleri Visual Basic, C++, JavaScript, Python ve desteklenen diğer diller için geçerlidir.

### <a name="create-a-sample-app-with-some-bugs"></a>Örnek uygulama oluşturma (bazı hatalar ile)

Daha sonra, birkaç hata içeren bir uygulama oluşturacağız.

1. Oluşturmak istediğiniz uygulama türüne bağlı olarak, Visual Studio 'Nun yüklü olması ve **.net masaüstü geliştirme** iş yükü ya da **.NET Core platformlar arası geliştirme** iş yükü yüklemiş olmanız gerekir.

    Visual Studio 'Yu henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa Araçlar **ve Özellikler al** > **Araçlar** ' a tıklayın. Visual Studio Yükleyicisi'ni başlatır. **.Net masaüstü geliştirme** (veya **.NET Core platformlar arası geliştirme**) iş yükünü seçin ve ardından **Değiştir**' i seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde **Yeni proje oluştur**' u seçin. Arama kutusuna **konsolunu** yazın ve **konsol uygulaması (.NET Core)** ya da **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. **İleri**’yi seçin. **Consoleapp-FirstApp** gibi bir proje adı yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **konsol uygulaması**' nı seçin ve ardından Ortadaki bölmede **konsol uygulaması (.NET Framework)** veya **konsol uygulaması (.NET Core)** seçeneğini belirleyin. **Consoleapp-FirstApp** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması (.NET Framework)** veya **konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, Visual Studio yükleyicisi açan araçlar **ve Özellikler al** > **Araçlar** ' a gidin. **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    Visual Studio, sağ bölmedeki Çözüm Gezgini görüntülenen konsol projesini oluşturur.

1. *Program.cs*' de, tüm varsayılan kodu şu kodla değiştirin:

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }

            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };

                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }

                // Expected Output:
                //  Tadpole  400,  Spiral
                //  Pinwheel  25,  Spiral
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }

        public class Galaxy
        {
            public string Name { get; set; }

            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }

        }

        public class GType
        {
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Bu kod için bizim amacımız, Galaxy adını, Galaxy uzaklığını ve Galaxy türünün tümünü bir listede görüntülemektir. Hata ayıklamak için, kodun amacını anlamak önemlidir. Aşağıda, çıktıda göstermek istediğimiz listeden bir satır için biçim verilmiştir:

    *Galaxy adı*, *mesafe*, *Galaxy türü*.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

1. **F5** tuşuna basın veya hata **ayıklamayı Başlat** düğmesine, kod düzenleyicisinin üzerinde bulunan hata ayıklama araç çubuğunda ![hata ayıklamayı başlatın](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") .

    Uygulama başlar ve hata ayıklayıcı tarafından bizim için bir özel durum gösterilmez. Ancak, konsol penceresinde gördüğünüz çıktı beklediğiniz gibi değildir. Beklenen çıktı aşağıdaki gibidir:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ancak bunun yerine şu şekilde görüyoruz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Çıkışa ve kodumuza bakarak, `GType` Galaxy türünü depolayan sınıfın adı olduğunu biliyoruz. Gerçek Galaxy türünü (örneğin, "sarmal"), sınıf adını değil göstermeye çalışıyoruz!

### <a name="debug-the-app"></a>Uygulamada hata ayıklama

1. Uygulama çalışmaya devam ettiğinden, bu kod satırında `Console.WriteLine` yöntemi çağrısının yanındaki sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Kesme noktasını ayarladığınızda, sol kenar boşluğunda kırmızı bir nokta görünür.

    Çıktıda bir sorun görtiğimiz için, hata ayıklayıcıdaki çıktıyı ayarlayan önceki koda bakarak hata ayıklamaya başlayacağız.

1. Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

    Uygulama, ayarladığınız kesme noktasında duraklatılır. Sarı vurgulama, hata ayıklayıcının duraklatıldığını gösterir (sarı kod satırı henüz yürütülmemiştir).

1. Sağ tarafta `GalaxyType` değişkeninin üzerine gelin ve ardından İngiliz anahtarı simgesinin solunda `theGalaxy.GalaxyType`' ı genişletin. `GalaxyType` bir özellik `MyGType`içerdiğini ve özellik değerinin `Spiral`olarak ayarlandığını görürsünüz.

    ![Bir değişkeni inceleyin](../debugger/media/beginners-inspect-variable.png)

    "Sarmal" Aslında konsola yazdırmak beklediğiniz doğru değerdir! Bu nedenle, uygulamayı çalıştırırken bu kodda bu değere erişebiliyor olmanız iyi bir başlangıç. Bu senaryoda, yanlış API kullandık. Hata ayıklayıcıda kod çalıştırırken bunu çözebiliriz.

1. Aynı kodda, hala hata ayıklarken imlecinizi `theGalaxy.GalaxyType` sonuna koyun ve `theGalaxy.GalaxyType.MyGType`olarak değiştirin. Bu değişikliği yapabilseniz de, kod Düzenleyicisi bu kodu derleyemeyeceğini belirten bir hata gösterir.

    ![Söz dizimi hatası](../debugger/media/beginners-edit.png)

1. **Düzenle ve devam et** Ileti kutusunda **Düzenle** ' ye tıklayın. **Hata listesi** penceresinde şimdi bir hata mesajı görürsünüz. Hata, `'object'` `MyGType`tanımı içermediğini gösterir.

    ![Söz dizimi hatası](../debugger/media/beginners-no-definition.png)

    Her Galaxy 'u `GType` türünde bir nesneyle ayarladığımızda (`MyGType` özelliğine sahiptir), hata ayıklayıcı `theGalaxy` nesnesini `GType`türünde bir nesne olarak tanımaz. Ne var ne yok? Galaxy türünü ayarlayan herhangi bir koda bakmak istiyorsunuz. Bunu yaptığınızda, `GType` sınıfının kesinlikle bir `MyGType`özelliğine sahip olduğunu, ancak bir şey olmadığını görürsünüz. `object` hakkındaki hata iletisi Clue olarak açılır; Dil yorumlayıcısında tür, `GType`türünde bir nesne yerine `object` türünde bir nesne gibi görünür.

1. Galaxy türünü ayarlamayla ilgili kodunuza bakarak, `Galaxy` sınıfının `GalaxyType` özelliğini `GType`yerine `object` olarak bulabilirsiniz.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Yukarıdaki kodu şu şekilde değiştirin:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kodu yeniden derlemek ve yeniden başlatmak için hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

    Artık, hata ayıklayıcı `Console.WriteLine`durakladığında, `theGalaxy.GalaxyType.MyGType`üzerine geldiğinizde ve değerin düzgün şekilde ayarlandığını görebilirsiniz.

1. Sol kenar boşluğunda kesme noktası çemberuna tıklayarak kesme noktasını kaldırın (veya sağ **tıklayıp kesme noktası > kesme** **noktasını sil**' i seçin ve sonra devam etmek için **F5** ' e basın.

    Uygulama çalışır ve çıktıyı görüntüler. Şimdi oldukça iyi görünüyor, ancak bir şey fark edersiniz. Küçük Magellanic bulutu Galaxy 'nin konsol çıkışında düzensiz bir Galaxy olarak gösterilmesini bekliyorduk, ancak hiç Galaxy türü göstermemektedir.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Bu kod satırında bir kesme noktası ayarlayın.

    ```csharp
    public GType(char type)
    ```

    Bu kod, Galaxy türünün ayarlandığı, bu nedenle ona daha yakından bakmak istiyoruz.

1. Yeniden başlatmak için hata ayıklama araç çubuğundaki ![uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") **yeniden başlat** (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

    Hata ayıklayıcı, kesme noktasını ayarladığınız kod satırında duraklatılır.

1. `type` değişkeninin üzerine gelin. `S` (karakter kodundan sonra) bir değer görürsünüz. Düzensiz bir Galaxy türü olduğunu bildiğiniz için `I`bir değerle ilgileniyorsunuz.

1. **F5** tuşuna basın ve `type` değişkeninin üzerine gelin. `type` değişkeninde `I` bir değer görene kadar bu adımı yineleyin.

    ![Bir değişkeni inceleyin](../debugger/media/beginners-inspecting-data.png)

1. Şimdi **, hata ayıklama > ** **adımla** veya hata ayıklama araç çubuğundaki **adımla** **düğmesine basın.**

    **F11** hata ayıklayıcıyı ilerletir (ve kodu yürütür). **F10** (**Adımlama**), benzer bir komuttur ve her ikisi de hata ayıklayıcıyı nasıl kullanacağınızı öğrenirken son derece yararlıdır.

1. ' I ' değeri için `switch` deyimindeki kod satırında durana kadar **F11** tuşuna basın. Burada, bir typo 'dan kaynaklanan açık bir sorun görürsünüz. Kodun düzensiz bir Galaxy türü olarak `MyGType` ayarlandığı yere ilerletmesini bekletin, ancak bunun yerine hata ayıklayıcı bu kodu tamamen atlar ve `switch` bildiriminin `default` bölümünde duraklatılır.

    ![Yazım hatası bulma](../debugger/media/beginners-typo.png)

    Koda bakarak `case 'l'` bildiriminde bir yazım hatası görürsünüz. `case 'I'` olmalıdır.

1. `case 'l'` için koda tıklayın ve `case 'I'`ile değiştirin.

1. Kesme noktasını kaldırın ve ardından uygulamayı yeniden başlatmak için **Yeniden Başlat** düğmesine tıklayın.

    Hatalar Şimdi düzeltildi ve istediğiniz çıktıyı görürsünüz!

    Uygulamayı bitirebilmesi için herhangi bir tuşa basın.

## <a name="summary"></a>Özet

Bir sorun gördüğünüzde, sorun ile ilgili kod bölgesini bulmak için **F10** ve **F11** gibi bir hata ayıklayıcı ve [adım komutlarını](../debugger/navigating-through-code-with-the-debugger.md) kullanın.

> [!NOTE]
> Sorunun gerçekleştiği kod bölgesini belirlemek zordur, sorun gerçekleşmeden önce çalışan kodda bir kesme noktası ayarlayın ve ardından sorun bildirimini görene kadar adım komutlarını kullanın. Ayrıca, iletileri **Çıkış** penceresinde günlüğe kaydetmek için [izlenenoktaları](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) da kullanabilirsiniz. Günlüğe kaydedilen iletilere bakarak (ve yaşıyorsanız henüz günlüğe kaydedilmedi!), genellikle kod bölgesini sorun ile ayırabilirsiniz. Bunu daraltmak için bu işlemi birkaç kez tekrarlamanız gerekebilir.

Sorun ile ilgili kod bölgesini bulduğunuzda araştırmak için hata ayıklayıcıyı kullanın. Bir sorunun nedenini bulmak için, uygulamanızı hata ayıklayıcıda çalıştırırken sorun kodunu inceleyin:

* [Değişkenleri inceleyin](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) ve içerdikleri değer türlerini içerip içermediğini denetleyin. Hatalı bir değer bulursanız, bozuk değerin nerede ayarlandığını bulun (değerin nerede ayarlandığını bulmak için, hata ayıklayıcıyı yeniden başlatmanız, [çağrı yığınına](../debugger/how-to-use-the-call-stack-window.md)veya her ikisine birden bakmak) gerekebilir.

* Uygulamanızın beklediği kodu yürüttüğünü denetleyin. (Örneğin, örnek uygulamada, switch ifadesinin kodunu, Galaxy türünü düzensiz olarak ayarlamak için bekliyorduk, ancak uygulama, typo nedeniyle kodu atladı.)

> [!TIP]
> Hataları bulmanıza yardımcı olması için bir hata ayıklayıcı kullanırsınız. Hata ayıklama aracı yalnızca kodunuzun amacını biliyor durumunda *sizin için* hata bulabilir. Bir araç, geliştirici, bu amacı ifade eden yalnızca kodunuzun amacını bilir. [Birim testlerini](../test/improve-code-quality.md) yazmak bunu nasıl yapaöğreneceksiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, birkaç genel hata ayıklama kavramı öğrendiniz. Daha sonra, hata ayıklayıcı hakkında daha fazla bilgi edinmek için başlayabilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
