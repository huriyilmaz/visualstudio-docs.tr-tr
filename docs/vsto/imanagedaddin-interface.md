---
title: IManagedAddin arabirimi
description: IManagedAddin arabirimini kullanarak yönetilen eklentilerde yönetilen VSTO oluşturun.
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 283a8034aa49f5af06eae2c5d8176830b5f83cee
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134713635"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin arabirimi
  IManagedAddin arabirimini kullanarak, yönetilen eklentilerini yük VSTO bileşeni oluşturun. Bu arabirim 2007'de Microsoft Office eklendi.

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
 Aşağıdaki tabloda IManagedAddin arabirimi tarafından tanımlanan yöntemler listeleniyor.

|Adı|Açıklama|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Bir uygulama Microsoft Office eklentisinde yönetilen bir VSTO yüklerken çağrılır.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Bir uygulamanın yönetilen Microsoft Office kaldırmadan hemen önce VSTO çağrılır.|

## <a name="remarks"></a>Açıklamalar
 Microsoft Office, 2007 Microsoft Office sistemiyle başlayarak IManagedAddin arabirimini kullanarak Office VSTO yüklemenize yardımcı olur. IManagedAddin arabirimini, VSTO Eklenti yükleyicisi (VSTOLoader.dll) ve yerine yönetilen VSTO Eklentileri için kendi VSTO Eklenti yükleyicinizi ve çalışma zamanlarınızı *oluşturmak* için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerçekleştirebilirsiniz. Daha fazla bilgi için [bkz. VSTO Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

## <a name="how-managed-add-ins-are-loaded"></a>Yönetilen Eklentiler nasıl yüklenir?
 Bir uygulama başlatıldığında aşağıdaki adımlar gerçekleşir:

1. Uygulama, VSTO kayıt defteri anahtarı altındaki girdileri arayarak eklentileri keşfeder:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Bu kayıt defteri anahtarının altındaki her giriş, eklentinin VSTO kimliğidir. Genellikle, bu eklenti derlemesi VSTO adıdır.

2. Uygulama, `Manifest` eklentinin her bir girişi için girdinin VSTO bir girişe başvurur.

    Yönetilen VSTO Eklentileri, bir bildirimin tam yolunuHKEY_CURRENT_USER\Software\Microsoft\Office`Manifest` **\\ _\<application name>_ \Addins altındaki girdide \\ _\<add-in ID>_ depolar.** Bildirim, eklentiyi yüklemeye yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML VSTO dosyasıdır.

3. Uygulama bir giriş `Manifest` bulursa, uygulama, Eklenti yükleyici bileşenine VSTO yönetilen bir bileşeni yüklemeye çalışır. Uygulama bunu IManagedAddin arabirimini uygulayan bir COM nesnesi oluşturmayı denerek yapar.

    , bir VSTO yükleyici bileşeni (VSTOLoader.dll) içerir veya IManagedAddin arabirimini kullanarak kendi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bileşeninizi oluşturabilirsiniz.**

4. Uygulama [IManagedAddin::Load](../vsto/imanagedaddin-load.md) yöntemini çağırarak girdinin değerini `Manifest` geçer.

5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) yöntemi, VSTO Eklentiyi yüklemek için gereken görevleri gerçekleştirir; örneğin, yüklenen VSTO Eklenti için uygulama etki alanını ve güvenlik ilkesi yapılandırma.

   Uygulamaların yönetilen eklentileri bulmak Microsoft Office yüklemek için VSTO kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. VSTO için kayıt [defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin uygulama kılavuzu
 IManagedAddin'i kullanıyorsanız, aşağıdaki CLSID'i kullanarak uygulamasını içeren DLL'i kaydetmelisiniz:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office bu CLSID'i kullanarak IManagedAddin uygulayan COM nesnesini oluşturur.

> [!CAUTION]
> Bu CLSID, içinde *VSTOLoader.dll* tarafından da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanılır. Bu nedenle, kendi VSTO Eklenti yükleyici ve çalışma zamanı bileşeninizi oluşturmak için IManagedAddin kullanırsanız, bileşeninizi kullanan VSTO Eklentileri çalıştıran bilgisayarlara [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dağıtamazsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio&#41;'de &#40;Office API başvurusu Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
