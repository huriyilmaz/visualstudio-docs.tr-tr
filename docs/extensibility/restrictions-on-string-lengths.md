---
title: Dize uzunlukları için kısıtlamalar | Microsoft Docs
description: Kaynak denetimi eklentisi API 'SI tarafından uygulanan çeşitli işlevler tarafından kullanılan dizelerin uzunluklarının sınırları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5412e930937d029f803f5c6c2b4ddc9d396d9485
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715528"
---
# <a name="restrictions-on-string-lengths"></a>Dize uzunlukları kısıtlamaları
Kaynak denetimi eklentisi API 'SI, çeşitli işlevlerde kullanılan dizelerin uzunluklarının sınırlarını sınırlar.

## <a name="string-length-values"></a>Dize uzunluğu değerleri

|Sabit|Değer|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Uzunluk Sonlandırıcı içermez `null` . "_LEN" yerine "_SIZE" sonekine sahip diğer sabitler, Sonlandırıcı için alan içerir `null` .

|Sabit|Değer|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
