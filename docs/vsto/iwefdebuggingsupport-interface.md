---
title: IWefDebuggingSupport arabirimi
description: Uygulama uygulamalarının hata ayıklamasını kolaylaştırmak için Visual Studio gibi bir hata ayıklama Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f6c6e039a04f8e30cec024370fed94c0f025f51f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147835"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport arabirimi
  Uygulamalar için hata ayıklamayı kolaylaştırmak Visual Studio hata ayıklama ortamı tarafından Office. Word Office gibi bir uygulama Excel, bu arabirimi Visual Studio'den edinebilir ve ardından hata ayıklama oturumu sırasında belirli noktalarda arabirimde yöntemleri çağıran bir uygulamadır.

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
 Aşağıdaki tabloda IWefDebuggingSupport arabiriminin tanımladığı yöntemler listeleniyor.

|Ad|Açıklama|
|----------|-----------------|
|[GetAutoInsertExtensions yöntemi](../vsto/getautoinsertextensions-method.md)|Hata ayıklama sırasında otomatik Office uygulamalar hakkında bilgi alır.|
|[SetWefProcessId yöntemi](../vsto/setwefprocessid-method.md)|Web Uzantıları Çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısını sağlar.|
