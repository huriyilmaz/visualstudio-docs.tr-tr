---
description: Bir hata ayıklama belgesi için bir sağlama toplamı temsil eder ve bileşenler arasında sağlama toplamı geçişine izin vermez.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3bcd872ed06fac90d48bc773250fd007d3ed1d21e8b4714876d62e038df2f813
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434002"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Bir hata ayıklama belgesi için bir sağlama toplamı temsil eder ve bileşenler arasında sağlama toplamı geçişine izin vermez.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini kullanıma sunan herhangi bir bileşen tarafından uygulanabilir. Ancak, bir sembol dosyasında (*. pdb) gömülü sağlama toplamı IDE 'ye geri geçirilebilir ve bir kaynak bulunurken kullanılmak üzere hata ayıklama motorları tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocumentChecksum2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Belge sağlama toplamını ve algoritma tanımlayıcısını, en fazla kullanılacak bayt sayısını alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
