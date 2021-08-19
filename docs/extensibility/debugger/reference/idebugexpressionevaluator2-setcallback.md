---
description: ", hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullanacağı geri çağırma arabirimini belirtmek için ifade değerlendirici ' i (EE) sağlar."
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66d69dc119b23f06efebb9c8d87cf96792118bd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138672"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
, hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullanacağı geri çağırma arabirimini belirtmek için ifade değerlendirici ' i (EE) sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
'ndaki Ayarlar geri çağırması için kullanılacak arabirim.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem, bir ifade değerlendiricisi 'nin ölçüm ayarlarını okumak için kullanabileceği oturum hata ayıklama Yöneticisi için bir arabirim sağlar. Bilgisayardaki ölçümleri okumak için uzaktan hata ayıklama için faydalıdır [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="example"></a>Örnek
Aşağıdaki örnekler, [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) arabirimini kullanıma sunan bir **Cee** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
