---
title: VCMessage görevi | Microsoft Docs
ms.date: 06/27/2018
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
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631217"
---
# <a name="vcmessage-task"></a>VCMessage görevi

Bir derleme sırasında uyarı ve hata iletilerini günlüğe kaydeder.

## <a name="remarks"></a>Açıklamalar

 Bu görev, C++ projeleri için MSBuild uygulamasına yardımcı olur ve Kullanıcı tarafından çağrılması amaçlanmamıştır. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **VCMessage** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Arguments**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek iletilerin noktalı virgülle ayrılmış listesi.|
|**Kod**|Gerekli **dize** parametresi.<br /><br /> İletiyi niteleyen bir hata numarası.|
|**Tür**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek ileti türünü belirtir. Bir uyarı iletisi oluşturmak için "uyarı" ya da bir hata iletisi oluşturmak için "hata" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
