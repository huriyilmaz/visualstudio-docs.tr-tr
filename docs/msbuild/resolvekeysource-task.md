---
title: ResolveKeySource Görev | Microsoft Docs
description: Güçlü ad anahtarı kaynağını belirleyen MSBuild ResolveKeySource görevinin parametreleri hakkında bilgi edinebilirsiniz.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 91e2c10ca95004154bf91e11906d440b57e4ca72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108388"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource görevi

Güçlü ad anahtar kaynağını belirler.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `ResolveKeySource` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|İsteğe `Int32` bağlı parametre.<br /><br /> Geri sayım iletiyi görüntülemek için saniye olarak süre miktarını alır veya ayarlar.|
|`AutoClosePasswordPromptTimeout`|İsteğe `Int32` bağlı parametre.<br /><br /> Parola istemi iletişim kutusunu kapatmadan önce bekleme süresi (saniye olarak) alır veya ayarlar.|
|`CertificateFile`|İsteğe `String` bağlı parametre.<br /><br /> Sertifika dosyasının yolunu alır veya ayarlar.|
|`CertificateThumbprint`|İsteğe `String` bağlı parametre.<br /><br /> Sertifika parmak izini alır veya ayarlar.|
|`KeyFile`|İsteğe `String` bağlı parametre.<br /><br /> Anahtar dosyasının yolunu alır veya ayarlar.|
|`ResolvedKeyContainer`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çözümlenen anahtar kapsayıcısı alır veya ayarlar.|
|`ResolvedKeyFile`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çözümlenen anahtar dosyasını alır veya ayarlar.|
|`ResolvedThumbprint`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çözümlenen sertifika parmak izini alır veya ayarlar.|
|`ShowImportDialogDespitePreviousFailures`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` önceki hatalara rağmen içeri aktarma iletişim kutusunu gösterir.|
|`SuppressAutoClosePasswordPrompt`|İsteğe `Boolean` bağlı parametre.<br /><br /> Parola istemi iletişim kutusunun otomatik olarak kapanması gerekip gerek olmadığını belirten bir Boole değeri alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
