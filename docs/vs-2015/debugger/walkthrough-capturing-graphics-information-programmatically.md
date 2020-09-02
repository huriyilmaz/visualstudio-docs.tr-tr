---
title: 'İzlenecek yol: grafik bilgilerini programlama yoluyla yakalama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9de8e2a2ee69911f5505937494d2912c724326e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847816"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>İzlenecek yol: Grafik Bilgilerini Program Aracılığıyla Yakalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Direct3D uygulamasından grafik bilgilerini programlı bir şekilde yakalamak için grafik tanılama kullanabilirsiniz.  
  
 Programlı yakalama, gibi senaryolarda faydalıdır:  
  
- Grafik uygulamanız, bir dokusunu oluştururken olduğu gibi swapzincirini kullanmazsa programlı olarak yakalamayı başlatın.  
  
- Uygulamanız, hesaplamalar gerçekleştirmek için DirectCompute kullandığında olduğu gibi, uygulama hiç işlenmezse, programlı olarak yakalamayı başlatın.  
  
- `CaptureCurrentFrame`Bir işleme sorunu, el ile test sırasında tahmin etmek ve yakalamak zor olduğunda, ancak çalışma zamanında uygulamanın durumu hakkında bilgiler kullanılarak programlı bir şekilde tahmin edilebilir.  
  
## <a name="programmatic-capture-in-windows-81"></a><a name="CaptureDX11_2"></a> Windows 8.1 'de Programlı yakalama  
 İzlenecek yolun bu bölümü, güçlü yakalama yöntemini kullanan Windows 8.1 üzerinde DirectX 11,2 API kullanan uygulamalarda Programlı yakalamayı gösterir. Windows 8,0 ' de DirectX 'in önceki sürümlerini kullanan uygulamalarda Programlı yakalama 'yı kullanma hakkında daha fazla bilgi için bu izlenecek yolda [windows 8,0 ve daha önceki sürümlerde Programlı yakalama](#CaptureDX11_1) bölümüne bakın.  
  
 Bu bölümde bu görevlerin nasıl yapılacağı gösterilmektedir:  
  
- Uygulamanızı programlı yakalama kullanacak şekilde hazırlama  
  
- IDXGraphicsAnalysis arabirimini alma  
  
- Graf bilgilerini yakalama  
  
> [!NOTE]
> Programlı yakalama 'nın önceki uygulamaları, Yakalama işlevselliği sağlamak için uzak araçlara güvendi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Windows 8.1 doğrudan Direct3D 11,2 aracılığıyla yakalamayı destekler. Sonuç olarak, Windows 8.1 üzerinde Programlı yakalama için Uzak Araçları yüklemeye artık ihtiyacınız yoktur.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Uygulamanızı programlı yakalama kullanacak şekilde hazırlama  
 Uygulamanızda Programlı yakalama 'yı kullanmak için gereken üst bilgileri içermesi gerekir. Bu üstbilgiler Windows 8.1 SDK 'nın bir parçasıdır.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Programlı yakalama üstbilgilerini dahil etmek için  
  
- Bu üst bilgileri IDXGraphicsAnalysis arabirimini tanımlayabileceğiniz kaynak dosyasına ekleyin:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    > Windows 8.1 uygulamalarınızda Programlı yakalama gerçekleştirmek için Windows 8,0 ve önceki sürümlerde Programlı yakalamayı destekleyen vsgcapture. h başlık dosyasını eklemeyin. Bu üstbilgi DirectX 11,2 ile uyumsuzdur. D3d11_2. h üst bilgisi eklendikten sonra bu dosya varsa, derleyici bir uyarı verir. Vsgcapture. h, d3d11_2. h öncesinde varsa, uygulama başlatılmaz.  
  
    > [!NOTE]
    > Makinenizde Haziran 2010 DirectX SDK 'Sı yüklüyse ve projenizin içerme yolu içeriyorsa `%DXSDK_DIR%includex86` , bunu ekleme yolunun sonuna taşıyın. Kitaplık yolunuzda aynısını yapın.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Windows Phone 8,1 SDK 'Sı DXProgrammableCapture. h üst bilgisini içermediğinden, `IDXGraphicsAnalysis` ve yöntemlerini kullanabilmeniz için arabirimi kendiniz tanımlamanız gerekir `BeginCapture()` `EndCapture()` . Önceki bölümde açıklandığı gibi diğer üstbilgileri ekleyin.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini tanımlamak için  
  
- Üst bilgi dosyalarını dahil ettiğiniz dosyada IDXGraphicsAnalysis arabirimini tanımlayın.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Kolaylık olması için, bu adımları yeni bir başlık dosyasında gerçekleştirebilir ve ardından uygulamanıza gereken yere dahil edebilirsiniz.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini alma  
 DirectX 11,2 ' den grafik bilgilerini yakalamadan önce DXGI hata ayıklama arabirimini almanız gerekir.  
  
> [!IMPORTANT]
> Programlı yakalama kullanırken, uygulamanızı hala grafik tanılama (alt + F5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ) altında veya [komut satırı yakalama aracı](../debugger/command-line-capture-tool.md)altında çalıştırmanız gerekir.  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini almak için  
  
- DXGI hata ayıklama arabirimine IDXGraphicsAnalysis arabirimini bağlamak için aşağıdaki kodu kullanın.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     `HRESULT` `DXGIGetDebugInterface1` Kullanmadan önce geçerli bir arabirim aldığınızdan emin olmak için tarafından döndürülen ' i denetlediğinizden emin olun:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    > `DXGIGetDebugInterface1` `E_NOINTERFACE` () Döndürürse `error: E_NOINTERFACE No such interface supported` , uygulamanın grafik tanılama (alt + F5) altında çalıştığından emin olun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Artık geçerli bir `IDXGraphicsAnalysis` arabiriminiz olduğuna göre, `BeginCapture` `EndCapture` grafik bilgilerini yakalamak için ve kullanabilirsiniz.  
  
##### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için  
  
- Grafik bilgilerini yakalamaya başlamak için şunu kullanın `BeginCapture` :  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Yakalama çağrıldığında hemen başlar `BeginCapture` ; sonraki çerçevenin başlamasını beklemez. Yakalama, geçerli çerçeve sunulduktan sonra ya da çağırdığınızda `EndCapture` :  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="programmatic-capture-in-windows-80-and-earlier"></a><a name="CaptureDX11_1"></a> Windows 8,0 ve önceki sürümlerde Programlı yakalama  
 Bu izlenecek yolda, Windows 8,0 ve önceki sürümlerde, eski yakalama yöntemini kullanan DirectX 11,1 API kullanan uygulamalarda Programlı yakalama gösterilmektedir. Windows 8.1 DirectX 11,2 kullanan uygulamalarda Programlı yakalama 'yı kullanma hakkında bilgi için, bu kılavuzda daha önce Windows 8.1 bkz. [Programlı yakalama](#CaptureDX11_2) .  
  
 Bu bölümde şu görevler gösterilir:  
  
- Bilgisayarınızı Programlı yakalamayı kullanacak şekilde hazırlama  
  
- Uygulamanızı programlı yakalama kullanacak şekilde hazırlama  
  
- Grafik günlük dosyasının adını ve konumunu yapılandırma  
  
- `CaptureCurrentFrame`API 'yi kullanma  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Bilgisayarınızı Programlı yakalamayı kullanacak şekilde hazırlama  
 Programlı yakalama API 'SI, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yakalama işlevselliği sağlamak Için uzak araçları kullanır. Yerel bilgisayarınızda Programlı yakalama kullanırken Uygulamanın çalıştırılacağı bilgisayarın uzak araçların yüklü olması gerekir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yerel bir bilgisayarda Programlı yakalama gerçekleştirdiğinizde çalışıyor olması gerekmez.  
  
 Bir bilgisayarda çalışan bir uygulamada uzaktan yakalama API 'Lerini kullanmak için, önce bu bilgisayara için uzak araçları yüklemeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Uzak araçların farklı sürümleri farklı donanım platformlarını destekler. Uzak araçların nasıl yükleneceği hakkında bilgi için Microsoft İndirmeleri web sitesindeki [Uzak Araçlar indirme sayfasına](https://visualstudio.microsoft.com/downloads#remote-tools) bakın.  
  
 Alternatif olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 32 bitlik uygulamalar için uzaktan yakalama gerçekleştirmek üzere gerekli bileşenleri yüklenir.  
  
> [!NOTE]
> , Dahil olmak üzere çoğu Windows masaüstü uygulaması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[win8](../includes/win8-md.md)] ARM cihazlarda DESTEKLENMEDIĞINDEN, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ARM cihazlarda grafik tanılamayı yakalamaya yönelik tek yol, programlama Ile birlikte uzak Araçlar kullanmaktır.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Uygulamanızı programlı yakalama kullanacak şekilde hazırlama  
 Grafik Tanılama araçlarını kullanmak için önce temel aldığı grafik bilgilerini yakalamanız gerekir. API 'yi kullanarak bilgileri programlı bir şekilde yakalayabilirsiniz `CaptureCurrentFrame` .  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Uygulamanızı ekran aracılığıyla grafik bilgilerini yakalamaya hazırlamak için  
  
1. `vsgcapture.h`Üstbilginin, uygulamanın kaynak koduna eklendiğinden emin olun. Tek bir konuma dahil edilebilir — örneğin, Programlı yakalama API 'sini çağırabileceğiniz kaynak kodu dosyasında veya birden çok kaynak kodu dosyasından API 'yi çağırmak için önceden derlenmiş bir üstbilgi dosyasında.  
  
2. Uygulamanın kaynak kodunda, geçerli karenin geri kalanını her yakalamak istediğinizde çağırın `g_pVsgDbg->CaptureCurrentFrame()` . Bu yöntem hiçbir parametre almaz ve bir değer döndürmez.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Grafik günlük dosyasının adını ve konumunu yapılandırma  
 Grafik günlüğü, ve makroları tarafından tanımlanan konumda oluşturulur `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` .  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Grafik günlük dosyasının adını ve konumunu yapılandırmak için  
  
- Grafik günlüğünün geçici dizine yazılmasını engellemek için, satırdan önce şunu `#include <vsgcapture.h>` ekleyin:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Bu değeri, grafik günlüğünü çalışma diziniyle ilişkili bir konuma veya tanımı `VSG_DEFAULT_RUN_FILENAME` mutlak bir yol ise mutlak bir yola yazmak için tanımlayabilirsiniz.  
  
- Grafik günlüğünü farklı bir konuma kaydetmek ya da satıra göre farklı bir dosya adı vermek için şunu `#include <vsgcapture.h>` ekleyin:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Bu adımı gerçekleştirmezseniz dosya adı default. vsglog olur. Tanımlamadıysanız `DONT_SAVE_VSGLOG_TO_TEMP` , dosyanın konumu geçici dizine görelidir; Aksi takdirde, çalışma diziniyle veya mutlak bir dosya adı belirttiyseniz başka bir konumda göreli olur.  
  
  [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]Uygulamalar için, Temp dizininin konumu her bir Kullanıcı ve uygulamaya özeldir ve genellikle C:\Users \\ *Kullanıcı*adı \AppData\Local\Packages \\ *paket aile adı*\tempstate gibi bir konumda bulunur \\ . Masaüstü uygulamaları için, Temp dizininin konumu her kullanıcıya özeldir ve genellikle C:\Users \\ *Kullanıcı adı*\AppData\Local\Temp gibi bir konumda bulunur \\ .  
  
> [!NOTE]
> Belirli bir konuma yazmak için bu konuma yazma izinlerinizin olması gerekir; Aksi takdirde bir hata oluşur. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]Uygulamaların veri yazabilecedikleri konum hakkında Masaüstü uygulamalarından daha kısıtlı olduğunu ve belirli konumlara yazmak için ek yapılandırma gerektirebileceğini unutmayın.  
  
### <a name="capturing-the-graphics-information"></a>Grafik bilgilerini yakalama  
 Programlı yakalama için uygulamayı hazırladıktan ve isteğe bağlı olarak grafik günlük dosyasının konumunu ve adını yapılandırdıktan sonra, uygulamayı derleyin ve verileri yakalamak için çalıştırın veya hata ayıklayın; [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Program aracılığıyla yakalama API 'sini kullandığınızda grafik tanılamayı başlatmayın. Grafik günlüğü, belirttiğiniz konuma yazılır. Bu günlüğün bu sürümünü korumak istiyorsanız, başka bir konuma taşıyın; Aksi takdirde, uygulamayı yeniden çalıştırdığınızda üzerine yazılır.  
  
> [!TIP]
> Programlı yakalama kullanırken grafik bilgilerini hala el ile yakalayabilirsiniz, ancak **yazdırma ekranına**basmanız yeterlidir. Programlı yakalama API 'SI tarafından yakalanmayan ek grafik bilgilerini yakalamak için bu tekniği kullanabilirsiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda grafik bilgilerinin programlı bir şekilde nasıl yakalanacağı gösterilmiştir. Sonraki adım olarak bu seçeneği göz önünde bulundurun:  
  
- Grafik Tanılama araçlarını kullanarak yakalanan grafik bilgilerini çözümlemeyi öğrenin. Bkz. [genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: grafik bilgilerini yakalama](../debugger/walkthrough-capturing-graphics-information.md)   
 [Grafik bilgilerini yakalama](../debugger/capturing-graphics-information.md)   
 [Komut Satırı Yakalama Aracı](../debugger/command-line-capture-tool.md)
