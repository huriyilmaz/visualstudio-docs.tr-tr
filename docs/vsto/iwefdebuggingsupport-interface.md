---
title: IWefDebuggingSupport arabirimi
description: Microsoft Office uygulamalarda hata ayıklamayı kolaylaştırmak için Visual Studio gibi bir hata ayıklama ortamını nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: d6ea24abb178b177103be66acc274b3f27f99818
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134714271"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport arabirimi
  Office için uygulamalarda hata ayıklamayı kolaylaştırmak için Visual Studio gibi bir hata ayıklama ortamı tarafından uygulanır. Word veya Excel gibi Office uygulaması, bu arayüzü Visual Studio alır ve ardından hata ayıklama oturumu sırasında belirli noktalarda arabirimdeki yöntemleri çağırır.

## <a name="syntax"></a>Syntax

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda IWefDebuggingSupport arabiriminin tanımladığı Yöntemler listelenmiştir.

|Adı|Açıklama|
|----------|-----------------|
|[Getautoınserbir yöntemi](../vsto/getautoinsertextensions-method.md)|hata ayıklama sırasında otomatik olarak eklenecek Office uygulamalar hakkında bilgi alır.|
|[SetWefProcessId yöntemi](../vsto/setwefprocessid-method.md)|Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısı sağlar.|
