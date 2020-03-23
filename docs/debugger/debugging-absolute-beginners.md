---
title: Mutlak yeni başlayanlar için hata ayıklama kodu
description: İlk kez hata ayıklama ediyorsanız, Visual Studio ile uygulamanızı hata ayıklama modunda çalıştırmanıza yardımcı olacak birkaç ilke öğrenin
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416404"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Mutlak yeni başlayanlar için hata ayıklama nasıl

Başarısız olmadan, yazılım geliştiricileri olarak yazdığımız kod her zaman beklediğimiz şeyi yapmaz. Bazen tamamen farklı bir şey yapar! Bu durumda, bir sonraki görev nedenini anlamaktır ve kodumuza saatlerce bakmaya devam etmek cazip olsada, hata ayıklama aracı nı veya hata ayıklayıcıyı kullanmak çok daha kolay ve verimlidir.

Bir hata ayıklayıcı, ne yazık ki, sihirli bizim kod tüm sorunları veya "hataları" ortaya çıkarabilir bir şey değildir. *Hata ayıklama,* bir programlama hatası yaptığınız tam noktayı bulmak için Visual Studio gibi bir hata ayıklama aracında kodunuzu adım adım çalıştırmak anlamına gelir. Daha sonra, kodunuzda yapmanız gereken düzeltmeleri anlarsınız ve hata ayıklama araçları genellikle programı çalıştırmaya devam edebilmeniz için geçici değişiklikler yapmanıza olanak sağlar.

Etkili bir hata ayıklama kullanarak da öğrenmek için zaman ve uygulama alır ama sonuçta her yazılım geliştiricisi için temel bir görevdir bir beceridir. Bu makalede, daha sonra, hata ayıklama temel ilkelerini tanıtmak ve başlamak için ipuçları sağlar.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Kendinize doğru soruları sorarak sorunu açıklığa kavuşturun

Düzeltmeye çalışmadan önce karşılaştığınız sorunu açıklığa kavuşturmaya yardımcı olur. Kodunuzda zaten bir sorunla karşılaştığınızı bekliyoruz, aksi takdirde burada nasıl hata ayıklama yapacağınızı anlamaya çalışmazsınız! Bu nedenle, hata ayıklamaya başlamadan önce, çözmeye çalıştığınız sorunu tanımladığınızdan emin olun:

* Kodunuzu ne yapmasını bekliyordunuz?

* Onun yerine ne oldu?

    Uygulamanızı çalıştırırken bir hata (özel durum) ile karşılaştıysanız, bu iyi bir şey olabilir! Özel durum, genellikle bir tür hata olan kod çalıştırırken karşılaşılan beklenmeyen bir olaydır. Hata ayıklama aracı sizi kodunuzun özel durum oluştuğu yere götürebilir ve olası düzeltmeleri araştırmanıza yardımcı olabilir.

    Başka bir şey olduysa, sorunun belirtisi nedir? Bu sorunun kodunuzda nerede oluştuğundan zaten şüpheleniyor musunuz? Örneğin, kodunuz bir metin görüntüleniyorsa, ancak metin yanlışsa, verilerinizin kötü olduğunu veya görüntü metnini ayarlayan kodun bir tür hatası olduğunu bilirsiniz. Hata ayıklayıcıdaki kodu karıştırarak, değişkenlerinizdeki her değişikliği inceleyerek tam olarak ne zaman ve nasıl yanlış değerlere atandığını keşfedebilirsiniz.

## <a name="examine-your-assumptions"></a>Varsayımlarınızı inceleyin

Bir hatayı veya hatayı araştırmadan önce, belirli bir sonuç beklemenizi sağlayan varsayımları düşünün. Gizli veya bilinmeyen varsayımlar, hata ayıklayıcıda sorunun nedenine doğru baktığınızda bile bir sorunu tanımlamanın önüne çıkabilir. Olası varsayımlar uzun bir liste olabilir! Varsayımlarınıza meydan okumak için kendinize sormanız gereken birkaç soru aşağıda verilmiştir.

* Doğru API'yi (yani doğru nesneyi, işlevi, yöntemi veya özelliği) mi kullanıyorsunuz? Kullandığınız bir API, düşündüğünüz şeyi yapmayabilir. (Hata ayıklamadaki API çağrısını inceledikten sonra, doğru API'yi belirlemeye yardımcı olmak için belgelere bir yolculuk gerekebilir.)

* API'yi doğru mu kullanıyorsunuz? Belki doğru API kullanılan ama doğru şekilde kullanmadı.

* Kodunuz yazım hataları içeriyor mu? Değişken adının basit bir yazım hatası gibi bazı yazım hatalarının, özellikle kullanılmadan önce bildirilmesi gerekmeyen değişkenlerle çalışırken görülmesi zor olabilir.

* Kodunuzda bir değişiklik yaptınız mı ve bunun gördüğünüz sorunla ilgisi olmadığını varsaydınız mı?

* Bir nesnenin veya değişkenin gerçekte olandan farklı belirli bir değer (veya belirli bir değer türü) içermesini mi bekliyordunuz?

* Kodun amacını biliyor musun? Başka birinin kodunu ayıklamak genellikle daha zordur. Kodunuz bu değilse, kodu etkili bir şekilde hata ayıklamadan önce kodun tam olarak ne yaptığını öğrenmek için zaman harcamanız gerekebilir.

    > [!TIP]
    > Kod yazarken, küçük başlayın ve çalışan kod ile başlayın! (İyi örnek kod burada yararlıdır.) Bazen, ulaşmaya çalıştığınız temel görevi gösteren küçük bir kod parçasıyla başlayarak büyük veya karmaşık bir kod kümesini düzeltmek daha kolaydır. Ardından, her noktada hataları test ederek kodu artımlı olarak değiştirebilir veya ekleyebilirsiniz.

Varsayımlarınızı sorgulayarak, kodunuzda bir sorun bulmak için gereken süreyi azaltabilirsiniz. Ayrıca, bir sorunu gidermek için gereken süreyi azaltabilirsiniz.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Sorunun nerede oluştuğunu bulmak için hata ayıklama modunda kodunuzu gözden geçirin

Normalde bir uygulamayı çalıştırdığınızda, hataları ve yanlış sonuçları yalnızca kod çalıştırdıktan sonra görürsünüz. Bir program da size nedenini söylemeden beklenmedik bir şekilde sonlandırabilir.

Hata ayıklama modu olarak da adlandırılan bir hata ayıklama içinde bir uygulamayı çalıştırmak, hata *ayıklamanın*program çalışırken gerçekleşen her şeyi etkin olarak izlediği anlamına gelir. Ayrıca, uygulamayı durumunu incelemek için herhangi bir noktada duraklatmanızı ve ardından her ayrıntıyı izlemek için kodunuzu satır satır basmanızı sağlar.

Visual Studio'da, **Hata** Ayıklama Aracı Çubuğu'nda Hata **Ayıklama** > Menüsü komutu veya **Hata Ayıklama** ![Başlatma](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklama'yı Başlatma") düğmesi kullanarak hata ayıklama moduna girersiniz.**Start Debugging** Herhangi bir özel durum oluşursa, Visual Studio'nun Özel Durum Yardımcısı sizi özel durum oluştuğu noktaya götürür ve diğer yararlı bilgiler sağlar. Kodunuzdaki özel durumları nasıl işlerek hakkında daha fazla bilgi için Hata [Ayıklama teknikleri ve araçlarına](../debugger/write-better-code-with-visual-studio.md)bakın.

Bir özel durum almadıysanız, büyük olasılıkla kodundaki sorunu nerede arayacağınız hakkında iyi bir fikriniz vardır. Kodunuzu daha dikkatli incelemek için kendinize bir şans vermek için hata ayıklayıcıile *kesme noktalarını* kullandığınız yerburasıdır. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede duraklatması gerektiğini gösterir, böylece değişkenlerin değerlerine, belleğin davranışına veya kodun çalıştığı sıraya göz atabilirsiniz.

Visual Studio'da, bir kod satırının yanındaki sol kenar boşluğuna tıklayarak hızlı bir şekilde bir kesme noktası ayarlayabilirsiniz. Veya imleci bir çizgiye yerleştirin ve **F9**tuşuna basın.

Bu kavramları niçin gösterdiğimizi göstermek için, sizi zaten birkaç hata içeren bazı örnek kodlara götürüruz. C# kullanıyoruz, ancak hata ayıklama özellikleri Visual Basic, C++, JavaScript, Python ve diğer desteklenen diller için geçerlidir.

### <a name="create-a-sample-app-with-some-bugs"></a>Örnek bir uygulama oluşturma (bazı hatalarla)

Ardından, birkaç hata içeren bir uygulama oluşturacağız.

1. Oluşturmak istediğiniz uygulama türüne bağlı olarak Visual Studio yüklü olmalı ve **.NET masaüstü geliştirme** iş yükü veya **.NET Core çapraz platform geliştirme** iş yükü yüklü olmalıdır.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'nuz varsa, **Araçlar** > **Araçları ve Özellikleri Al'ı**tıklatın. Visual Studio Installer başlattı. **.NET masaüstü geliştirme** (veya **.NET Core çapraz platform geliştirme)** iş yükünü seçin ve ardından **Değiştir'i**seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde yeni **bir proje oluştur'u**seçin. Arama kutusuna **konsol** yazın ve ardından **Konsol Uygulaması (.NET Core)** veya **Konsol Uygulaması 'nı (.NET Framework)** seçin. **İleri**’yi seçin. **ConsoleApp-FirstApp** gibi bir proje adı yazın ve **Oluştur'a**tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **Konsol Uygulaması'nı**seçin ve orta bölmede Konsol **Uygulaması (.NET Framework)** veya **Konsol Uygulaması (.NET Core)** seçeneğini belirleyin. **ConsoleApp-FirstApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

    **Konsol Uygulaması (.NET Framework)** veya Console **App (.NET Core)** proje şablonu görmüyorsanız, Visual Studio Installer'ı açan **Araçlar** > **Araçları ve Özellikleri Al'a**gidin. **.NET Core çapraz platform geliştirme** veya **.NET masaüstü geliştirme iş** yükünü seçin ve sonra **Değiştir'i**seçin.

    Visual Studio, sağ bölmede Solution Explorer'da görünen konsol projesini oluşturur.

1. *Program.cs,* tüm varsayılan kodu aşağıdaki kodla değiştirin:

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

    Bu kod için amacımız galaksinin adını, galaksiye olan uzaklığı ve galaksi türünü bir listede göstermektir. Hata ayıklama için, kodun amacını anlamak önemlidir. Çıktıda göstermek istediğimiz listeden bir satırın biçimi aşağıda veda edebilirsiniz:

    *galaksi adı*, *mesafe*, *galaksi türü*.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Kod düzenleyicisinin üzerinde bulunan Hata ![Ayıklama](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklama'yı Başlatma") Araç Çubuğu'nda Hata Ayıklama Başlat düğmesine veya **F5'e** veya **Başlangıç Hata Ayıklama** düğmesine basın.

    Uygulama başlar ve hata ayıklama tarafından bize gösterilen hiçbir istisna yoktur. Ancak, konsol penceresinde gördüğünüz çıktı beklediğiniz gibi değildir. İşte beklenen çıktı:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ama bunun yerine şunu görüyoruz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Çıktıya ve kodumuza baktığımızda galaksi `GType` türünü depolayan sınıfın adının bu olduğunu biliyoruz. Biz gerçek galaksi türünü göstermeye çalışıyoruz (örneğin"Spiral"), sınıf adını değil!

### <a name="debug-the-app"></a>Uygulamayı hata ayıklama

1. Uygulama hala çalışıyorken, bu kod satırındaki `Console.WriteLine` yöntem çağrısının yanındaki sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Kesme noktasını ayarladığınızda, sol kenar boşluğunda kırmızı bir nokta belirir.

    Çıktıda bir sorun gördüğümüzden, hata ayıklayıcıda çıktıyı ayarlayan önceki koda bakarak hata ayıklamaya başlarız.

1. Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl** + **Shift** + **F5)** Uygulamayı Yeniden **Başlat** ![Restart App](../debugger/media/dbg-tour-restart.png "Yeniden BaşlatApp") düğmesini tıklatın.

    Uygulama ayarladığınız kesme noktasında duraklar. Sarı vurgulama, hata ayıklayıcının duraklatılmış olduğu yeri gösterir (sarı kod satırı henüz yürütülmedi).

1. Sağdaki değişkenin `GalaxyType` üzerine dokunun ve ardından anahtar simgesinin solunda genişleyin. `theGalaxy.GalaxyType` Bir özellik `GalaxyType` `MyGType`içerdiğini ve özellik değerinin `Spiral`.

    ![Bir değişkeni inceleyin](../debugger/media/beginners-inspect-variable.png)

    "Spiral" aslında konsola yazdırmayı beklediğiniz doğru değerdir! Bu nedenle, uygulamayı çalıştırırken bu koddaki bu değere erişebilmeniz iyi bir başlangıçtır. Bu senaryoda, yanlış API kullanıyoruz. Hata ayıklayıcıda kod çalıştırırken bunu düzeltip düzeltebileceğimizi göreceğiz.

1. Aynı kodda, hata ayıklama devam ederken, sonuna imleci `theGalaxy.GalaxyType` koyun ve `theGalaxy.GalaxyType.MyGType`değiştirin. Bu değişikliği yapabiliyor olsanız da, kod düzenleyicisi bu kodu derleyedileremediğinizi belirten bir hata gösterir.

    ![Sözdizimi hatası](../debugger/media/beginners-edit.png)

1. **Edit ve Devam** ileti kutusunda **Edit'i** tıklatın. **Şimdi Hata Listesi** penceresinde bir hata iletisi görüyorsunuz. Hata, `MyGType`'' `'object'` için bir tanım içermediğini gösterir.

    ![Sözdizimi hatası](../debugger/media/beginners-no-definition.png)

    Her galaksiyi `GType` bir tür nesnesi `MyGType` (özelliği olan) ayarlasak da, `theGalaxy` hata ayıklayan `GType`nesneyi bir tür nesnesi olarak tanımaz. Neler oluyor? Galaksi tipini belirleyen herhangi bir koda bakmak istiyorsun. Bunu yaptığınızda, `GType` sınıfın kesinlikle bir özelliği olduğunu `MyGType`görürsünüz, ancak bir şeyler doğru değildir. Hakkında `object` hata mesajı ipucu olduğu ortaya çıkıyor; dil yorumlayıcısına, tür türünden `object` `GType`bir nesne yerine tür nesnesi gibi görünür.

1. Galaksi türünü ayarlama ile ilgili kodunuzu `GalaxyType` incebaktığınızda, `Galaxy` sınıfın özelliğinin `object` `GType`"" yerine " olarak belirtildiğini görürüz.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Önceki kodu şu şekilde değiştirin:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kodu yeniden derlemek ve yeniden başlatmak için Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl** + **Shift** + **F5)** Uygulamayı **Yeniden Başlat** ![Restart App](../debugger/media/dbg-tour-restart.png "Yeniden BaşlatApp") düğmesini tıklatın.

    Şimdi, hata ayıklama `Console.WriteLine`duraklatıldığında, üzerinde `theGalaxy.GalaxyType.MyGType`gezinebilir ve değerin düzgün ayarlı olduğunu görebilirsiniz.

1. Sol kenar boşluğundaki kesme noktası çemberine tıklayarak kesme noktasını kaldırın (veya sağ tıklatın ve **Breakpoint** > **Delete Breakpoint'i**seçin ) ve devam etmek için **F5** tuşuna basın.

    Uygulama çalışır ve çıktı görüntüler. Şimdi oldukça iyi görünüyor, ama bir şey fark yok; Küçük Macellan Bulutu galaksisinin konsol çıkışında düzensiz bir gökada olarak ortaya çıkmasını bekliyordunuz, ama hiç galaksi tipi göstermiyor.

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

    Bu kod galaksi tipinin ayarlandığı yerdir, bu yüzden ona daha yakından bakmak istiyoruz.

1. Yeniden **başlatmak** için Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl** + **Shift** + **F5)** Uygulamayı ![Yeniden Başlat](../debugger/media/dbg-tour-restart.png "Yeniden BaşlatApp") düğmesini tıklatın.

    Hata ayıklayıcı, kesme noktasını ayarladığınız kod satırında duraklar.

1. Değişkenin üzerine `type` titre. Bir değer `S` (karakter kodunu izleyerek) görürsünüz. Düzensiz bir galaksi türü `I`olduğunu bildiğiniz için bir değerle ilgileniyorsunuz.

1. **F5 tuşuna** basın `type` ve değişkenin üzerine tekrar basın. `I` Değişkende bir değer görene `type` kadar bu adımı tekrarlayın.

    ![Bir değişkeni inceleyin](../debugger/media/beginners-inspecting-data.png)

1. Şimdi, Hata Ayıklama Araç Çubuğu'nda **F11** **(Hata Ayıklama** > **Adım** veya Hata Ayıklama Araç Çubuğu'nda **Adım adım)** düğmesine basın.

    **F11** hata ayıklayıcıyı (ve kodu yürütür) aynı anda bir deyimi ilerler. **F10** (**Step Over**) benzer bir komutdur ve her ikisi de hata ayıklama nın nasıl kullanılacağını öğrenirken son derece yararlıdır.

1. `switch` 'I' değeri için deyimdeki kod satırında duruncaya kadar **F11** tuşuna basın. Burada, yazım hatasından kaynaklanan açık bir sorun görürsünüz. Kodun Düzensiz gökada türü olarak `MyGType` ayarlandığı yere ilerlemesini bekliyordunuz, ancak hata ayıklayıcı bunun yerine `default` bu `switch` kodu tamamen atlar ve deyimin bölümünde duraklar.

    ![Yazım hatası bul](../debugger/media/beginners-typo.png)

    Koda baktığınızda, ifadede `case 'l'` bir yazım hatası görüyorsunuz. `case 'I'` olmalıdır.

1. Kodu tıklatın `case 'l'` ve `case 'I'`değiştirin.

1. Kesme noktanızı kaldırın ve uygulamayı yeniden başlatmak için **Yeniden Başlat** düğmesini tıklatın.

    Hatalar şimdi sabit ve beklediğiniz Çıktı bakın!

    Uygulamayı bitirmek için herhangi bir tuşa basın.

## <a name="summary"></a>Özet

Bir sorun gördüğünüzde, sorunla birlikte kod bölgesini bulmak için Hata ayıklayıcı ve **F11** gibi hata ayıklayıcı ve [adım komutlarını](../debugger/navigating-through-code-with-the-debugger.md) kullanın. **F11**

> [!NOTE]
> Sorunun oluştuğu kod bölgesini tanımlamak zorsa, sorun oluşmadan önce çalışan kodda bir kesme noktası ayarlayın ve sorun bildirimini görene kadar adım komutlarını kullanın. İletileri **Çıkış** penceresine günlüğe kaydetmek için [izleme noktalarını](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) da kullanabilirsiniz. Günlüğe kaydedilmiş iletilere bakarak (ve hangi iletilerin henüz günlüğe kaydolmadığını fark ederek!), genellikle sorunla kod bölgesini yalıtabilirsiniz. Daraltmak için bu işlemi birkaç kez yinelemeniz gerekebilir.

Sorunla birlikte kod bölgesini bulduğunuzda, araştırmak için hata ayıklayıcıyı kullanın. Bir sorunun nedenini bulmak için, hata ayıklayıcıda uygulamanızı çalıştırırken sorun kodunu inceleyin:

* [Değişkenleri inceleyin](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) ve içermeleri gereken değerlerin türünü içerip içermediklerini denetleyin. Kötü bir değer bulursanız, kötü değerin nerede ayarlandığını öğrenin (değerin nerede ayarlandığını bulmak için hata ayıklayıcıyı yeniden başlatmanız, [arama yığınına](../debugger/how-to-use-the-call-stack-window.md)veya her ikisine bakmanız gerekebilir).

* Uygulamanızın beklediğiniz kodu yürütüp yürütmediğini denetleyin. (Örneğin, örnek uygulamada, anahtar deyiminin kodunun gökada türünü Düzensiz olarak ayarlamasını bekliyorduk, ancak uygulama yazım hatası nedeniyle kodu atladı.)

> [!TIP]
> Hataları bulmanıza yardımcı olmak için hata ayıklama kullanırsınız. Hata ayıklama aracı, yalnızca kodunuzu kullanma amacını biliyorsa *hataları sizin için* bulabilir. Bir araç, yalnızca geliştirici olarak bu amacı ifade ederseniz, kodunuzu niçin bildiğini bilebilir. [Birim testleri](../test/improve-code-quality.md) yazmak bunu nasıl yaptığınızdır.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, birkaç genel hata ayıklama kavramları öğrendim. Ardından, hata ayıklama hakkında daha fazla bilgi edinmeye başlayabilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
