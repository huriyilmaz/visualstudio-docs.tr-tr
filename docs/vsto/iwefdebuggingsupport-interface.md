---
title: IWefDebuggingSupport arabirimi
description: Microsoft Office uygulamalarında hata ayıklamayı kolaylaştırmak için Visual Studio gibi bir hata ayıklama ortamını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525327"
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

|Ad|Açıklama|
|----------|-----------------|
|[Getautoınserbir yöntemi](../vsto/getautoinsertextensions-method.md)|Hata ayıklama sırasında otomatik olarak eklenecek Office uygulamaları hakkında bilgi alır.|
|[SetWefProcessId yöntemi](../vsto/setwefprocessid-method.md)|Web uzantıları çerçevesi (WEF) içeriğini çalıştıracak işlem tanımlayıcısı sağlar.|
