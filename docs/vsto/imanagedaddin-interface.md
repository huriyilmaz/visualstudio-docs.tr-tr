---
title: IManagedAddin arabirimi
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b436d76164b1744cffe16593149f64d219d04bf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541134"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin arabirimi
  Yönetilen VSTO Eklentilerini yükleyen bir bileşen oluşturmak için IManagedAddin arabirimini uygulayın. Bu arabirim 2007 Microsoft Office sistemine eklenmiştir.

## <a name="syntax"></a>Syntax

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, IManagedAddin arabirimi tarafından tanımlanan Yöntemler listelenmiştir.

|Ad|Açıklama|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office bir uygulama yönetilen bir VSTO eklentisini yüklediğinde çağırılır.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office bir uygulama, yönetilen VSTO eklentisini kaldırmadan hemen önce çağırılır.|

## <a name="remarks"></a>Açıklamalar
 Microsoft Office uygulamalar, 2007 Microsoft Office sisteminden başlayarak Office VSTO Eklentilerini yüklemeye yardımcı olması için IManagedAddin arabirimini kullanın. VSTO eklentisi yükleyicisini (*VSTOLoader.dll*) kullanmak yerine, yönetilen VSTO eklentileri IÇIN kendi VSTO eklenti yükleyicinizi ve çalışma zamanını oluşturmak üzere IManagedAddin arabirimini uygulayabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Yönetilen eklentiler nasıl yüklenir
 Bir uygulama başlatıldığında aşağıdaki adımlar oluşur:

1. Uygulama, aşağıdaki kayıt defteri anahtarı altındaki girdileri arayarak VSTO Eklentilerini bulur:

    **HKEY_CURRENT_USER \Software\Microsoft\Office \\ *\<application name>* \ eklentileri\\**

    Bu kayıt defteri anahtarı altındaki her giriş, VSTO eklentisinin benzersiz KIMLIĞIDIR. Genellikle, bu, VSTO eklenti derlemesinin adıdır.

2. Uygulama, `Manifest` her VSTO eklentisi için giriş altında bir giriş arar.

    Yönetilen VSTO eklentileri `Manifest` **HKEY_CURRENT_USER \Software\microsoft\office \\ _\<application name>_ \\ _\<add-in ID>_ \ AddIns**altındaki girişte bir bildirimin tam yolunu saklayabilir. Bildirim, VSTO eklentisini yüklemeye yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML dosyasıdır).

3. Uygulama bir `Manifest` giriş bulursa, uygulama yönetilen BIR VSTO eklentisi yükleyici bileşeni yüklemeye çalışır. Uygulama, IManagedAddin arabirimini uygulayan bir COM nesnesi oluşturmaya çalışırken bunu yapar.

    , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] BIR VSTO eklentisi yükleyici bileşeni (*VSTOLoader.dll*) içerir veya IManagedAddin arabirimini uygulayarak kendi kendinize de oluşturabilirsiniz.

4. Uygulama, [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) yöntemini çağırır ve girdinin değerini geçirir `Manifest` .

5. [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) yöntemi, YÜKLENMEKTE olan VSTO eklentisi için uygulama etki alanını ve güvenlik ilkesini yapılandırma gıbı, VSTO eklentisini yüklemek için gereken görevleri gerçekleştirir.

   Microsoft Office uygulamalar tarafından yönetilen VSTO eklentileri bulma ve yükleme için kullanılan kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin uygulama kılavuzu
 IManagedAddin uygularsanız, uygulamayı içeren DLL 'yi aşağıdaki CLSID 'yi kullanarak kaydetmeniz gerekir:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office uygulamalar, IManagedAddin uygulayan COM nesnesini oluşturmak için bu CLSID 'yi kullanır.

> [!CAUTION]
> Bu CLSID, içinde *VSTOLoader.dll* tarafından da kullanılır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bu nedenle, kendi VSTO eklenti yükleyicinizi ve çalışma zamanı bileşenini oluşturmak için IManagedAddin kullanıyorsanız, bileşeninizi ' i kullanan VSTO Eklentilerini çalıştıran bilgisayarlara dağıtamazsınız [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen API başvurusu &#40;Visual Studio 'da Office geliştirme&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
