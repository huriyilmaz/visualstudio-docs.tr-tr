---
title: "Adım adım kılavuz: Profil Oluşturma API'lerini | Microsoft Docs"
description: Profil oluşturma sırasında toplanan veri miktarını sınırlamak için profil oluşturma API'lerini kullanmayı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 99fdbae8612de92c178ebb502e63e4c974224da4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637057"
---
# <a name="walkthrough-using-profiler-apis"></a>İzlenecek yol: Profil Oluşturucu API’lerini kullanma

Kılavuzda, api'leri kullanarak C# Profil Oluşturma Araçları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2. Profil oluşturma sırasında toplanan veri miktarını sınırlamak için profil oluşturma API'lerini kullanabilirsiniz.

 Bu kılavuzda yer alan adımlar genellikle bir C/C++ uygulaması için geçerlidir. Her dil için derleme ortamınızı uygun şekilde yapılandırmanız gerekir.

 Genellikle örnek profil oluşturma kullanarak uygulama performansını analiz etmeniz gerekir. Örnek profil oluşturma bir performans sorununa yol açan bilgiler sağlanmasa da, ölçümleme profili oluşturma daha ayrıntılı bir düzeye sahip olabilir. Ölçüm aracı profili oluşturma, iş parçacığı etkileşimini araştırmada çok yararlıdır.

 Ancak daha fazla ayrıntı düzeyi, daha fazla verinin toplanmış olduğu anlamına gelir. Ölçümleme profili oluşturmanın büyük veri dosyaları oluşturduğuna bakabilirsiniz. Ayrıca, ölçümlemenin uygulamanın performansını etkileme olasılığı daha fazladır. Daha fazla bilgi için [bkz. Ölçüm ölçüm verisi değerlerini anlama](../profiling/understanding-instrumentation-data-values.md) [ve Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)

 Veri Visual Studio profili oluşturma, veri toplamayı sınırlamaya olanak sağlar. Bu kılavuz, profil oluşturma API'lerini kullanarak veri toplamayı sınırlamak için bir örnek sunar. Veri Visual Studio, bir uygulamanın içinde veri toplamayı denetlemek için bir API sağlar.

 ::: moniker range="vs-2017"
 Yerel kod için, Visual Studio profil oluşturma API'leri *VSPerf.dll.* *VSPerf.h* üst bilgi dosyası ve içeri aktarma kitaplığı *VSPerf.lib,* *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK dizininde* bulunur.  64 bit uygulamalar için klasör *şu şekildedir: Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 Yönetilen kod için profil oluşturma API'leri *Microsoft.VisualStudio.Profiler.dll.* Bu DLL, *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools dizininde* bulunur. 64 bit uygulamalar için klasör *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64 şeklindedir.* Daha fazla bilgi için bkz. [Profil Oluşturma](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzda, geliştirme ortamı seçiminizin hata ayıklamayı ve örneklemeyi destekleyecek şekilde yapılandırıldığından emin oluruz. Aşağıdaki konular, bu önkoşullara genel bir bakış sağlar:

- [Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)

- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)

 Varsayılan olarak, profil oluşturma başlatıcı genel düzeyde veri toplar. Programın başındaki aşağıdaki kod genel profil oluşturmayı kapatıyor.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Api çağrısı kullanmadan komut satırına veri toplamayı kapatabilirsiniz. Aşağıdaki adımlarda, komut satırı derleme ortamının profil oluşturma araçlarını ve geliştirme araçlarınız olarak çalıştırılacak şekilde yapılandırıldığından emin oluruz. Bu, VSInstr ve VSPerfCmd için gerekli ayarları içerir. Bkz. [Komut satırı profil oluşturma araçları.](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="limit-data-collection-using-profiler-apis"></a>Profil oluşturma API'lerini kullanarak veri toplamayı sınırlama

#### <a name="to-create-the-code-to-profile"></a>Profili oluşturularak kod oluşturmak için

1. Visual Studio'de yeni bir C# projesi oluşturun veya tercihlerinize bağlı olarak bir komut satırı derlemesi kullanın.

    > [!NOTE]
    > Derlemeniz, *Microsoft.VisualStudio.Profiler.dll\Shared\Common\VSPerfCollectionTools* dizininde bulunan Microsoft Visual Studio kitaplığına başvuracak. 

2. Aşağıdaki kodu kopyalayıp projenize yapıştırın:

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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Visual Studio IDE'de verileri toplamak ve görüntülemek için

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE'i açın. Analiz menüsünde **ProfilLeyici'nin** üzerine **gelin ve** Yeni Performans **Oturumu'seçin.**

2. Derlenmiş ikili dosyanızı, **Performans Gezgini** **penceresindeki Hedefler listesine** ekleyin. Hedefler'e **sağ tıklayın** ve Hedef İkili **Ekle'yi seçin.** Hedef İkili Dosya Ekle iletişim **kutusunda ikili dosyayı** bulun ve aç'a **tıklayın.**

3. Araç **çubuğundaki** Yöntem **listesinden** Ölçümler'Performans Gezgini seçin. 

4. Profil Oluşturma **ile Başlat'a tıklayın.**

    Profil oluşturma, ikili dosyayı işler ve yürütür ve bir performans raporu dosyası oluşturun. Performans raporu dosyası, rapor **dosyasının** Raporlar düğümünde **Performans Gezgini.**

5. Sonuçta elde edilen performans raporu dosyasını açın.

   Varsayılan olarak, profil oluşturma başlatıcı genel düzeyde veri toplar. Programın başındaki aşağıdaki kod genel profil oluşturmayı kapatıyor.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Komut satırına veri toplamak ve görüntülemek için

1. Bu kılavuzda daha önce yer alan "Profile Kod Oluşturma" yordamında oluşturduğunuz örnek kodun hata ayıklama sürümünü derle.

2. Yönetilen bir uygulamanın profilini oluşturmak için aşağıdaki komutu yazarak uygun ortam değişkenlerini ayarlayın:

     **VsPerfCLREnv /traceon**

3. Şu komutu yazın: **VSInstr \<filename>.exe**

4. Şu komutu yazın: **VSPerfCmd /start:trace /output: \<filename> .vsp**

5. Şu komutu yazın: **VSPerfCmd /globaloff**

6. Programınızı yürütün.

7. Şu komutu yazın: **VSPerfCmd /shutdown**

8. Şu komutu yazın: **VSPerfReport /calltrace: \<filename> .vsp**

     A. *csv* dosyası, elde edilen performans verileriyle geçerli dizinde oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu](/previous-versions/ms242704(v=vs.140))
- [Visual Studio profil oluşturma API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- [Komut satırı profili](../profiling/using-the-profiling-tools-from-the-command-line.md)
