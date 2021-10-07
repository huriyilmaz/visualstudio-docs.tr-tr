---
title: Mutlak yeni başlayanlar için hata ayıklama kodu
description: İlk kez hata ayıklarsanız, uygulamalarınızı hata ayıklama modunda çalıştırmanıza yardımcı olacak birkaç ilkeyi Visual Studio
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d9fa7fd2c3d0a69f7a52fabc57fae54ee53ae688
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635574"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Mutlak yeni başlayanlar için hata ayıklama

Başarısız olmadan, yazılım geliştiricileri olarak yazacakları kod her zaman bekleneni yapmaz. Bazen tamamen farklı bir şey yapar! Bu olduğunda, bir sonraki görev bunun neden olduğunu çözmektir ve kodumuza saatler boyunca sürekli olarak ilgi göstermemiz gerekse de, hata ayıklama aracı veya hata ayıklayıcı kullanmak çok daha kolay ve verimlidir.

Ne yazık ki hata ayıklayıcı, kodumuzdaki tüm sorunları veya "hataları" sihirli bir şekilde ortaya çıkaran bir şey değil. *Hata ayıklama,* programlama hatasının tam olarak hangi noktada olduğunu bulmak için kodunuzu Visual Studio gibi bir hata ayıklama aracında adım adım çalıştırma anlamına gelir. Ardından kodunda hangi düzeltmeleri yapmak zorunda olduğunu anlarsınız ve hata ayıklama araçları genellikle programı çalıştırmaya devam etmek için geçici değişiklikler yapmanızı sağlar.

Hata ayıklayıcısını etkili bir şekilde kullanmak da öğrenmek için zaman ve uygulama gereken bir beceridir, ancak sonuçta her yazılım geliştiricisi için temel bir görevdir. Bu makalede, hata ayıklamanın temel ilkelerini tanıtıyor ve başlamanız için ipuçları sağlandı.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Kendinize doğru soruları sorarak sorunu netleştirin

Düzeltmeyi denemeden önce karşınıza geçen sorunu netleştirmeye yardımcı olur. Kodunda zaten bir sorunla karşınıza çıkmanızı bekliyoruz, aksi takdirde burada hata ayıklamayı bulmaya çalışmazsınız! Bu nedenle, hata ayıklamaya başlamadan önce çözmeye çalıştığın sorunu tanımlarken emin olun:

* Kodunuzun ne yapmalarını bekliyorsunuz?

* Bunun yerine ne oldu?

    Uygulamayı çalıştırma sırasında bir hata (özel durum) ile karşılaştınız, bu iyi bir şey olabilir! Özel durum, genellikle bir tür hata olan, kod çalıştırıldı sırasında karşılaşılan beklenmeyen bir olaydır. Hata ayıklama aracı sizi kodunda özel durumun meydana geldiği tam yere götürerek olası düzeltmeleri araştırmanıza yardımcı olabilir.

    Başka bir şey olduysa sorunun belirtisi nedir? Bu sorunun kodunda nerede meydana geldiğine zaten şüphe ediyor musunuz? Örneğin, kodunuz bazı metinler görüntülese ama metin yanlışsa, verilerinizin hatalı olduğunu veya görüntüleme metnini ayaran kodun bir tür hataya sahip olduğunu bilirsiniz. Hata ayıklayıcısındaki kodu adım adım inceler ve değişkenlerinize yapılan her değişikliği inceler ve yanlış değerlerin tam olarak ne zaman ve nasıl atandığı keşfedebilirsiniz.

## <a name="examine-your-assumptions"></a>Varsayımlarınızı inceleme

Bir hatayı veya hatayı araştırmadan önce, belirli bir sonuç beklediğinizi varsayımları düşünelim. Gizli veya bilinmeyen varsayımlar, bir hata ayıklayıcıda sorunun nedenini doğru bakarak bile bir sorunu belirleme yolunda olabilir. Olası varsayımların uzun bir listesiniz olabilir! Varsayımlarınızı ifade etmek için kendinize sormanız gereken birkaç soru vardır.

* Doğru API'yi (yani doğru nesne, işlev, yöntem veya özellik) kullanıyor musunuz? Kullanmakta olduğunuz API, yaptığı gibi bir şey yapmayabilirsiniz. (Hata ayıklayıcıda API çağrısını inceledikten sonra, bunu düzeltmek için doğru API'yi belirlemeye yardımcı olmak üzere belgelere bir yolculuk yapmak gerekli olabilir.)

* API'yi doğru kullanıyor musunuz? Doğru API'yi kullandı ama doğru şekilde kullanmadı da olabilir.

* Kodunuz yazım hatası içeriyor mu? Özellikle değişkenlerin kullanılmadan önce bildirillerini gerektirmeyen dillerle çalışırken, bir değişken adının basit yazım hatası gibi bazı yazım hatalarını görmek zor olabilir.

* Kodunuzda bir değişiklik yaptınız ve bu değişikliğin, karşınıza çıktı mı?

* Bir nesnenin veya değişkenin gerçekten olandan farklı bir değer (veya belirli bir değer türü) içermesi mi bekliyorsunuz?

* Kodun amacını biliyor musunuz? Başka birinin kodunda hata ayıklamak genellikle daha zordur. Kodunuz bu değilse, etkili bir şekilde hata ayıklamadan önce kodun tam olarak ne yaptığını öğrenmek için zaman harcamanız gerekebilirsiniz.

    > [!TIP]
    > Kod yazarken küçük bir başlangıç ve işe yarar bir kodla başlama! (İyi örnek kod burada yararlı olur.) Bazen, başarmaya çalıştığın temel görevi gösteren küçük bir kod parçasıyla başlayarak büyük veya karmaşık bir kod kümesi düzeltmek daha kolaydır. Ardından, her noktada hataları test etmek için artımlı olarak kod değiştirebilir veya eklersiniz.

Varsayımlarınızı sorgularken, kodunda bir sorun bulma süresini azaltabilirsiniz. Ayrıca, bir sorunu düzeltmek için gereken zamanı azaltabilirsiniz.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Sorunun nerede olduğunu bulmak için hata ayıklama modunda kodunuzun üzerinden geçin

Normalde bir uygulamayı çalıştırdıktan sonra hatalar ve yanlış sonuçlarla karşınız olur. Bir program size neden olduğunu söylemeden beklenmedik bir şekilde sonlandırılmayabilirsiniz.

Hata ayıklama modu olarak da adlandırılan bir hata ayıklayıcısı içinde bir uygulamanın çalıştırnıyor *olması,* hata ayıklayıcının program çalışır durumdayken olan her şeyi etkin bir şekilde izleyen anlamına gelir. Ayrıca uygulamayı herhangi bir noktada duraklatarak durumunu incelemenizi ve ardından her ayrıntıyı izlemek için kod satırınıza adım adım ilerler.

Bu Visual Studio **F5** kullanarak hata ayıklama moduna girersiniz (veya Hata Ayıklamayı Başlat hata ayıklama menü komutu veya Hata Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat  >   düğmesi).  ![](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") Herhangi bir özel durum oluşursa, Visual Studio Özel Durum Yardımcısı sizi özel durumun oluştuğu tam noktaya kadar alır ve diğer yararlı bilgileri sağlar. Kodundaki özel durumları işleme hakkında daha fazla bilgi için bkz. [Hata ayıklama teknikleri ve araçları.](../debugger/write-better-code-with-visual-studio.md)

Özel durumla ilgili bir durum elde etmeyebilirsiniz. Büyük olasılıkla kodunda sorunun nerede olduğunu öğrenebilirsiniz. Burada hata *ayıklayıcıyla kesme noktaları* kullanarak kodunuzu daha dikkatli inceleme fırsatınız olur. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya kodun çalışma sırasına bakabilirsiniz.

Bu Visual Studio, bir kod satırı yanındaki sol kenar boşluğuna tıklayarak hızla bir kesme noktası ayarlayın. Veya imleci bir satıra yerleştirerek **F9 tuşuna basın.**

Bu kavramların gösterildiğine yardımcı olmak için, zaten birkaç hataya sahip olan bazı örnek kodlar üzerinden sizi alıcaz. C# kullanıyoruz, ancak hata ayıklama özellikleri Visual Basic, C++, JavaScript, Python ve desteklenen diğer diller için geçerlidir. Örnek kod Visual Basic de sağlanır, ancak ekran görüntüleri C# içindedir.

### <a name="create-a-sample-app-with-some-bugs"></a>Örnek uygulama oluşturma (bazı hatalarla)

Ardından, birkaç hataya sahip bir uygulama oluşturacak.

1. .NET Core Visual Studio ve .NET Core platformlar arası geliştirme **iş yükünün yüklü** olması gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları **ve** Özellikleri  >  **Al'a tıklayın.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.** Arama **kutusuna** konsol yazın, dil olarak **C#** **Visual Basic** seçin ve ardından .NET Core için **Konsol** Uygulaması'nu seçin. **İleri**’yi seçin. ConsoleApp_FirstApp gibi **bir proje ConsoleApp_FirstApp'a** **tıklayın.**

    Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** veya **Visual Basic** altında Konsol Uygulaması'nu seçin ve orta bölmede Konsol Uygulaması **(.NET Core)** öğesini seçin. ConsoleApp_FirstApp gibi **bir ad yazın ve** Tamam'a **tıklayın.**
    ::: moniker-end

    .NET Core için Konsol Uygulaması **proje** şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve bu  >  işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

    Visual Studio, sağ bölmede görünen Çözüm Gezgini konsol projesini oluşturur.

1. *Program.cs (veya* *Program.vb)* içinde tüm varsayılan kodu aşağıdaki kodla değiştirin. (Önce C# veya Visual Basic. doğru dil sekmesini seçin.)

   #### <a name="c"></a>[C#](#tab/csharp)

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

   #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    Imports System
    Imports System.Collections.Generic

    Namespace ConsoleApp_FirstApp
        Friend Class Program
            Public Shared Sub Main(ByVal args As String())
                Console.WriteLine("Welcome to Galaxy News!")
                Call IterateThroughList()
                Console.ReadKey()
            End Sub

            Private Shared Sub IterateThroughList()
                Dim theGalaxies = New List(Of Galaxy) From {
                    New Galaxy() With {
                        .Name = "Tadpole",
                        .MegaLightYears = 400,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Pinwheel",
                        .MegaLightYears = 25,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Cartwheel",
                        .MegaLightYears = 500,
                        .GalaxyType = New GType("L"c)
                    },
                    New Galaxy() With {
                        .Name = "Small Magellanic Cloud",
                        .MegaLightYears = 0.2,
                        .GalaxyType = New GType("I"c)
                    },
                    New Galaxy() With {
                        .Name = "Andromeda",
                        .MegaLightYears = 3,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Maffei 1",
                        .MegaLightYears = 11,
                        .GalaxyType = New GType("E"c)
                    }
                }
    
                For Each theGalaxy As Galaxy In theGalaxies
                    Console.WriteLine(theGalaxy.Name & "  " & theGalaxy.MegaLightYears & ",  " & theGalaxy.GalaxyType)
                Next

            End Sub
        End Class
    
        Public Class Galaxy
            Public Property Name As String
            Public Property MegaLightYears As Double
            Public Property GalaxyType As Object
        End Class
    
        Public Class GType
    
            Shared Operator &(ByVal left As String, ByVal right As GType) As String
                Return New String(left & right.ToString())
            End Operator
            Public Sub New(ByVal type As Char)
                Select Case type
                    Case "S"c
                        MyGType = GType.Type.Spiral
                    Case "E"c
                        MyGType = GType.Type.Elliptical
                    Case "l"c
                        MyGType = GType.Type.Irregular
                    Case "L"c
                        MyGType = GType.Type.Lenticular
                    Case Else
                End Select
    
            End Sub
    
            Private _MyGType As String
            Public Property MyGType As Object
                Get
                    Return _MyGType
                End Get
                Set(ByVal value As Object)
                    _MyGType = value.ToString()
                End Set
            End Property
    
            Private Enum Type
                Spiral
                Elliptical
                Irregular
                Lenticular
            End Enum
        End Class
    End Namespace
    ```

    ---

    Bu kodun amacı, galaxy adını, galaxy ile olan mesafeyi ve galaxy türünün hepsini bir listede görüntülemektir. Hata ayıklamak için kodun amacını anlamak önemlidir. Çıkışta göstermek istediğiniz listeden bir satırın biçimi şu şekildedir:

    *galaxy name*, *distance*, *galaxy type*.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

1. F5 **tuşuna** basın **veya kod düzenleyicisinin** ![üzerinde bulunan](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") Hata Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın.

    Uygulama başlatılır ve hata ayıklayıcı tarafından bize gösterilen özel durumlar yoktur. Ancak konsol penceresinde gördüğünüz çıkış beklediğiniz gibi değildir. Beklenen çıkış şu şekildedir:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ancak bunun yerine şunları görüyoruz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Çıkışa bakarak kodumuza bakarak, bunun galaxy türünü depo alan `GType` sınıfın adı olduğunu biliyoruz. Sınıf adını değil gerçek galaxy türünü (örneğin ,"Galaxy" gibi) göstermeye çalışıyoruz!

### <a name="debug-the-app"></a>Uygulamada hata ayıklama

1. Uygulama hala çalışıyorken, bu kod satırına yöntem çağrısının yanındaki sol kenar `Console.WriteLine` boşluğuna tıklayarak bir kesme noktası ayarlayın.

    #### <a name="c"></a>[C#](#tab/csharp)

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    For Each theGalaxy As Galaxy In theGalaxies
        Console.WriteLine(theGalaxy.Name & "  " & theGalaxy.MegaLightYears & ",  " & theGalaxy.GalaxyType)
    Next
    ```

    ---
    Kesme noktasını ayarladığınızda, sol kenar boşluğunda kırmızı bir nokta görünür.

    Çıktıda bir sorun görtiğimiz için, hata ayıklayıcıdaki çıktıyı ayarlayan önceki koda bakarak hata ayıklamaya başlayacağız.

1. Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın.

    Uygulama, ayarladığınız kesme noktasında duraklatılır. Sarı vurgulama, hata ayıklayıcının duraklatıldığını gösterir (sarı kod satırı henüz yürütülmemiştir).

1. `GalaxyType`Sağ taraftaki değişkenin üzerine gelin ve ardından, İngiliz anahtarı simgesinin solunda öğesini genişletin `theGalaxy.GalaxyType` . `GalaxyType`Bir özellik içerdiğini `MyGType` ve özellik değeri olarak ayarlandığını görürsünüz `Spiral` .

    ![sarı renkli bir kod satırıyla Visual Studio hata ayıklayıcının ekran görüntüsü ve satırın sonundaki thegalaxy. galaxytype özelliğinin altında genişletilmiş bir menü.](../debugger/media/beginners-inspect-variable.png)

    "Sarmal" Aslında konsola yazdırmak beklediğiniz doğru değerdir! Bu nedenle, uygulamayı çalıştırırken bu kodda bu değere erişebiliyor olmanız iyi bir başlangıç. Bu senaryoda, yanlış API kullandık. Hata ayıklayıcıda kod çalıştırırken bunu çözebiliriz.

1. Aynı kodda, hala hata ayıklarken imlecinizi sonuna koyun `theGalaxy.GalaxyType` ve olarak değiştirin `theGalaxy.GalaxyType.MyGType` . Bu değişikliği yapabilseniz de, kod Düzenleyicisi bu kodu derleyemeyeceğini belirten bir hata gösterir. (Visual Basic, hatayı görmezsiniz ve kodun bu bölümü işe yarar)

    ![kırmızı renkte vurgulanmış bir kod satırıyla Visual Studio hata ayıklayıcının ekran görüntüsü ve düzenle ve devam et ileti kutusu seçili düzenle düğmesi seçili.](../debugger/media/beginners-edit.png)

   > [!NOTE]
   > Visual Basic örnek kodunda hata ayıklamak için, **yeniden başlat** ![uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") yeniden başlat düğmesine tıklayana kadar sonraki birkaç adımı atlayın.

1. **Düzenle ve devam et** Ileti kutusunda **Düzenle** ' ye tıklayın. **Hata listesi** penceresinde şimdi bir hata mesajı görürsünüz. Hata, öğesinin `'object'` için bir tanım içermediğini gösterir `MyGType` .

    ![kırmızı renkle vurgulanmış bir kod satırıyla Visual Studio hata ayıklayıcının ekran görüntüsü ve listede iki hata bulunan bir Hata Listesi penceresi.](../debugger/media/beginners-no-definition.png)

    Her Galaxy 'yi türünde bir nesne `GType` (özelliğine sahiptir) olarak ayarladığımızda `MyGType` , hata ayıklayıcı `theGalaxy` nesneyi türünde bir nesne olarak tanımıyor `GType` . Neler oluyor? Galaxy türünü ayarlayan herhangi bir koda bakmak istiyorsunuz. Bunu yaptığınızda, `GType` sınıfının özelliği kesinlikle olduğunu görürsünüz `MyGType` ancak bir şey doğru değildir. Bir hata iletisi, `object` Clue olmak üzere şu şekilde görünür; dil Yorumlayıcısına, türü türünde bir nesne yerine türünde bir nesne gibi görünüyor `object` `GType` .

1. Galaxy türünü ayarlamayla ilgili kodunuza bakarak, `GalaxyType` `Galaxy` sınıfının özelliği yerine olarak belirtilir `object` `GType` .

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Yukarıdaki kodu şu şekilde değiştirin:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kodu yeniden  ![](../debugger/media/dbg-tour-restart.png "RestartApp")   +    +  derlemek ve yeniden başlatmak için hata ayıklama araç çubuğundaki uygulamayı yeniden Başlat (CTRL SHIFT **F5**) düğmesine tıklayın.

    Artık hata ayıklayıcı üzerinde durakladığında, üzerine `Console.WriteLine` gelin `theGalaxy.GalaxyType.MyGType` ve değerin düzgün şekilde ayarlandığını görebilirsiniz.

1. Sol kenar boşluğunda kesme noktası çemberuna tıklayarak kesme noktasını kaldırın (veya sağ tıklayıp **kesme** noktası  >  **Sil kesme noktası**' nı seçin ve sonra devam etmek için **F5** ' e basın.

    Uygulama çalışır ve çıktıyı görüntüler. Şimdi oldukça iyi görünüyor, ancak bir şey fark edersiniz. Küçük Magellanic bulutu Galaxy 'nin konsol çıkışında düzensiz bir Galaxy olarak gösterilmesini bekliyorduk, ancak hiç Galaxy türü göstermemektedir.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Anahtar ifadesinden önce Bu kod satırında bir kesme noktası ayarlayın (Visual Basic içindeki SELECT ifadesinden önce).

    #### <a name="c"></a>[C#](#tab/csharp)

    ```csharp
    public GType(char type)
    ```

    #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    Public Sub New(ByVal type As Char)
    ```

    ---

    Bu kod, Galaxy türünün ayarlandığı, bu nedenle ona daha yakından bakmak istiyoruz.

1. Yeniden başlatmak için hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın.

    Hata ayıklayıcı, kesme noktasını ayarladığınız kod satırında duraklatılır.

1. Değişkenin üzerine gelin `type` . Bir değeri `S` (karakter kodundan sonra) görürsünüz. Öğesinin düzensiz bir Galaxy türü olduğunu bildiğiniz için bir değeriyle ilgileniyorsunuz `I` .

1. **F5** tuşuna basın ve değişkenin üzerine gelin `type` . Değişkende bir değer görene kadar bu adımı yineleyin `I` `type` .

    ![Visual Studio hata ayıklayıcının, sarı renkli bir kod satırı ve tür değişkeninin değerini 73 ' I ' olarak gösteren küçük bir pencere görüntüsü.](../debugger/media/beginners-inspecting-data.png)

1. Şimdi, hata ayıklama araç çubuğundaki **F11** (**Hata Ayıkla**  >  **adımla** veya **adımla** düğmesine basın) tuşuna basın.

    **F11** hata ayıklayıcıyı ilerletir (ve kodu yürütür). **F10** (**Adımlama**), benzer bir komuttur ve her ikisi de hata ayıklayıcıyı nasıl kullanacağınızı öğrenirken son derece yararlıdır.

1.  `switch` ' I ' değeri (Visual Basic için olan) için deyimdeki kod satırında durana kadar F11 tuşuna basın `Select` . Burada, bir typo 'dan kaynaklanan açık bir sorun görürsünüz. Kodun düzensiz bir Galaxy türü olarak ayarlandığı yere ilerletmesini bekliyorduk `MyGType` , ancak hata ayıklayıcı bunun yerine bu kodu tamamen atlar ve `default` `switch` deyimin bölümünde ( `Else` Visual Basic bildiri) duraklatılır.

    ![Yazım hatası bulma](../debugger/media/beginners-typo.png)

    Koda bakarak, bildiriminde bir yazım hatası görürsünüz `case 'l'` . `case 'I'` olmalıdır.

1. Kodunda öğesine tıklayın `case 'l'` ve bunu ile değiştirin `case 'I'` .

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
