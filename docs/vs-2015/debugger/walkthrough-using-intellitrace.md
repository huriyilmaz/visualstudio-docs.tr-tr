---
title: 'İzlenecek yol: IntelliTrace kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64844201"
---
# <a name="walkthrough-using-intellitrace"></a>İnceleme: IntelliTrace’i Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace kullanarak belirli olaylar veya olay kategorileri hakkında bilgi toplamak veya olaylara ek olarak tek tek işlev çağrıları hakkında bilgi toplamak için kullanabilirsiniz. Aşağıdaki yordamlarda bunun nasıl yapılacağı gösterilmektedir.  
  
 IntelliTrace 'i Visual Studio Enterprise sürümünde (ancak Professional veya Community sürümlerinde kullanamazsınız) kullanabilirsiniz.  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> IntelliTrace 'i yalnızca olaylarla kullanma  
 Yalnızca IntelliTrace olayları ile hata ayıklamayı deneyebilirsiniz. IntelliTrace olayları hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve diğer sistem olaylardır. Hata ayıklamaya başlamadan önce IntelliTrace 'in kaydettiği olayları denetlemek için belirli olayları açmanız veya kapatmanız gerekir. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).  
  
 Aşağıdaki adımlarda yalnızca IntelliTrace olayları ile hata ayıklama gösterilmektedir:  
  
1. Dosya erişimi için IntelliTrace olayını açın. **Araçlar/Seçenekler/IntelliTrace/IntelliTrace olayları** sayfasına gidin ve **Dosya** kategorisini genişletin. **Dosya** olay kategorisini denetleyin. Bu, tüm dosya olaylarının (erişim, kapatma, silme) denetlenmesini sağlar.  
  
2. Bir C# konsol uygulaması oluşturun. Program.cs dosyasında aşağıdaki `using` ifadeyi ekleyin:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Ana yöntemde bir oluşturun, <xref:System.IO.FileStream> buradan okuyun, kapatın ve dosyayı silin. Yalnızca bir kesme noktası ayarlamak için bir yer eklemek üzere başka bir satır ekleyin:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
4. Üzerinde bir kesme noktası ayarlayın `Console.WriteLine("done");`  
  
5. Hata ayıklamayı her zamanki gibi başlatın. ( **F5** tuşuna basın veya hata **Ayıkla/hata ayıklamayı Başlat**seçeneğine tıklayın.  
  
    > [!TIP]
    > Bu Windows 'daki değerleri görmek ve kaydetmek için, hata ayıklama sırasında **Yereller** ve **oto** pencerelerini açık tutun.  
  
6. Yürütme kesme noktasında durmaktadır. **Tanılama araçları** penceresini görmüyorsanız, **Hata Ayıkla/Windows/IntelliTrace olayları**' na tıklayın.  
  
     **Tanılama araçları** penceresinde **Olaylar** sekmesini bulun (3 sekme, **olay**, **bellek kullanımı**ve **CPU kullanımı**görmeniz gerekir). **Olaylar** sekmesi, hata ayıklayıcının yürütmeden önce son olayla biten kronolojik bir olay listesini gösterir. **Erişim WordSearchInputs.txt**adlı bir olay görmeniz gerekir.  
  
     Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTrace&#45;güncelleştirme 1](../debugger/media/intellitrace-update1.png "IntelliTrace-güncelleştirme 1")  
  
7. Ayrıntılarını genişletmek için olayı seçin.  
  
     Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Dosya yolu bağlantısını seçerek dosyayı açabilirsiniz. Tam yol adı kullanılabilir değilse, **Dosya Aç** iletişim kutusu görüntülenir.  
  
     Hata **ayıklamayı etkinleştir**' e tıklayarak hata ayıklayıcının bağlamını seçili olayın toplandığı zamana ayarlar, **çağrı yığınında**geçmiş verileri, **Yereller** ve diğer katılan hata ayıklayıcı pencerelerini gösterir. Kaynak kodu kullanılabiliyorsa, Visual Studio bunu incelemenize olanak sağlamak için işaretçiyi kaynak penceresinde karşılık gelen koda taşıdır.  
  
     Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.  
  
     ![HistoricalDebugging&#45;güncelleştirme 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-güncelleştirme 1")  
  
8. Hatayı bulamazsanız, hataya en önde gelen diğer olayları incelemeyi deneyin. Ayrıca, işlev çağrıları arasında ilerlemek için IntelliTrace kayıt çağrı bilgilerine sahip olabilirsiniz.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Olaylar ve işlev çağrıları ile IntelliTrace kullanma  
 IntelliTrace, etkinliklerle birlikte işlev çağrılarını kaydedebilir. Bu, çağrı yığını geçmişini görmenizi ve kodunuzda geri ve ileri doğru ilerlemenizi sağlar. IntelliTrace, işlev adları, işlev girdisi ve çıkış noktaları gibi verileri ve belirli parametre değerlerini ve dönüş değerlerini kaydeder. [IntelliTrace özelliklerine](../debugger/intellitrace-features.md)bakın.  
  
1. Çağrı toplamayı açın. ( **Araçlar/Seçenekler/IntelliTrace/genel**sayfasında **IntelliTrace olayları ' nı ve çağrı bilgileri**' ni seçin. Bir sonraki hata ayıklama oturumu başladığında IntelliTrace bu bilgileri toplamaya başlar.  
  
    > [!TIP]
    > Bu, uygulamanızı yavaşlatabilir ve diske kaydettiğiniz tüm IntelliTrace günlük dosyalarının (. iTrace dosyaları) boyutunu artırabilir. En fazla çağrı verilerini almak, ancak etkileri en aza indirmek için yalnızca sizi ilgilendiren modüllerden verileri kaydedin. . İTrace dosyalarınızın en büyük boyutunu değiştirmek için, **Araçlar/Seçenekler/IntelliTrace/gelişmiş**' e gidin ve maksimum disk alanı miktarını belirtin. Varsayılan değer 250 MB 'tır.  
  
2. Önceki bölümde oluşturulan C# konsol uygulamasında hata ayıklamayı başlatın. Yürütme kesme noktasında durmaktadır. **Tanılama araçları** penceresini görmüyorsanız, **Hata Ayıkla/Windows/IntelliTrace olayları**' na tıklayın.  
  
3. **Çağrılar** sekmesine geçin.  
  
     Artık uygulamanızın işlev çağrılarını, kök çağrısıyla (geçerli çözümde, ana giriş noktasında) başlayarak ve yürütmenin hangi konumuyla bitiyorsunuz görürsünüz.  
  
     İşlev çağrılarından birini seçin ve çift tıklayın. İşlev girişinin ve çıkış noktalarının yanı sıra, geçerli çağrının diğer işlevlere ve çağrı tarafından oluşturulan IntelliTrace olaylarına yapılan çağrıları görmeniz gerekir. Geçmiş hata ayıklaması açık değilse, bu eylem açar. Geçmiş hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [geçmiş hata ayıklama](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > Bazı çağrıların soluk olduğunu görebilirsiniz. Bunun nedeni, IntelliTrace 'in ilgili modüllerden veri kaydetmez. Bu verileri görmek için IntelliTrace 'in bu modüllerden veri toplamasını sağlayabilirsiniz. Modülleri belirtme hakkında bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar
