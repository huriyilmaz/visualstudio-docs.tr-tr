---
title: 'IDebugExpressionEvaluator2:: SetCorPath | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetCorPath
- IDebugExpressionEvaluator2::SetCorPath
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bea93c3f10a946353c52231d0ac3802f0b2ec8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729268"
---
# <a name="idebugexpressionevaluator2setcorpath"></a>IDebugExpressionEvaluator2::SetCorPath
Hata ayıklayıcıda yüklenen ortak dil çalışma zamanının (CLR) yolunu ayarlar.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Hata ayıklayıcıda yüklenen CLR 'nin yolu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) arabirimini kullanıma sunan bir **ExpressionEvaluatorPackage** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

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
