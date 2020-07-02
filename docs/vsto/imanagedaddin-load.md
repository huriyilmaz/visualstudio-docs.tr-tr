---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1307d720e005855770ee68659374dbbfae247d65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541043"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Yönetilen bir VSTO eklentisi yüklendiğinde çağırılır.

## <a name="syntax"></a>Söz dizimi

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

 *BstrManifestURL* parametresi, `Manifest` VSTO eklentisi için **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \addıns \\ _\<add-in ID>_ ** kayıt defteri anahtarı altındaki girişin değerini içerir. Daha fazla bilgi için bkz. [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).

 Yüklenmekte olan VSTO eklentisi için uygulama etki alanını ve güvenlik ilkesini yapılandırma gibi görevleri gerçekleştirmek için [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) yöntemini uygulayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin Arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
