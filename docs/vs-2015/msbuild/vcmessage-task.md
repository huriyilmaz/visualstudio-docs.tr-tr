---
title: VCMessage görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 508d1fe33046f6051c9c5c1b8e54036e78ae7d2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193347"
---
# <a name="vcmessage-task"></a>VCMessage Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir derleme sırasında uyarı ve hata iletilerini günlüğe kaydeder.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, Visual C++ için MSBuild uygulamasına yardımcı olur ve Kullanıcı tarafından çağrılması amaçlanmamıştır. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **VCMessage** görevinin parametreleri açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**Arguments**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek iletilerin noktalı virgülle ayrılmış listesi.|  
|**Kod**|Gerekli **dize** parametresi.<br /><br /> İletiyi niteleyen bir hata numarası.|  
|**Tür**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek ileti türünü belirtir. `"Warning"`Uyarı iletisi yayma veya `"Error"` hata iletisi yayma seçeneklerinden birini belirtin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
