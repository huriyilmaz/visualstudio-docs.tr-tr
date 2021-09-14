---
title: Sembol Türlerinin Sınıf Hiyerarşisi | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK'sı için uygulamanın sınıf Visual Studio sembol türlerinin listesini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e46e0f5c9b8b4afc3757875996dfc74bb86df33
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630728"
---
# <a name="class-hierarchy-of-symbol-types"></a>Simge Türlerinin Sınıf Hiyerarşisi
Aşağıdaki tabloda, sınıf hiyerarşisinde sembol türleri açık almaktadır.

## <a name="symbol-types"></a>Sembol Türleri

|Sembol türü|Description|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Her sınıfı, yapıyı ve birleyi temsil etmek için kullanılan sembol.|
|[Enum (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Numaralandı türler için sembol.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|İşaretçi türleri simgesi.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Dizi türleri için sembol.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Temel türler için sembol|
|[Tür Tanımı (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Diğer türler için adlar tanıtan sembol.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Kullanıcı tanımlı bir türün (UDT) her temel sınıfı için kullanılan sembol.|
|[Arkadaş (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Arkadaş sınıfları ve arkadaş işlevleri simgesi.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Her benzersiz işlev imzasının simgesi.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Bir işleve her parametrenin simgesi.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Sanal tablonun boyutunun simgesi.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Sanal tablo simgesi.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Satıcı tanımlı türün simgesi.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Meta verilerde tanımlanan bir türün simgesi.|
|[Boyut](../../debugger/debug-interface-access/dimension.md)|Dizi boyutları için sembol.|

> [!NOTE]
> Her simge, simgeyle ilgili bilgileri ve diğer sembollere yapılan başvuruları içeren özelliklere sahip olabilir. Bu özellikler tek tek sembol konu başlıklarında listelenir.

## <a name="see-also"></a>Ayrıca bkz.
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)