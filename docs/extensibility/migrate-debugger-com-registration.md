---
title: 64 bit hata ayıklayıcı COM sınıf kaydını geçir | Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62433701"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 bit hata ayıklayıcı COM sınıfı kaydını geçirme

RegAsm, regsvr32 veya doğrudan kayıt defterine (uzaktan hata ayıklayıcı) *msvsmon.exe* yüklenen HKEY_CLASSES_ROOT com sınıflarını kaydeden hata ayıklayıcı uzantıları için, artık bu kaydı, HKEY_CLASSES_ROOT yazmaya gerek kalmadan msvsmon 'ye sağlamak mümkündür. Bu, eski .NET Debugger ifadesi değerlendiricileri veya *msvsmon.exe* işleminde yüklenecek şekilde yapılandırılmış hata ayıklama altyapılarını etkiler.

## <a name="msvsmon-comclass-def"></a>Msvsmon-ComClass-def

Bu tekniği kullanmak için * *.msvsmon-comclass-def.json* msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64 *) yanına bir dosyaya.msvsmon-comclass-def.jsekleyin.

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
