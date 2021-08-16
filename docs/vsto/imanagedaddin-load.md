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
ms.openlocfilehash: f30c6a45d4ff43811e34ec4357961e0c80ae0eb9637b9fd7aee661a54296f75f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366075"
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
