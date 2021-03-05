---
description: ', Hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullanacağı geri çağırma arabirimini belirtmek için ifade değerlendirici (EE) sağlar.'
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc858ab5d26ccffe33d26296e033ac577ddba440
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152396"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
, Hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullanacağı geri çağırma arabirimini belirtmek için ifade değerlendirici (EE) sağlar.

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
