---
title: IManagedAddin arabirimi
description: yönetilen VSTO eklentilerini yükleyen bir bileşen oluşturmak için ımanagedaddin arabirimini uygulayın.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8fe3ac3ca61d54f14cd72387623461dd5057740b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633854"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin arabirimi
  yönetilen VSTO eklentilerini yükleyen bir bileşen oluşturmak için ımanagedaddin arabirimini uygulayın. bu arabirim 2007 Microsoft Office sistemine eklenmiştir.

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
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office bir uygulama yönetilen VSTO eklentisini kaldırmadan hemen önce çağırılır.|

## <a name="remarks"></a>Açıklamalar
 Microsoft Office uygulamalar, 2007 Microsoft Office sisteminden başlayarak, Office VSTO eklentileri yüklemeye yardımcı olması için ımanagedaddin arabirimini kullanın. VSTO eklenti yükleyicisini (*VSTOLoader.dll*) ve kullanmak yerine, yönetilen VSTO eklentileri için kendi VSTO eklenti yükleyicinizi ve çalışma zamanını oluşturmak üzere ımanagedaddin arabirimini uygulayabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . daha fazla bilgi için bkz. [VSTO eklentilerin mimarisi](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Yönetilen eklentiler nasıl yüklenir
 Bir uygulama başlatıldığında aşağıdaki adımlar oluşur:

1. uygulama, aşağıdaki kayıt defteri anahtarı altındaki girdileri arayarak VSTO eklentileri bulur:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \addıns\\**

    bu kayıt defteri anahtarı altındaki her giriş, VSTO eklentisinin benzersiz kimliğidir. genellikle, bu VSTO eklenti derlemesinin adıdır.

2. uygulama, `Manifest` her bir VSTO eklentisi için giriş altında bir giriş arar.

    yönetilen VSTO eklentiler, bir bildirimin tam yolunu `Manifest` **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \addıns \\ _\<add-in ID>_** altındaki girişte depolayabilirler. bildirim, VSTO eklentisinin yüklenmesine yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML dosyasıdır).

3. uygulama bir `Manifest` giriş bulursa, uygulama yönetilen bir VSTO eklentisi yükleyici bileşeni yüklemeye çalışır. Uygulama, IManagedAddin arabirimini uygulayan bir COM nesnesi oluşturmaya çalışırken bunu yapar.

    , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bir VSTO eklentisi yükleyici bileşeni (*VSTOLoader.dll*) içerir veya ımanagedaddin arabirimini uygulayarak kendi kendinize de oluşturabilirsiniz.

4. Uygulama, [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) yöntemini çağırır ve girdinin değerini geçirir `Manifest` .

5. [ımanagedaddin:: load](../vsto/imanagedaddin-load.md) yöntemi, yüklenmekte olan VSTO eklentisi için uygulama etki alanını ve güvenlik ilkesini yapılandırma gibi VSTO eklentisini yüklemek için gereken görevleri gerçekleştirir.

   Microsoft Office uygulamalar tarafından yönetilen VSTO eklentileri bulma ve yükleme için kullanılan kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin uygulama kılavuzu
 IManagedAddin uygularsanız, uygulamayı içeren DLL 'yi aşağıdaki CLSID 'yi kullanarak kaydetmeniz gerekir:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office uygulamalar, ımanagedaddin uygulayan COM nesnesini oluşturmak için bu clsıd 'yi kullanır.

> [!CAUTION]
> Bu CLSID, içinde *VSTOLoader.dll* tarafından da kullanılır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . bu nedenle, kendi VSTO eklentisi yükleyicisini ve çalışma zamanı bileşenini oluşturmak için ımanagedaddin kullanıyorsanız, bileşeninizi, ' a bağlı VSTO eklentileri çalıştıran bilgisayarlara dağıtamazsınız [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [yönetilmeyen apı başvurusu &#40;Office geliştirme Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
