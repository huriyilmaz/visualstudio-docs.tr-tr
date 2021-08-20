---
title: Dize uzunlukları için kısıtlamalar | Microsoft Docs
description: Kaynak denetimi eklentisi API 'SI tarafından uygulanan çeşitli işlevler tarafından kullanılan dizelerin uzunluklarının sınırları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5322ff52097a55994cec569597841202677d7dfd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086397"
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
