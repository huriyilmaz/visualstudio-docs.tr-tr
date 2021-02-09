---
title: SetWefProcessId yöntemi
description: SetWefProcessId yönteminin, Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısını nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882414"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId yöntemi
  Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısı sağlar.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*Dwprocessıd*|WEF içeriğini çalıştırmak için kullanılacak işlem tanımlayıcısı.|

## <a name="return-value"></a>Döndürülen değer
 Metodun başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, WEF içerik işlemi oluşturulduktan sonra, ancak WEF içeriği çalıştırılmadan önce çağrılmalıdır.

 Geliştirme ortamının WEF içerik işlemine bir hata ayıklayıcı eklemesi istiyorsanız, bu yöntemin uygulamanızda bu işlemi gerçekleştirmesi gerekir.
