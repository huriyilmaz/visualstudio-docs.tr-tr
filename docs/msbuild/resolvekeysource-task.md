---
title: ResolveKeySource görevi | Microsoft Docs
description: Tanımlayıcı ad anahtar kaynağını belirleyen MSBuild ResolveKeySource görevinin parametreleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c06e012f84f1f18805ca458289c023679d0593d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912550"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource görevi

Tanımlayıcı ad anahtar kaynağını belirler.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveKeySource` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|İsteğe bağlı `Int32` parametre.<br /><br /> Sayıyı aşağı doğru göstermek için geçmesi gereken süreyi saniye cinsinden alır veya ayarlar.|
|`AutoClosePasswordPromptTimeout`|İsteğe bağlı `Int32` parametre.<br /><br /> Parola istemi iletişim kutusunu kapatmadan önce beklenecek süreyi saniye cinsinden alır veya ayarlar.|
|`CertificateFile`|İsteğe bağlı `String` parametre.<br /><br /> Sertifika dosyasının yolunu alır veya ayarlar.|
|`CertificateThumbprint`|İsteğe bağlı `String` parametre.<br /><br /> Sertifika parmak izini alır veya ayarlar.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Anahtar dosyasının yolunu alır veya ayarlar.|
|`ResolvedKeyContainer`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen anahtar kapsayıcısını alır veya ayarlar.|
|`ResolvedKeyFile`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen anahtar dosyasını alır veya ayarlar.|
|`ResolvedThumbprint`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen sertifika parmak izini alır veya ayarlar.|
|`ShowImportDialogDespitePreviousFailures`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Önceki hatalara karşın içeri aktarma iletişim kutusunu gösterir.|
|`SuppressAutoClosePasswordPrompt`|İsteğe bağlı `Boolean` parametre.<br /><br /> Parola istem iletişim kutusunun otomatik olarak kapanmayacağını belirten bir Boole değeri alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
