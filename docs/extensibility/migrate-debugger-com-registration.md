---
title: 64 bit hata ayıklayıcı COM sınıf kaydını geçir | Microsoft Docs
description: HKEY_CLASSES_ROOT yazmadan hata ayıklayıcı uzantıları için COM sınıflarını msvsmon 'e kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886723"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 bit hata ayıklayıcı COM sınıfı kaydını geçirme

RegAsm, regsvr32 veya doğrudan kayıt defterine (uzaktan hata ayıklayıcı) *msvsmon.exe* yüklenen HKEY_CLASSES_ROOT com sınıflarını kaydeden hata ayıklayıcı uzantıları için, artık bu kaydı, HKEY_CLASSES_ROOT yazmaya gerek kalmadan msvsmon 'ye sağlamak mümkündür. Bu, eski .NET Debugger ifadesi değerlendiricileri veya *msvsmon.exe* işleminde yüklenecek şekilde yapılandırılmış hata ayıklama altyapılarını etkiler.

## <a name="msvsmon-comclass-def"></a>Msvsmon-ComClass-def

Bu tekniği kullanmak için *msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64 *) yanına bir dosyaya.msvsmon-comclass-def.jsekleyin.

Aşağıda, bir yönetilen ve bir yerel sınıf kaydeden örnek bir msvsmon-ComClass-def dosyası verilmiştir:

Dosya adı: *MyCompany.MyExample.msvsmon-comclass-def.json*

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
