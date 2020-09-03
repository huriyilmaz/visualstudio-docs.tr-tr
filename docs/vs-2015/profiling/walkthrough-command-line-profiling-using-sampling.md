---
title: 'İzlenecek yol: örnekleme kullanarak komut satırı profili oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820319"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>İzlenecek yol: Örnekleme Yöntemini Kullanarak Komut Satırı Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, performans sorunlarını belirlemek için komut satırı araçları ve örnekleme kullanarak bir uygulamanın profilini oluşturmayı gösterir.  
  
 Bu kılavuzda, komut satırı araçlarını kullanarak yönetilen bir uygulamanın profilini oluşturmaya ve uygulamadaki performans sorunlarını yalıtmak ve tanımlamak için örnekleme kullanmayı öğreneceksiniz.  
  
 Bu kılavuzda, aşağıdaki adımları izleyeceğinizi göreceksiniz:  
  
- Komut satırı araçlarını ve örneklemesi kullanarak bir uygulama profili oluşturma.  
  
- Performans sorunlarını bulmak ve gidermek için örneklenmiş profil oluşturma sonuçlarını çözümleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , veya [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Ara anlama [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
- Komut satırı araçlarıyla çalışmanın ara anlama  
  
- [PeopleTrax örneğinin](../profiling/peopletrax-sample-profiling-tools.md) bir kopyası  
  
- Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, hata ayıklama sembol bilgilerinin kullanılabilir olması en iyisidir.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak komut satırı profili oluşturma  
 Örnekleme, belirli bir işlemin etkin işlevi belirlemede düzenli aralıklarla yokladığı profil oluşturma yöntemidir. Elde edilen veriler, işlemin örneklendiği sırada işlevin çağrı yığınının en üstünde ne sıklıkta olduğunu gösteren bir sayı sağlar.  
  
> [!NOTE]
> Profil Oluşturma Araçlarının komut satırı araçları, Visual Studio yükleme dizini altındaki \Team Tools\Performance Tools alt dizininde yer alır. 64 bit bilgisayarlarda, araçların her ikisi de 64 bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için, yolu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax, 32 bitlik bir uygulamadır.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>PeopleTrax uygulamasını örnekleme yöntemini kullanarak profili eklemek için  
  
1. PeopleTrax örnek uygulamasını yükleyip uygulamanın yayın sürümünü oluşturun.  
  
2. Bir komut istemi penceresi açın ve Profil Oluşturma Araçları dizinini yerel yol ortam değişkenine ekleyin.  
  
3. Çalışma dizinini PeopleTrax ikililerini içeren dizin olarak değiştirin.  
  
4. Uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. Profil oluşturucuyu denetleyen komut satırı aracı olan VSPerfCmd.exe çalıştırarak profil oluşturmayı başlatın. Aşağıdaki komut, örnekleme modunda uygulamayı ve profil oluşturucuyu başlatır:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Profil Oluşturucu işlemi başlatılır ve PeopleTrax.exe işlemine ekler. Profil Oluşturucu işlemi, toplanan profil oluşturma verilerini rapor dosyasına yazmaya başlar.  
  
6. **Kişi al**seçeneğine tıklayın.  
  
7. **ExportData**öğesine tıklayın.  
  
     Not Defteri açılır ve **PeopleTrax**adresinden dışarıya aktarılmış verileri içeren yeni bir dosya görüntüler.  
  
8. Not defteri 'ni kapatın ve sonra **PeopleTrax** uygulamasını kapatın.  
  
9. Profil oluşturucuyu kapatın. Aşağıdaki komutu yazın:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Ortam değişkenlerini sıfırlamak için aşağıdaki komutu kullanın:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Profil oluşturma verileri. vsp dosyasında depolanır ve aşağıdaki yöntemlerden birini kullanarak sonuçları çözümleyin:  
  
    - Visual Studio IDE 'de. vsp dosyasını açın.  
  
         veya  
  
    - VSPerfReport.exe komut satırı aracını kullanarak bir virgülle ayrılmış değer (. csv) dosyası oluşturun. IDE dışında kullanmak üzere raporlar oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdaki komutu kullanın:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)
