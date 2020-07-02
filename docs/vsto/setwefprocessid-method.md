---
title: SetWefProcessId yöntemi
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537338"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId yöntemi
  Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısı sağlar.

## <a name="syntax"></a>Söz dizimi

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
