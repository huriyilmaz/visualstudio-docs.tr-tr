---
title: SetWefProcessId yöntemi
description: SetWefProcessId yönteminin Web Uzantıları Çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısını nasıl sağladığını öğrenin.
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
ms.openlocfilehash: 6d3fee5832c96de8fddec605399c9bd6ef565c2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032179"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId yöntemi
  Web Uzantıları Çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısını sağlar.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*dwProcessId*|WEF içeriğini çalıştırmak için kullanılacak işlem tanımlayıcısı.|

## <a name="return-value"></a>Döndürülen değer
 Yöntemin başarıyla tamamlandıktan sonra tamamlandıktan sonra bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem WEF içerik işlemi oluşturulduktan sonra ancak herhangi bir WEF içeriği çalışmadan önce çağrıl gerekir.

 Geliştirme ortamının WEF içerik sürecine bir hata ayıklayıcı eklemesi gerekirse, ortamın bu yöntemi uygulamanıza bu işlemi gerçekleştirmesi gerekir.
