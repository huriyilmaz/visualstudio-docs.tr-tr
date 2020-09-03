---
title: Hata ayıklayıcısını kullanmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202353"
---
# <a name="getting-started-with-the-debugger"></a>Hata Ayıklayıcısını Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcısı, herhangi bir dilde kolayca kullanılabilir. Burada basit bir C# programında hata ayıklamanın nasıl yapılacağını göstereceğiz, ancak C++ ve JavaScript gibi diğer dillerdeki koda aynı adımları uygulayabilirsiniz.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Temel C# projesinde hata ayıklama  
 Basit bir C# konsol uygulaması (**dosya/yeni/proje**) ile başlayalım, sonra **Visual C#** ' yi seçip **konsol uygulaması**' nı seçin. Daha önce Visual Studio ile hiç çalıştıysanız, bkz. [Izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). **Main** yöntemi yalnızca 10 kez bir tamsayı değişkenine 1 ekler ve sonucu konsola yazdırır:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 **Hata ayıklama** yapılandırmasında bu kodu derleyin. Bu yapılandırma varsayılan olarak ayarlanır. Yapılandırma hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).  
  
 Hata ayıklama **/hata ayıklamayı Başlat** ' a tıklayarak bu kodu hata ayıklayıcıda çalıştırın (ya da araç çubuğundan veya **F5**' i **başlatın** ). Uygulamanın neredeyse hemen çıkması gerekir, bu nedenle konsol penceresinde herhangi bir şeyin yazdırılıp yazdırılmadığını söylenemez.  
  
 Bir kesme noktası ayarlayıp daha sonra ilerleyerek konsol penceresini görmek için yeterince uzun bir yürütme durdurabilirsiniz. Bir kesme noktası ayarlamak için imlecinizi `Console.WriteLine` satıra koyun ve **Hata Ayıkla/yeni kesme noktası/Işlev kesme noktası**' na tıklayın veya aynı satırdaki sol kenar boşluğuna tıklayın. Kesme noktası şöyle görünmelidir:  
  
 ![Kesme noktası ayarlama](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Kesme noktaları hakkında daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Değişkenleri İncele  
 Genellikle hata ayıklama işlemi, belirli bir noktada beklediğinizi değerleri içermeyen değişkenleri bulmayı içerir. Değişkenleri inceleyebileceğiniz bazı yolları göstereceğiz.  
  
 Hata ayıklamayı yeniden başlatın. Yürütme, `Console.WriteLine` kod yürütmeden önce duraklar. Devam ederek yürütülmesine neden olabilirsiniz ( **Hata Ayıkla/Step Over** veya **F10**' e tıklayın). Bu durumda, **adımla** (**F11**) ve aynı sonucu elde edebilirsiniz; daha sonra bu farkı açıklayacağız. Metodun son küme ayracı ile çizgi, sarı bir şekilde açılmalıdır. Konsol penceresine bakın. **10**görmeniz gerekir.  
  
 Bir veri ipucunda geçerli değeri görüntülemek için **testInt** değişkeninin üzerine gelebilmeniz gerekir.  
  
 ![DBG&#95;&#95;verileri&#95;Ipuçları](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Kod penceresinin hemen altında, **oto**, **Yereller**ve **Gözcü** pencerelerini görmeniz gerekir. Bu pencereler, yürütme sırasında değişkenlerin geçerli değerlerini gösterir. Hem **oto** hem de **Yereller** Windows, **testint** 'i **10**değeriyle gösterir.  
  
 ![Hata ayıklanırken oto penceresi](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Bu pencereler hakkında daha fazla bilgi için bkz. [oto ve Yereller pencereleri](../debugger/autos-and-locals-windows.md).  
  
 Programda yürüyoruz, değişken değerinin nasıl değişeceğiz. Satırda bir kesme noktası ayarlayın `testInt += 1;` ve hata ayıklamayı yeniden başlatın. **TestInt** ' ın **Yereller** ve **oto** pencerelerinde **0**olduğunu ve **1** **olduğunu görmeniz** gerekir. Hata ayıklamaya devam ettiğinizde (**Hata Ayıkla/devam**et **veya araç çubuğunda ya** da **F5**), **testInt** değerinin **1**, sonra **2**vb. değişikliklerinin olduğunu görebilirsiniz. Bu değişikliklere baktıktan sonra, kesme noktasını kaldırın (**hata ayıklama/kesme noktası**veya kenar boşluğunda tıklatın) ve hata ayıklamaya devam edin. Tüm kesme noktalarını kaldırmak istiyorsanız, **hata ayıkla/tüm kesme noktalarını Sil**' e tıklayın veya **CTRL + SHIFT + F9**tuşlarına basın ve **tüm kesme noktalarını kaldırmak**isteyip istemediğinizi soran iletişim kutusunda **Evet** ' e tıklayın.  
  
## <a name="stepping-into-and-over-function-calls"></a>Işlev çağrılarına adımla ve bunların üzerinde Adımlama  
 Hata ayıklayıcı ifadede (**adımla**) bir kod yürütebilir veya hata ayıklayıcı işlevleri atlarken **(işlev**kodu hala yürütülür) kodu yürütebilir (işlev kodu hala yürütülür). Aynı hata ayıklama oturumunda her iki yöntem arasında geçiş yapabilirsiniz.  
  
 **Adımla** ve **adımla**arasındaki farkı görmek için, başka bir yöntem tarafından çağrılan bir yöntem eklememiz gerekir. C# uygulamasına bir yöntem ekleyin ve bunu Main yönteminden çağırın. Kod şuna benzemelidir:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Main yöntemindeki çağrıda bir kesme noktası ayarlayın `Method1();` ve hata ayıklamayı başlatın. Yürütme molalarından **Hata Ayıkla/adımla** **' ya tıklayın (ya da** araç çubuğundaki veya **F11**). Method1 () içindeki ilk küme ayracından yürütme sonları yeniden kesilir:  
  
 ![Koda adımla](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Hata ayıklamayı durdurun ve yeniden başlatın ve kesme noktasında yürütme kesildiğinde **Hata Ayıkla/adımla** **(ya da araç çubuğunda veya** **F10**) seçeneğine tıklayın. Yürütme molaları yeniden `Console.WriteLine("end");` .  
  
 Hata ayıklayıcıyla kod gezinme hakkında daha fazla bilgi edinmek istiyorsanız, bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md).
