---
title: 'İzlenecek yol: grafik bilgilerini programlama yoluyla yakalama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7533c205b95b016c43bd2eef614b4c2825596e74
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835660"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>İzlenecek Yol: Grafik Bilgilerini Programla Yakalama
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Direct3D uygulamasından grafik bilgilerini programlı bir şekilde yakalamak için grafik tanılama kullanabilirsiniz.

Programlı yakalama, gibi senaryolarda faydalıdır:

- Grafik uygulamanız, bir dokusunu oluştururken olduğu gibi swapzincirini kullanmazsa programlı olarak yakalamayı başlatın.

- Uygulamanız, hesaplamalar gerçekleştirmek için DirectCompute kullandığında olduğu gibi, uygulama hiç işlenmezse, programlı olarak yakalamayı başlatın.

- `CaptureCurrentFrame`Bir işleme sorunu, el ile test sırasında tahmin etmek ve yakalamak zor olduğunda, ancak çalışma zamanında uygulamanın durumu hakkında bilgiler kullanılarak programlı bir şekilde tahmin edilebilir.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a>Windows 10 ' da programlı yakalama
Bu izlenecek yolda, güçlü yakalama yöntemini kullanan Windows 10 ' da DirectX 11,2 API kullanan uygulamalarda Programlı yakalama gösterilmektedir.

Bu bölümde bu görevlerin nasıl yapılacağı gösterilmektedir:

- Uygulamanızı programlı yakalama kullanacak şekilde hazırlama

- IDXGraphicsAnalysis arabirimini alma

- Graf bilgilerini yakalama

> [!NOTE]
> Programlı yakalama 'nın önceki uygulamaları, Yakalama işlevselliği sağlamak için Visual Studio için Uzak Araçlar güvendi.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Uygulamanızı programlı yakalama kullanacak şekilde hazırlama
Uygulamanızda Programlı yakalama 'yı kullanmak için gereken üst bilgileri içermesi gerekir. Bu üstbilgiler Windows 10 SDK 'sının bir parçasıdır.

##### <a name="to-include-programmatic-capture-headers"></a>Programlı yakalama üstbilgilerini dahil etmek için

- Bu üst bilgileri IDXGraphicsAnalysis arabirimini tanımlayabileceğiniz kaynak dosyasına ekleyin:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Windows 10 uygulamalarınızda Programlı yakalama gerçekleştirmek için Windows 8,0 ve önceki sürümlerde Programlı yakalamayı destekleyen vsgcapture. h başlık dosyasını eklemeyin. Bu üstbilgi DirectX 11,2 ile uyumsuzdur. D3d11_2. h üst bilgisi eklendikten sonra bu dosya varsa, derleyici bir uyarı verir. Vsgcapture. h, d3d11_2. h öncesinde varsa, uygulama başlatılmaz.

    > [!NOTE]
    > Makinenizde Haziran 2010 DirectX SDK 'Sı yüklüyse ve projenizin içerme yolu içeriyorsa `%DXSDK_DIR%includex86` , bunu ekleme yolunun sonuna taşıyın. Kitaplık yolunuzda aynısını yapın.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini alma
DirectX 11,2 ' den grafik bilgilerini yakalamadan önce DXGI hata ayıklama arabirimini almanız gerekir.

> [!IMPORTANT]
> Programlı yakalama kullanırken, uygulamanızı hala grafik tanılama (alt + F5 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ) altında veya [komut satırı yakalama aracı](command-line-capture-tool.md)altında çalıştırmanız gerekir.

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis arabirimini almak için

- DXGI hata ayıklama arabirimine IDXGraphicsAnalysis arabirimini bağlamak için aşağıdaki kodu kullanın.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  `HRESULT`Kullanmadan önce geçerli bir arabirim aldığınızdan emin olmak Için [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) tarafından döndürülen ' i kontrol ettiğinizden emin olun:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > `DXGIGetDebugInterface1` `E_NOINTERFACE` () Döndürürse `error: E_NOINTERFACE No such interface supported` , uygulamanın grafik tanılama (alt + F5) altında çalıştığından emin olun [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

### <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
Artık geçerli bir `IDXGraphicsAnalysis` arabiriminiz olduğuna göre, `BeginCapture` `EndCapture` grafik bilgilerini yakalamak için ve kullanabilirsiniz.

##### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için

- Grafik bilgilerini yakalamaya başlamak için şunu kullanın `BeginCapture` :

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Yakalama çağrıldığında hemen başlar `BeginCapture` ; sonraki çerçevenin başlamasını beklemez. Yakalama, geçerli çerçeve sunulduktan sonra ya da çağırdığınızda `EndCapture` :

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Çağrısından sonra `EndCapture` grafik nesnesini serbest bırakın.

## <a name="next-steps"></a>Sonraki Adımlar
Bu kılavuzda grafik bilgilerinin programlı bir şekilde nasıl yakalanacağı gösterilmiştir. Sonraki adım olarak bu seçeneği göz önünde bulundurun:

- Grafik Tanılama araçlarını kullanarak yakalanan grafik bilgilerini çözümlemeyi öğrenin. Bkz. [genel bakış](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)
- [Grafik Bilgilerini Yakalama](capturing-graphics-information.md)
- [Komut Satırı Yakalama Aracı](command-line-capture-tool.md)
