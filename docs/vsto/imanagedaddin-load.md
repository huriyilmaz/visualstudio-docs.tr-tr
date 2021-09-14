---
title: IManagedAddin::Load
description: yönetilen bir VSTO eklentisi yüklendiğinde çağırılır.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7be4be6b08c5ea9b0813e4782a0ac1a77cec2890
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726707"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  yönetilen bir VSTO eklentisi yüklendiğinde çağırılır.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*bstrManifestURL 'Si*|VSTO eklentisi için bildirimin tam yolu.|
|*pdispApplication*|VSTO eklentisini yükleyen ana bilgisayar uygulamasını temsil eden bir ıdispatch işaretçisi.|

## <a name="return-value"></a>Dönüş Değeri
 Metodun başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 bildirim, VSTO eklentisinin yüklenmesine yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML dosyasıdır). örneğin, bir bildirim VSTO eklenti derlemesinin konumunu ve VSTO eklentisi yüklendiğinde örnek oluşturmak için giriş noktası sınıfını belirtebilir.

 *bstrmanifesturl* parametresi, `Manifest` VSTO eklentisinin **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \\ _\<add-in ID>_ \addıns** kayıt defteri anahtarı altındaki girişin değerini içerir. Daha fazla bilgi için bkz. [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).

 yüklenmekte olan VSTO eklentisi için uygulama etki alanını ve güvenlik ilkesini yapılandırma gibi görevleri gerçekleştirmek için [ımanagedaddin:: Load](../vsto/imanagedaddin-load.md) yöntemini uygulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin Arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
