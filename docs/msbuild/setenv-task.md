---
title: SetEnv görev | Microsoft Docs
description: Belirli bir MSBuild değerini ayarlamak veya silmek için SetEnv görevini nasıl kullandığını öğrenin.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 9de76654cb4fb0a2a8ab906a5a6bdc4223bfcbf07d6cc257cc7e50458311cf14
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427554"
---
# <a name="setenv-task"></a>SetEnv görevi

Belirtilen ortam değişkeninin değerini ayarlar veya siler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **SetEnv** görevinin parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ad**|Gerekli **Dize** parametresi.<br /><br /> Ortam değişkeninin adı.|
|**OutputEnvironmentVariable**|İsteğe **bağlı Dize** çıkış parametresi.<br /><br /> **Name** parametresi tarafından belirtilen ortam değişkenine atanan değeri içerir.|
|**Ön ek**|Zorunlu `Boolean` parametre.<br /><br /> ise, Name parametresi tarafından belirtilen ortam değişkeninin değerinden önce Value parametresinin değerini birler ve ardından sonucu ortam `true` değişkenine atar.   ise, `false` yalnızca Value parametresinin **değerini ortam** değişkenine atar.|
|**Hedef**|İsteğe **bağlı Dize** parametresi.<br /><br /> Ortam değişkeninin depolandığı konumu belirtir. "Kullanıcı" veya "Makine" belirtin.<br /><br /> Daha fazla bilgi için [bkz. EnvironmentVariableTarget Sabit Sabit Bilgisi.](xref:System.EnvironmentVariableTarget)|
|**Değer**|İsteğe **bağlı Dize** parametresi.<br /><br /> **Name** parametresi tarafından belirtilen ortam değişkenine atanan değer. **Değer boşsa** ve değişken mevcutsa değişken silinir. Değişken yoksa, işlem gerçekleştirilese bile hata oluşmaz.<br /><br /> Daha fazla bilgi için [bkz. Environment::SetEnvironmentVariable Metodu.](xref:System.Environment.SetEnvironmentVariable%2A)|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
