---
title: "İzleyici: Profiler API'lerini kullanma | Microsoft Dokümanlar"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 81071a44b51b1441782b25741126873fc720ed7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779889"
---
# <a name="walkthrough-using-profiler-apis"></a>İzlenecek yol: Profil oluşturucu API'ler Kullanma

İzleme, Profil Oluşturma Araçları API'lerini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nasıl kullanılacağını göstermek için bir C# uygulaması kullanır. Enstrümantasyon profiloluşturma sırasında toplanan veri miktarını sınırlamak için profil oluşturucu API'lerini kullanırsınız.

 Bu yordamdaki adımlar genellikle bir C/C++ uygulaması için geçerlidir. Her dil için yapı ortamınızı uygun şekilde yapılandırmanız gerekir.

 Genellikle, örnek profil oluşturma kullanarak uygulama performansını çözümlemeye başlarsınız. Örnek profil oluşturma, bir darboğaz saptayan bilgiler sağlamazsa, enstrümantasyon profil oluşturma daha büyük bir ayrıntı düzeyi sağlayabilir. Enstrümantasyon profilleme iş parçacığı etkileşimi araştırmak için çok yararlıdır.

 Ancak, daha büyük bir ayrıntı düzeyi, daha fazla veri toplandığı anlamına gelir. Bu enstrümantasyon profil oluşturma büyük veri dosyaları oluşturur bulabilirsiniz. Ayrıca, enstrümantasyon uygulamanın performansını etkileme olasılığı daha yüksektir. Daha fazla bilgi için [bkz.](../profiling/understanding-instrumentation-data-values.md) [Understand sampling data values](../profiling/understanding-sampling-data-values.md)

 Visual Studio profilleyicisi veri toplamayı sınırlamanızı sağlar. Bu izlik, profil oluşturucu API'lerini kullanarak veri toplamayı nasıl sınırlandırılağın bir örneğini sunar. Visual Studio profiloluşturucusu, bir uygulama nın içinden veri toplamayı denetlemek için bir API sağlar.

 ::: moniker range="vs-2017"
 Yerel kod için Visual Studio profil oluşturucu API'leri *VSPerf.dll'dedir.* Başlık dosyası, *VSPerf.h*ve alma kitaplığı *VSPerf.lib,* Microsoft *Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* dizininde bulunur.  64 bit uygulamalar için klasör *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 Yönetilen kod için profil oluşturucu API'ler *Microsoft.VisualStudio.Profiler.dll'dedir.* Bu *DLL, Microsoft Visual Studio\Shared\SHARED\VSPerfCollectionTools* dizininde bulunur. 64 bit uygulamalar için klasör *Microsoft Visual Studio\Shared\ORTAK\VSPerfCollectionTools\x64'* tir. Daha fazla bilgi için [Profiler'a](/previous-versions/ms242704(v=vs.140))bakın.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yol, geliştirme ortamı seçtiğiniz hata ayıklama ve örnekleme yi destekleyecek şekilde yapılandırıldığı varsayar. Aşağıdaki konular bu ön koşullara genel bir bakış sağlar:

- [Nasıl yapılır: Toplama yöntemlerini seçin](../profiling/how-to-choose-collection-methods.md)

- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)

 Varsayılan olarak, profil oluşturucu başlatıldığında, profil oluşturucu genel düzeyde veri toplar. Programın başındaki aşağıdaki kod, genel profil oluşturmayı kapatır.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 API çağrısı kullanmadan komut satırında veri toplamayı kapatabilirsiniz. Aşağıdaki adımlar, komut satırı oluşturma ortamının profil oluşturma araçlarını çalıştıracak şekilde ve geliştirme araçlarınız olarak yapılandırıldığından varsayılır. Bu vsinstr ve VSPerfCmd için gerekli ayarları içerir. Bkz. [Komut satırı profil oluşturma araçları.](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="limit-data-collection-using-profiler-apis"></a>Profil oluşturucu API'leri kullanarak veri toplamayı sınırlandırın

#### <a name="to-create-the-code-to-profile"></a>Profil kodu oluşturmak için

1. Visual Studio'da yeni bir C# projesi oluşturun veya tercihinize bağlı olarak bir komut satırı oluşturma kullanın.

    > [!NOTE]
    > Yapınız, *Microsoft Visual Studio\Shared\Shared\VSPerfCollectionTools* dizininde bulunan *Microsoft.VisualStudio.Profiler.dll* kitaplığına başvurmalıdır.

2. Aşağıdaki kodu kopyalayın ve projenize yapıştırın:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication1
    {
        class Program
        {
            public class A
            {
                private int _x;

                public A(int x)
                {
                    _x = x;
                }

                public int DoNotProfileThis()
                {
                    return _x * _x;
                }

                public int OnlyProfileThis()
                {
                    return _x + _x;
                }

                public static void Main()
                {
                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    A a = new A(2);
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis());

                    DataCollection.StartProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    int x;
                    x = a.OnlyProfileThis();

                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    Console.WriteLine("2 doubled is {0}", x);
                }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Visual Studio IDE'de veri toplamak ve görüntülemek için

1. IDE'yi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açın. **Çözümle** menüsünde **Profiler'ı**işaret edin ve ardından **Yeni Performans Oturumu'nu**seçin.

2. Derlenmiş ikilinizi **Performans Gezgini** **penceresindeki Hedefler** listesine ekleyin. Sağ tıkla **Hedefleri**ve ardından **Hedef İkili Ekle'yi**seçin. **Hedef İkili Ekle** iletişim kutusunda ikiliyi bulun ve sonra **Aç'ı**tıklatın.

3. **Performans Gezgini** araç çubuğundaki **Yöntem** listesinden **Enstrümantasyon'u** seçin.

4. **Profil Oluşturma ile Başlat'ı**tıklatın.

    Profil oluşturucu, ikiliyi enstrüman ve çalıştıracak ve bir performans raporu dosyası oluşturacaktır. Performans raporu **dosyası, Performans Gezgini'nin** **Raporlar** düğümünde görünür.

5. Ortaya çıkan performans raporu dosyasını açın.

   Varsayılan olarak, profil oluşturucu başlatıldığında, profil oluşturucu genel düzeyde veri toplar. Programın başındaki aşağıdaki kod, genel profil oluşturmayı kapatır.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Komut satırında veri toplamak ve görüntülemek için

1. Bu gözden geçirmenin daha önceki "Profil kodu oluşturma" yordamında oluşturduğunuz örnek kodun hata ayıklama sürümünü derle.

2. Yönetilen bir uygulamayı profillemek için, uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:

     **VsPerfCLREnv /traceon**

3. Aşağıdaki komutu yazın: **VSInstr \<dosya adı>.exe**

4. Aşağıdaki komutu yazın: **VSPerfCmd /start:trace /output:\<filename>.vsp**

5. Aşağıdaki komutu yazın: **VSPerfCmd /globaloff**

6. Programınızı uygulayın.

7. Aşağıdaki komutu yazın: **VSPerfCmd /shutdown**

8. Aşağıdaki komutu yazın: **VSPerfReport\</calltrace: filename>.vsp**

     A. *csv* dosyası, elde edilen performans verileriyle birlikte geçerli dizinde oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu](/previous-versions/ms242704(v=vs.140))
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
