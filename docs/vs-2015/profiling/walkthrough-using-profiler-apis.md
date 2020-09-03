---
title: "İzlenecek yol: profil oluşturucu API 'Leri kullanma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5fc0f5a11d29fdb1ee570dc32066fdd492ed8db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871547"
---
# <a name="walkthrough-using-profiler-apis"></a>İzlenecek yol: Profilini Oluşturucu API'ler Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İzlenecek yol, Profil Oluşturma Araçları API 'Lerinin nasıl kullanılacağını göstermek için bir C# uygulaması kullanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . İzleme profili oluşturma sırasında toplanan veri miktarını sınırlamak için profil oluşturucu API 'Lerini kullanacaksınız.

 Bu yönergedeki adımlar, genellikle bir C/C++ uygulaması için geçerlidir. Her dil için yapı ortamınızı uygun şekilde yapılandırmanız gerekecektir.

 Genellikle, örnek profil oluşturma kullanarak uygulama performansını çözümlemeye başlayabilirsiniz. Örnek profil oluşturma bir performans sorunu olduğunu işaret eden bilgiler sağlamıyorsa, izleme profili oluşturma daha fazla ayrıntı sağlayabilir. İzleme profili oluşturma, iş parçacığı etkileşimini araştırmak için çok yararlıdır.

 Ancak, daha fazla ayrıntı düzeyi daha fazla verinin toplandığı anlamına gelir. İzleme profili oluşturmanın büyük veri dosyaları oluşturduğunu fark edebilirsiniz. Ayrıca, izleme, uygulamanın performansını etkilemenin daha olasıdır. Daha fazla bilgi için bkz. [Izleme verileri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md) ve [örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)

 Visual Studio Profiler, veri toplamayı sınırlandırmanıza olanak sağlar. Bu izlenecek yol, profil oluşturucu API 'Leri kullanılarak veri koleksiyonunun nasıl sınırlandıralınacağını gösteren bir örnek sunmaktadır. Visual Studio Profiler, bir uygulamanın içinden veri toplamayı denetlemek için bir API sağlar.

 Yerel kod için, Visual Studio Profiler API 'Leri VSPerf.dll. VSPerf. h ve içeri aktarma kitaplığı olan VSPerf. lib üstbilgi dosyası, Microsoft Visual Studio 9 \ Team Tools\Performance araçları dizininde bulunur.

 Yönetilen kod için, profil oluşturucu API 'Leri Microsoft.VisualStudio.Profiler.dll. Bu DLL, Microsoft Visual Studio 9 \ Team Tools\Performance araçları dizininde bulunur. Daha fazla bilgi için bkz. [Profil Oluşturucu](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yol, geliştirme ortamınızın tercih ettiğiniz hata ayıklama ve örnekleme işlemini destekleyecek şekilde yapılandırıldığını varsayar. Aşağıdaki konular, bu önkoşullara genel bir bakış sağlar:

 [Nasıl Yapılır: Toplama Metotlarını Seçme](../profiling/how-to-choose-collection-methods.md)

 [Nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)

 Varsayılan olarak, profil oluşturucu başlatıldığında, profil oluşturucu verileri genel düzeyde toplar. Programın başlangıcında aşağıdaki kod genel profil oluşturmayı devre dışı bırakır.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 API çağrısı kullanmadan, komut satırında veri toplamayı kapatabilirsiniz. Aşağıdaki adımlarda, komut satırı yapı ortamınızın profil oluşturma araçlarını ve geliştirme araçlarınızı çalıştırmak için yapılandırıldığı varsayılır. Bu, VSInstr ve VSPerfCmd için gerekli olan ayarları içerir. Bkz. komut satırı Profil Oluşturma Araçları.

## <a name="limiting-data-collection-using-profiler-apis"></a>Profil oluşturucu API 'Leri kullanarak veri toplamayı sınırlandırma

#### <a name="to-create-the-code-to-profile"></a>Profili oluşturulacak kodu oluşturmak için

1. Visual Studio 'da yeni bir C# projesi oluşturun veya tercihlerinize bağlı olarak bir komut satırı oluşturma kullanın.

    > [!NOTE]
    > Derlemeniz, Microsoft Visual Studio 9 \ Team Tools\Performance araçları dizininde bulunan Microsoft.VisualStudio.Profiler.dll kitaplığına başvurmalıdır.

2. Aşağıdaki kodu kopyalayıp projenize yapıştırın:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication2
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
              A a;
              a = new A(2);
              int x;
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());
              DataCollection.StartProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Visual Studio IDE 'de verileri toplamak ve görüntülemek için

1. IDE 'yi açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . **Çözümle** menüsünde, **Profil Oluşturucu**' nın üzerine gelin ve ardından **yeni performans oturumu** ' nu seçin.

2. Derlenmiş ikilinizi **Performans Gezgini** penceresindeki **hedefler** listesine ekleyin. **Hedefler**' e sağ tıklayın ve ardından **hedef ikilisi Ekle**' yi seçin. **Hedef Ikili Ekle** iletişim kutusunda ikiliyi bulun ve **Aç**' a tıklayın.

3. **Performans Gezgini** araç çubuğundaki **Yöntem** listesinden **izleme** ' yi seçin.

4. **Profil oluşturma Ile Başlat**' a tıklayın.

    Profil Oluşturucu ikili dosyayı seçip yürütür ve bir performans rapor dosyası oluşturur. Performans raporu dosyası **Performans Gezgini** **Reports** düğümünde görünür.

5. Elde edilen performans raporu dosyasını açın.

   Varsayılan olarak, profil oluşturucu başlatıldığında profil oluşturucu verileri genel düzeyde toplar. Programın başlangıcında aşağıdaki kod genel profil oluşturmayı devre dışı bırakır.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Komut satırında verileri toplamak ve görüntülemek için

1. Bu kılavuzda daha önce açıklanan "profil oluşturmak için kod oluşturma" yordamında oluşturduğunuz örnek kodun hata ayıklama sürümünü derleyin.

2. Yönetilen bir uygulamanın profilini almak için, uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:

     **VsPefCLREnv/TRACEON**

3. Şu komutu yazın:**vsinstr \<filename> . exe**

4. Şu komutu yazın:**VSPerfCmd/start: Trace/output: \<filename> . vsp**

5. Şu komutu yazın:**VSPerfCmd/globaloff**

6. Programınızı yürütün.

7. Şu komutu yazın:**VSPerfCmd/shutdown**

8. Şu komutu yazın:**VSPerfReport/calltrace: \<filename> . vsp**

     Geçerli dizinde elde edilen performans verileriyle bir. csv dosyası oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu](/previous-versions/ms242704(v=vs.140))
- [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)