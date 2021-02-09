---
title: SetEnv Görevi | Microsoft Docs
description: MSBuild 'in belirtilen bir ortam değişkeninin değerini ayarlamak veya silmek için SetEnv görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76fc0d0dafac542ffde8656c643ec01b7ce23a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861679"
---
# <a name="setenv-task"></a>SetEnv görevi

Belirtilen ortam değişkeninin değerini ayarlar veya siler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **SetEnv** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ad**|Gerekli **dize** parametresi.<br /><br /> Ortam değişkeninin adı.|
|**OutputEnvironmentVariable**|İsteğe bağlı **dize** çıkış parametresi.<br /><br /> **Ad** parametresiyle belirtilen ortam değişkenine atanan değeri içerir.|
|**Ön ek**|Zorunlu `Boolean` parametre.<br /><br /> İse `true` , **değer** parametresinin değerini, **ad** parametresiyle belirtilen ortam değişkeni değerinden önce birleştirir ve sonra sonucu ortam değişkenine atar. İse `false` , ortam değişkenine yalnızca **Value** parametresinin değerini atar.|
|**Hedef**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir ortam değişkeninin depolandığı konumu belirtir. "Kullanıcı" veya "makine" belirtin.<br /><br /> Daha fazla bilgi için bkz. [EnvironmentVariableTarget numaralandırması](xref:System.EnvironmentVariableTarget).|
|**Değer**|İsteğe bağlı **dize** parametresi.<br /><br /> **Name** parametresiyle belirtilen ortam değişkenine atanan değer. **Değer** boşsa ve değişken varsa, değişken silinir. Değişken yoksa, işlem gerçekleştirilemediği halde bir hata oluşmaz.<br /><br /> Daha fazla bilgi için bkz. [Environment:: SetEnvironmentVariable yöntemi](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
