---
title: IManagedAddin::Load
description: Yönetilen bir VSTO yüklendiğinde çağrılır.
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 6315d434f83974365059f7d828b6aa04a40960f6
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134713648"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Yönetilen bir VSTO yüklendiğinde çağrılır.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*bstrManifestURL*|VSTO Eklenti için bildirimin tam yolu.|
|*pdispApplication*|IDispatch'e, eklentiyi yük eden konak uygulamayı temsil eden VSTO işaretçisi.|

## <a name="return-value"></a>Dönüş Değeri
 Yöntemin başarıyla tamamlandıktan sonra tamamlandıktan sonra bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Bildirim, eklentiyi yüklemeye yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML VSTO dosyasıdır. Örneğin, bir bildirim, VSTO Eklenti yüklendiğinde örneği VSTO add-in derlemesi ve giriş noktası sınıfı konumunu belirtebilirsiniz.

 *bstrManifestURL* parametresi,HKEY_CURRENT_USER\Software\Microsoft\Office`Manifest` **\\ _\<application name>_ \\ _\<add-in ID>_ Addins** kayıt defteri anahtarı altındaki girişin değerini VSTO içerir. Daha fazla bilgi için bkz. [IManagedAddin arabirimi.](../vsto/imanagedaddin-interface.md)

 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) yöntemini, yüklenen uygulama etki alanı ve güvenlik VSTO yapılandırma gibi görevleri gerçekleştirin.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin Arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
