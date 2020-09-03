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
ms.openlocfilehash: 960ebb94cf03ef293011645e732a0f0379d0fd47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852242"
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
|**Ön ek**|Zorunlu `Boolean` parametre.<br /><br /> İse `true` , **değer** parametresinin değerini, **ad** parametresiyle belirtilen ortam değişkeni değerinden önce birleştirir ve sonra sonucu ortam değişkenine atar. İse `false` , ortam değişkenine yalnızca **Value** parametresinin değerini atar.|  
|**Hedef**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir ortam değişkeninin depolandığı konumu belirtir. " `User` " Veya " `Machine` " belirtin.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "EnvironmentVariableTarget numaralandırması" konusuna bakın.|  
|**Değer**|İsteğe bağlı **dize** parametresi.<br /><br /> **Name** parametresiyle belirtilen ortam değişkenine atanan değer. **Değer** boşsa ve değişken varsa, değişken silinir. Değişken yoksa, işlem gerçekleştirilemediği halde bir hata oluşmaz.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesinde "Environment:: SetEnvironmentVariable yöntemi" başlığına bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
