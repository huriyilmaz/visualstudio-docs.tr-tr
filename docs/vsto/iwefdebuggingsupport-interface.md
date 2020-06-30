---
title: IWefDebuggingSupport arabirimi
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544735"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport arabirimi
  Office uygulamalarında hata ayıklamayı kolaylaştırmak için Visual Studio gibi bir hata ayıklama ortamı tarafından uygulanır. Word veya Excel gibi Office uygulaması, bu arabirimi Visual Studio 'dan alır ve ardından hata ayıklama oturumu sırasında belirli noktalarda arabirimdeki yöntemleri çağırır.

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

|Name|Description|
|----------|-----------------|
|[Getautoınserbir yöntemi](../vsto/getautoinsertextensions-method.md)|Hata ayıklama sırasında otomatik olarak eklenecek Office uygulamaları hakkında bilgi alır.|
|[SetWefProcessId yöntemi](../vsto/setwefprocessid-method.md)|Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısı sağlar.|
