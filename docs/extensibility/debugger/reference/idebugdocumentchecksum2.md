---
title: IDebugDocumentChecksum2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731901"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Hata ayıklama belgesi için bir denetim ummasını temsil eder ve denetimleri bileşenler arasında geçirmeyi sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu [arabirim, IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini ortaya çıkaran herhangi bir bileşen tarafından uygulanabilir. Ancak, bir sembol dosyasına (*.pdb) katıştırılmış checksum'un IDE'ye geri aktarılabilmeleri ve kaynak bulurken kullanılabilmelerini sağlamak için hata ayıklama motorları tarafından esas olarak uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugDocumentChecksum2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Kullanılacak maksimum bayt sayısı verilen belge denetimini ve algoritma tanımlayıcısını alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
