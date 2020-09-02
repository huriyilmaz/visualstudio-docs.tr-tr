---
title: 'İzlenecek yol: Izleme kullanarak komut satırı profili oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817637"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>İzlenecek yol: Araç Haline Getirme Yöntemini Kullanarak Komut Satırı Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] profil oluşturma araçları izleme yöntemini kullanarak ayrıntılı zamanlama ve çağrı sayısı verileri toplamak üzere tek başına bir uygulamanın profilini oluşturmayı sağlar. Bu kılavuzda, aşağıdaki görevleri yerine getirecaksınız:  
  
- İşaretlenmiş ikililer oluşturmak için [vsinstr](../profiling/vsinstr.md) komut satırı aracını kullanın.  
  
- .NET profil oluşturma verilerini toplamak üzere ortam değişkenlerini ayarlamak için [VSPerfCLREnv](../profiling/vsperfclrenv.md) aracını kullanın.  
  
- Profil oluşturma verilerini toplamak için [VSPerfCmd](../profiling/vsperfcmd.md) aracını kullanın.  
  
- Profil oluşturma verilerinin dosya tabanlı raporlarını oluşturmak için [VSPerfReport](../profiling/vsperfreport.md) aracını kullanın.  
  
## <a name="prerequisites"></a>Ön koşullar  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- C 'nin ara anlama #  
  
- Komut satırı araçlarıyla çalışmanın ara anlama  
  
- [PeopleTrax örneğinin](../profiling/peopletrax-sample-profiling-tools.md) bir kopyası  
  
- Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, hata ayıklama sembol bilgilerinin kullanılabilir olması en iyisidir. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Izleme yöntemini kullanarak komut satırı profili oluşturma  
 İzleme, profili oluşturulan ikili dosyaların özel olarak oluşturulmuş sürümlerinin, girişte zamanlama bilgilerini toplayıp işaretlenmiş bir modüldeki işlevlere çıkış yapan araştırma işlevleri içerdiği bir profil oluşturma yöntemidir. Bu profil oluşturma yöntemi örneklemeye göre daha fazla olduğu için daha fazla ek yük doğurur. Belgelenmiş ikili dosyalar aynı zamanda hata ayıklama veya sürüm ikilileriyle daha büyüktür ve dağıtıma yönelik değildir.  
  
> [!NOTE]
> Belgelenmiş ikili dosyaları müşterilerinize göndermeyin. İşaretlenmiş ikililer, çeşitli riskler içerebilir. İkili dosyalar, uygulamanızın ters mühendisin yanı sıra güvenlik risklerini kolaylaştıran bilgiler içerir.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>PeopleTrax uygulamasını izleme yöntemini kullanarak profil haline getirme  
  
1. PeopleTrax örnek uygulamasını yükleyip yayın sürümünü oluşturun.  
  
2. Bir komut istemi penceresi açın ve **profil oluşturma araçları** dizinini yerel yol ortam değişkenine ekleyin.  
  
3. Çalışma dizinini PeopleTrax ikililerini içeren dizinle değiştirin.  
  
4. Dosya tabanlı raporları içerecek bir dizin oluşturun. Aşağıdaki komutu yazın:  
  
    ```  
    md Reports  
    ```  
  
5. Uygulamadaki ikilileri işaretlemek için VSInstr komut satırı aracını kullanın. Ayrı komut satırlarına aşağıdaki komutları yazın:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Göz önünde** Varsayılan olarak, VSInstr orijinal dosyanın izlenmeyen bir yedeğini kaydeder. Yedekleme dosyasının adı. orig uzantısına sahiptir. Örneğin, "MyApp.exe" öğesinin özgün sürümü "MyApp.exe. orig" olarak kaydedilir.  
  
6. Uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Profil oluşturucuyu başlatmak için aşağıdaki komutu yazın:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. İzleme modunda profil oluşturucuyu başlattıktan sonra, veri toplamak için PeopleTrax.exe işlemin belgelenmiş sürümünü çalıştırın.  
  
     **PeopleTrax** uygulama penceresi görüntülenir.  
  
9. **Kişi al**seçeneğine tıklayın.  
  
     PeopleTrax veri kılavuzu, verilerle doldurulur.  
  
10. **Verileri dışarı aktar**' a tıklayın.  
  
     Not Defteri başlar ve **PeopleTrax** uygulamasındaki kişilerin listesini içeren yeni bir dosya görüntüler.  
  
11. Not defteri 'ni kapatın ve sonra **PeopleTrax** uygulamasını kapatın.  
  
12. Profil oluşturucuyu kapatın. Aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Ortam değişkenlerini sıfırlamak için aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. VSPerfReport aracını kullanarak veya virgülle ayrılmış değer (. csv) rapor dosyaları oluşturun. Şunu yazın:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Oluşturulan raporları bir elektronik tablo programında analiz edebilir veya IDE 'yi kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rapor. vsp dosyasındaki profil oluşturma verilerini çözümleyebilirsiniz. Daha fazla bilgi için bkz. [performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)
