---
title: 64 bit hata ayıklayıcı COM sınıf kaydını geçirme| Microsoft Docs
description: Hata ayıklayıcısı uzantıları için, hata ayıklayıcıya yazmadan msvsmon'a COM sınıflarını HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- greggm
ms.openlocfilehash: a9b569f78720d59bf6321ff972bd7f2668ca6729
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152126"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 bit hata ayıklayıcı COM sınıf kaydını geçirme

regasm, regsvr32 kullanarak veya doğrudan kayıt defterine yazarak HKEY_CLASSES_ROOT'de COM sınıflarını kaydeden ve *msvsmon.exe'ye* (uzaktan hata ayıklayıcısı) yüklenen hata ayıklayıcı uzantıları için, artık bu kaydı HKEY_CLASSES_ROOT'ye yazmaya gerek kalmadan msvsmon'a sağlamak mümkündür. Bu, eski .NET hata ayıklayıcısı ifade değerlendiricilerini veya bu işlemde yükleyebilecek şekilde yapılandırılmış *hata ayıklamamsvsmon.exe* etkiler.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Bu tekniği kullanmak için **msvsmon'.msvsmon-comclass-def.js* (InstallDir:* \Common7\IDE\Remote Debugger\x64*) yanına bir dosya ekleyin.

Bir yönetilen ve bir yerel sınıfı kaydeden örnek bir msvsmon-comclass-def dosyası şöyledir:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.jsaçık*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
