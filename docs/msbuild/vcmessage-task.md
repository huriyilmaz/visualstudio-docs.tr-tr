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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be4f963a5944882f14118be54e498fd4712c2e46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747180"
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
|**Türüyle**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek ileti türünü belirtir. Bir uyarı iletisi oluşturmak için "uyarı" ya da bir hata iletisi oluşturmak için "hata" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)