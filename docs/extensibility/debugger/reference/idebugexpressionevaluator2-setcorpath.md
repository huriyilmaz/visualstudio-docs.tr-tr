---
description: Hata ayıklayıcısında yüklenen ortak dil çalışma zamanının (CLR) yolunu ayarlar.
title: IDebugExpressionEvaluator2::SetCorPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetCorPath
- IDebugExpressionEvaluator2::SetCorPath
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f49cb103dd5737e92053a2097f320bf5c24d1dea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138646"
---
# <a name="idebugexpressionevaluator2setcorpath"></a>IDebugExpressionEvaluator2::SetCorPath
Hata ayıklayıcısında yüklenen ortak dil çalışma zamanının (CLR) yolunu ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetCorPath(
   LPCOLESTR pcstrCorPath
);
```

```csharp
int SetCorPath(
   string pcstrCorPath
);
```

## <a name="parameters"></a>Parametreler
`pcstrCorPath`\
[in] Hata ayıklayıcıda yüklenen CLR'nin yolu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) arabirimini ortaya çıkaran **ExpressionEvaluatorPackage** nesnesi için bu yöntemin nasıl uygulandığını gösterir.

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::SetCorPath(LPCOLESTR pcstrCorPath)
{
    VerifyInPtr(pcstrCorPath);
    HRESULT hr = E_FAIL;

    VBEECompilerSingleton *pVBEECompilerSingleton = VBEECompilerSingleton::Instance();

    if (pVBEECompilerSingleton)
    {
        pVBEECompilerSingleton->LockEECompiler();

        try
        {
            if (!m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))
            {
                CComObject<CVBEECompilerHost> *pEECompilerHost;

                if (SUCCEEDED(CComObject<CVBEECompilerHost>::CreateInstance(&pEECompilerHost)))
                {
                    pEECompilerHost->AddRef();
                    pEECompilerHost->Init(pcstrCorPath);

                    CComPtr<IVbCompilerHost> srpVBHost;
                    HRESULT hr2 = pEECompilerHost->QueryInterface(IID_IVbCompilerHost, (void **)&srpVBHost);

                    pEECompilerHost->Release();

                    if (SUCCEEDED(hr2))
                    {
                        m_pCompiler->RegisterEECompilerHost(srpVBHost);
                    }
                }
            }
            else
            {
                hr = S_OK;
            }

            if (m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))
            {
                ULONG cErrors = 0;
                ULONG cWarnings = 0;

                m_pCompiler->CompileToBound(m_pCompilerHost, &cErrors, &cWarnings, NULL);

                // This needs to happen after bound
                if (m_pCompilerHost->GetVbLibraryType() == TLB_AutoDetect)
                {
                    m_pCompilerHost->AutoSetVbLibraryType();
                }

                VSASSERT(m_pCompiler && m_pCompilerHost && m_pCompilerHost->GetIntrinsicSymbol(t_i4) != NULL, "Invalid state");

                if (cErrors + cWarnings > 0)
                {
                    VSFAIL("Errors from mscorlib.dll and vb runtime!");
                    __leave;
                }

                hr = S_OK;
            }
            else
            {
                VSFAIL("FindCompilerHost shouldn't have failed!");
            }
        }
        catch_hresult;

        VSASSERT(m_pCompilerHost->GetComPlusProject()->GetCompState() >= CS_Bound, "Debugger mscorlib not in bound state");

        pVBEECompilerSingleton->UnlockEECompiler();
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
