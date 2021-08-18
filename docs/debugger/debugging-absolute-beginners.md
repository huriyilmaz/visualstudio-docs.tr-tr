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
ms.openlocfilehash: d7285648ad1cb9f93dd11f5374f1eb2cf8ecbfdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065786"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Mutlak yeni başlayanlar için hata ayıklama

Başarısız olmadan, yazılım geliştiricileri olarak yazacakları kod her zaman bekleneni yapmaz. Bazen tamamen farklı bir şey yapar! Bu olduğunda, bir sonraki görev bunun neden olduğunu çözmektir ve kodumuza saatler boyunca sürekli olarak ilgi göstermemiz istnse de hata ayıklama aracı veya hata ayıklayıcı kullanmak çok daha kolay ve verimlidir.

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

* Doğru API'yi mi (yani doğru nesneyi, işlevi, yöntemi veya özelliği) kullanıyor musunuz? Kullanmakta olduğunuz API, yaptığı gibi bir şey yapmayabilirsiniz. (Hata ayıklayıcıda API çağrısını inceledikten sonra, bunu düzeltmek için doğru API'yi belirlemeye yardımcı olmak üzere belgelere bir yolculuk yapmak gerekli olabilir.)

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

Bu Visual Studio **F5** kullanarak hata ayıklama moduna girersiniz (veya Hata Ayıklamayı Başlat hata ayıklama menü komutu veya Hata Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat  >   düğmesi).  ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Herhangi bir özel durum oluşursa, Visual Studio Özel Durum Yardımcısı sizi özel durumun oluştuğu tam noktaya kadar alır ve diğer yararlı bilgileri sağlar. Kodundaki özel durumları işleme hakkında daha fazla bilgi için bkz. [Hata ayıklama teknikleri ve araçları.](../debugger/write-better-code-with-visual-studio.md)

Özel durumla ilgili bir durumla ilgili bir fikir elde etmeyebilirsiniz. Kodda sorunun nerede olduğunu öğrenebilirsiniz. Burada hata *ayıklayıcıyla kesme noktaları* kullanarak kodunuzu daha dikkatli inceleme fırsatınız olur. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya kodun çalışma sırasına göz atmak için çalışan kodunuzu nerede duraklatmak gerektiğini gösterir.

Bu Visual Studio, bir kod satırı yanındaki sol kenar boşluğuna tıklayarak hızla bir kesme noktası ayarlayın. Veya imleci bir satıra yerleştirerek **F9 tuşuna basın.**

Bu kavramların gösterildiğine yardımcı olmak için, zaten birkaç hataya sahip olan bazı örnek kodlar üzerinden sizi alıcaz. C# kullanıyoruz ancak hata ayıklama özellikleri Visual Basic, C++, JavaScript, Python ve diğer desteklenen diller için geçerlidir. Örnek kod Visual Basic, ancak ekran görüntüleri C# içindedir.

### <a name="create-a-sample-app-with-some-bugs"></a>Örnek uygulama oluşturma (bazı hatalarla)

Ardından, birkaç hataya sahip bir uygulama oluşturacak.

1. .NET Core Visual Studio ve .NET Core platformlar arası geliştirme **iş yükünün yüklü** olması gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları **ve** Özellikleri  >  **Al'a tıklayın.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.** Arama **kutusuna** konsol yazın, dil olarak **C#** **Visual Basic** seçin ve ardından .NET Core için **Konsol** Uygulaması'nu seçin. **İleri**’yi seçin. ConsoleApp_FirstApp gibi **bir proje ConsoleApp_FirstApp'a** **tıklayın.**

    Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** veya **Visual Basic** altında Konsol Uygulaması'nu seçin ve orta bölmede Konsol Uygulaması **(.NET Core)** öğesini seçin.  ConsoleApp_FirstApp gibi **bir ad yazın ve** Tamam'a **tıklayın.**
    ::: moniker-end

    .NET Core için Konsol Uygulaması **proje** şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve bu  >  işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

    Visual Studio, sağ bölmede yer alan Çözüm Gezgini konsol projesini oluşturur.

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

1. Kod düzenleyicisinin üzerinde bulunan ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **Hata Ayıklama Araç Çubuğunda** **F5'e** veya Hata Ayıklamayı Başlat düğmesine Hata Ayıklamayı Başlat'a basın.

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

    Çıkışa bakarak kodumuza bakarak, bunun galaxy türünü depo alan `GType` sınıfın adı olduğunu biliyoruz. Gerçek galaxy türünü (örneğin, sınıf adını değil ,"Galaxy" gibi) göstermeye çalışıyoruz!

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
    Kesme noktası ayarlendiğinde, sol kenar boşluğunda kırmızı bir nokta görünür.

    Çıkışta bir sorun gördüğünüzden, hata ayıklayıcıda çıkışı ayaranın önceki koduna bakarak hata ayıklamaya başlayacağız.

1. Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") Yeniden Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

    Uygulama, ayar istediğiniz kesme noktası üzerinden duraklatılır. Sarı vurgulama, hata ayıklayıcının nerede duraklatılmış olduğunu gösterir (sarı kod satırı henüz yürütülmedi).

1. Sağ tarafta `GalaxyType` değişkenin üzerine gelin ve ardından İngiliz anahtarı simgesinin sol tarafından `theGalaxy.GalaxyType` genişletin. özelliğini `GalaxyType` içerdiğini ve `MyGType` özellik değerinin olarak ayar olduğunu `Spiral` görüyorsunuz.

    ![Satır sonundakiGalaxy.GalaxyType özelliğinin altına genişletilmiş sarı bir kod satırı ve bir menü ile birlikte Visual Studio Debugger'ın ekran görüntüsü.](../debugger/media/beginners-inspect-variable.png)

    Konsola yazdırmayı beklediğiniz doğru değer aslında "Xbox" değeridir! Bu nedenle, uygulamayı çalıştırarak bu kodda bu değere erişebilirsiniz. Bu senaryoda yanlış API'yi kullanıyoruz. Hata ayıklayıcıda kod çalışırken bunu düzeltebilir olup olamayacaklarını göreceğiz.

1. Aynı kodda hata ayıklamaya devam ederken imlecinizi sonuna yerleştirerek `theGalaxy.GalaxyType` olarak `theGalaxy.GalaxyType.MyGType` değiştirebilirsiniz. Bu değişikliği yapmakla birlikte, kod düzenleyicisi size bu kodu derleyemiyor olduğunu belirten bir hata gösterir. (Visual Basic'da hatayı göresiniz ve bu kod bölümü çalışır)

    ![Hata Ayıklayıcısı Visual Studio kırmızı renkle vurgulanmış bir kod satırı ve Düzenle düğmesinin seçili olduğu Düzenle ve Devam Et ileti kutusunun ekran görüntüsü.](../debugger/media/beginners-edit.png)

   > [!NOTE]
   > Örnek kodda Visual Basic ayıklamak için, Uygulamayı Yeniden Başlat düğmesine tıklamanız gerekene kadar **sonraki birkaç** ![adımı atlayabilirsiniz.](../debugger/media/dbg-tour-restart.png "RestartApp")

1. Düzenle **ve** Devam **Değiştir ileti kutusunda Düzenle'ye** tıklayın. Şimdi Hata Listesi penceresinde bir **hata iletisi** görüyorsunuz. Hata, için `'object'` bir tanım içere olmadığını `MyGType` gösterir.

    ![Hata Ayıklayıcısı Visual Studio kırmızı renkle vurgulanmış bir kod satırı ve iki hatanın listelenmiş olduğu Hata Listesi penceresinin ekran görüntüsü.](../debugger/media/beginners-no-definition.png)

    Her bir galaxyyi türünde (özelliğine sahip olan) bir nesneyle ayarlasanız da, hata ayıklayıcı nesneyi türünde `GType` `MyGType` bir nesne olarak `theGalaxy` `GType` tanımaz. Neler oluyor? Galaxy türünü ayaran tüm kodlara göz atabilirsiniz. Bunu yapmak için sınıfının kesinlikle özelliğine sahip olduğunu `GType` ancak bir şeyin doğru olmadığını `MyGType` görüyorsunuz. ile ilgili hata iletisi ipucu olarak görünür. Dil yorumlayıcıya göre tür, türünde bir nesne yerine türünde bir `object` `object` nesne gibi `GType` görünür.

1. Galaxy türünü ayarlamayla ilgili kodunuzun üzerinden bakarak sınıfının `GalaxyType` özelliğinin `Galaxy` yerine olarak belirtiliyor olduğunu `object` `GType` bulabilirsiniz.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Yukarıdaki kodu şu şekilde değiştirebilirsiniz:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kodu yeniden **derlemek** ![ve](../debugger/media/dbg-tour-restart.png "RestartApp") yeniden başlatmak için Hata Ayıklama Araç Çubuğunda (**Ctrl**  +  **Shift**  +  **F5**) Uygulamayı Yeniden Başlat düğmesine tıklayın.

    Artık, hata ayıklayıcısı üzerinde `Console.WriteLine` duraklatılırsa üzerine gelin ve `theGalaxy.GalaxyType.MyGType` değerin düzgün ayar olduğunu kontrol edin.

1. Sol kenar boşluğunda kesme noktası dairesine tıklayarak (veya sağ tıklar ve Kesme Noktası Silme Kesme Noktası Sil'i seçerek) kesme noktası kaldırın ve devam etmek için   >   **F5'e** basın.

    Uygulama çalışır ve çıkışı görüntüler. Şu anda oldukça iyi görünüyor ama fark etmezsiniz; Small Magellanic Cloud galaxy'nın konsol çıkışında Düzensiz bir galaxy olarak ortaya çıkışını bekleniyordu ama hiçbir galaxy türü göstermedi.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Bu kod satırına switch deyiminden önce (anahtarda Select deyiminden önce) bir kesme Visual Basic.

    #### <a name="c"></a>[C#](#tab/csharp)

    ```csharp
    public GType(char type)
    ```

    #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    Public Sub New(ByVal type As Char)
    ```

    ---

    Bu kodda galaxy türü ayarlanmıştır, bu nedenle buna daha yakından bakmak gerekir.

1. Yeniden başlatmak **için Hata** ![Ayıklama Araç](../debugger/media/dbg-tour-restart.png "RestartApp") Çubuğunda (**Ctrl**  +  **Shift**  +  **F5**) Uygulamayı Yeniden Başlat düğmesine tıklayın.

    Hata ayıklayıcısı, kesme noktası ayarlayıcının ayar bulunduğu kod satırı üzerinde duraklatılır.

1. Değişkenin üzerine `type` gelin. değerini (karakter `S` kodunun ardından) görüyorsunuz. Düzensiz bir galaxy türü olduğunu `I` biliyorsanız değeriyle ilgileniyorsanız.

1. **F5 tuşuna** basın ve değişkenin üzerine `type` tekrar gelin. değişkende değerini görene kadar bu `I` adımı `type` yineler.

    ![Hata Ayıklayıcısı'Visual Studio ve tür değişkeninin değerini 73 'I' olarak gösteren küçük bir pencere ve sarı kod satırıyla ekran görüntüsü.](../debugger/media/beginners-inspecting-data.png)

1. Şimdi **F11 'e** (**Hata Ayıklama**  >  **Adımını At veya** Hata Ayıklama Araç Çubuğundaki Adımla düğmesine basın). 

    **F11,** hata ayıklayıcıyı bir defada bir deyimini ilerleter (ve kodu yürütür). **F10** (**Adım At**) benzer bir komutdur ve her ikisi de hata ayıklayıcıyı kullanmayı öğrenerek son derece yararlıdır.

1. Deyiminde 'I' ( deyiminin değeri için kod satırı) durana kadar **F11** `switch` `Select` tuşuna Visual Basic. Burada yazım hatasından elde edilen net bir sorun görüyorsunuz. Kodun Düzensiz bir galaxy türü olarak ayarlayıp ilerlemesi bekleniyordu, ancak hata ayıklayıcı bunun yerine bu kodu tamamen atlar ve deyiminin bölümünde duraklatılır ( deyiminde `MyGType` `default` `switch` `Else` Visual Basic).

    ![Yazım hatası bulma](../debugger/media/beginners-typo.png)

    Koda bakarak deyiminde bir yazım hatası `case 'l'` görüyorsunuz. `case 'I'` olmalıdır.

1. koduna tıklayın `case 'l'` ve ile `case 'I'` değiştirin.

1. Kesme noktanızı kaldırın ve uygulamayı yeniden başlatmak **için** Yeniden Başlat düğmesine tıklayın.

    Hatalar şimdi düzeltildi ve beklediğiniz Çıkışı görüyorsunuz!

    Uygulamayı tamamlamak için herhangi bir tuşa basın.

## <a name="summary"></a>Özet

Bir sorun gördüğünüzde hata ayıklayıcısını ve **F10** ve **F11** gibi adım komutlarını kullanarak sorunu olan kodun bölgelerini bulun. [](../debugger/navigating-through-code-with-the-debugger.md)

> [!NOTE]
> Sorunun oluştuğu kodun bölgesini tanımlamak zorsa, sorun oluşmadan önce çalışan kodda bir kesme noktası ayarlayın ve ardından sorun bildirimini görene kadar adım komutlarını kullanın. İletileri Çıkış [penceresine günlüğe göndermek](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) için izleme noktaları da **kullanabilirsiniz.** Günlüğe kaydedilen iletilere bakarak (ve hangi iletilerin henüz günlüğe kaydedilmemiş olduğunu! öğrenerek), genellikle kodun bölgelerini sorunla yalıtabilirsiniz. Daraltmak için bu işlemi birkaç kez tekrarlamanız gerekir.

Sorunu olan kodun bölgelerini bulurken, araştırmak için hata ayıklayıcısını kullanın. Bir sorunun nedenini bulmak için, hata ayıklayıcıda uygulama çalışırken sorun kodunu incelenin:

* [Değişkenleri inceler](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) ve içermeleri gereken değer türünü içerip içer çalıştıklarını kontrol edin. Hatalı bir değer bulursanız, hatalı değerin nerede ayar olduğunu bulursanız (değerin ayar bulunduğu yeri bulmak için hata ayıklayıcıyı yeniden başlatmanız, çağrı yığınına [veya](../debugger/how-to-use-the-call-stack-window.md)her ikisini birden aramanız gerekir).

* Beklediğiniz kodun uygulama tarafından yürütülip yürütüle olmadığını kontrol edin. (Örneğin, örnek uygulamada switch deyiminin kodunun galaxy türünü Düzensiz olarak ayarlaması bekleniyordu, ancak uygulama yazım hatası nedeniyle kodu atlamıştı.)

> [!TIP]
> Hataları bulanıza yardımcı olmak için bir hata ayıklayıcı kullanırsiniz. Hata ayıklama aracı, yalnızca *kodunuzun amacını* biliyorsa sizin için hataları bulabilir. Bir araç, yalnızca siz geliştirici olarak bu amacı ifade ederseniz kodunuzun amacını bebilirsiniz. Birim [testleri](../test/improve-code-quality.md) yazma, bunu nasıl yapar?

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede bazı genel hata ayıklama kavramlarını öğrendinsiniz. Bundan sonra hata ayıklayıcı hakkında daha fazla bilgi öğrenmeye başlayabiliriz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
