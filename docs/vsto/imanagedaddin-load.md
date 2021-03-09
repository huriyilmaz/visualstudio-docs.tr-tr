---
title: IManagedAddin::Load
description: Yönetilen bir VSTO eklentisi yüklendiğinde çağırılır.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469768"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Yönetilen bir VSTO eklentisi yüklendiğinde çağırılır.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*bstrManifestURL 'Si*|VSTO eklentisi bildiriminin tam yolu.|
|*pdispApplication*|VSTO eklentisini yükleyen konak uygulamasını temsil eden bir IDispatch işaretçisi.|

## <a name="return-value"></a>Dönüş Değeri
 Metodun başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Bildirim, VSTO eklentisini yüklemeye yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML dosyasıdır). Örneğin, bir bildirim VSTO eklenti derlemesinin konumunu ve VSTO eklentisi yüklendiğinde örnek oluşturmak için giriş noktası sınıfını belirtebilir.

 *BstrManifestURL* parametresi, `Manifest` VSTO eklentisinin **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \\ _\<add-in ID>_ \addıns** kayıt defteri anahtarı altındaki girişin değerini içerir. Daha fazla bilgi için bkz. [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).

 Yüklenmekte olan VSTO eklentisi için uygulama etki alanını ve güvenlik ilkesini yapılandırma gibi görevleri gerçekleştirmek için [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) yöntemini uygulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin Arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
