---
title: Geçmiş hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192179"
---
# <a name="historical-debugging"></a>Geçmiş Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçmiş hata ayıklama, IntelliTrace tarafından toplanan bilgilere bağlı bir hata ayıklama modudur. Geri taşımanızı ve uygulamanızın yürütülmesini ve durumunu incelemenizi sağlar.  
  
 IntelliTrace 'i Visual Studio Enterprise sürümünde (ancak Professional veya Community sürümlerinde kullanamazsınız) kullanabilirsiniz.  
  
## <a name="why-use-historical-debugging"></a>Geçmiş hata ayıklama neden kullanılmalıdır?  
 Hataları bulmak için kesme noktalarının ayarlanması, bir veya daha fazla isabetsizlik olabilir. Kodunuzda hatanın olması şüpheli olan yere bir kesme noktası, sonra da uygulamayı hata ayıklayıcısında çalıştırmanız ve yürütme sonlarının hata kaynağını açığa çıkarması için gereken yerde bir kesme noktası ayarlayın. Aksi takdirde, bir kesme noktasını kodda başka bir yerde ayarlamayı ve hata ayıklayıcıyı yeniden çalıştırmayı denemeniz gerekir.  
  
 ![kesme noktası ayarlama](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Uygulama içinde dolaşırken IntelliTrace ve geçmiş hata ayıklamayı kullanabilir ve kesme noktaları ayarlamak zorunda kalmadan durumunu (çağrı yığını ve yerel değişkenler) inceleyebilir, hata ayıklamayı yeniden başlatabilir ve test adımlarını tekrarlayabilirsiniz. Bu, özellikle de hata, yürütülmesi uzun süren bir test senaryosunda derin olduğunda sizi çok zaman kaydedebilir.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Geçmiş hata ayıklamayı kullanmaya başlamak Nasıl yaparım? mı?  
 IntelliTrace varsayılan olarak açık. Yapmanız gereken tek şey, hangi olayların ve işlev çağrılarının sizi ilgilentireceğinize karar verir. Ne aramak istediğinizi tanımlama hakkında daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md). IntelliTrace ile hata ayıklamanın adım adım bir hesabı için bkz. [Izlenecek yol: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Geçmiş hata ayıklama ile kodunuzda gezinme  
 Hata içeren basit bir programla başlayalım. Bir C# konsol uygulamasında aşağıdaki kodu ekleyin:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Çağırma sonrasında beklenen değerin 20 olduğunu varsayacağız `resultInt` `AddAll()` (20 kat arttırılmasının sonucu `testInt` ). (Ayrıca, içinde hatayı göremedik `AddInt()` ). Ancak sonuç aslında 44 ' dir. Hatayı 10 kez adımla nasıl bulabiliriz `AddAll()` ? Hatayı daha hızlı ve daha kolay bulmak için geçmiş hata ayıklamayı kullanabiliriz. Bunu şu şekilde yapabilirsiniz:  
  
1. Araçlar/Seçenekler/IntelliTrace/genel ' de IntelliTrace ' in etkinleştirildiğinden emin olun ve IntelliTrace olayları ve çağrı bilgileri seçeneğini belirleyin. Bu seçeneği seçmezseniz, gezinti Cilt payının (aşağıda açıklandığı gibi) görümeyeceksiniz.  
  
2. Satırda bir kesme noktası ayarlayın `Console.WriteLine(resultInt);` .  
  
3. Hata ayıklamayı başlatın. Kod kesme noktasına yürütülür. **Yereller** penceresinde, değerinin 44 olduğunu görebilirsiniz `resultInt` .  
  
4. **Tanılama araçları** penceresini açın (**hata ayıkla/tanılama araçları göster**). Kod penceresi şöyle görünmelidir:  
  
    ![Kesme noktasında kod penceresi](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Sol kenar boşluğunun yanında, kesme noktasının hemen üzerinde bir çift ok görmeniz gerekir. Bu alana gezinti cilt payı denir ve geçmiş hata ayıklama için kullanılır. Oka tıklayın.  
  
    Kod penceresinde, yukarıdaki kod satırının ( `int resultInt = AddIterative(testInt);` ) pembe renkte olduğunu görmeniz gerekir. Pencerenin üstünde, şimdi geçmiş hata ayıklamada olduğunuz bir ileti görmeniz gerekir.  
  
    Kod penceresi şimdi şöyle görünür:  
  
    ![geçmiş hata ayıklama modundaki kod penceresi](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Şimdi, `AddAll()` Gezinti cilt payındaki yönteme (**F11**veya **Step into** düğmesine) erişebilirsiniz. İleri (**F10**) veya gezinti cilt payındaki **sonraki çağrıya git** . Pembe çizgi artık `j = AddInt(j);` satır üzerinde. Bu durumda **F10** , sonraki kod satırına ilerlemez. Bunun yerine, sonraki işlev çağrısının adımları vardır. Geçmiş hata ayıklama çağrıdan çağrıya gider ve bir işlev çağrısı içermeyen kod satırlarını atlar.  
  
7. Şimdi yöntemine adımlayın `AddInt()` . Hatayı Bu kodda hemen görmeniz gerekir.  
  
   Bu yordam, geçmiş hata ayıklaması ile yapabileceklerinize ilişkin yüzeyi ortaya ayıklamış. Farklı ayarlar hakkında daha fazla bilgi edinmek ve gezinti cilt payı içindeki farklı düğmelerin etkileri hakkında daha fazla bilgi edinmek için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).
