---
title: Özel Hata Ayıklama AltyapısıNı | Microsoft Docs
description: Hata ayıklama altyapısının kendisini com kurallarına göre sınıf fabrikası olarak kaydetmenin yanı sıra kayıt defteri aracılığıyla Visual Studio olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d1537958b783d35be4d95303ecdd19fe03dababae1b411bd261230ef27ab2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377066"
---
# <a name="register-a-custom-debug-engine"></a>Özel hata ayıklama altyapısını kaydetme
Hata ayıklama altyapısının kendisini com kurallarına göre bir sınıf fabrikası olarak kaydetmesi ve Visual Studio kayıt defteri alt anahtarı Visual Studio kaydetmesi gerekir.

> [!NOTE]
> Öğretici: [ATL COM](/previous-versions/bb147024(v=vs.90))kullanarak hata ayıklama altyapısının bir parçası olarak inşa edilen TextInterpreter örneğinde hata ayıklama altyapısını kaydetme örneği bulabilirsiniz.

## <a name="dll-server-process"></a>DLL sunucusu işlemi
 Hata ayıklama altyapısı genellikle kendi DLL'sinde COM sunucusu olarak ayarlanır. Bu nedenle, hata ayıklama altyapısının sınıf fabrikasının CLSID'sini, Visual Studio com'a kaydetmesi gerekir. Ardından, hata ayıklama altyapısının desteklediği herhangi bir Visual Studio (ölçümler olarak da bilinir) kurmak için hata ayıklama altyapısının kendisini bu altyapıya kaydetmesi gerekir. Kayıt defteri alt anahtarına Visual Studio seçimi, hata ayıklama altyapısının desteklediği özelliklere bağlıdır.

 [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) yalnızca bir hata ayıklama altyapısını kaydetmek için gereken kayıt defteri konumlarını açıklamakla birlikte; Ayrıca, C++ geliştiricileri için kayıt defterinin daha kolay yönlendirilmesine neden olan bir dizi yararlı işlev ve bildirim içeren *dbgmetric.lib* kitaplığını açıklar.

### <a name="example"></a>Örnek
 Aşağıdaki örnekte (TextInterpreter örneğinden), bir hata ayıklama altyapısını veritabanına kaydetmek için `SetMetric` işlevinin *(dbgmetric.lib'den)* nasıl Visual Studio. Geçirilen ölçümler *dbgmetric.lib içinde de tanımlanır.*

> [!NOTE]
> TextInterpreter temel bir hata ayıklama altyapısıdır; diğer özellikleri ayarlamaz ve bu nedenle kaydetmez. Daha eksiksiz bir hata ayıklama altyapısı, hata ayıklama altyapısının desteklediği her özellik için bir çağrı veya bunların `SetMetric` eşdeğerlerinin tam listesine sahip olur.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Öğretici: ATL COM kullanarak hata ayıklama altyapısını bina](/previous-versions/bb147024(v=vs.90))