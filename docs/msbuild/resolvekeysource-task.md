---
title: ResolveKeySource görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09b3917e1c67014a780d11e2ae9a944844e63e25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595195"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource görevi
Tanımlayıcı ad anahtar kaynağını belirler.

## <a name="task-parameters"></a>Görev parametreleri
 Aşağıdaki tabloda `ResolveKeySource` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|İsteğe bağlı `Int32` parametresi.<br /><br /> Sayıyı aşağı doğru göstermek için geçmesi gereken süreyi saniye cinsinden alır veya ayarlar.|
|`AutoClosePasswordPromptTimeout`|İsteğe bağlı `Int32` parametresi.<br /><br /> Parola istemi iletişim kutusunu kapatmadan önce beklenecek süreyi saniye cinsinden alır veya ayarlar.|
|`CertificateFile`|İsteğe bağlı `String` parametresi.<br /><br /> Sertifika dosyasının yolunu alır veya ayarlar.|
|`CertificateThumbprint`|İsteğe bağlı `String` parametresi.<br /><br /> Sertifika parmak izini alır veya ayarlar.|
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Anahtar dosyasının yolunu alır veya ayarlar.|
|`ResolvedKeyContainer`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen anahtar kapsayıcısını alır veya ayarlar.|
|`ResolvedKeyFile`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen anahtar dosyasını alır veya ayarlar.|
|`ResolvedThumbprint`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çözümlenen sertifika parmak izini alır veya ayarlar.|
|`ShowImportDialogDespitePreviousFailures`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, önceki hatalara karşın içeri aktarma iletişim kutusunu gösterir.|
|`SuppressAutoClosePasswordPrompt`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Parola istem iletişim kutusunun otomatik olarak kapanmayacağını belirten bir Boole değeri alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
