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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e066da4c1c294669ad4baf4932c6d934e283a9c4914e9c23efc45ef3b1f2335d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226108"
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
