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
ms.openlocfilehash: 66b1bf1eb222d70c18bfb94c65dddd2903864c68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591118"
---
# <a name="vcmessage-task"></a>VCMessage görevi
Bir derleme sırasında uyarı ve hata iletilerini günlüğe kaydeder.

## <a name="remarks"></a>Açıklamalar
 Bu görev, projeler için C++ MSBuild uygulamaya yardımcı olur ve Kullanıcı tarafından çağrılması amaçlanmamıştır. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda **VCMessage** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Bağımsız Değişkenler**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek iletilerin noktalı virgülle ayrılmış listesi.|
|**Kod**|Gerekli **dize** parametresi.<br /><br /> İletiyi niteleyen bir hata numarası.|
|**Türü**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek ileti türünü belirtir. Bir uyarı iletisi oluşturmak için "uyarı" ya da bir hata iletisi oluşturmak için "hata" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
