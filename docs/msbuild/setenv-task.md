---
title: SetEnv görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5df538e7eb86a20dfc06e6e6558bded577ba3d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632387"
---
# <a name="setenv-task"></a>SetEnv görev

Belirli bir ortam değişkeninin değerini ayarlar veya siler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki **tabloda SetEnv** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Adı**|Gerekli **String** parametresi.<br /><br /> Bir ortam değişkeninin adı.|
|**ÇıktıÇevreDeğişken**|İsteğe bağlı **String** çıkış parametresi.<br /><br /> **Ad** parametresi tarafından belirtilen ortam değişkenine atanan değeri içerir.|
|**Ön ek**|Zorunlu `Boolean` parametre.<br /><br /> , `true` **Ad** parametresi tarafından belirtilen ortam değişkeninin değerinden önce **Değer** parametresinin değerini birleştirir ve sonucu çevre değişkenine atar. Eğer `false`, yalnızca **Değer** parametresinin değerini ortam değişkenine atar.|
|**Hedef**|İsteğe bağlı **String** parametresi.<br /><br /> Bir ortam değişkeninin depolandığı konumu belirtir. "Kullanıcı" veya "Makine" belirtin.<br /><br /> Daha fazla bilgi için [Bkz. EnvironmentVariableTarget Numaralandırma.](xref:System.EnvironmentVariableTarget)|
|**Değer**|İsteğe bağlı **String** parametresi.<br /><br /> **Ad** parametresi tarafından belirtilen ortam değişkenine atanan değer. **Değer** boşsa ve değişken varsa, değişken silinir. Değişken yoksa, işlem gerçekleştirilemese bile hata oluşmaz.<br /><br /> Daha fazla bilgi için [bkz: Çevre::SetEnvironmentVariable Method](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
