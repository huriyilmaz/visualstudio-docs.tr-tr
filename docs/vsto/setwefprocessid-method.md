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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524328"
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
