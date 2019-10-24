---
title: SetEnv Görevi | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ec3170c9662cd9ef67521addfdf0d0095bd23b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747207"
---
# <a name="setenv-task"></a>SetEnv Görevi
Belirtilen ortam değişkeninin değerini ayarlar veya siler.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda **SetEnv** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ad**|Gerekli **dize** parametresi.<br /><br /> Ortam değişkeninin adı.|
|**OutputEnvironmentVariable**|İsteğe bağlı **dize** çıkış parametresi.<br /><br /> **Ad** parametresiyle belirtilen ortam değişkenine atanan değeri içerir.|
|**Koy**|Zorunlu `Boolean` parametresi.<br /><br /> @No__t_0, **değer** parametresinin değerini, **ad** parametresiyle belirtilen ortam değişkeni değerinden önce birleştirir ve sonra sonucu ortam değişkenine atar. @No__t_0, ortam değişkenine yalnızca **Value** parametresinin değerini atar.|
|**Hedef**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir ortam değişkeninin depolandığı konumu belirtir. "Kullanıcı" veya "makine" belirtin.<br /><br /> Daha fazla bilgi için bkz. [EnvironmentVariableTarget numaralandırması](xref:System.EnvironmentVariableTarget).|
|**Değer**|İsteğe bağlı **dize** parametresi.<br /><br /> **Name** parametresiyle belirtilen ortam değişkenine atanan değer. **Değer** boşsa ve değişken varsa, değişken silinir. Değişken yoksa, işlem gerçekleştirilemediği halde bir hata oluşmaz.<br /><br /> Daha fazla bilgi için bkz. [Environment:: SetEnvironmentVariable yöntemi](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)