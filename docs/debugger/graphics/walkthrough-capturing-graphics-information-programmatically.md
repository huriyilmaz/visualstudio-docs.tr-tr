---
title: Grafik bilgilerini program aracılığıyla yakalama
description: Direct3D uygulamasından Visual Studio Grafik Tanılama bilgilerini program aracılığıyla yakalamak için nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c251ee95d86431a64f3c5e7c1f103b98fba3abc632de3b0db2f00d0e95a7549
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239876"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>İzlenecek yol: Grafik Bilgilerini Program Aracılığıyla Yakalama
Direct3D Grafik Tanılama grafik bilgilerini program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aracılığıyla yakalamak için Grafik Tanılama'yi kullanabilirsiniz.

Programlı yakalama, şu senaryolarda yararlıdır:

- Grafik uygulamanız dokuya işlemesi gibi swapchain'i kullanmazsa program aracılığıyla yakalamaya başlayabilirsiniz.

- Örneğin, hesaplamaları gerçekleştirmek için DirectCompute'ı kullandığında, uygulama hiç iş işlemezse, yakalamayı program aracılığıyla başlatabilirsiniz.

- El ile test için tahmin etmek ve yakalamak zor ancak çalışma zamanında uygulamanın durumu hakkında bilgiler kullanılarak program aracılığıyla tahmin edilebilen bir işleme `CaptureCurrentFrame` sorunu olduğunda çağrısı.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a>Windows 10'de programlı yakalama
Bu adım adım kılavuzda, sağlam yakalama yöntemini kullanan directX 11.2 API'sini Windows 10 uygulamalarda programlı yakalamayı gösterir.

Bu bölümde, bu görevlerin nasıl gerçekleştirllleri gösterir:

- Programlı yakalama kullanmak için uygulama hazırlama

- IDXGraphicsAnalysis arabirimini alma

- Graf bilgilerini yakalama

> [!NOTE]
> Programlı yakalamanın önceki uygulamaları, yakalama işlevi Visual Studio için Uzak Araçlar özelliklerine dayanıyordu.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Programlı yakalama kullanmak için uygulama hazırlama
Uygulamanıza programlı yakalama kullanmak için gerekli üst bilgileri içermesi gerekir. Bu üst bilgiler, Windows 10 SDK'sı kapsamındadır.

##### <a name="to-include-programmatic-capture-headers"></a>Programlı yakalama üst bilgilerini dahil etmek için

- IDXGraphicsAnalysis arabirimini tanımladığınız kaynak dosyaya şu üst bilgileri girin:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Windows 8.0 ve önceki sürümlerde programlı yakalamayı destekleyen vsgcapture.h üst bilgi dosyasını, Windows 10 uygulamalarınıza dahil edin. Bu üst bilgi DirectX 11.2 ile uyumsuz. D3d11_2.h üst bilgisi dahil edildikten sonra bu dosya dahil edilirse, derleyici bir uyarı gösterir. vsgcapture.h, d3d11_2.h'den önce dahil edilirse uygulama başlamaz.

    > [!NOTE]
    > Makinenize Haziran 2010 DirectX SDK'sı yüklüyse ve projenizin dahil etme yolu içeriyorsa, bunu dahil etme `%DXSDK_DIR%includex86` yolunun sonuna taşımanız gerekir. Kitaplık yolunuz için de aynısını kullanın.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini alma
DirectX 11.2'den grafik bilgilerini yakalamadan önce DXGI hata ayıklama arabirimini alasiniz.

> [!IMPORTANT]
> Programlı yakalama kullanırken, uygulamalarınızı grafik tanılamaları altında ('da Alt+F5) veya Komut Satırı Yakalama Aracı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [altında çalıştırmanız gerekir.](command-line-capture-tool.md)

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini almak için

- IDXGraphicsAnalysis arabirimini DXGI hata ayıklama arabirimine bağlayan aşağıdaki kodu kullanın.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  `HRESULT` [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) tarafından döndürülenleri kontrol edin ve bunu kullanmadan önce geçerli bir arabirim elde edin:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > döndürürse `DXGIGetDebugInterface1` `E_NOINTERFACE` ( ), `error: E_NOINTERFACE No such interface supported` uygulamanın grafik tanılaması altında ('da Alt+F5) çalıştırıldıklerinden emin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olun.

### <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
Geçerli bir arabirime sahip `IDXGraphicsAnalysis` olduğunuza göre, grafik bilgilerini yakalamak `BeginCapture` için ve `EndCapture` kullanabilirsiniz.

##### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için

- Grafik bilgilerini yakalamaya başlamak için `BeginCapture` kullanın:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Yakalama, `BeginCapture` çağrıldıktan hemen sonra başlar; sonraki karenin başlamayı beklemez. Yakalama, geçerli çerçeve sunlarda veya çağrısında durduğunda `EndCapture` durur:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- çağrısının ardından `EndCapture` grafik nesnesini serbest bırakın.

## <a name="next-steps"></a>Sonraki Adımlar
Bu kılavuzda grafik bilgilerini program aracılığıyla nasıl yakalayabilirsiniz? Bir sonraki adım olarak şu seçeneği göz önünde önünde belirtin:

- Yakalanan grafik bilgilerini analiz etmek için Grafik Tanılama öğrenin. Bkz. [Genel Bakış.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)
- [Grafik Bilgilerini Yakalama](capturing-graphics-information.md)
- [Komut Satırı Yakalama Aracı](command-line-capture-tool.md)
