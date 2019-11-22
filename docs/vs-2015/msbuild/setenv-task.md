---
title: SetEnv Görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc9b15efb8fca12382fae94912d22c39b96bd4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295966"
---
# <a name="setenv-task"></a>SetEnv Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen ortam değişkeninin değerini ayarlar veya siler.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **SetEnv** görevinin parametreleri açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**Ad**|Gerekli **dize** parametresi.<br /><br /> Ortam değişkeninin adı.|  
|**OutputEnvironmentVariable**|İsteğe bağlı **dize** çıkış parametresi.<br /><br /> **Ad** parametresiyle belirtilen ortam değişkenine atanan değeri içerir.|  
|**Koy**|Zorunlu `Boolean` parametresi.<br /><br /> `true`, **değer** parametresinin değerini, **ad** parametresiyle belirtilen ortam değişkeni değerinden önce birleştirir ve sonra sonucu ortam değişkenine atar. `false`, ortam değişkenine yalnızca **Value** parametresinin değerini atar.|  
|**Hedef**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir ortam değişkeninin depolandığı konumu belirtir. "`User`" veya "`Machine`" belirtin.<br /><br /> Daha fazla bilgi için [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) Web sitesindeki "EnvironmentVariableTarget numaralandırması" konusuna bakın.|  
|**Değer**|İsteğe bağlı **dize** parametresi.<br /><br /> **Name** parametresiyle belirtilen ortam değişkenine atanan değer. **Değer** boşsa ve değişken varsa, değişken silinir. Değişken yoksa, işlem gerçekleştirilemediği halde bir hata oluşmaz.<br /><br /> Daha fazla bilgi için [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) Web sitesinde "Environment:: SetEnvironmentVariable yöntemi" başlığına bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)
