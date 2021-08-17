---
title: Mutlak yeni başlayanlar için hata ayıklama kodu
description: İlk kez hata ayıklaması yapıyorsanız, Visual Studio ile uygulamanızı hata ayıklama modunda çalıştırmanıza yardımcı olacak birkaç ilke öğrenin
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
ms.openlocfilehash: e6a6e3d2f775d7c57179601d38fa4c0a2307887b95afb5160b0257033ce8a8e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436285"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Mutlak yeni başlayanlar için hata ayıklama

Hata olmadan, yazılım geliştiricileri olarak yazdığımız kod, her zaman bunu yapması Beklendiğimiz şeyi yapmaz. Bazen tamamen farklı bir şey yapar! Bu durumda, bir sonraki görev nedenini anlamak ve yalnızca kodumuza saat için bir hata ayıklama işlemi yapmak istememize rağmen bir hata ayıklayıcı aracı ya da hata ayıklayıcının kullanılması çok daha kolay ve verimlidir.

Ne yazık ki hata ayıklayıcı, tüm sorunları veya kodlarımızda "hataları" açığa çıkarılabilecek bir şey değildir. *hata ayıklama* , bir programlama hatası yaptığınız kesin noktayı bulmak için Visual Studio gibi bir hata ayıklama aracında kod adım adım adımları çalıştırmanın anlamına gelir. Kodunuzda yapmanız gereken düzeltmeleri öğreniyor ve hata ayıklama araçları, programı çalıştırmaya devam edebilmeniz için genellikle geçici değişiklikler yapmanıza olanak sağlar.

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

Hata ayıklayıcı içinde, *hata ayıklama modu* olarak da adlandırılan bir uygulama çalıştırmak, hata ayıklayıcının program çalışırken meydana gelen her şeyi etkin bir şekilde izlediği anlamına gelir. Ayrıca, durumu incelemek için uygulamayı dilediğiniz zaman duraklatıp, ardından her ayrıntıyı olduğu gibi izlemek için kod satırlarınızın satıra göre ilerleyebileceğiniz bir işlem yapabilirsiniz.

Visual Studio, **F5** kullanarak hata ayıklama moduna girer ( **ya da hata** ayıklamayı  >  **başlat** menü komutunu ya da hata **ayıklamayı** başlat düğmesine hata ayıklama araç çubuğundan ![başla](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") ). herhangi bir özel durum oluşursa, Visual Studio özel durum yardımcısı sizi özel durumun gerçekleştiği kesin noktaya götürür ve diğer yararlı bilgileri sağlar. Kodunuzda özel durumların nasıl işleneceği hakkında daha fazla bilgi için bkz. [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md).

Bir özel durum almadıysanız, büyük olasılıkla kodunuzda sorunu nerede aramanız gerektiği konusunda iyi bir fikir sahibi olabilirsiniz. Bu, kendinize kodunuzu daha dikkatli bir şekilde incelemenize olanak tanımak için hata ayıklayıcı ile *kesme noktaları* kullanırsınız. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede duraklatılacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun çalıştığı diziye bakabilirsiniz.

Visual Studio, bir kod satırının yanındaki sol kenar boşluğuna tıklayarak hızla bir kesme noktası ayarlayabilirsiniz. Ya da imleci bir satıra yerleştirip **F9** tuşuna basın.

Bu kavramları göstermeye yardımcı olmak için, daha önce birkaç hata içeren bazı örnek kodlar aracılığıyla sizi ele aldık. C# kullanıyorum, ancak hata ayıklama özellikleri Visual Basic, C++, JavaScript, Python ve diğer desteklenen diller için geçerlidir. Visual Basic için örnek kod de sağlanır, ancak ekran görüntüleri C# dilinde olur.

### <a name="create-a-sample-app-with-some-bugs"></a>Örnek uygulama oluşturma (bazı hatalar ile)

Daha sonra, birkaç hata içeren bir uygulama oluşturacağız.

1. Visual Studio yüklü ve **.net Core platformlar arası geliştirme** iş yükü yüklü olmalıdır.

    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.

    iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al**' a tıklayın. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde **Yeni proje oluştur**' u seçin. arama kutusuna **konsol** yazın, dil olarak **C#** veya **Visual Basic** seçin ve ardından .net Core için **konsol uygulaması** ' nı seçin. **İleri**’yi seçin. **ConsoleApp_FirstApp** gibi bir proje adı yazın ve **İleri**' ye tıklayın.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** veya **Visual Basic** altında, **konsol uygulaması**' nı seçin ve ardından ortadaki bölmede **konsol uygulaması (.net Core)** seçeneğini belirleyin. **ConsoleApp_FirstApp** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    .net Core için **konsol uygulaması** proje şablonunu görmüyorsanız, **araçlar**  >  **ve özellikler al**' a gidin ve Visual Studio Yükleyicisi ' ni açar. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    Visual Studio sağ bölmedeki Çözüm Gezgini görüntülenen konsol projesini oluşturur.

1. *Program. cs* (veya *program. vb*) içinde, tüm varsayılan kodu aşağıdaki kodla değiştirin. (Önce, C# veya Visual Basic doğru dil sekmesini seçin.)

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

    Bu kod için bizim amacımız, Galaxy adını, Galaxy uzaklığını ve Galaxy türünün tümünü bir listede görüntülemektir. Hata ayıklamak için, kodun amacını anlamak önemlidir. Aşağıda, çıktıda göstermek istediğimiz listeden bir satır için biçim verilmiştir:

    *Galaxy adı*, *mesafe*, *Galaxy türü*.

### <a name="run-the-app"></a>Uygulamayı çalıştırma

1. **F5** tuşuna basın veya hata **ayıklamayı Başlat** düğmesine, kod düzenleyicisinin üzerinde bulunan hata ayıklama araç çubuğunda ![hata ayıklamayı başlatın](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") .

    Uygulama başlar ve hata ayıklayıcı tarafından bizim için bir özel durum gösterilmez. Ancak, konsol penceresinde gördüğünüz çıktı beklediğiniz gibi değildir. Beklenen çıkış şu şekildedir:

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

1. Uygulama çalışmaya devam ettiğinden, `Console.WriteLine` Bu kod satırında yöntem çağrısının yanındaki sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın.

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

1. Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı Yeniden](../debugger/media/dbg-tour-restart.png "RestartApp") Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

    Uygulama, ayar istediğiniz kesme noktası üzerinden duraklatılır. Sarı vurgulama, hata ayıklayıcının nerede duraklatılmış olduğunu gösterir (sarı kod satırı henüz yürütülmedi).

1. Sağ tarafta `GalaxyType` değişkenin üzerine gelin ve ardından İngiliz anahtarı simgesinin sol tarafından `theGalaxy.GalaxyType` genişletin. özelliğini `GalaxyType` içerdiğini ve `MyGType` özellik değerinin olarak ayar olduğunu `Spiral` görüyorsunuz.

    ![Satır sonundakiGalaxy.GalaxyType özelliğinin altına genişletilmiş sarı bir kod satırı ve bir menü ile birlikte Visual Studio Debugger'ın ekran görüntüsü.](../debugger/media/beginners-inspect-variable.png)

    Konsola yazdırmayı beklediğiniz doğru değer aslında "Xbox" değeridir! Bu nedenle, uygulamayı çalıştırarak bu kodda bu değere erişebilirsiniz. Bu senaryoda yanlış API'yi kullanıyoruz. Hata ayıklayıcıda kod çalışırken bunu düzeltebilir olup olamayacaklarını göreceğiz.

1. Aynı kodda hata ayıklamaya devam ederken imlecinizi sonuna yerleştirerek `theGalaxy.GalaxyType` olarak `theGalaxy.GalaxyType.MyGType` değiştirebilirsiniz. Bu değişikliği yapmakla birlikte, kod düzenleyicisi size bu kodu derleyene olmadığını belirten bir hata gösterir. (Visual Basic'da hatayı göresiniz ve bu kod bölümü çalışır)

    ![Hata Ayıklayıcısı Visual Studio kırmızı renkle vurgulanmış bir kod satırı ve Düzenle düğmesinin seçili olduğu Düzenle ve Devam Et ileti kutusunun ekran görüntüsü.](../debugger/media/beginners-edit.png)

   > [!NOTE]
   > Örnek kodda Visual Basic ayıklamak için, Uygulamayı Yeniden Başlat düğmesine tıklamanız gerekene kadar sonraki **birkaç adımı** ![atlayabilirsiniz.](../debugger/media/dbg-tour-restart.png "RestartApp")

1. Düzenle **ve** **Devam' ileti kutusunda Düzenle'ye** tıklayın. Şimdi Hata Listesi penceresinde bir **hata iletisi** görüyorsunuz. Hata, için `'object'` bir tanım içere olmadığını `MyGType` gösterir.

    ![Hata Ayıklayıcısı Visual Studio kırmızı renkle vurgulanmış bir kod satırı ve iki hatanın listelenmiş olduğu Hata Listesi penceresinin ekran görüntüsü.](../debugger/media/beginners-no-definition.png)

    Her bir galaxyyi türünde (özelliğine sahip olan) bir nesneyle ayarlasanız da, hata ayıklayıcı nesneyi türünde `GType` `MyGType` bir nesne olarak `theGalaxy` `GType` tanımaz. Neler oluyor? Galaxy türünü ayaran tüm kodlara göz atabilirsiniz. Bunu yapmak için sınıfının kesinlikle özelliğine sahip olduğunu `GType` ancak bir şeyin doğru olmadığını `MyGType` görüyorsunuz. ile ilgili hata iletisi ipucunu verir; dil yorumlayıcıya göre tür, türünde bir nesne yerine türünde bir `object` `object` nesne gibi `GType` görünür.

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

1. Sol kenar boşluğunda kesme noktası dairesine tıklayarak kesme noktası öğesini kaldırın (veya sağ tıklar ve Kesme Noktası Silme'yi seçin) ve devam etmek için  >   **F5'e** basın.

    Uygulama çalışır ve çıkışı görüntüler. Şu anda oldukça iyi görünüyor ama fark etmezsiniz; Small Magellanic Cloud galaxy'nın konsol çıkışında Düzensiz bir galaxy olarak ortaya çıkışını bekleniyordu ama hiçbir galaxy türü göstermedi.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Bu kod satırına switch deyiminden önce bir kesme noktası ayarlayın (anahtar ifadesinde Select deyiminden Visual Basic).

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

1. Yeniden başlatmak **için Hata** ![Ayıklama Araç](../debugger/media/dbg-tour-restart.png "RestartApp") Çubuğundaki (**Ctrl**  +  **Shift**  +  **F5**) Uygulamayı Yeniden Başlat düğmesine tıklayın.

    Hata ayıklayıcısı, kesme noktası ayar istediğiniz kod satırı üzerinde duraklatılır.

1. Değişkenin üzerine `type` gelin. değerini (karakter `S` kodunun ardından) görüyorsunuz. Düzensiz bir galaxy türü olduğunu `I` biliyorsanız değeriyle ilgileniyorsanız.

1. **F5 tuşuna** basın ve değişkenin üzerine `type` tekrar gelin. değişkende değerini görene kadar bu `I` adımı `type` yineler.

    ![Hata Ayıklayıcısı'Visual Studio ve tür değişkeninin değerini 73 'I' olarak gösteren küçük bir pencere ve sarı kod satırıyla birlikte ekran görüntüsü.](../debugger/media/beginners-inspecting-data.png)

1. Şimdi **F11 'e** (**Hata Ayıklama**  >  **Adımını At veya** Hata Ayıklama Araç Çubuğundaki Adımla düğmesine basın). 

    **F11,** hata ayıklayıcıyı bir defada bir deyimini ilerleter (ve kodu yürütür). **F10** (**Adım At**) benzer bir komutdur ve her ikisi de hata ayıklayıcıyı kullanmayı öğrenerek son derece yararlıdır.

1. Deyiminde 'I' ( deyiminin değeri için kod satırı) durana kadar **F11** `switch` `Select` tuşuna Visual Basic. Burada yazım hatasından elde edilen net bir sorun görüyorsunuz. Kodun Düzensiz galaxy türü olarak ayarlayıp ilerlemesi bekleniyordu, ancak hata ayıklayıcı bunun yerine bu kodu tamamen atlar ve deyiminin bölümünde duraklatılır ( deyiminde `MyGType` `default` `switch` `Else` Visual Basic).

    ![Yazım hatası bulma](../debugger/media/beginners-typo.png)

    Koda bakarak deyiminde bir yazım hatası `case 'l'` görüyorsunuz. `case 'I'` olmalıdır.

1. koduna tıklayın `case 'l'` ve ile `case 'I'` değiştirin.

1. Kesme noktanızı kaldırın ve uygulamayı yeniden başlatmak **için** Yeniden Başlat düğmesine tıklayın.

    Hatalar şimdi düzeltildi ve beklediğiniz Çıkışı görüyorsunuz!

    Uygulamayı tamamlamak için herhangi bir tuşa basın.

## <a name="summary"></a>Özet

Bir sorun gördüğünüzde hata ayıklayıcısını ve **F10** ve **F11** gibi adım komutlarını kullanarak sorunu olan kodun bölgelerini bulun. [](../debugger/navigating-through-code-with-the-debugger.md)

> [!NOTE]
> Sorunun oluştuğu kodun bölgesini tanımlamak zorsa, sorun oluşmadan önce çalışan kodda bir kesme noktası ayarlayın ve ardından sorun bildirimini görene kadar adım komutlarını kullanın. İletileri Çıkış [penceresine günlüğe göndermek](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) için izleme noktaları da **kullanabilirsiniz.** Günlüğe kaydedilen iletilere bakarak (ve hangi iletilerin henüz günlüğe kaydedilmemiş olduğunu! öğrenerek), genellikle kod bölgesinden sorunu yalıtabilirsiniz. Daraltmak için bu işlemi birkaç kez tekrarlamanız gerekir.

Sorunu olan kodun bölgelerini bulurken, araştırmak için hata ayıklayıcısını kullanın. Bir sorunun nedenini bulmak için, hata ayıklayıcıda uygulama çalışırken sorun kodunu incelersiniz:

* [Değişkenleri inceler](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) ve içermeleri gereken değer türünü içerip içer çalıştıklarını kontrol edin. Hatalı bir değer bulursanız, hatalı değerin nerede ayar olduğunu bulursanız (değerin ayar bulunduğu yeri bulmak için hata ayıklayıcıyı yeniden başlatmanız, çağrı yığınına [veya](../debugger/how-to-use-the-call-stack-window.md)her ikisini birden aramanız gerekir).

* Beklediğiniz kodun uygulama tarafından yürütülip yürütüle olmadığını kontrol edin. (Örneğin, örnek uygulamada switch deyiminin kodunun galaxy türünü Düzensiz olarak ayarlaması bekleniyordu, ancak uygulama yazım hatası nedeniyle kodu atlamıştı.)

> [!TIP]
> Hataları bulanıza yardımcı olmak için bir hata ayıklayıcı kullanırsiniz. Hata ayıklama aracı, yalnızca *kodunuzun amacını* biliyorsa sizin için hataları bulabilir. Bir araç yalnızca geliştirici olarak bu amacı ifade ederseniz kodunuzun amacını bebilirsiniz. Birim [testleri](../test/improve-code-quality.md) yazma, bunu nasıl yapar?

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede bazı genel hata ayıklama kavramlarını öğrendinsiniz. Bundan sonra hata ayıklayıcı hakkında daha fazla bilgi öğrenmeye başlayabiliriz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
