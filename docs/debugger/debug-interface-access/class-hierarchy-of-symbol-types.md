---
title: Sembol türlerinin sınıf hiyerarşisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed6817c5c01b66143739b2f81899f2b58886d8e8
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462276"
---
# <a name="class-hierarchy-of-symbol-types"></a>Simge Türlerinin Sınıf Hiyerarşisi
Aşağıdaki tablo, sınıf hiyerarşisindeki sembol türlerini açıklar.

## <a name="symbol-types"></a>Sembol türleri

|Sembol türü|Açıklama|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Her bir sınıfı, yapıyı ve birleşimi temsil etmek için kullanılan simge.|
|[Enum (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Numaralandırılmış türlerin simgesi.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|İşaretçi türleri simgesi.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Dizi türleri için sembol.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Taban türleri sembolü|
|[Typedef (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Diğer türlerin adlarını tanıtan simge.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Kullanıcı tanımlı türün (UDT) her temel sınıfı için kullanılan simge.|
|[Arkadaş (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend sınıfları ve arkadaş işlevleri sembolü.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Her benzersiz işlev imzası için simge.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Bir işleve her parametre için sembol.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Sanal tablo boyutu için simge.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Sanal tablo simgesi.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Satıcı tanımlı tür sembolü.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Meta verilerde tanımlanan bir türün sembolü.|
|[Boyut](../../debugger/debug-interface-access/dimension.md)|Dizi boyutları sembolü.|

> [!NOTE]
> Her sembolün, sembol hakkındaki bilgileri ve diğer simgelere başvuruları tutan özellikleri olabilir. Bu özellikler, tek sembol konularında listelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)