---
title: IManagedAddin::Load
description: Yönetilen bir VSTO yüklendiğinde çağrılır.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032660"
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
 Bildirim, eklentiyi yüklemeye yardımcı olmak için kullanılan bilgileri sağlayan bir dosyadır (genellikle bir XML VSTO dosyasıdır. Örneğin, bir bildirim, VSTO Eklentisi yüklendiğinde örneği için giriş noktası sınıfı ve VSTO derlemenin konumunu belirtebilirsiniz.

 *bstrManifestURL* parametresi, VSTO `Manifest` Add-in için **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** kayıt defteri anahtarı altındaki girdinin değerini içerir. Daha fazla bilgi için bkz. [IManagedAddin arabirimi.](../vsto/imanagedaddin-interface.md)

 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) yöntemini, yüklenen uygulama etki alanı ve güvenlik VSTO yapılandırma gibi görevleri gerçekleştirin.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin Arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
