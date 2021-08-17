---
title: VCMessage görevi | Microsoft Docs
description: MSBuild, bir C++ projeleri için derleme sırasında uyarı ve hata iletilerini günlüğe kaydetmek için vcmessage görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ad0be84534352316aabf0272074f7e8c2c41ff6f7d4c6b313933c3b23e9e7a5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397208"
---
# <a name="vcmessage-task"></a>VCMessage görevi

Bir derleme sırasında uyarı ve hata iletilerini günlüğe kaydeder.

## <a name="remarks"></a>Açıklamalar

 bu görev, C++ projeleri için MSBuild uygulamaya yardımcı olur ve kullanıcı tarafından çağrılması amaçlanmamıştır. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **VCMessage** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Bağımsız değişkenler**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek iletilerin noktalı virgülle ayrılmış listesi.|
|**Kod**|Gerekli **dize** parametresi.<br /><br /> İletiyi niteleyen bir hata numarası.|
|**Tür**|İsteğe bağlı **dize** parametresi.<br /><br /> Görüntülenecek ileti türünü belirtir. Bir uyarı iletisi oluşturmak için "uyarı" ya da bir hata iletisi oluşturmak için "hata" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
